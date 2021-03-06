# Welcome to the most expensive city —— Hong Kong Property Analysis
</br>

![  ](https://github.com/mackenziezhang/hkbu-big-data-media/blob/master/Final%20Project/WechatIMG599.jpeg)
</br>
A data analysis of Hong Kong residential property from 2008 to 2017. </br>


</br></br>
### Prerequisites
</br>

```
import pyecharts
//a package which allows you to write echarts in jupyter notebook.
import pandas
import matplotlib
import seaborn 
```

</br></br>
### Installing
</br>
Please see the ipynb for the codes.
</br>
</br>

### Contents
</br>
1.	Median Multiple</br>
2.	Housing price index</br>
3.	Contracts and Consideration</br>
4.	Distribution of domestic households by tenure of accommodation</br>
5.	Completion and size</br>
6.	Unit Price in 3 districts</br>
7.	Land Sale</br>

</br></br>
## Analysis

</br></br>
### Median Multiple
</br>

![  ](https://github.com/mackenziezhang/hkbu-big-data-media/blob/master/Final%20Project/house%20affordability.png)</br>
</br>
Hong Kong is one of the most expensive places to live on Earth because of the imbalance between its population (huge) and and its land (tiny).</br></br>

According to 14th Annual Demographia International Housing Affordability Survey: 2018, Hong Kong is the least affordable market for the 8th consecutive year among 92 major housing markets. </br></br>
Demographia rates middle-income housing affordability using the “Median Multiple,” which is the median house price divided by the median household income. The Median Multiple and other price-to-income multiples are similar, but it removes the impact of low-income households and high-income households.</br></br>

Hong Kong has least affordable housing, with a Median Multiple of 19.4, the least affordable Median Multiple yet recorded. It means one ordinary family must spend more than 19 years on buying one housing without eating, drinking and paying tax. This figure is far more than Sydney (12.9) and Vancouver (12.6), which rank the second and the third place.</br></br>

### Contracts and Consideration 
</br>

![ ](https://github.com/mackenziezhang/hkbu-big-data-media/blob/master/Final%20Project/标记.png)
</br></br>
Housing Price Index

[demo](https://mackenziezhang.github.io/hkbu-big-data-media/Final%20Project/%E5%90%88%E7%BA%A6%E6%95%B0%E7%9B%AE.html)
</br></br>
The two charts show Hong Kong housing price index and the number of contracts signed and consideration during the 10 years until 2018. </br>
</br>
There are several major events happened during 2008 to 2018:</br>
</br>
The first round of US quantitative easing happened in 2008, resulted in the rebound of the housing market. Because Hong Kong dollar pegged with US dollar, so the movement of HK dollar interest rates hinges on the US monetary policy. In November 2008, US government implemented the first round of quantitative easing under the pressure of global financial crisis, driven HK dollar interest rates to historical low levels, so more Hong Kong investors turned to invest house at that time, the rising demand of house caused the increase of housing index and the number of contracts. </br>
</br>
The second round and third round of quantitative  easing  happened in 2010 and 2012 respectively further accelerated the rise of housing price index and the tight demand-supply balance.</br>
</br>
After the continuous increase of price index, contracts and considerations, Hong Kong government implemented several demand control measure to cool down the housing market since 2010. In 2012, government implemented an enhanced special stamp duty, requiring those who sell a property within 3 years after purchase to pay 5%-20% of the sale price; In 2013, the government further imposed 15% stamp duty on all second properties; this series of actions lead to the short decrease of contracts and consideration in 2012 and 2013 respectively.</br>
</br>
In 2014, the government take action to cool the housing market on supply side, that is the promulgation of long term housing strategy in December, which plan to provide more housing and aimed to avert the tight supply-demand of Hong Kong housing market, the policy appears to be working gradually after its implementation, price index and the number of contracts began to decline at the mid of 2015. The interest rate hike of US in December 2015 further cool the housing market down.</br></br>
However, the continuous increasing demand, low interest rate and influx of capital from Mainland China and other countries fuelled the boost of housing price in recent years.  The second chart shows that the contracts signed after 2014 decreased a lot, but the consideration during 2014 to 2018 is basically unchanged compared to the consideration during 2008 and 2013, implies the continued soaring housing prices.</br>
</br>
</br>

### Distribution of domestic households by tenure of accommodation
</br>

[demo](https://mackenziezhang.github.io/hkbu-big-data-media/Final%20Project/percentage.html)
</br>
Housing affordability can be measured in different ways.</br></br>
One way is to judge from the distribution of domestic households by tenure of accommodation.</br></br>
Owners contain residents of both public sector housing and private sector housing.
Tenants comprise of sole tenants and co-tenants.
Others include main tenants, sub-tenants and rent free domestic households. </br></br>
Primarily, it can be seen from the graph that the total amount of households in Hong Kong is growing every year, add up to 0.25 million increase in the past decade, which coincide with the city’s population growth, from 6.96 million in 2008 to 7.41 million in 2017.</br>
</br>
Although the changes of the amount of owner-occupiers can barely be identified from the graph, for the proportion of owner-occupiers, it experienced a drop over the past ten years. In 2008, owners of the domestic households made up 53.5% of the total distribution while in 2017 the number fell by 4% to 49.5%.</br>
</br>
In contrast, it is very obvious that the number of tenant households is in a steady uptrend. It rose from 0.97 million in 2008 to 1.19 million in 2017. Accordingly, the proportion of tenant households increased by more than 4% over the past decade.</br>
</br>
A possible explanation for this general trend is the deteriorating home purchase affordability and the rising difficulty in home ownership in Hong Kong. </br>
</br>

### Completion 
</br>

[demo](https://mackenziezhang.github.io/hkbu-big-data-media/Final%20Project/Completion%202008-2017.html) </br>
</br>
It is clear that the number of newly completed flats with saleable areas of 40 – 69.9 sq m ranks the top, followed by 70 – 99.9 sq m and less than 40 sq m.</br>
</br>
The residential units built by private developers have become increasingly smaller as affordability of prospective buyers decreases from 2008 to 2017. Small flats with less down payment required are particularly attractive to many first-time home buyers, particularly the young ones.</br>
</br>
Reflecting the above trend, the number of newly completed small-sized flats has increased visibly since 2012. The number of newly completed flats with saleable areas of less than 40 sq m was 636 in 2011 and it doubled in 2012. The number reached 6891 in 2017.</br>
</br>
</br>



### Prices of 3 distincts 
</br>

[demo](https://mackenziezhang.github.io/hkbu-big-data-media/Final%20Project/timebar1.html)
</br>
The discrepancy of housing prices among different house types is striking in Hong Kong. This bar chart presents HK’s property price per square meter with several variables. We can see the result in the city’s three main districts with different sizes of houses in the past ten years. </br>

Some useful findings can be generated from the chart.</br>

In general, it demonstrates a trend that the bigger the apartment, the higher the unit price. However, this rule did not apply to New Territories. More interestingly, it even shows a downward trend. Besides the price of small-medium apartment, 40 sq m to 70 sq m, since 2014, the bigger the flat size in New Territories, the lower the unit price. </br>

Our assumption is that the potential customers of large-sized apartment or what we called luxury real estate might not care very much about the unit price for the reason that expensive prices are a symbol of their status. Therefore, rich people may not be interested in purchasing a property in New Territories.</br>

Another finding is that the average property price in New Territories per square meter varies slightly with the increase of housing size, compared with a significant difference in the other two areas. The difference of unit price between large-sized flats and small-sized flats is greatest in Hong Kong Island and smallest in New Territories. </br>

As we all know, the city’s economic hub is located in Hong Kong Island. Kowloon has become increasingly developed and prosperous in recent years. While New Territories is conceived by many as the most remote and undeveloped district. </br>

The conclusion might be the profitability of housing prices of large-sized flats is greater when these flats are closer to the city’s core area; which means that the more prosperous the area, the greater price difference among different size of flats can be found.
</br></br>

### Land Sale
</br>

[demo](https://mackenziezhang.github.io/hkbu-big-data-media/Final%20Project/%E5%8D%96%E5%9C%B0%E6%95%B0%E9%87%8F%E9%87%91%E9%A2%9D1.html)
It’s easy to tell from the chart that in recent years, land sale in New Territories is far more than that in Hong Kong Island and Kowloon. In years of 2009, 2013 and 2015, Hong Kong Island even did not sell any land. In theory, an increase in supply will cause a reduction in the equilibrium price. </br>
Therefore, it might help to explain why house unit price of New Territories is far lower than that of Hong Kong Island and Kowloon.

</br>
</br>
## Built With
</br>
* [Pyecharts](http://pyecharts.org/#/zh-cn/charts) - The packeage allowing you to write echarts in python</br></br>
* [香港政府地政总署](https://www.landsd.gov.hk/)</br></br>
* [香港政府一站通](https://www.data.gov.hk/)</br></br>
* [香港政府土地注册处](https://landreg.gov.hk)</br></br>
* [14th Annual Demographia International Housing Affordability] </br></br>
</br>

## Authors
</br>
* **Zhang Jin** - *Data mining and analysing*</br></br>
* **Zhu Jieyan** - *Data mining and analysing*</br></br>
* **Zhang Ruirong** - *Graphs and analysis*</br></br>
* **Niu Qizhen** - *Graphs and analysis*</br>
</br>
