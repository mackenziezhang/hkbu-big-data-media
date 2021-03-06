# Homework 3
</br>
A simple analysis of dataset I collected on zhaopin.com(see HW2 zhaopin.spider)
</br>
</br>

### Prerequisites
</br>
Pandas, Matplotlib, seaborn, numpy.
</br></br>

```
import pandas as pd
import matplotlib.pyplot as plt
from matplotlib.font_manager import FontProperties
from matplotlib.ticker import MultipleLocator, FormatStrFormatter  
import seaborn as sns
import csv
import numpy as np
```
</br>
</br>

### Process 
</br>
See the code file.
</br>
</br>

### Analysis 
</br>
</br>
1. The distribution of salaries among banks in Hangzhou
</br></br>

![ ](https://github.com/mackenziezhang/hkbu-big-data-media/blob/master/Homework3/%E6%80%BB%E4%BD%93%E8%96%AA%E9%85%AC.png?raw=true)
</br>
Salaries are mainly between 5K-20K, but there's obvious fault around 10K, which is a watershed. Starting salary seems good, and the pay rise is worth looking forward to.  
</br></br>
2. The demand of work experience 
</br></br>

![ ](https://github.com/mackenziezhang/hkbu-big-data-media/blob/master/Homework3/%E5%B7%A5%E4%BD%9C%E7%BB%8F%E9%AA%8C.png?raw=true)
</br>
People with experience of "1-3 years" and "3-5 years" are the most competitive. Although many companies put "unlimited" on the webpage, they still have detailed work experience demands in the descriptions. It can be seent that most banks in Hangzhou prefer experienced employees, there will be high barriers for people who seek for career change. Positions which demand experience of 5-10 years are much less, therefore, 5 years is relatively important, one who tries to entry this industry should plan a long-term strategy. 
</br></br>
3. The relationship between work experience and salaries
</br></br>

![ ](https://github.com/mackenziezhang/hkbu-big-data-media/blob/master/Homework3/%E4%B8%8D%E5%90%8C%E5%B7%A5%E4%BD%9C%E7%BB%8F%E9%AA%8C%E8%96%AA%E9%85%AC.png?raw=true)
</br>
The salaries for experience of 5-10 years are much higher than which of 3-5 years, further explaining 5 years is a watershed. Before that, the differences among "1-3 years", "3-5 years" and "unlimited" are not that significant, but surely, as work experience increases, salaries rise.
</br></br>
4. Top 10 positions
</br></br>

![ ](https://github.com/mackenziezhang/hkbu-big-data-media/blob/master/Homework3/WechatIMG565.jpeg?raw=true)
</br>
Wow, 70% of them demand 5-10 years' experience, and the highest one is almost 10 times of the lowest one. If you work hard in banks for 10 years, you will have a chance to get 1 million per year:) 
</br>
</br></br>


## Authors
</br>
* **Zhang Ruirong** - *Initial work* - [Mackenzie](https://github.com/mackenziezhang)


