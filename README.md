
# Zhaopin.com spider 


To aviod being jobless after graduation, I should consider what kinds of jobs I'm going to do and which company I will work for. It seems that Hangzhou is a good choice with comfortable environment and comparatively affordable house price, and banks provide higher salary.




## Getting Started



I entered "Hangzhou" and chose "bank" on the https://www.zhaopin.com/, then I got my inital webpage http://sou.zhaopin.com/jobs/searchresult.ashx?in=300500&jl=%E6%9D%AD%E5%B7%9E&sm=0&el=4&we=-1&isfilter=1&bj=2071000&sg=e8078f0e56ec4d41a7ed3315fd2a2dbb&p=1




### Prerequisites


Python 3, bs4, codecs, pandas, ordereddict, requests, etree
Software: Openrefine


### Installing

```
import requests
from bs4 import BeautifulSoup
import csv
import codecs
import pandas as pd
from collections import OrderedDict
from lxml import etree
```

And we start.

```
# To get basic information such as positions, companies and salaries.
zwmcs = []
gsmcs = []
zwyxs = []
def get_basic_information(urls):
    for url in urls:
        r = requests.get(url)
        page = BeautifulSoup(r.text, "lxml")
        for i in page.find_all('td', class_="zwmc"):
            zwmc = i.text.strip()
            zwmcs.append(zwmc)
        for i in page.find_all('td', class_="gsmc"):
            gsmc = i.text.strip()
            gsmcs.append(gsmc)
        for i in page.find_all('td', class_="zwyx"):
            zwyx = i.text.strip()
            zwyxs.append(zwyx)
    # Then write them in a csv. OrderedDict is used to make the data ordered.
    jobs = OrderedDict()
    jobs['职位名称'] = zwmcs
    jobs['公司名称'] = gsmcs
    jobs['职位月薪'] = zwyxs
    header = jobs.keys()
    rows= pd.DataFrame(jobs).to_dict('records')

#I wrote gbk because the page was in Chinese. UTF-8 didn't work.
    with codecs.open('zhilian.csv', 'w', 'gbk') as f: 
        f.write(','.join(header))
        f.write('\n')
        for data in rows:
            f.write(",".join(str(data[h]) for h in header))
            f.write('\n')
    return jobs
    
# Run the function with the urls.
urls = ['http://sou.zhaopin.com/jobs/searchresult.ashx?in=300500&jl=%E6%9D%AD%E5%B7%9E&sm=0&el=4&we=-1&isfilter=1&bj=2071000&sg=e8078f0e56ec4d41a7ed3315fd2a2dbb&p={}'.format(str(i))for i in range(1,3)] 
# there were 2 pages so I wrote a list generation to get the full information.
get_basic_information(urls)
```

And I found I missed an important information-work experience demanded which is in the next page, therefore I need to get all of the links first.


```
def get_links(urls):
    links = []
    for url in urls:
        r = requests.get(url)
        page = etree.HTML(r.text)
        for i in page.xpath('//td[@class="zwmc"]//a/@href'):#I used xpath to get the href.
            links.append(i)
    return links
urls = ['http://sou.zhaopin.com/jobs/searchresult.ashx?in=300500&jl=%E6%9D%AD%E5%B7%9E&sm=0&el=4&we=-1&isfilter=1&bj=2071000&sg=e8078f0e56ec4d41a7ed3315fd2a2dbb&p={}'.format(str(i))for i in range(1,3)]
# Run the function.
get_links(urls)
```
Then I need to scrape the work experience tag.

```
gzjys = []
for i in get_links(urls):
    r = requests.get(i)
    page = etree.HTML(r.text)
    for i in page.xpath('//div[@class="terminalpage-left"]//ul[@class="terminal-ul clearfix"]/li[5]//strong'):
        gzjy = i.text.strip()
        gzjys.append(gzjy)
print(gzjys)
```
Wow seems perfect. But...wait a moment, there were only 97 items in my gzjys list, while there were 100 links. 
The problem was 3 of the links were linked to another kind of webpages which were different from others. Then I just found them and inserted the work experience demands into gzjys list. 


```
gzjys.insert(15, '不限')
gzjys.insert(15, '不限')
gzjys.insert(15, '不限')
```
Write all of those lists in a csv.


```
jobs = OrderedDict()
jobs['职位名称'] = zwmcs
jobs['公司名称'] = gsmcs
jobs['职位月薪'] = zwyxs
jobs['工作经验'] = gzjys
header = jobs.keys()
rows= pd.DataFrame(jobs).to_dict('records')

with codecs.open('zhilian.csv', 'w', 'gbk') as f:
    f.write(','.join(header))
    f.write('\n')
    for data in rows:
        f.write(",".join(str(data[h]) for h in header))
        f.write('\n')
```
Then I got a csv, but the data demanded cleaning. I used Openrefine to delete all items without clear salaries like "Salary Negotiable（面议）" which wouldn't help my decision.(p.s.Openrefine is really fantastic!!!)

Next step, analyze the data with pandas.

```
df = pd.read_csv('zhilian-csv.csv')
df['公司名称'].value_counts()
```

Results(first 5):

```
招商银行股份有限公司杭州分行            10
浙江民泰商业银行股份有限公司             7
北京恒天明泽基金销售有限公司杭州分公司        6
浙江稠州商业银行股份有限公司             5
中国光大银行杭州分行                 5
```
Wow, it seems that CMB China needs more new staff.
In order to compare the salaris, I need an average number of ranges.

```
def split_salary(i):
    try:
        splt = i.split('-',1)
        first = float(splt[0])
        second = float(splt[1])
        return int((first+second)/2)
    except:
        return float(i)
df['月薪平均'] = df['职位月薪'].apply(split_salary)
```
By this way, I got a row of average salary.

```
df['月薪平均'].value_counts()

7000      15
12500     13
17500      9
11500      9
9000       8
15000      7
5000       4
6000       3
25000      3
10000      2
6150       2
3000       2
40000      2
14500      1
9500       1
7750       1
125000     1
12000      1
13500      1

df['月薪平均'].mean()
13165.29411764706

df['月薪平均'].median()
11500.0
```
The most common salary is 7k, maybe I can take this number as my minimum demand of payment. The average salary is 13,165, and the median is 11,500, wow, it seems I probably have a good future.
But now I has no experience, so I should look at the items without work experience limit first.

```
df[(df['月薪平均'] > 8000) & ((df['工作经验'] == '不限') | (df['工作经验'] == '无经验'))]

职位名称	公司名称	职位月薪	工作经验	月薪平均
7	投行产品经理	招商银行股份有限公司杭州分行	15001-20000	不限	17500
20	上饶银行2018春季校园招聘.	上饶银行股份有限公司	8001-10000	不限	9000
30	授信审查岗	浙江民泰商业银行股份有限公司	10000-15000	不限	12500
36	存款管理岗	浙江民泰商业银行股份有限公司	10000-15000	不限	12500
37	小微评审岗	杭州联合农村商业银行股份有限公司	8000-15000	不限	11500
42	高级团队长	北京恒天明泽基金销售有限公司杭州分公司	15001-20000	不限	17500
52	催收专员	平安普惠投资咨询有限公司杭州教工路分公司	8000-12000	不限	10000
53	风控专员	平安普惠投资咨询有限公司杭州教工路分公司	8000-12000	不限	10000
59	客服 非销售	平安普惠投资咨询有限公司杭州教工路分公司	7000-12000	不限	9500
60	2018届春季校园招聘（杭州分行）	江苏银行股份有限公司杭州分行	10001-15000	无经验	12500
66	诚招银行信贷专员（双休）	杭州银雁金融配套服务有限公司金华分公司	8001-10000	不限	9000
```
Wow, Jiangsu Bank gives graduates 12,500 per month! Let's see how much this company gives other experienced position.

```
df[df['公司名称'].str.contains('江苏银行')]

	职位名称	公司名称	职位月薪	工作经验	月薪平均
48	财私顾问（零售业务部财富中心）	江苏银行股份有限公司杭州分行	10001-15000	3-5年	12500
60	2018届春季校园招聘（杭州分行）	江苏银行股份有限公司杭州分行	10001-15000	无经验	12500
69	支行业务发展部经理或副经理	江苏银行股份有限公司杭州分行	10000-20000	3-5年	15000
```
Emmmm...maybe I should compare the salaries in other banks for those who have 3-5 years'experience.

```
df[df['工作经验'] == '3-5年'].sort_values(by='月薪平均')

职位名称	公司名称	职位月薪	工作经验	月薪平均
64	分支机构综合管理部综合管理岗	金华银行股份有限公司杭州分行	6001-8000	3-5年	7000
13	银行渠道经理（可以不考勤）	杭州惠超房地产代理有限公司	8001-10000	3-5年	9000
40	风险审查岗（尽调）	杭州鑫合汇互联网金融服务有限公司	8001-10000	3-5年	9000
33	风险审查岗（审批）	杭州鑫合汇互联网金融服务有限公司	8001-10000	3-5年	9000
81	项目管理岗	浙江稠州商业银行股份有限公司	8000-15000	3-5年	11500
45	风控法务经理	杭州常裕金融控股集团有限公司	8000-15000	3-5年	11500
84	信贷/小贷/企业贷主管	杭州冰川投资管理有限公司	8000-16000	3-5年	12000
48	财私顾问（零售业务部财富中心）	江苏银行股份有限公司杭州分行	10001-15000	3-5年	12500
41	高级理财经理	北京恒天明泽基金销售有限公司杭州分公司	10001-15000	3-5年	12500
82	高级理财经理	北京恒天明泽基金销售有限公司杭州分公司	10001-15000	3-5年	12500
0	公司客户经理（正式）	招商银行股份有限公司杭州分行	10001-15000	3-5年	12500
28	高级理财经理	北京恒天明泽基金销售有限公司杭州分公司	10001-15000	3-5年	12500
14	风控经理	浙江联合中小企业财富管理有限公司	10001-15000	3-5年	12500
6	理财经理	北京恒天明泽基金销售有限公司杭州分公司	10001-15000	3-5年	12500
2	风险经理	招商银行股份有限公司杭州分行	10000-15000	3-5年	12500
56	信用卡主任	杭州冰川投资管理有限公司	9000-18000	3-5年	13500
31	信贷/小贷/企业贷主管	杭州冰川投资管理有限公司	10000-20000	3-5年	15000
38	财富管理岗	浙江民泰商业银行股份有限公司	10000-20000	3-5年	15000
27	信用卡部授信审批岗	浙江民泰商业银行股份有限公司	10000-20000	3-5年	15000
47	支付业务管理岗	浙江民泰商业银行股份有限公司	10000-20000	3-5年	15000
69	支行业务发展部经理或副经理	江苏银行股份有限公司杭州分行	10000-20000	3-5年	15000
32	信贷部业务管理岗	浙江民泰商业银行股份有限公司	10000-20000	3-5年	15000
35	信用卡风险管理岗	浙江民泰商业银行股份有限公司	10000-20000	3-5年	15000
10	投资顾问	招商银行股份有限公司杭州分行	15001-20000	3-5年	17500
5	托管产品经理	招商银行股份有限公司杭州分行	15001-20000	3-5年	17500
68	风险审查（杭州）	杭州鑫合汇互联网金融服务有限公司	15001-20000	3-5年	17500

df[df['工作经验'] == '3-5年'].mean()
月薪平均    13076.923077

df[df['工作经验'] == '3-5年'].median()
月薪平均    12500.0
```
Well, for the other two positions in Jiangsu Bank, the 12,500 one is equal to the median, the 15,000 one is higer than the average and the median. The career development is not bad.
However, I can't just look at good things...So let's see how poor I probably will be.

```
df['月薪平均'].min()
3000

df[df['月薪平均'] == 3000]

职位名称	公司名称	职位月薪	工作经验	月薪平均
18	银行行政助理	招商信诺人寿保险有限公司	2001-4000	1-3年	3000
19	银行行政助理（质检）	招商信诺人寿保险有限公司	2001-4000	不限	3000

df[df['月薪平均'] < 6000]

职位名称	公司名称	职位月薪	工作经验	月薪平均
15	风险督察	交通银行太平洋信用卡中心	4001-6000	不限	5000
18	银行行政助理	招商信诺人寿保险有限公司	2001-4000	1-3年	3000
19	银行行政助理（质检）	招商信诺人寿保险有限公司	2001-4000	不限	3000
49	信用分析师	杭州联合资信评估咨询有限公司	4001-6000	1-3年	5000
70	兴业银行信用卡行政助理	兴业银行杭州分行	4001-6000	不限	5000
74	客户经理	兴业银行股份有限公司杭州清泰支行	4001-6000	1-3年	5000

df[df['职位名称'].str.contains('行政')]

职位名称	公司名称	职位月薪	工作经验	月薪平均
18	银行行政助理	招商信诺人寿保险有限公司	2001-4000	1-3年	3000
19	银行行政助理（质检）	招商信诺人寿保险有限公司	2001-4000	不限	3000
70	兴业银行信用卡行政助理	兴业银行杭州分行	4001-6000	不限	5000
```
Wow,3,000? It's even not enough for food and rents...But luckily, for the whole six positions the salaries under 6,000, half of them are administrations, and all of administration jobs offer lower payments. Therefore, if I avoid applying for administration, probably I won't be so poor...

P.S. please look at my file to find the charts.

So that's how I did a research to target a job. The result is Jiangsu Bank, and to avoid administration. I'm going to send my CV, good luck to me...


## Authors

* **Zhang Ruirong** - *Initial work* - [Mackenzie](https://github.com/mackenziezhang)

