# learning-statistics-with-r-danielle-navarro
A personal journey through Learning Statistics with R by Danielle Navarro — a book I’ve genuinely fallen in love with for the clarity, intuition, and warmth with which it teaches statistics. It makes ideas that once seemed abstract feel remarkably natural, and this repository is my little record of that journey.

## Chapter 5: Descriptive Statistics
---
In the `lsr` package - 

* `who()` - inspects active variables in the environment.
* `sort()` - display the observations in increasing numerical order.
* `table()` - counts the frequency of each unique value and displays the resulting frequency table



### 5.1 Measures of central tendency / which values are “in the middle” or “popular” in the data
#### Mean
*  **Note:** Calculates the arithmetic average of a numeric variable.
* **Statistical notation:** $\bar{X} = \frac{1}{N} \sum_{i=1}^{N} X_i$
* **R code:** mean for all observations: `mean(x = afl_margins)`, or just `mean(afl_margins)`, mean for the first five observations: `mean(afl_margins[1:5])`


#### Median
* **Note:** Calculates the middle value
* **R code:** `median(x = afl_margins)`



#### Trimmed Mean
* **Note:** Discards the most extreme examples on both ends (i.e., the largest and the smallest), and then take the mean of everything else. It preserves the best characteristics of the mean and the median: just like a median, you aren’t highly influenced by extreme outliers, but like the mean, you “use” more than one of the observations.

It is described in terms of the percentage of observation on either side that are discarded. So, for instance, a 10% trimmed mean discards the largest 10% of the observations and the smallest 10% of the observations, and then takes the mean of the remaining 80% of the observations. Not surprisingly, the 0% trimmed mean is just the regular mean, and the 50% trimmed mean is the median. In that sense, trimmed means provide a whole family of central tendency measures that span the range from the mean to the median.

* **R code:** For a vector titled dataset, `dataset <- c(-15, 2, 3, 4, 5, 6, 7, 8, 9, 12)`,
* for a 10% trimmed mean: `mean(x = dataset, trim = .1)`,
* for calculating the 5% trimmed mean for the afl_margins data, `mean(x = afl_margins, trim = .05)`



#### Mode
* **Note:** the value that occurs most frequently.
* **R code:** `modeOf(x = afl_finalists)` (only in lsr package), for the modal frequency: `maxFreq(x = afl_finalists)`



### 5.2 Measures of variability / how “spread out” are the data? 
#### Range
* **Note:** the biggest value minus the smallest value.
* **R code:** `range()` outputs both the minimum value and the maximum value in a vector: `range(afl_margins)`


#### Interquartile range
* **Note:** It calculates the difference between the 25th quantile and the 75th quantile / percentiles. The 10th percentile of a data set is the smallest number x, such that 10% of the data is less than x. This way, the median of a data set is its 50th quantile / percentile. For a better interpretation of IQR, it is the range spanned by the “middle half” of the data.
* **R code:**
* for calculating the 50% quantile: `quantile(x = afl_margins, probs = .5)`,
* to get the 25th and 75th percentile: `quantile(x = afl_margins, probs = c(.25, .75))`,
* to get the IQR: `IQR(x = afl_margins)`


#### Mean absolute deviation
* **Note:** the average of the absolute differences between each observation and the mean. It measures how far, on average, the observations lie from the mean.
* **Statistical notation:** $\text{AAD}(X) = \frac{1}{N} \sum_{i=1}^{N} |X_i - \bar{X}|$

* **R code:** For a vector `X <- c(56, 31, 56, 8, 32)`,
* to calculate the AAD, `aad(X)` 


#### Variance / mean square deviation
* **Note:** Average of the squared deviations from the mean
* **Statistical notation:** The variance of a data set X is sometimes written as `Var(X)`, but it’s more commonly denoted `s^2`
* For population variance (rarely used),

$$
Var(X) = \frac{1}{N}\sum_{i=1}^{N}(X_i-\bar{X})^2
$$

* For sample variance (R by default uses this when var() function is used),

$$
Var(X) = \frac{1}{N-1}\sum_{i=1}^{N}(X_i-\bar{X})^2
$$

* **R code:**  For calculating the sample variance, `var(afl_margins)`



#### Standard deviation / root mean squared deviation (RMSD)
* **Note:** It is the square root of variance, fixes the unit. 
* **Statistical notation:** Expressed as "s", “sd” and “std dev".
* For population SD (rarely used) ,

$$
\sigma = \sqrt{\frac{1}{N}\sum_{i=1}^{N}(X_i-\bar{X})^2}
$$

* For sample SD (R by default uses this when sd() function is used),

$$
s = \sqrt{\frac{1}{N-1}\sum_{i=1}^{n}(X_i-\bar{X})^2}
$$

* **R code:**  to calculate the sample standard deviation, `sd(afl_margins)`

