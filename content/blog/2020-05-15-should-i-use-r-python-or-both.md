---
title: Should I use R, Python, or both?
author: ''
date: '2020-05-15'
slug: should-i-use-r-python-or-both
categories: []
tags: []
description: ''
![](/blog/2020-05-15-should-i-use-r-python-or-both_files/rpython.png){width=350px height=200px}
---



## Python
Python and R are both fascinating on their own. However when put together, these two softwares can become a powerful tool that can solve complex issues.  Below we have an example of how we have used Python to determine all possible k-mers of a particular sequence, which is particularly very useful in the field of bioinformatics.
```{python}
##Python Chunk
my_seq = "ATCATCATG"
def k_mercount(sequence):
    subs = [sequence[x:x+3] for x in range(len(sequence)) if len(sequence[x:x+3]) > 2]
    kmers = {}
    for i in subs:
        if i in kmers:
            kmers[i] += 1
        else:
            kmers[i] = 1
    print(kmers)
k_mercount(my_seq)
```
## R
Now we will demonstrate the use of R on a dataset. We have conducted a MANOVA test on the dataset below in order to determine if any signifance exists been all three numerical variables that were in the SLID dataset across different kinds of language language, which is categorial variable. Note that a significance does exist. In a real investigation, an ANOVA would have been the next step.
```{R}
## R Chunk
library(carData)
Data = SLID
Data = Data[complete.cases(Data),]
man1<-manova(cbind(education,age,wages)~language, data=Data)
summary(man1)

```

## Python and R Together
Finally, we will demonstrate how we can use these two softwares together. Below we have used Python to create a random matrix, than is then mean centered using R. These kinds of of methods are particularly useful in gene expression analysis in bioinformatics as mean centering helps make data somewhat more easier to interpret. I have actually utilized such mean centering techniques in my own research investigations.

```{python}
## Python Chunk
import numpy as np
np.random.seed( 348 )
one_D = np.random.randint(1,10,25)
two_D = one_D.reshape(5,5)
```

```{R}
## R Chunck
library(reticulate)
mean_shift = function(ran_matrix) {
  for (i in 1:nrow(ran_matrix)){
    mean_values = mean(as.numeric(ran_matrix[i,]))
    for (j in 1:ncol(ran_matrix)){
      ran_matrix[i,j] = ran_matrix[i,j] - mean_values}
    
  }
  ran_center = ran_matrix
  return (ran_center)
}
x = as.matrix(py$two_D)
mean_shift(x)
```

## Final Thoughts
After having used both softwares, I feel R is much more useful in regards to statiscal analysis. This maybe due to the fact that I have used R more in general in my research and some of my other classes, giving me much more experience with R. It is worth noting that much of what can be done on Python can also be done on R. However, when these softwares are used together, they can accomplish much more. Since my usage on both of these softwares together is limited, I cannot say much in regards to future applications. Yet, teeing that R can do a lot of what Python does, along with being able to perform statistical analysis in an easier manner, I can say in my opion R is much more useful than Python for my purposes. 