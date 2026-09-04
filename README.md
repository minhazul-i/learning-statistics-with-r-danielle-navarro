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

* **R code:** For a vector titled dataset, `dataset <- c(-15, 2, 3, 4, 5, 6, 7, 8, 9, 12)`, for a 10% trimmed mean: `mean(x = dataset, trim = .1)`, for calculating the 5% trimmed mean for the afl_margins data, `mean(x = afl_margins, trim = .05)`



#### Mode
* **Note:** the value that occurs most frequently.
* **R code:** `modeOf(x = afl_finalists)` (only in lsr package), for the modal frequency: `maxFreq(x = afl_finalists)`



### 5.2 Measures of variability / how “spread out” are the data? 
