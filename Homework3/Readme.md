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
1. The distribution of salaries among banks in Hangzhou
</br></br>
![Salaries](https://github.com/mackenziezhang/hkbu-big-data-media/raw/master/Homework3/总体薪酬.png)
</br>
Salaries are mainly between 5K-20K, but there's obvious fault around 10K, which is a watershed. Starting salary seems good, and the pay rise is worth looking forward to.  
</br></br>
2. The demand of work experience 
</br></br>
![work experience](https://github.com/mackenziezhang/hkbu-big-data-media/raw/master/Homework3/工作经验.png)
</br>
People with experience of "1-3 years" and "3-5 years" are the most competitive. Although many companies put "unlimited" on the webpage, they still have detailed work experience demands in the descriptions. It can be seent that most banks in Hangzhou prefer experienced employees, there will be high barriers for people who seek for career change. Positions which demand experience of 5-10 years are much less, therefore, 5 years is relatively important, one who tries to entry this industry should plan a long-term strategy. 
</br></br>
3. The relationship between work experience and salaries
</br></br>
![relationship between work experience and salaries](https://github.com/mackenziezhang/hkbu-big-data-media/raw/master/Homework3/不同工作经验薪酬.png)
</br>
The salaries for experience of 5-10 years are much higher than which of 3-5 years, further explaining 5 years is a watershed. Before that, the differences among "1-3 years", "3-5 years" and "unlimited" are not that significant, but surely, as work experience increases, salaries rise.
</br></br>
4. Top 10 positions
</br></br>
![TOP 10](https://github.com/mackenziezhang/hkbu-big-data-media/raw/master/Homework3/WechatIMG565.jpeg)
</br>
Wow, 70% of them demand 5-10 years' experience, and the highest one is almost 10 times of the lowest one. If you work hard in banks for 10 years, you will have a chance to get 1 million per year:) 
</br>
</br></br>


## Authors
</br>
* **Zhang Ruirong** - *Initial work* - [Mackenzie](https://github.com/mackenziezhang)


