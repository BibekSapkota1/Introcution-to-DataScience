---
title: "T-test"
author: "Bibek Sapkota"
output:
  pdf_document: default
  html_notebook: default
---

task 1: Load built-in sleep data set

```r
sleep
```

```
##    extra group ID
## 1    0.7     1  1
## 2   -1.6     1  2
## 3   -0.2     1  3
## 4   -1.2     1  4
## 5   -0.1     1  5
## 6    3.4     1  6
## 7    3.7     1  7
## 8    0.8     1  8
## 9    0.0     1  9
## 10   2.0     1 10
## 11   1.9     2  1
## 12   0.8     2  2
## 13   1.1     2  3
## 14   0.1     2  4
## 15  -0.1     2  5
## 16   4.4     2  6
## 17   5.5     2  7
## 18   1.6     2  8
## 19   4.6     2  9
## 20   3.4     2 10
```

task 2:Making a wide version of the sleep data; below we’ll see how to work with data in both long and wide formats

```r
sleep_wide <- data.frame(
    ID=1:10,
    group1=sleep$extra[1:10],
    group2=sleep$extra[11:20]
)
sleep_wide
```

```
##    ID group1 group2
## 1   1    0.7    1.9
## 2   2   -1.6    0.8
## 3   3   -0.2    1.1
## 4   4   -1.2    0.1
## 5   5   -0.1   -0.1
## 6   6    3.4    4.4
## 7   7    3.7    5.5
## 8   8    0.8    1.6
## 9   9    0.0    4.6
## 10 10    2.0    3.4
```

## Compare two samples using T-test

task 1:Welch t-test

```r
t.test(extra ~ group, sleep)
```

```
## 
## 	Welch Two Sample t-test
## 
## data:  extra by group
## t = -1.8608, df = 17.776, p-value = 0.07939
## alternative hypothesis: true difference in means between group 1 and group 2 is not equal to 0
## 95 percent confidence interval:
##  -3.3654832  0.2054832
## sample estimates:
## mean in group 1 mean in group 2 
##            0.75            2.33
```

task 2: Student t-test

```r
t.test(extra ~ group, sleep, var.equal=TRUE)
```

```
## 
## 	Two Sample t-test
## 
## data:  extra by group
## t = -1.8608, df = 18, p-value = 0.07919
## alternative hypothesis: true difference in means between group 1 and group 2 is not equal to 0
## 95 percent confidence interval:
##  -3.363874  0.203874
## sample estimates:
## mean in group 1 mean in group 2 
##            0.75            2.33
```

### Q1:What is the p-value of the t-test? 
0.s- The p value of t-test is 0.07919

### Q2:If significance level (∝) equals 0.05, do you accept alternative hypothesis (or reject null hypothesis) 
Ans-  If the p-value is less than or equal to 0.05, you reject the null hypothesis and accept the alternative hypothesis, indicating statistical significance. If the p-value is greater than 0.05, you do not reject the null hypothesis, meaning there isn't enough evidence to support the alternative hypothesis.






