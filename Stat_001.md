# Stat 001

## Statistics - Populations and Samples

- The terms `population` and `sample` are important in statistics and refer to key concepts that are closely related.
  - Population: Everything in the group that we want to learn about.
  - Sample: A part of the population.

| Population                      | Sample                   |
| ------------------------------- | ------------------------ |
| All of the people in Germany    | 500 Germans              |
| All of the customers of Netflix | 300 Netflix customers    |
| Every car manufacturer          | Tesla, Toyota, BMW, Ford |

- For good statistical analysis, the sample needs to be as "similar" as possible to the population. If they are similar enough, we say that the sample is representative of the population.

## Statistics - Mean

- a type of average value, which describes where center of the data is located.
- usually referred to as 'the average'.
- the sum of all the values in the data divided by the total number of values in the data.
- calculated for numerical variables. A variable is something in the data that can vary, like:

### Calculating the Mean

- Calculating the population mean ($\mu$):

$$\mu = \frac{\sum x_{i}}{n}$$

- Calculating the sample mean ($\bar{x}$):

$$\bar{x} = \frac{\sum x_{i}}{n}$$

- The bottom part of the fraction ($n$) is the total number of observations.
- $\sum$ is the symbol for adding together a list of numbers.
- $x_{i}$ is the list of values in the data: $x_{1}, x_{2}, x_{3}, ...$
- The top part of the fraction ($\sum x_{i}$) is the sum of $x_{1}, x_{2}, x_{3}, ...$ added together.
- So, if a sample has 4 observations with values: 4, 11, 7, 14 the calculation is:

$$\bar{x} = \frac{4 + 11 + 7 + 14}{4} = \frac{36}{4} = \underline{9}$$

### Calculation with Programming

- The mean can easily be calculated with many programming languages.
- Using software and programming to calculate statistics is more common for bigger sets of data, as calculating by hand becomes difficult.

```py
# With Python use the NumPy library mean() method to find the mean of the values 4,11,7,14:
import numpy
values = [4,11,7,14]
x = numpy.mean(values) # 9.0
```

```R
# Use the R mean() function to find the mean of the values 4,11,7,14:
values <- c(4,7,11,14)
mean(values)
```

## Statistics - Median

- The median is a type of average value, which describes where the center of the data is located.
- The median is the middle value in a data set ordered from low to high.

### Finding the Median

- The median can only be calculated for numerical variables.
- The formula for finding the middle value is:

$$\frac{n + 1}{2}$$

- Where $n$ is the total number of observations.
- If the total number of observations is an odd number, the formula gives a whole number and the value of this observation is the median.

$$13, 21, 21, \underline{40}, 48, 55, 72$$

- Here, there are 7 total observations, so the median is the 4th value:

$$\frac{7 + 1}{2} = \frac{8}{2} = 4$$

- The 4th value in the ordered list is 40, so that is the median.
- If the total number of observations is an even number, the formula gives a decimal number between two observations.

$$13, 21, 21, \underline{40}, \underline{42}, 48, 55, 72$$

- Here, there are 8 total observations, so the median is between the 4th and 5th values:

$$\frac{8 + 1}{2} = \frac{9}{2} = 4.5$$

- The 4th and 5th values in the ordered list is 40 and 42, so the median is the mean of these two values. That is, the sum of those two values divided by 2:

$$\frac{40 + 42}{2} = \frac{82}{2} = 41$$

- It is important that the numbers are ordered before you can find the median.

### Finding the Median with Programming

```py
import numpy
values = [13,21,21,40,42,48,55,72]
x = numpy.median(values) # 41.0
```

```r
# Use the R median() function
values <- c(13,21,21,40,42,48,55,72)
median(values) # [1] 41
```

## Statistics - Mode

- The mode is a type of average value, which describes where most of the data is located.
- The mode is the value(s) that are the most common in the data.
- A dataset can have multiple values that are modes.
- A distribution of values with only one mode is called unimodal.
- A distribution of values with two modes is called bimodal. In general, a distribution with more than one mode is called multimodal.
- Mode can be found for both categorical and numerical data.

### Finding the Mode

$$4, \underline{7}, 3, 8, 11, \underline{7}, 10, 19, 6, 9, \underline{12}, \underline{12}$$

- Both 7 and 12 appears two times each, and the other values only once. The modes of this data is 7 and 12.

$$Alice, \underline{John}, Bob, Maria, \underline{John}, Julia, Carol$$

- John appears two times, and the other values only once. The mode of this data is John.

### Finding the Mode with Programming

```py
from statistics import multimode
values = [4,7,3,8,11,7,10,19,6,9,12,12]
x = multimode(values) # [7, 12]
```

```R
# Using R with a user-defined function
mode <- function(x) {
  unique_values <- unique(x)
  table <- tabulate(match(x, unique_values))
  unique_values[table == max(table)]
}
values <- c(4,7,3,8,11,7,10,19,6,9,12,12)
mode(values)
# [1]  7 12
```

- R has no built-in function to find the mode.

## Statistics - Variation

- Variation is a measure of how spread out the data is around the center of the data.

### The Variation of the Data

- Measures of variation are statistics of how far away the values in the observations (data points) are from each other.
- There are different measures of variation. The most commonly used are:
  1. Range
  2. Quartiles and Percentiles
  3. Interquartile Range
  4. `Standard deviation`
- Measures of variation combined with an average (measure of center) gives a good picture of the distribution of the data.
- These measures of variation can only be calculated for numerical data.

## Statistics - 1 Range

- The range is the difference between the smallest and the largest value of the data.
- Range is the simplest measure of variation.
- Here is a histogram of the age of all 934 Nobel Prize winners up to the year 2020, showing the range:

<img width="500" alt="Variation1" src="https://www.w3schools.com/statistics/img_histogram_range.svg">

- The youngest winner was 17 years and the oldest was 97 years. The range of ages for Nobel Prize winners is then 80 years.

### Calculating the Range

- The range can only be calculated for numerical data.
- First, find the smallest and largest values.

$$13, 21, 21, 40, 48, 55, 72$$

- Calculate the difference by subtracting the smallest from the largest:

$$72 - 13 = 59$$

### Calculating the Range with Programming

```py
# With Python use the NumPy library ptp() method
import numpy
values = [13,21,21,40,48,55,72]
x = numpy.ptp(values) # 59
```

```R
# Use the R min() and max() functions
values <- c(13,21,21,40,48,55,72)
max(values) - min(values)
# [1] 59
range(values)
# [1] 13 72
```

- The range() function in R returns the smallest and largest values.

## Statistics - 2 Quartiles and Percentiles

- Quartiles and percentiles are ways of separating equal numbers of values in the data into parts.

### Quartiles

- Quartiles are values that separate the data into four equal parts.

<img width="500" alt="Variation2" src="https://www.w3schools.com/statistics/img_histogram_quartiles.svg">

- The quartiles (Q0,Q1,Q2,Q3,Q4) are the values that separate each quarter.
- Between Q0 and Q1 are the 25% lowest values in the data. Between Q1 and Q2 are the next 25%. And so on.
- Q0 is the smallest value in the data.
- Q1 is the value separating the first quarter from the second quarter of the data.
- Q2 is the middle value (median), separating the bottom from the top half.
- Q3 is the value separating the third quarter from the fourth quarter
- Q4 is the largest value in the data.

### Calculating Quartiles with Programming

```py
# With Python use the NumPy library quantile() method
import numpy
values = [13,21,21,40,42,48,55,72]
x = numpy.quantile(values, [0,0.25,0.5,0.75,1])
# [13.   21.   41.   49.75 72.  ]
```

```R
# Use the R quantile() function
values <- c(13,21,21,40,42,48,55,72)
quantile(values)
```

### Percentiles

- Percentiles are values that separate the data into 100 equal parts.
- The 95th percentile separates the lowest 95% of the values from the top 5%
- The 25th percentile (P25%) is the same as the first quartile (Q1).
- The 50th percentile (P50%) is the same as the second quartile (Q2) and the median.
- The 75th percentile (P75%) is the same as the third quartile (Q3)

### Calculating Percentiles with Programming

```py
# With Python use the NumPy library percentile() method
import numpy
values = [13,21,21,40,42,48,55,72]
x = numpy.percentile(values, 65)
# 45.3
```

```R
# Use the R quantile() function
values <- c(13,21,21,40,42,48,55,72)
quantile(values, 0.65)
# 65% 
# 45.3 
```

## Statistics - 3 Interquartile Range

- Interquartile range is the difference between the first and third quartiles (Q1 and Q3).
- The 'middle half' of the data is between the first and third quartile.
- The first quartile is the value in the data that separates the bottom 25% of values from the top 75%.
- The third quartile is the value in the data that separates the bottom 75% of the values from the top 25%

<img width="500" alt="Variation3" src="https://www.w3schools.com/statistics/img_histogram_iqr.svg">

- Here, the middle half of the data is between 51 and 69 years. The interquartile range for Nobel Prize winners is then 18 years.

### Calculating the Interquartile Range with Programming

```py
# With Python use the SciPy library iqr() method
from scipy import stats
values = [13,21,21,40,42,48,55,72]
x = stats.iqr(values) # 28.75
```

```R
# Use the R IQR() function
values <- c(13,21,21,40,42,48,55,72)
IQR(values)
# [1] 28.75
```

## Statistics - 4 Standard deviation

- `Standard deviation` is the most used measure of variation.
- `Standard deviation` (σ) measures how far a 'typical' observation is from the average of the data (μ).
- `Standard deviation` is important for many statistical methods.

<img width="500" alt="Variation4" src="https://www.w3schools.com/statistics/img_histogram_std.svg">

- Each dotted line in the histogram shows a shift of one extra `Standard deviation`.
- If the data is normally distributed:
- Roughly 68.3% of the data is within 1 `Standard deviation` of the average (from μ-1σ to μ+1σ)
- Roughly 95.5% of the data is within 2 `Standard deviations` of the average (from μ-2σ to μ+2σ)
- Roughly 99.7% of the data is within 3 `Standard deviations` of the average (from μ-3σ to μ+3σ)
- A normal distribution has a "bell" shape and spreads out equally on both sides.

### Calculating the Standard deviation

- You can calculate the `Standard deviation` for both the population and the sample.
- The formulas are the almost same and uses different symbols to refer to the `Standard deviation` ($\sigma$) and `sample Standard deviation` ($s$).

$$\sigma =\sqrt{\frac{\sum(x_{i} - \mu)^{2}}{n}}$$

$$s =\sqrt{\frac{\sum(x_{i} - \bar{x})^{2}}{n - 1}}$$

- $n$ is the total number of observations.
- $\sigma$ is the symbol for adding together a list of numbers.
- $x_{i}$ is the list of values in the data: $x_{1}, x_{2}, x_{3}, ...$
- $\mu$ is the population mean and $\bar{x}$ is the sample mean (average value).
- $(x_{i} - \mu)$ and $(x_{i} - \bar{x})$ are the differences between the values of the observations ($x_{i}$) and the mean.
- Each difference is squared and added together.
- Then the sum is divided by $n$ or $(n - 1)$ and then we find the square root.
- Using these 4 values for calculating the population `Standard deviation`:

$$4, 11, 7, 14$$

- We must first find the mean:

$$\mu = \frac{\sum x_{i}}{n} = \frac{4 + 11 + 7 + 14}{4} = \frac{36}{4} = \underline{9}$$

- Then we find the difference between each value and the mean $(x_{i} - \mu)$

$$4 - 9 = -5$$
$$11 - 9 = 2$$
$$7 - 9 = -2$$
$$14 - 9 = 5$$

- Each value is then squared, or multiplied with itself $(x_{i} - \mu)^{2}$

$$(-5)^{2} = (-5)(-5) = 25$$
$$2^{2} = 2*2 = 4$$
$$(-2)^{2} = (-2)(-2) = 4$$
$$5^{2} = 5*5 = 25$$

- All of the squared differences are then added together

$$25 + 4 + 4 + 25 = 58$$

- Then the sum is divided by the total number of observations $n$

$$\frac{58}{4} = 14.5$$ 

- Finally, we take the square root of this number:

$$\sqrt{14.5} \approx \underline{3.81}$$

- So, the `Standard deviation` of the values is roughly: 

### Calculating the `Standard deviation` with Programming

- Population `Standard deviation`

```py
# With Python use the NumPy library std() method
import numpy
values = [4,11,7,14]
x = numpy.std(values)
# 3.8078865529319543
```

```R
# Use an R formula
values <- c(4,7,11,14)
sqrt(mean((values-mean(values))^2))
# [1] 3.807887
```

- Sample `Standard deviation`

```py
# With Python use the NumPy library std() method
import numpy
values = [4,11,7,14]
x = numpy.std(values, ddof=1)
# 4.396968652757639
```

```R
# Use the R sd() function
values <- c(4,7,11,14)
sd(values)
# [1] 4.396969
```

## Statistics - Statistical Inference

- Using data analysis and statistics to make conclusions about a population is called statistical inference.
- The main types of statistical inference are:
  - Estimation
  - Hypothesis testing

### Estimation

- Statistics from a sample are used to estimate population parameters.
- The most likely value is called a point estimate.
- There is always uncertainty when estimating.
- The uncertainty is often expressed as confidence intervals defined by a likely lowest and highest value for the parameter.
- An example could be a confidence interval for the number of bicycles a Dutch person owns:

```
"The average number of bikes a Dutch person owns is between 3.5 and 6."
```

### Hypothesis Testing

- Hypothesis testing is a method to check if a claim about a population is true. More precisely, it checks how likely it is that a hypothesis is true is based on the sample data.
- There are different types of hypothesis testing.
- The steps of the test depends on:
- Type of data (categorical or numerical)
- If you are looking at:
  - A single group
  - Comparing one group to another
- Comparing the same group before and after a change
- Some examples of claims or questions that can be checked with hypothesis testing:

```
90% of Australians are left handed
Is the average weight of dogs more than 40kg?
Do doctors make more money than lawyers?
```

### Probability Distributions

- Statistical inference methods rely on probability calculation and probability distributions.

## Statistics - Normal Distribution

- The normal distribution is an important probability distribution used in statistics.
- Many real world examples of data are normally distributed.
- The normal distribution is described by the mean ($\mu$) and the `Standard deviation` ($\sigma$).
- The normal distribution is often referred to as a 'bell curve' because of it's shape:
  - Most of the values are around the center ($\mu$)
  - The median and mean are equal
  - It has only one mode
  - It is symmetric, meaning it decreases the same amount on the left and the right of the center
- The area under the curve of the normal distribution represents probabilities for the data.
- The area under the whole curve is equal to 1, or 100%
- Here is a graph of a normal distribution with probabilities between `Standard deviations` ($\sigma$):

<img width="500" alt="normaldistri1" src="https://www.w3schools.com/statistics/img_normal_distribution.svg">

- Roughly 68.3% of the data is within 1 `Standard deviation` of the average (from μ-1σ to μ+1σ)
- Roughly 95.5% of the data is within 2 `Standard deviations` of the average (from μ-2σ to μ+2σ)
- Roughly 99.7% of the data is within 3 `Standard deviations` of the average (from μ-3σ to μ+3σ)
- Probabilities of the normal distribution can only be calculated for intervals (between two values).

### Different Mean and `Standard deviations`

- The mean describes where the center of the normal distribution is.
- Here is a graph showing three different normal distributions with the same `Standard deviation` but different means.

<img width="500" alt="normaldistri2" src="https://www.w3schools.com/statistics/img_norm_means.svg">

- The `Standard deviation` describes how spread out the normal distribution is.
- Here is a graph showing three different normal distributions with the same mean but different `Standard deviations`.

<img width="500" alt="normaldistri3" src="https://www.w3schools.com/statistics/img_norm_stds.svg">

- The purple curve has the biggest `Standard deviation` and the black curve has the smallest `Standard deviation`.
- The area under each of the curves is still 1, or 100%.

### A Real Data Example of Normally Distributed Data

- Real world data is often normally distributed.
- Here is a histogram of the age of Nobel Prize winners when they won the prize:

<img width="500" alt="normaldistri4" src="https://www.w3schools.com/statistics/img_nobel_norm.svg">

- The normal distribution drawn on top of the histogram is based on the population mean ($\mu$) and `Standard deviation` ($\sigma$) of the real data.
- We can see that the histogram close to a normal distribution.

### Probability Distributions

- Probability distributions are functions that calculates the probabilities of the outcomes of random variables.
- Typical examples of random variables are coin tosses and dice rolls.
- Here is an graph showing the results of a growing number of coin tosses and the expected values of the results (heads or tails).
- The expected values of the coin toss is the probability distribution of the coin toss.

- Notice how the result of random coin tosses gets closer to the expected values (50%) as the number of tosses increases.

<img width="500" alt="normaldistri5" src="https://www.w3schools.com/statistics/img_1_2dice_100f2.gif">

- Similarly, here is a graph showing the results of a growing number of dice rolls and the expected values of the results (from 1 to 6).

- the result of random dice rolls gets closer to the expected values (1/6, or 16.666%) as the number of rolls increases.

<img width="500" alt="normaldistri6" src="https://www.w3schools.com/statistics/img_1_6dice_100f2.gif">

- When the random variable is a sum of dice rolls the results and expected values take a different shape.

<img width="500" alt="normaldistri7" src="https://www.w3schools.com/statistics/img_2_6dice_100f2.gif">

- As we keep increasing the number of dice for a sum the shape of the results and expected values look more and more like a normal distribution.

<img width="500" alt="normaldistri8" src="https://www.w3schools.com/statistics/img_3_6dice_100f2.gif">

<img width="500" alt="normaldistri6" src="https://www.w3schools.com/statistics/img_5_6dice_100f2.gif">

- Many real world variables follow a similar pattern and naturally form normal distributions.
- Normally distributed variables can be analyzed with well-known techniques.

## Statistics - standard normal distribution

- The `standard normal distribution` is a normal distribution where the mean is 0 and the `Standard deviation` is 1.
- Normally distributed data can be transformed into a `standard normal distribution`.
- Standardizing normally distributed data makes it easier to compare different sets of data.
- The `standard normal distribution` is used for:
  - Calculating confidence intervals
  - Hypothesis tests

####  a graph of the `standard normal distribution` with probability values (p-values) between the `Standard deviations`:

<img width="500" alt="stdnor1" src="https://www.w3schools.com/statistics/img_standard_normal.svg">

- Standardizing makes it easier to calculate probabilities.
- The functions for calculating probabilities are complex and difficult to calculate by hand. Typically, probabilities are found by looking up tables of pre-calculated values, or by using software and programming.
- The `standard normal distribution` is also called the `Z-distribution` and the values are called `Z-values` (or `Z-scores`).

### Z-Values

- Z-values express how many `Standard deviations` from the mean a value is.
- The formula for calculating a Z-value is:

$$Z = \frac{x - \mu}{\sigma} $$

- $x$ is the value we are standardizing, 
- $\mu$ is the mean, and
- $\sigma$ is the `Standard deviation`.

'''

**The mean height of people in Germany is 170 cm  ($\mu$)**
**The standard deviation of the height of people in Germany is 10 cm ($\sigma$)**
**Bob is 200 cm tall (x)**

'''
- Bob is 30 cm taller than the average person in Germany.
- 30 cm is 3 times 10 cm. So Bob's height is 3 `Standard deviations` larger than mean height in Germany.

$$Z = \frac{x - \mu}{\sigma} = \frac{200 - 170}{10} = \frac{30}{10} = \underline{3}$$

- The Z-value of Bob's height (200 cm) is 3.

### Finding the P-value of a Z-Value

- Using a Z-table or programming we can calculate how many people Germany are shorter than Bob and how many are taller.

```py
# With Python use the Scipy Stats library norm.cdf() function find the probability of getting less than a Z-value of 3:
import scipy.stats as stats
print(stats.norm.cdf(3))
# 0.9986501019683699
```

```R
# With R use the built-in pnorm() function find the probability of getting less than a Z-value of 3:
pnorm(3)
# [1] 0.9986501
```

- Using either method we can find that the probability is $\approx 0.9987 or, 99.87\%$
- Which means that Bob is taller than 99.87% of the people in Germany.

#### a graph of the `standard normal distribution` and a Z-value of 3 to visualize the probability:

<img width="500" alt="stdnor1" src="https://www.w3schools.com/statistics/img_z_score3.svg">

- These methods find the p-value up to the particular z-value we have.
- To find the p-value above the z-value we can calculate 1 minus the probability.
- So we can calculate $1 - 0.9987 = 0.0013,\space or\space 0.13\%$.
- Which means that only 0.13% of Germans are taller than Bob.

### Finding the P-Value Between Z-Values

- If we instead want to know how many people are between 155 cm and 165 cm in Germany using the same example:

'''

**The mean height of people in Germany is 170 cm ($\mu$)**
**The `Standard deviation` of the height of people in Germany is 10 cm ($\sigma$)**

'''

- Now we need to calculate Z-values for both 155 cm and 165 cm:

$$Z = \frac{x - \mu}{\sigma} = \frac{155 - 170}{10} = \frac{-15}{10} = \underline{-1.5}$$

- The Z-value of 155 cm is -1.5

$$Z = \frac{x - \mu}{\sigma} = \frac{165 - 170}{10} = \frac{-5}{10} = \underline{-0.5}$$

- The Z-value of 165 cm is -0.5

- Using the Z-table or programming we can find the p-value for the two z-values:
  - The probability of a z-value smaller than -0.5 (shorter than 165 cm) is 30.85%
  - The probability of a z-value smaller than -1.5 (shorter than 155 cm) is 6.68%
- Subtract 6.68% from 30.85% to find the probability of getting a z-value between them.

$$30.85\% - 6.68\% = \underline{24.17\%}$$

- Here is a set of graphs illustrating the process:

<img width="500" alt="stdnor1" src="https://www.w3schools.com/statistics/img_z_scores.svg">

### Finding the Z-value of a P-Value

- You can also use p-values (probability) to find z-values.

'''

**How tall are you if you are taller than 90% of Germans?**

'''

- The p-value is 0.9, or 90%.
- Using a Z-table or programming we can calculate the z-value:


```py
# With Python use the Scipy Stats library norm.ppf() function
import scipy.stats as stats
print(stats.norm.ppf(0.9))
# 1.2815515655446004
```

```R
# With R use the built-in qnorm() function
qnorm(0.9)
# [1] 1.281552
```

- a person that is 1.281 `Standard deviations` taller than the mean height of Germans is taller than 90% of Germans.

$$Z = \frac{x - \mu}{\sigma}$$

$$1.281 = \frac{x - 170}{10}$$

$$1.281\times 10 = x - 170$$

$$12.81 = x - 170$$

$$12.81 + 170 = x$$

$$\underline{182.81} = x$$

'''

**You have to be at least 182.81 cm tall to be taller than 90% of Germans**

'''

## Statistics - Student's T Distribution

- The student's t-distribution is similar to a normal distribution and used in statistical inference to adjust for uncertainty.
- The t-distribution is used for estimation and hypothesis testing of a population mean (average).
- The t-distribution is adjusted for the extra uncertainty of estimating the mean.
- If the sample is small, the t-distribution is wider. If the sample is big, the t-distribution is narrower.
- The bigger the sample size is, the closer the t-distribution gets to the standard normal distribution.
- Below is a graph of a few different t-distributions.

<img width="500" alt="tdist1" src="https://www.w3schools.com/statistics/img_t_distribution.svg">

- Notice how some of the curves have bigger tails.
- This is due to the uncertainty from a smaller sample size.
- The green curve has the smallest sample size.
- For the t-distribution this is expressed as 'degrees of freedom' (df), which is calculated by subtracting 1 from the sample size (n).
- For example a sample size of 30 will make 29 degrees of freedom for the t-distribution.
- The t-distribution is used to find critical t-values and p-values (probabilities) for estimation and hypothesis testing.
- Finding the critical t-values and p-values of the t-distribution is similar z-values and p-values of the standard normal distribution. But make sure to use the correct degrees of freedom.

### Finding the P-Value of a T-Value

- You can find the p-values of a t-value by using a t-table or with programming.

Example
```py
# With Python use the Scipy Stats library t.cdf() function
# find the probability of getting less than a t-value of 2.1 with 29 degrees of freedom:

import scipy.stats as stats
print(stats.t.cdf(2.1, 29))
# 0.9777290209818548
```

```R
# With R use the built-in pt() function
pt(2.1, 29)
# [1] 0.977729
```

### Finding the T-value of a P-Value

- You can find the t-values of a p-value by using a t-table or with programming.

```py
# With Python use the Scipy Stats library t.ppf() function
# find the t-value separating the top 25% from the bottom 75% with 29 degrees of freedom:
import scipy.stats as stats
print(stats.t.ppf(0.75, 29))
# 0.6830438592467808
```

```R
# With R use the built-in qt() function
qt(0.75, 29)
# [1] 0.6830439
```

## Statistics - Estimation

- Point estimates are the most likely value for a population parameter.
- Confidence intervals express the uncertainty of an estimated population parameter.

### The Point Estimate

- A point estimate is calculated from a sample.
- The point estimate depends on the type of data:
  - Categorical data: the number of occurrences divided by the sample size.
  - Numerical data: the mean (the average) of the sample.

'''

**The point estimate for the average height of people in Denmark is 180 cm.**

'''

- Estimates are always uncertain. This uncertainty can be expressed with a confidence interval.

### Confidence Intervals

- The confidence interval is defined by a lower bound and an upper bound.
- This gives us a range of values that the true parameter is likely to be between.

'''

**The average height of people in Denmark is between 170 cm and 190 cm.**

'''

- Here, 170 cm is the lower bound, and 190 cm is the upper bound.
- The lower and upper bounds of a confidence interval is based on the confidence level.

### The Confidence Level

- Confidence levels can be expressed as percentages or decimal numbers, and the most commonly used are:
  - 90% (0.90)
  - 95% (0.95)
  - 99% (0.99)
- The higher the confidence level, the bigger the interval will be.
- For example, the confidence intervals for the average height of people in Denmark might be:

```
90% confidence level: between 175 cm and 185 cm.
95% confidence level: between 170 cm and 190 cm.
99% confidence level: between 160 cm and 200 cm.
```

- We use this confidence level together with a probability distribution to decide how large the margin of error is.

### The Margin of Error

- The margin of error is the distance between the point estimate and the lower and upper bounds.
- The margin of error is based on the confidence level and the data we have from the sample.
- For example, if the point estimate for the average height of people in Denmark is 180 cm:

```
5 cm margin of error: between 175 cm and 185 cm.
10 cm margin of error: between 170 cm and 190 cm.
20 cm margin of error: between 160 cm and 200 cm.
```

### Steps for Calculating the Confidence Interval

- The following steps are used to calculate a confidence interval:
  - Check the conditions
  - Find the point estimate
  - Decide the confidence level
  - Calculate the margin of error
  - Calculate the confidence interval
- One condition is that the sample is randomly selected from the population.
- The other conditions depends on what type of parameter you are calculate the confidence interval for.
- Commonly estimated parameters are:
  - Proportions (for qualitative data)
  - Mean values (for numerical data)
- You will learn the steps for both types in the following pages.

## Statistics - Estimating Population Proportions
A population proportion is the share of a population that belongs to a particular category.

Confidence intervals are used to estimate population proportions.

Estimating Population Proportions
A statistic from a sample is used to estimate a parameter of the population.

The most likely value for a parameter is the point estimate.

Additionally, we can calculate a lower bound and an upper bound for the estimated parameter.

The margin of error is the difference between the lower and upper bounds from the point estimate.

Together, the lower and upper bounds define a confidence interval.

Calculating a Confidence Interval
The following steps are used to calculate a confidence interval:

Check the conditions
Find the point estimate
Decide the confidence level
Calculate the margin of error
Calculate the confidence interval
For example:

Population: Nobel Prize winners
Category: Born in the United States of America
We can take a sample and see how many of them were born in the US.

The sample data is used to make an estimation of the share of all the Nobel Prize winners born in the US.

By randomly selecting 30 Nobel Prize winners we could find that:

6 out of 30 Nobel Prize winners in the sample were born in the US

From this data we can calculate a confidence interval with the steps below.

1. Checking the Conditions
The conditions for calculating a confidence interval for a proportion are:

The sample is randomly selected
There is only two options:
Being in the category
Not being in the category
The sample needs at least:
5 members in the category
5 members not in the category
In our example, we randomly selected 6 people that were born in the US.

The rest were not born in the US, so there are 24 in the other category.

The conditions are fulfilled in this case.

Note: It is possible to calculate a confidence interval without having 5 of each category. But special adjustments need to be made.

2. Finding the Point Estimate
The point estimate is the sample proportion (
).

The formula for calculating the sample proportion is the number of occurrences (
) divided by the sample size (
):

 

In our example, 6 out of 30 were born in the US: 
 is 6, and 
 is 30.

So the point estimate for the proportion is:

 
 
 
 

So 20% of the sample were born in the US.

3. Deciding the Confidence Level
The confidence level is expressed with a percentage or a decimal number.

For example, if the confidence level is 95% or 0.95:

The remaining probability (
) is then: 5%, or 1 - 0.95 = 0.05.

Commonly used confidence levels are:

90% with 
 = 0.1
95% with 
 = 0.05
99% with 
 = 0.01
Note: A 95% confidence level means that if we take 100 different samples and make confidence intervals for each:

The true parameter will be inside the confidence interval 95 out of those 100 times.

We use the standard normal distribution to find the margin of error for the confidence interval.

The remaining probabilities (
) are divided in two so that half is in each tail area of the distribution.

The values on the z-value axis that separate the tails area from the middle are called critical z-values.

Below are graphs of the standard normal distribution showing the tail areas (
) for different confidence levels.

Standard Normal Distributions with two tail areas, with different sizes.

4. Calculating the Margin of Error
The margin of error is the difference between the point estimate and the lower and upper bounds.

The margin of error (
) for a proportion is calculated with a critical z-value and the standard error:

 

The critical z-value 
 is calculated from the standard normal distribution and the confidence level.

The standard error 
 
 is calculated from the point estimate (
) and sample size (
).

In our example with 6 US-born Nobel Prize winners out of a sample of 30 the standard error is:

 
 
 
 
 
 

If we choose 95% as the confidence level, the 
 is 0.05.

So we need to find the critical z-value 

The critical z-value can be found using a Z-table or with a programming language function:

ExampleGet your own Python Server
With Python use the Scipy Stats library norm.ppf() function find the Z-value for an 
/2 = 0.025

import scipy.stats as stats
print(stats.norm.ppf(1-0.025))
Example
With R use the built-in qnorm() function to find the Z-value for an 
/2 = 0.025

qnorm(1-0.025)
Using either method we can find that the critical Z-value 
 is  
 
 

The standard error 
 
 was  
 
 

So the margin of error (
) is:

 
 
 

5. Calculate the Confidence Interval
The lower and upper bounds of the confidence interval are found by subtracting and adding the margin of error (
) from the point estimate (
).

In our example the point estimate was 0.2 and the margin of error was 0.143, then:

The lower bound is:

 
 

The upper bound is:

 
 

The confidence interval is:

 or 

And we can summarize the confidence interval by stating:

The 95% confidence interval for the proportion of Nobel Prize winners born in the US is between 5.7% and 34.4%

Calculating a Confidence Interval with Programming
A confidence interval can be calculated with many programming languages.

Using software and programming to calculate statistics is more common for bigger sets of data, as calculating manually becomes difficult.

Example
With Python, use the scipy and math libraries to calculate the confidence interval for an estimated proportion.

Here, the sample size is 30 and the occurrences is 6.

import scipy.stats as stats
import math

# Specify sample occurrences (x), sample size (n) and confidence level
x = 6
n = 30
confidence_level = 0.95

# Calculate the point estimate, alpha, the critical z-value, the standard error, and the margin of error
point_estimate = x/n
alpha = (1-confidence_level)
critical_z = stats.norm.ppf(1-alpha/2)
standard_error = math.sqrt((point_estimate*(1-point_estimate)/n))
margin_of_error = critical_z * standard_error

# Calculate the lower and upper bound of the confidence interval
lower_bound = point_estimate - margin_of_error
upper_bound = point_estimate + margin_of_error

# Print the results
print("Point Estimate: {:.3f}".format(point_estimate))
print("Critical Z-value: {:.3f}".format(critical_z))
print("Margin of Error: {:.3f}".format(margin_of_error))
print("Confidence Interval: [{:.3f},{:.3f}]".format(lower_bound,upper_bound))
print("The {:.1%} confidence interval for the population proportion is:".format(confidence_level))
print("between {:.3f} and {:.3f}".format(lower_bound,upper_bound))
Example
With R, use the built-in math and statistics functions to calculate the confidence interval for an estimated proportion.

Here, the sample size is 30 and the occurrences is 6.

# Specify sample occurrences (x), sample size (n) and confidence level
x = 6
n = 30
confidence_level = 0.95

# Calculate the point estimate, alpha, the critical z-value, the standard error, and the margin of error
point_estimate = x/n
alpha = (1-confidence_level)
critical_z = qnorm(1-alpha/2)
standard_error = sqrt(point_estimate*(1-point_estimate)/n)
margin_of_error = critical_z * standard_error

# Calculate the lower and upper bound of the confidence interval
lower_bound = point_estimate - margin_of_error
upper_bound = point_estimate + margin_of_error

# Print the results
sprintf("Point Estimate: %0.3f", point_estimate)
sprintf("Critical Z-value: %0.3f", critical_z)
sprintf("Margin of Error: %0.3f", margin_of_error)
sprintf("Confidence Interval: [%0.3f,%0.3f]", lower_bound, upper_bound)
sprintf("The %0.1f%% confidence interval for the population proportion is:", confidence_level*100)
sprintf("between %0.4f and %0.4f", lower_bound, upper_bound)


## Statistics - Estimating Population Means
A population mean is an average of a numerical population variable.

Confidence intervals are used to estimate population means.

Estimating Population Mean
A statistic from a sample is used to estimate a parameter of the population.

The most likely value for a parameter is the point estimate.

Additionally, we can calculate a lower bound and an upper bound for the estimated parameter.

The margin of error is the difference between the lower and upper bounds from the point estimate.

Together, the lower and upper bounds define a confidence interval.

Calculating a Confidence Interval
The following steps are used to calculate a confidence interval:

Check the conditions
Find the point estimate
Decide the confidence level
Calculate the margin of error
Calculate the confidence interval
For example:

Population: Nobel Prize winners
Variable: Age when they received the Nobel Prize
We can take a sample and calculate the mean and the standard deviation of that sample.

The sample data is used to make an estimation of the average age of all the Nobel Prize winners.

By randomly selecting 30 Nobel Prize winners we could find that:

The mean age in the sample is 62.1

The standard deviation of age in the sample is 13.46

From this data we can calculate a confidence interval with the steps below.

1. Checking the Conditions
The conditions for calculating a confidence interval for a mean are:

The sample is randomly selected
And either:
The population data is normally distributed
Sample size is large enough
A moderately large sample size, like 30, is typically large enough.

In the example, the sample size was 30 and it was randomly selected, so the conditions are fulfilled.

Note: Checking if the data is normally distributed can be done with specialized statistical tests.

2. Finding the Point Estimate
The point estimate is the sample mean (
).

The formula for calculating the sample mean is the sum of all the values 
 divided by the sample size (
):

 

In our example, the mean age was 62.1 in the sample.

3. Deciding the Confidence Level
The confidence level is expressed with a percentage or a decimal number.

For example, if the confidence level is 95% or 0.95:

The remaining probability (
) is then: 5%, or 1 - 0.95 = 0.05.

Commonly used confidence levels are:

90% with 
 = 0.1
95% with 
 = 0.05
99% with 
 = 0.01
Note: A 95% confidence level means that if we take 100 different samples and make confidence intervals for each:

The true parameter will be inside the confidence interval 95 out of those 100 times.

We use the student's t-distribution to find the margin of error for the confidence interval.

The t-distribution is adjusted for the sample size with 'degrees of freedom' (df).

The degrees of freedom is the sample size (n) - 1, so in this example it is 30 - 1 = 29

The remaining probabilities (
) are divided in two so that half is in each tail area of the distribution.

The values on the t-value axis that separate the tails area from the middle are called critical t-values.

Below are graphs of the standard normal distribution showing the tail areas (
) for different confidence levels at 29 degrees of freedom (df).

Student's t-distributions with two tail areas, with different sizes.

4. Calculating the Margin of Error
The margin of error is the difference between the point estimate and the lower and upper bounds.

The margin of error (
) for a proportion is calculated with a critical t-value and the standard error:

 

The critical t-value 
 is calculated from the standard normal distribution and the confidence level.

The standard error 
 
 is calculated from the sample standard deviation (
) and the sample size (
).

In our example with a sample standard deviation (
) of 13.46 and sample size of 30 the standard error is:

 
 
 
 
 

If we choose 95% as the confidence level, the 
 is 0.05.

So we need to find the critical t-value 

The critical t-value can be found using a t-table or with a programming language function:

ExampleGet your own Python Server
With Python use the Scipy Stats library t.ppf() function find the t-value for an 
/2 = 0.025 and 29 degrees of freedom.

import scipy.stats as stats
print(stats.t.ppf(1-0.025, 29))
Example
With R use the built-in qt() function to find the t-value for an 
/2 = 0.025 and 29 degrees of freedom.

qt(1-0.025, 29)
Using either method we can find that the critical t-value 
 is  
 
 

The standard error 
 
 was  
 
 

So the margin of error (
) is:

 
 
 

5. Calculate the Confidence Interval
The lower and upper bounds of the confidence interval are found by subtracting and adding the margin of error (
) from the point estimate (
).

In our example the point estimate was 0.2 and the margin of error was 0.143, then:

The lower bound is:

 
 

The upper bound is:

 
 

The confidence interval is:


And we can summarize the confidence interval by stating:

The 95% confidence interval for the mean age of Nobel Prize winners is between 57.06 and 67.14 years

Calculating a Confidence Interval with Programming
A confidence interval can be calculated with many programming languages.

Using software and programming to calculate statistics is more common for bigger sets of data, as calculating manually becomes difficult.

Note: The results from using the programming code will be more accurate because of rounding of values when calculating by hand.

Example
With Python use the scipy and math libraries to calculate the confidence interval for an estimated proportion.

Here, the sample size is 30, sample mean is 62.1 and sample standard deviation is 13.46.

import scipy.stats as stats
import math

# Specify sample mean (x_bar), sample standard deviation (s), sample size (n) and confidence level
x_bar = 62.1
s = 13.46
n = 30
confidence_level = 0.95

# Calculate alpha, degrees of freedom (df), the critical t-value, and the margin of error
alpha = (1-confidence_level)
df = n - 1
standard_error = s/math.sqrt(n)
critical_t = stats.t.ppf(1-alpha/2, df)
margin_of_error = critical_t * standard_error

# Calculate the lower and upper bound of the confidence interval
lower_bound = x_bar - margin_of_error
upper_bound = x_bar + margin_of_error

# Print the results
print("Critical t-value: {:.3f}".format(critical_t))
print("Margin of Error: {:.3f}".format(margin_of_error))
print("Confidence Interval: [{:.3f},{:.3f}]".format(lower_bound,upper_bound))
print("The {:.1%} confidence interval for the population mean is:".format(confidence_level))
print("between {:.3f} and {:.3f}".format(lower_bound,upper_bound))
Example
R can use built-in math and statistics functions to calculate the confidence interval for an estimated proportion.

Here, the sample size is 30, sample mean is 62.1 and sample standard deviation is 13.46.

# Specify sample mean (x_bar), sample standard deviation (s), sample size (n) and confidence level
x_bar = 62.1
s = 13.46
n = 30
confidence_level = 0.95

# Calculate alpha, degrees of freedom (df), the critical t-value, and the margin of error
alpha = (1-confidence_level)
df = n - 1
standard_error = s/sqrt(n)
critical_t = qt(1-alpha/2, 29)
margin_of_error = critical_t * standard_error

# Calculate the lower and upper bound of the confidence interval
lower_bound = x_bar - margin_of_error
upper_bound = x_bar + margin_of_error

# Print the results
sprintf("Critical t-value: %0.3f", critical_t)
sprintf("Margin of Error: %0.3f", margin_of_error)
sprintf("Confidence Interval: [%0.3f,%0.3f]", lower_bound, upper_bound)
sprintf("The %0.1f%% confidence interval for the population mean is:", confidence_level*100)
sprintf("between %0.4f and %0.4f", lower_bound, upper_bound)
Note: R also has a built in function for calculating a confidence interval for a population mean.

Example
R can use the built-in t.test() function to calculate the confidence interval for an estimated mean.

Here, the sample is 30 randomly generated values with a mean of 60 and standard deviation is 12.5 using the rnorm() function to generate the sample.

# Specify sample size (n) and confidence level
n = 30
confidence_level = 0.95

# Set random seed and generate sample data with mean of 60 and standard deviation of 12.5
set.seed(3)
sample <- rnorm(n, 60, 12.5)

# t.test function for sample data, confidence level, and selecting the $conf.int option
t.test(sample, conf.level = confidence_level)$conf.int


## Statistics - Hypothesis Testing
Hypothesis testing is a formal way of checking if a hypothesis about a population is true or not.

Hypothesis Testing
A hypothesis is a claim about a population parameter.

A hypothesis test is a formal procedure to check if a hypothesis is true or not.

Examples of claims that can be checked:

The average height of people in Denmark is more than 170 cm.

The share of left handed people in Australia is not 10%.

The average income of dentists is less the average income of lawyers.

The Null and Alternative Hypothesis
Hypothesis testing is based on making two different claims about a population parameter.

The null hypothesis (
) and the alternative hypothesis (
) are the claims.

The two claims needs to be mutually exclusive, meaning only one of them can be true.

The alternative hypothesis is typically what we are trying to prove.

For example, we want to check the following claim:

"The average height of people in Denmark is more than 170 cm."

In this case, the parameter is the average height of people in Denmark (
).

The null and alternative hypothesis would be:

Null hypothesis: The average height of people in Denmark is 170 cm.

Alternative hypothesis: The average height of people in Denmark is more than 170 cm.

The claims are often expressed with symbols like this:

: 

: 

If the data supports the alternative hypothesis, we reject the null hypothesis and accept the alternative hypothesis.

If the data does not support the alternative hypothesis, we keep the null hypothesis.

Note: The alternative hypothesis is also referred to as (
).

The Significance Level
The significance level (
) is the uncertainty we accept when rejecting the null hypothesis in the hypothesis test.

The significance level is a percentage probability of accidentally making the wrong conclusion.

Typical significance levels are:

 (10%)
 (5%)
 (1%)
A lower significance level means that the evidence in the data needs to be stronger to reject the null hypothesis.

There is no "correct" significance level - it only states the uncertainty of the conclusion.

Note: A 5% significance level means that when we reject a null hypothesis:

We expect to reject a true null hypothesis 5 out of 100 times.

The Test Statistic
The test statistic is used to decide the outcome of the hypothesis test.

The test statistic is a standardized value calculated from the sample.

Standardization means converting a statistic to a well known probability distribution.

The type of probability distribution depends on the type of test.

Common examples are:

Standard Normal Distribution (Z): used for Testing Population Proportions
Student's T-Distribution (T): used for Testing Population Means
Note: You will learn how to calculate the test statistic for each type of test in the following chapters.

The Critical Value and P-Value Approach
There are two main approaches used for hypothesis tests:

The critical value approach compares the test statistic with the critical value of the significance level.
The p-value approach compares the p-value of the test statistic and with the significance level.
The Critical Value Approach
The critical value approach checks if the test statistic is in the rejection region.

The rejection region is an area of probability in the tails of the distribution.

The size of the rejection region is decided by the significance level (
).

The value that separates the rejection region from the rest is called the critical value.

Here is a graphical illustration:

Graph of T-Distribution for right-tailed test, rejection region (alpha), critical value, and test statistic in the rejection area.

If the test statistic is inside this rejection region, the null hypothesis is rejected.

For example, if the test statistic is 2.3 and the critical value is 2 for a significance level (
):

We reject the null hypothesis (
) at 0.05 significance level (
)

The P-Value Approach
The p-value approach checks if the p-value of the test statistic is smaller than the significance level (
).

The p-value of the test statistic is the area of probability in the tails of the distribution from the value of the test statistic.

Here is a graphical illustration:

Graphs of T-Distributions for right-tailed test with tail area (alpha), and tail area equal to p-value of test statistic.

If the p-value is smaller than the significance level, the null hypothesis is rejected.

The p-value directly tells us the lowest significance level where we can reject the null hypothesis.

For example, if the p-value is 0.03:

We reject the null hypothesis (
) at a 0.05 significance level (
)

We keep the null hypothesis (
) at a 0.01 significance level (
)

Note: The two approaches are only different in how they present the conclusion.

Steps for a Hypothesis Test
The following steps are used for a hypothesis test:

Check the conditions
Define the claims
Decide the significance level
Calculate the test statistic
Conclusion
One condition is that the sample is randomly selected from the population.

The other conditions depends on what type of parameter you are testing the hypothesis for.

Common parameters to test hypotheses are:

Proportions (for qualitative data)
Mean values (for numerical data)
You will learn the steps for both types in the following pages.

## Statistics - Hypothesis Testing a Proportion
A population proportion is the share of a population that belongs to a particular category.

Hypothesis tests are used to check a claim about the size of that population proportion.

Hypothesis Testing a Proportion
The following steps are used for a hypothesis test:

Check the conditions
Define the claims
Decide the significance level
Calculate the test statistic
Conclusion
For example:

Population: Nobel Prize winners
Category: Born in the United States of America
And we want to check the claim:

"More than 20% of Nobel Prize winners were born in the US"

By taking a sample of 40 randomly selected Nobel Prize winners we could find that:

10 out of 40 Nobel Prize winners in the sample were born in the US

The sample proportion is then: 
 
, or 25%.

From this sample data we check the claim with the steps below.

1. Checking the Conditions
The conditions for calculating a confidence interval for a proportion are:

The sample is randomly selected
There is only two options:
Being in the category
Not being in the category
The sample needs at least:
5 members in the category
5 members not in the category
In our example, we randomly selected 10 people that were born in the US.

The rest were not born in the US, so there are 30 in the other category.

The conditions are fulfilled in this case.

Note: It is possible to do a hypothesis test without having 5 of each category. But special adjustments need to be made.

2. Defining the Claims
We need to define a null hypothesis (
) and an alternative hypothesis (
) based on the claim we are checking.

The claim was:

"More than 20% of Nobel Prize winners were born in the US"

In this case, the parameter is the proportion of Nobel Prize winners born in the US (
).

The null and alternative hypothesis are then:

Null hypothesis: 20% of Nobel Prize winners were born in the US.

Alternative hypothesis: More than 20% of Nobel Prize winners were born in the US.

Which can be expressed with symbols as:

: 

: 

This is a 'right tailed' test, because the alternative hypothesis claims that the proportion is more than in the null hypothesis.

If the data supports the alternative hypothesis, we reject the null hypothesis and accept the alternative hypothesis.

3. Deciding the Significance Level
The significance level (
) is the uncertainty we accept when rejecting the null hypothesis in a hypothesis test.

The significance level is a percentage probability of accidentally making the wrong conclusion.

Typical significance levels are:

 (10%)
 (5%)
 (1%)
A lower significance level means that the evidence in the data needs to be stronger to reject the null hypothesis.

There is no "correct" significance level - it only states the uncertainty of the conclusion.

Note: A 5% significance level means that when we reject a null hypothesis:

We expect to reject a true null hypothesis 5 out of 100 times.

4. Calculating the Test Statistic
The test statistic is used to decide the outcome of the hypothesis test.

The test statistic is a standardized value calculated from the sample.

The formula for the test statistic (TS) of a population proportion is:

 

 is the difference between the sample proportion (
) and the claimed population proportion (
).

 is the sample size.

In our example:

The claimed (
) population proportion (
) was 

The sample proportion (
) was 10 out of 40, or: 
 

The sample size (
) was 

So the test statistic (TS) is then:

 
 
 
 
 
 

You can also calculate the test statistic using programming language functions:

ExampleGet your own Python Server
With Python use the scipy and math libraries to calculate the test statistic for a proportion.

import scipy.stats as stats
import math

# Specify the number of occurrences (x), the sample size (n), and the proportion claimed in the null-hypothesis (p)
x = 10
n = 40
p = 0.2

# Calculate the sample proportion
p_hat = x/n

# Calculate and print the test statistic
print((p_hat-p)/(math.sqrt((p*(1-p))/(n))))
Example
With R use the built-in prop.test() function to calculate the test statistic for a proportion.

# Specify the sample occurrences (x), the sample size (n), and the null-hypothesis claim (p)
x <- 10
n <- 40
p <- 0.20

# Calculate the sample proportion
p_hat = x/n

# Calculate and print the test statistic
(p_hat-p)/(sqrt((p*(1-p))/(n)))
5. Concluding
There are two main approaches for making the conclusion of a hypothesis test:

The critical value approach compares the test statistic with the critical value of the significance level.
The P-value approach compares the P-value of the test statistic and with the significance level.
Note: The two approaches are only different in how they present the conclusion.

The Critical Value Approach
For the critical value approach we need to find the critical value (CV) of the significance level (
).

For a population proportion test, the critical value (CV) is a Z-value from a standard normal distribution.

This critical Z-value (CV) defines the rejection region for the test.

The rejection region is an area of probability in the tails of the standard normal distribution.

Because the claim is that the population proportion is more than 20%, the rejection region is in the right tail:

Standard Normal Distribution with a right tail area (rejection region) denoted as the greek symbol alpha

The size of the rejection region is decided by the significance level (
).

Choosing a significance level (
) of 0.05, or 5%, we can find the critical Z-value from a Z-table, or with a programming language function:

Note: The functions find the Z-value for an area from the left side.

To find the Z-value for a right tail we need to use the function on the area to the left of the tail (1-0.05 = 0.95).

Example
With Python use the Scipy Stats library norm.ppf() function find the Z-value for an 
 = 0.05 in the right tail.

import scipy.stats as stats
print(stats.norm.ppf(1-0.05))
Example
With R use the built-in qnorm() function to find the Z-value for an 
 = 0.05 in the right tail.

qnorm(1-0.05)
Using either method we can find that the critical Z-value is  
 
 

For a right tailed test we need to check if the test statistic (TS) is bigger than the critical value (CV).

If the test statistic is bigger than the critical value, the test statistic is in the rejection region.

When the test statistic is in the rejection region, we reject the null hypothesis (
).

Here, the test statistic (TS) was  
 
 
 and the critical value was  
 
 

Here is an illustration of this test in a graph:

Standard Normal Distribution with a right tail area (rejection region) equal to 0.05, a critical value of 1.6449, and a test statistic of 0.791

Since the test statistic was smaller than the critical value we do not reject the null hypothesis.

This means that the sample data does not support the alternative hypothesis.

And we can summarize the conclusion stating:

The sample data does not support the claim that "more than 20% of Nobel Prize winners were born in the US" at a 5% significance level.

The P-Value Approach
For the P-value approach we need to find the P-value of the test statistic (TS).

If the P-value is smaller than the significance level (
), we reject the null hypothesis (
).

The test statistic was found to be  
 
 

For a population proportion test, the test statistic is a Z-Value from a standard normal distribution.

Because this is a right tailed test, we need to find the P-value of a Z-value bigger than 0.791.

We can find the P-value using a Z-table, or with a programming language function:

Note: The functions find the P-value (area) to the left side of Z-value.

To find the P-value for a right tail we need to subtract the left area from the total area: 1 - the output of the function.

Example
With Python use the Scipy Stats library norm.cdf() function find the P-value of a Z-value bigger than 0.791:

import scipy.stats as stats
print(1-stats.norm.cdf(0.791))
Example
With R use the built-in pnorm() function find the P-value of a Z-value bigger than 0.791:

1-pnorm(0.791)
Using either method we can find that the P-value is  
 
 

This tells us that the significance level (
) would need to be bigger than 0.2145, or 21.45%, to reject the null hypothesis.

Here is an illustration of this test in a graph:



This P-value is bigger than any of the common significance levels (10%, 5%, 1%).

So the null hypothesis is kept at all of these significance levels.

And we can summarize the conclusion stating:

The sample data does not support the claim that "more than 20% of Nobel Prize winners were born in the US" at a 10%, 5%, or 1% significance level.

Note: It may still be true that the real population proportion is more than 20%.

But there was not strong enough evidence to support it with this sample.

Calculating a P-Value for a Hypothesis Test with Programming
Many programming languages can calculate the P-value to decide outcome of a hypothesis test.

Using software and programming to calculate statistics is more common for bigger sets of data, as calculating manually becomes difficult.

The P-value calculated here will tell us the lowest possible significance level where the null-hypothesis can be rejected.

Example
With Python use the scipy and math libraries to calculate the P-value for a right tailed hypothesis test for a proportion.

Here, the sample size is 40, the occurrences are 10, and the test is for a proportion bigger than 0.20.

import scipy.stats as stats
import math

# Specify the number of occurrences (x), the sample size (n), and the proportion claimed in the null-hypothesis (p)
x = 10
n = 40
p = 0.2

# Calculate the sample proportion
p_hat = x/n

# Calculate the test statistic
test_stat = (p_hat-p)/(math.sqrt((p*(1-p))/(n)))

# Output the p-value of the test statistic (right tailed test)
print(1-stats.norm.cdf(test_stat))
Example
With R use the built-in prop.test() function find the P-value for a right tailed hypothesis test for a proportion.

Here, the sample size is 40, the occurrences are 10, and the test is for a proportion bigger than 0.20.

# Specify the sample occurrences (x), the sample size (n), and the null-hypothesis claim (p)
x <- 10
n <- 40
p <- 0.20

# P-value from right-tail proportion test at 0.05 significance level
prop.test(x, n, p, alternative = c("greater"), conf.level = 0.95, correct = FALSE)$p.value
Note: The conf.level in the R code is the reverse of the significance level.

Here, the significance level is 0.05, or 5%, so the conf.level is 1-0.05 = 0.95, or 95%.

Left-Tailed and Two-Tailed Tests
This was an example of a right tailed test, where the alternative hypothesis claimed that parameter is bigger than the null hypothesis claim.

You can check out an equivalent step-by-step guide for other types here:

Left-Tailed Test
Two-Tailed Test


## Statistics - Hypothesis Testing a Mean
A population mean is an average of value a population.

Hypothesis tests are used to check a claim about the size of that population mean.

Hypothesis Testing a Mean
The following steps are used for a hypothesis test:

Check the conditions
Define the claims
Decide the significance level
Calculate the test statistic
Conclusion
For example:

Population: Nobel Prize winners
Category: Age when they received the prize.
And we want to check the claim:

"The average age of Nobel Prize winners when they received the prize is more than 55"

By taking a sample of 30 randomly selected Nobel Prize winners we could find that:

The mean age in the sample (
) is 62.1

The standard deviation of age in the sample (
) is 13.46

From this sample data we check the claim with the steps below.

1. Checking the Conditions
The conditions for calculating a confidence interval for a proportion are:

The sample is randomly selected
And either:
The population data is normally distributed
Sample size is large enough
A moderately large sample size, like 30, is typically large enough.

In the example, the sample size was 30 and it was randomly selected, so the conditions are fulfilled.

Note: Checking if the data is normally distributed can be done with specialized statistical tests.

2. Defining the Claims
We need to define a null hypothesis (
) and an alternative hypothesis (
) based on the claim we are checking.

The claim was:

"The average age of Nobel Prize winners when they received the prize is more than 55"

In this case, the parameter is the mean age of Nobel Prize winners when they received the prize (
).

The null and alternative hypothesis are then:

Null hypothesis: The average age was 55.

Alternative hypothesis: The average age was more than 55.

Which can be expressed with symbols as:

: 

: 

This is a 'right tailed' test, because the alternative hypothesis claims that the proportion is more than in the null hypothesis.

If the data supports the alternative hypothesis, we reject the null hypothesis and accept the alternative hypothesis.

3. Deciding the Significance Level
The significance level (
) is the uncertainty we accept when rejecting the null hypothesis in a hypothesis test.

The significance level is a percentage probability of accidentally making the wrong conclusion.

Typical significance levels are:

 (10%)
 (5%)
 (1%)
A lower significance level means that the evidence in the data needs to be stronger to reject the null hypothesis.

There is no "correct" significance level - it only states the uncertainty of the conclusion.

Note: A 5% significance level means that when we reject a null hypothesis:

We expect to reject a true null hypothesis 5 out of 100 times.

4. Calculating the Test Statistic
The test statistic is used to decide the outcome of the hypothesis test.

The test statistic is a standardized value calculated from the sample.

The formula for the test statistic (TS) of a population mean is:

 

 is the difference between the sample mean (
) and the claimed population mean (
).

 is the sample standard deviation.

 is the sample size.

In our example:

The claimed (
) population mean (
) was 

The sample mean (
) was 

The sample standard deviation (
) was 

The sample size (
) was 

So the test statistic (TS) is then:

 
 
 
 

You can also calculate the test statistic using programming language functions:

ExampleGet your own Python Server
With Python use the scipy and math libraries to calculate the test statistic.

import scipy.stats as stats
import math

# Specify the sample mean (x_bar), the sample standard deviation (s), the mean claimed in the null-hypothesis (mu_null), and the sample size (n)
x_bar = 62.1
s = 13.46
mu_null = 55
n = 30

# Calculate and print the test statistic
print((x_bar - mu_null)/(s/math.sqrt(n)))
Example
With R use built-in math and statistics functions to calculate the test statistic.

# Specify the sample mean (x_bar), the sample standard deviation (s), the mean claimed in the null-hypothesis (mu_null), and the sample size (n)
x_bar <- 62.1
s <- 13.46
mu_null <- 55
n <- 30

# Output the test statistic
(x_bar - mu_null)/(s/sqrt(n))
5. Concluding
There are two main approaches for making the conclusion of a hypothesis test:

The critical value approach compares the test statistic with the critical value of the significance level.
The P-value approach compares the P-value of the test statistic and with the significance level.
Note: The two approaches are only different in how they present the conclusion.

The Critical Value Approach
For the critical value approach we need to find the critical value (CV) of the significance level (
).

For a population mean test, the critical value (CV) is a T-value from a student's t-distribution.

This critical T-value (CV) defines the rejection region for the test.

The rejection region is an area of probability in the tails of the standard normal distribution.

Because the claim is that the population mean is more than 55, the rejection region is in the right tail:

Standard Normal Distribution with a right tail area (rejection region) denoted as the greek symbol alpha

The size of the rejection region is decided by the significance level (
).

The student's t-distribution is adjusted for the uncertainty from smaller samples.

This adjustment is called degrees of freedom (df), which is the sample size 

In this case the degrees of freedom (df) is:  
 
 

Choosing a significance level (
) of 0.01, or 1%, we can find the critical T-value from a T-table, or with a programming language function:

Example
With Python use the Scipy Stats library t.ppf() function find the T-Value for an 
 = 0.01 at 29 degrees of freedom (df).

import scipy.stats as stats
print(stats.t.ppf(1-0.01, 29))
Example
With R use the built-in qt() function to find the t-value for an 
 = 0.01 at 29 degrees of freedom (df).

qt(1-0.01, 29)
Using either method we can find that the critical T-Value is  
 
 

For a right tailed test we need to check if the test statistic (TS) is bigger than the critical value (CV).

If the test statistic is bigger than the critical value, the test statistic is in the rejection region.

When the test statistic is in the rejection region, we reject the null hypothesis (
).

Here, the test statistic (TS) was  
 
 
 and the critical value was  
 
 

Here is an illustration of this test in a graph:

Student's T-Distribution with a right tail area (rejection region) equal to 0.01, a critical value of 2.462, and a test statistic of 2.889

Since the test statistic was bigger than the critical value we reject the null hypothesis.

This means that the sample data supports the alternative hypothesis.

And we can summarize the conclusion stating:

The sample data supports the claim that "The average age of Nobel Prize winners when they received the prize is more than 55" at a 1% significance level.

The P-Value Approach
For the P-value approach we need to find the P-value of the test statistic (TS).

If the P-value is smaller than the significance level (
), we reject the null hypothesis (
).

The test statistic was found to be  
 
 

For a population proportion test, the test statistic is a T-Value from a student's t-distribution.

Because this is a right tailed test, we need to find the P-value of a t-value bigger than 2.889.

The student's t-distribution is adjusted according to degrees of freedom (df), which is the sample size  
 
 

We can find the P-value using a T-table, or with a programming language function:

Example
With Python use the Scipy Stats library t.cdf() function find the P-value of a T-value bigger than 2.889 at 29 degrees of freedom (df):

import scipy.stats as stats
print(1-stats.t.cdf(2.889, 29))
Example
With R use the built-in pt() function find the P-value of a T-Value bigger than 2.889 at 29 degrees of freedom (df):

1-pt(2.889, 29)
Using either method we can find that the P-value is  
 
 

This tells us that the significance level (
) would need to be bigger than 0.0036, or 0.36%, to reject the null hypothesis.

Here is an illustration of this test in a graph:



This P-value is smaller than any of the common significance levels (10%, 5%, 1%).

So the null hypothesis is rejected at all of these significance levels.

And we can summarize the conclusion stating:

The sample data supports the claim that "The average age of Nobel Prize winners when they received the prize is more than 55" at a 10%, 5%, or 1% significance level.

Note: An outcome of an hypothesis test that rejects the null hypothesis with a p-value of 0.36% means:

For this p-value, we only expect to reject a true null hypothesis 36 out of 10000 times.

Calculating a P-Value for a Hypothesis Test with Programming
Many programming languages can calculate the P-value to decide outcome of a hypothesis test.

Using software and programming to calculate statistics is more common for bigger sets of data, as calculating manually becomes difficult.

The P-value calculated here will tell us the lowest possible significance level where the null-hypothesis can be rejected.

Example
With Python use the scipy and math libraries to calculate the P-value for a right tailed hypothesis test for a mean.

Here, the sample size is 30, the sample mean is 62.1, the sample standard deviation is 13.46, and the test is for a mean bigger than 55.

import scipy.stats as stats
import math

# Specify the sample mean (x_bar), the sample standard deviation (s), the mean claimed in the null-hypothesis (mu_null), and the sample size (n)
x_bar = 62.1
s = 13.46
mu_null = 55
n = 30

# Calculate the test statistic
test_stat = (x_bar - mu_null)/(s/math.sqrt(n))

# Output the p-value of the test statistic (right tailed test)
print(1-stats.t.cdf(test_stat, n-1))
Example
With R use built-in math and statistics functions find the P-value for a right tailed hypothesis test for a mean.

Here, the sample size is 30, the sample mean is 62.1, the sample standard deviation is 13.46, and the test is for a mean bigger than 55.

# Specify the sample mean (x_bar), the sample standard deviation (s), the mean claimed in the null-hypothesis (mu_null), and the sample size (n)
x_bar <- 62.1
s <- 13.46
mu_null <- 55
n <- 30

# Calculate the test statistic
test_stat = (x_bar - mu_null)/(s/sqrt(n))

# P-value the p-value of the test statistic (right tailed test)
1-pt(test_stat, n-1)
Left-Tailed and Two-Tailed Tests
This was an example of a right tailed test, where the alternative hypothesis claimed that parameter is bigger than the null hypothesis claim.

You can check out an equivalent step-by-step guide for other types here:

Left-Tailed Test
Two-Tailed Test


## Statistics - Z-table
The Z-distribution is a standardized normal distribution where the mean is 0 and the standard deviation is 1.

The Z-distribution can be used to find which percent of a population is within a particular number of standard deviations.

Z-Distribution and Table for Negative Z-values
The numbers in the table cells correspond to the area under the graph.

The area under graph is the probability of getting a value that is smaller than z.

The probabilities are decimal values and can be thought of as percentages. For example: 0.1515 is 15.15%.

Z-Distribution and cumulative probability up to a negative Z-Score.

z	.00	.01	.02	.03	.04	.05	.06	.07	.08	.09
-3.4	0.0003	0.0003	0.0003	0.0003	0.0003	0.0003	0.0003	0.0003	0.0003	0.0002
-3.3	0.0005	0.0005	0.0005	0.0004	0.0004	0.0004	0.0004	0.0004	0.0004	0.0003
-3.2	0.0007	0.0007	0.0006	0.0006	0.0006	0.0006	0.0006	0.0005	0.0005	0.0005
-3.1	0.0010	0.0009	0.0009	0.0009	0.0008	0.0008	0.0008	0.0008	0.0007	0.0007
-3.0	0.0013	0.0013	0.0013	0.0012	0.0012	0.0011	0.0011	0.0011	0.0010	0.0010
-2.9	0.0019	0.0018	0.0018	0.0017	0.0016	0.0016	0.0015	0.0015	0.0014	0.0014
-2.8	0.0026	0.0025	0.0024	0.0023	0.0023	0.0022	0.0021	0.0021	0.0020	0.0019
-2.7	0.0035	0.0034	0.0033	0.0032	0.0031	0.0030	0.0029	0.0028	0.0027	0.0026
-2.6	0.0047	0.0045	0.0044	0.0043	0.0041	0.0040	0.0039	0.0038	0.0037	0.0036
-2.5	0.0062	0.0060	0.0059	0.0057	0.0055	0.0054	0.0052	0.0051	0.0049	0.0048
-2.4	0.0082	0.0080	0.0078	0.0075	0.0073	0.0071	0.0069	0.0068	0.0066	0.0064
-2.3	0.0107	0.0104	0.0102	0.0099	0.0096	0.0094	0.0091	0.0089	0.0087	0.0084
-2.2	0.0139	0.0136	0.0132	0.0129	0.0125	0.0122	0.0119	0.0116	0.0113	0.0110
-2.1	0.0179	0.0174	0.0170	0.0166	0.0162	0.0158	0.0154	0.0150	0.0146	0.0143
-2.0	0.0228	0.0222	0.0217	0.0212	0.0207	0.0202	0.0197	0.0192	0.0188	0.0183
-1.9	0.0287	0.0281	0.0274	0.0268	0.0262	0.0256	0.0250	0.0244	0.0239	0.0233
-1.8	0.0359	0.0351	0.0344	0.0336	0.0329	0.0322	0.0314	0.0307	0.0301	0.0294
-1.7	0.0446	0.0436	0.0427	0.0418	0.0409	0.0401	0.0392	0.0384	0.0375	0.0367
-1.6	0.0548	0.0537	0.0526	0.0516	0.0505	0.0495	0.0485	0.0475	0.0465	0.0455
-1.5	0.0668	0.0655	0.0643	0.0630	0.0618	0.0606	0.0594	0.0582	0.0571	0.0559
-1.4	0.0808	0.0793	0.0778	0.0764	0.0749	0.0735	0.0721	0.0708	0.0694	0.0681
-1.3	0.0968	0.0951	0.0934	0.0918	0.0901	0.0885	0.0869	0.0853	0.0838	0.0823
-1.2	0.1151	0.1131	0.1112	0.1093	0.1075	0.1056	0.1038	0.1020	0.1003	0.0985
-1.1	0.1357	0.1335	0.1314	0.1292	0.1271	0.1251	0.1230	0.1210	0.1190	0.1170
-1.0	0.1587	0.1562	0.1539	0.1515	0.1492	0.1469	0.1446	0.1423	0.1401	0.1379
-0.9	0.1841	0.1814	0.1788	0.1762	0.1736	0.1711	0.1685	0.1660	0.1635	0.1611
-0.8	0.2119	0.2090	0.2061	0.2033	0.2005	0.1977	0.1949	0.1922	0.1894	0.1867
-0.7	0.2420	0.2389	0.2358	0.2327	0.2296	0.2266	0.2236	0.2206	0.2177	0.2148
-0.6	0.2743	0.2709	0.2676	0.2643	0.2611	0.2578	0.2546	0.2514	0.2483	0.2451
-0.5	0.3085	0.3050	0.3015	0.2981	0.2946	0.2912	0.2877	0.2843	0.2810	0.2776
-0.4	0.3446	0.3409	0.3372	0.3336	0.3300	0.3264	0.3228	0.3192	0.3156	0.3121
-0.3	0.3821	0.3783	0.3745	0.3707	0.3669	0.3632	0.3594	0.3557	0.3520	0.3483
-0.2	0.4207	0.4168	0.4129	0.4090	0.4052	0.4013	0.3974	0.3936	0.3897	0.3859
-0.1	0.4602	0.4562	0.4522	0.4483	0.4443	0.4404	0.4364	0.4325	0.4286	0.4247
-0.0	0.5000	0.4960	0.4920	0.4880	0.4840	0.4801	0.4761	0.4721	0.4681	0.4641
Z-Distribution and Table of Positive Z-Values
The numbers in the table cells correspond to the area under the graph.

The area under graph is the probability of getting a value that is smaller than z.

The probabilities are decimal values and can be thought of as percentages. For example: 0.7088 is 70.88%.

Z-Distribution and cumulative probability up to a positive Z-Score.

z	.00	.01	.02	.03	.04	.05	.06	.07	.08	.09
0.0	0.5000	0.5040	0.5080	0.5120	0.5160	0.5199	0.5239	0.5279	0.5319	0.5359
0.1	0.5398	0.5438	0.5478	0.5517	0.5557	0.5596	0.5636	0.5675	0.5714	0.5753
0.2	0.5793	0.5832	0.5871	0.5910	0.5948	0.5987	0.6026	0.6064	0.6103	0.6141
0.3	0.6179	0.6217	0.6255	0.6293	0.6331	0.6368	0.6406	0.6443	0.6480	0.6517
0.4	0.6554	0.6591	0.6628	0.6664	0.6700	0.6736	0.6772	0.6808	0.6844	0.6879
0.5	0.6915	0.6950	0.6985	0.7019	0.7054	0.7088	0.7123	0.7157	0.7190	0.7224
0.6	0.7257	0.7291	0.7324	0.7357	0.7389	0.7422	0.7454	0.7486	0.7517	0.7549
0.7	0.7580	0.7611	0.7642	0.7673	0.7704	0.7734	0.7764	0.7794	0.7823	0.7852
0.8	0.7881	0.7910	0.7939	0.7967	0.7995	0.8023	0.8051	0.8078	0.8106	0.8133
0.9	0.8159	0.8186	0.8212	0.8238	0.8264	0.8289	0.8315	0.8340	0.8365	0.8389
1.0	0.8413	0.8438	0.8461	0.8485	0.8508	0.8531	0.8554	0.8577	0.8599	0.8621
1.1	0.8643	0.8665	0.8686	0.8708	0.8729	0.8749	0.8770	0.8790	0.8810	0.8830
1.2	0.8849	0.8869	0.8888	0.8907	0.8925	0.8944	0.8962	0.8980	0.8997	0.9015
1.3	0.9032	0.9049	0.9066	0.9082	0.9099	0.9115	0.9131	0.9147	0.9162	0.9177
1.4	0.9192	0.9207	0.9222	0.9236	0.9251	0.9265	0.9279	0.9292	0.9306	0.9319
1.5	0.9332	0.9345	0.9357	0.9370	0.9382	0.9394	0.9406	0.9418	0.9429	0.9441
1.6	0.9452	0.9463	0.9474	0.9484	0.9495	0.9505	0.9515	0.9525	0.9535	0.9545
1.7	0.9554	0.9564	0.9573	0.9582	0.9591	0.9599	0.9608	0.9616	0.9625	0.9633
1.8	0.9641	0.9649	0.9656	0.9664	0.9671	0.9678	0.9686	0.9693	0.9699	0.9706
1.9	0.9713	0.9719	0.9726	0.9732	0.9738	0.9744	0.9750	0.9756	0.9761	0.9767
2.0	0.9772	0.9778	0.9783	0.9788	0.9793	0.9798	0.9803	0.9808	0.9812	0.9817
2.1	0.9821	0.9826	0.9830	0.9834	0.9838	0.9842	0.9846	0.9850	0.9854	0.9857
2.2	0.9861	0.9864	0.9868	0.9871	0.9875	0.9878	0.9881	0.9884	0.9887	0.9890
2.3	0.9893	0.9896	0.9898	0.9901	0.9904	0.9906	0.9909	0.9911	0.9913	0.9916
2.4	0.9918	0.9920	0.9922	0.9925	0.9927	0.9929	0.9931	0.9932	0.9934	0.9936
2.5	0.9938	0.9940	0.9941	0.9943	0.9945	0.9946	0.9948	0.9949	0.9951	0.9952
2.6	0.9953	0.9955	0.9956	0.9957	0.9959	0.9960	0.9961	0.9962	0.9963	0.9964
2.7	0.9965	0.9966	0.9967	0.9968	0.9969	0.9970	0.9971	0.9972	0.9973	0.9974
2.8	0.9974	0.9975	0.9976	0.9977	0.9977	0.9978	0.9979	0.9979	0.9980	0.9981
2.9	0.9981	0.9982	0.9982	0.9983	0.9984	0.9984	0.9985	0.9985	0.9986	0.9986
3.0	0.9987	0.9987	0.9987	0.9988	0.9988	0.9989	0.9989	0.9989	0.9990	0.9990
3.1	0.9990	0.9991	0.9991	0.9991	0.9992	0.9992	0.9992	0.9992	0.9993	0.9993
3.2	0.9993	0.9993	0.9994	0.9994	0.9994	0.9994	0.9994	0.9995	0.9995	0.9995
3.3	0.9995	0.9995	0.9995	0.9996	0.9996	0.9996	0.9996	0.9996	0.9996	0.9997
3.4	0.9997	0.9997	0.9997	0.9997	0.9997	0.9997	0.9997	0.9997	0.9997	0.9998
Example of How to Use the Z-Table
The Z-value is found combining the numbers in the first column and the first row.

For example, the probability for getting a z-value smaller than 1.85 is found by finding the number in the table where the row is 1.8 and the column is 0.05.

So the probability is: 0.9678 is 96.78%.

Z-Distribution and cumulative probability up to a positive Z-Score.

z	.00	.01	.02	.03	.04	.05	.06	.07	.08	.09
0.0	0.5000	0.5040	0.5080	0.5120	0.5160	0.5199	0.5239	0.5279	0.5319	0.5359
0.1	0.5398	0.5438	0.5478	0.5517	0.5557	0.5596	0.5636	0.5675	0.5714	0.5753
0.2	0.5793	0.5832	0.5871	0.5910	0.5948	0.5987	0.6026	0.6064	0.6103	0.6141
0.3	0.6179	0.6217	0.6255	0.6293	0.6331	0.6368	0.6406	0.6443	0.6480	0.6517
0.4	0.6554	0.6591	0.6628	0.6664	0.6700	0.6736	0.6772	0.6808	0.6844	0.6879
0.5	0.6915	0.6950	0.6985	0.7019	0.7054	0.7088	0.7123	0.7157	0.7190	0.7224
0.6	0.7257	0.7291	0.7324	0.7357	0.7389	0.7422	0.7454	0.7486	0.7517	0.7549
0.7	0.7580	0.7611	0.7642	0.7673	0.7704	0.7734	0.7764	0.7794	0.7823	0.7852
0.8	0.7881	0.7910	0.7939	0.7967	0.7995	0.8023	0.8051	0.8078	0.8106	0.8133
0.9	0.8159	0.8186	0.8212	0.8238	0.8264	0.8289	0.8315	0.8340	0.8365	0.8389
1.0	0.8413	0.8438	0.8461	0.8485	0.8508	0.8531	0.8554	0.8577	0.8599	0.8621
1.1	0.8643	0.8665	0.8686	0.8708	0.8729	0.8749	0.8770	0.8790	0.8810	0.8830
1.2	0.8849	0.8869	0.8888	0.8907	0.8925	0.8944	0.8962	0.8980	0.8997	0.9015
1.3	0.9032	0.9049	0.9066	0.9082	0.9099	0.9115	0.9131	0.9147	0.9162	0.9177
1.4	0.9192	0.9207	0.9222	0.9236	0.9251	0.9265	0.9279	0.9292	0.9306	0.9319
1.5	0.9332	0.9345	0.9357	0.9370	0.9382	0.9394	0.9406	0.9418	0.9429	0.9441
1.6	0.9452	0.9463	0.9474	0.9484	0.9495	0.9505	0.9515	0.9525	0.9535	0.9545
1.7	0.9554	0.9564	0.9573	0.9582	0.9591	0.9599	0.9608	0.9616	0.9625	0.9633
1.8	0.9641	0.9649	0.9656	0.9664	0.9671	0.9678	0.9686	0.9693	0.9699	0.9706
1.9	0.9713	0.9719	0.9726	0.9732	0.9738	0.9744	0.9750	0.9756	0.9761	0.9767
2.0	0.9772	0.9778	0.9783	0.9788	0.9793	0.9798	0.9803	0.9808	0.9812	0.9817
2.1	0.9821	0.9826	0.9830	0.9834	0.9838	0.9842	0.9846	0.9850	0.9854	0.9857
2.2	0.9861	0.9864	0.9868	0.9871	0.9875	0.9878	0.9881	0.9884	0.9887	0.9890
2.3	0.9893	0.9896	0.9898	0.9901	0.9904	0.9906	0.9909	0.9911	0.9913	0.9916
2.4	0.9918	0.9920	0.9922	0.9925	0.9927	0.9929	0.9931	0.9932	0.9934	0.9936
2.5	0.9938	0.9940	0.9941	0.9943	0.9945	0.9946	0.9948	0.9949	0.9951	0.9952
2.6	0.9953	0.9955	0.9956	0.9957	0.9959	0.9960	0.9961	0.9962	0.9963	0.9964
2.7	0.9965	0.9966	0.9967	0.9968	0.9969	0.9970	0.9971	0.9972	0.9973	0.9974
2.8	0.9974	0.9975	0.9976	0.9977	0.9977	0.9978	0.9979	0.9979	0.9980	0.9981
2.9	0.9981	0.9982	0.9982	0.9983	0.9984	0.9984	0.9985	0.9985	0.9986	0.9986
3.0	0.9987	0.9987	0.9987	0.9988	0.9988	0.9989	0.9989	0.9989	0.9990	0.9990
3.1	0.9990	0.9991	0.9991	0.9991	0.9992	0.9992	0.9992	0.9992	0.9993	0.9993
3.2	0.9993	0.9993	0.9994	0.9994	0.9994	0.9994	0.9994	0.9995	0.9995	0.9995
3.3	0.9995	0.9995	0.9995	0.9996	0.9996	0.9996	0.9996	0.9996	0.9996	0.9997
3.4	0.9997	0.9997	0.9997	0.9997	0.9997	0.9997	0.9997	0.9997	0.9997	0.9998


## Statistics - T-table
The Student's t-distribution is similar to a normal distribution. But it is adjusted for uncertainty with smaller sample sizes.

Smaller sample sizes give fewer degrees of freedom (df), which makes the tails larger.

T-Distribution and Table of Critical T-Values
The numbers in the table cells correspond to critical t-values for different tail-areas (α).

The tail areas are probabilities. For example, 0.05 is 5% percent probability.

Each row corresponds to different degrees of freedom (df).

Left: T-Distribution and right tail area with critical t-value. Right: T-Distribution and two tail areas with critical t-values.

One tail	0.05	0.025	0.01	0.005	0.0025	0.001	0.0005
Two tails	0.1	0.05	0.02	0.01	0.005	0.002	0.001
df							
1	6.3138	12.7062	31.8205	63.6567	127.3213	318.3088	636.6192
2	2.9200	4.3027	6.9646	9.9248	14.0890	22.3271	31.5991
3	2.3534	3.1824	4.5407	5.8409	7.4533	10.2145	12.9240
4	2.1318	2.7764	3.7469	4.6041	5.5976	7.1732	8.6103
5	2.0150	2.5706	3.3649	4.0321	4.7733	5.8934	6.8688
6	1.9432	2.4469	3.1427	3.7074	4.3168	5.2076	5.9588
7	1.8946	2.3646	2.9980	3.4995	4.0293	4.7853	5.4079
8	1.8595	2.3060	2.8965	3.3554	3.8325	4.5008	5.0413
9	1.8331	2.2622	2.8214	3.2498	3.6897	4.2968	4.7809
10	1.8125	2.2281	2.7638	3.1693	3.5814	4.1437	4.5869
11	1.7959	2.2010	2.7181	3.1058	3.4966	4.0247	4.4370
12	1.7823	2.1788	2.6810	3.0545	3.4284	3.9296	4.3178
13	1.7709	2.1604	2.6503	3.0123	3.3725	3.8520	4.2208
14	1.7613	2.1448	2.6245	2.9768	3.3257	3.7874	4.1405
15	1.7531	2.1314	2.6025	2.9467	3.2860	3.7328	4.0728
16	1.7459	2.1199	2.5835	2.9208	3.2520	3.6862	4.0150
17	1.7396	2.1098	2.5669	2.8982	3.2224	3.6458	3.9651
18	1.7341	2.1009	2.5524	2.8784	3.1966	3.6105	3.9216
19	1.7291	2.0930	2.5395	2.8609	3.1737	3.5794	3.8834
20	1.7247	2.0860	2.5280	2.8453	3.1534	3.5518	3.8495
21	1.7207	2.0796	2.5176	2.8314	3.1352	3.5272	3.8193
22	1.7171	2.0739	2.5083	2.8188	3.1188	3.5050	3.7921
23	1.7139	2.0687	2.4999	2.8073	3.1040	3.4850	3.7676
24	1.7109	2.0639	2.4922	2.7969	3.0905	3.4668	3.7454
25	1.7081	2.0595	2.4851	2.7874	3.0782	3.4502	3.7251
26	1.7056	2.0555	2.4786	2.7787	3.0669	3.4350	3.7066
27	1.7033	2.0518	2.4727	2.7707	3.0565	3.4210	3.6896
28	1.7011	2.0484	2.4671	2.7633	3.0469	3.4082	3.6739
29	1.6991	2.0452	2.4620	2.7564	3.0380	3.3962	3.6594
30	1.6973	2.0423	2.4573	2.7500	3.0298	3.3852	3.6460
31	1.6955	2.0395	2.4528	2.7440	3.0221	3.3749	3.6335
32	1.6939	2.0369	2.4487	2.7385	3.0149	3.3653	3.6218
33	1.6924	2.0345	2.4448	2.7333	3.0082	3.3563	3.6109
34	1.6909	2.0322	2.4411	2.7284	3.0020	3.3479	3.6007
35	1.6896	2.0301	2.4377	2.7238	2.9960	3.3400	3.5911
36	1.6883	2.0281	2.4345	2.7195	2.9905	3.3326	3.5821
37	1.6871	2.0262	2.4314	2.7154	2.9852	3.3256	3.5737
38	1.6860	2.0244	2.4286	2.7116	2.9803	3.3190	3.5657
39	1.6849	2.0227	2.4258	2.7079	2.9756	3.3128	3.5581
40	1.6839	2.0211	2.4233	2.7045	2.9712	3.3069	3.5510
41	1.6829	2.0195	2.4208	2.7012	2.9670	3.3013	3.5442
42	1.6820	2.0181	2.4185	2.6981	2.9630	3.2960	3.5377
43	1.6811	2.0167	2.4163	2.6951	2.9592	3.2909	3.5316
44	1.6802	2.0154	2.4141	2.6923	2.9555	3.2861	3.5258
45	1.6794	2.0141	2.4121	2.6896	2.9521	3.2815	3.5203
46	1.6787	2.0129	2.4102	2.6870	2.9488	3.2771	3.5150
47	1.6779	2.0117	2.4083	2.6846	2.9456	3.2729	3.5099
48	1.6772	2.0106	2.4066	2.6822	2.9426	3.2689	3.5051
49	1.6766	2.0096	2.4049	2.6800	2.9397	3.2651	3.5004
50	1.6759	2.0086	2.4033	2.6778	2.9370	3.2614	3.4960
60	1.6706	2.0003	2.3901	2.6603	2.9146	3.2317	3.4602
70	1.6669	1.9944	2.3808	2.6479	2.8987	3.2108	3.4350
80	1.6641	1.9901	2.3739	2.6387	2.8870	3.1953	3.4163
90	1.6620	1.9867	2.3685	2.6316	2.8779	3.1833	3.4019
100	1.6602	1.9840	2.3642	2.6259	2.8707	3.1737	3.3905
200	1.6525	1.9719	2.3451	2.6006	2.8385	3.1315	3.3398
300	1.6499	1.9679	2.3388	2.5923	2.8279	3.1176	3.3233
400	1.6487	1.9659	2.3357	2.5882	2.8227	3.1107	3.3150
500	1.6479	1.9647	2.3338	2.5857	2.8195	3.1066	3.3101
600	1.6474	1.9639	2.3326	2.5840	2.8175	3.1039	3.3068
700	1.6470	1.9634	2.3317	2.5829	2.8160	3.1019	3.3045
800	1.6468	1.9629	2.3310	2.5820	2.8148	3.1005	3.3027
900	1.6465	1.9626	2.3305	2.5813	2.8140	3.0993	3.3014
1000	1.6464	1.9623	2.3301	2.5808	2.8133	3.0984	3.3003
10000	1.6450	1.9602	2.3267	2.5763	2.8077	3.0910	3.2915
∞	1.6449	1.9600	2.3263	2.5758	2.8070	3.0902	3.2905

## Statistics - Hypothesis Testing a Proportion (Left Tailed)
A population proportion is the share of a population that belongs to a particular category.

Hypothesis tests are used to check a claim about the size of that population proportion.

Hypothesis Testing a Proportion
The following steps are used for a hypothesis test:

Check the conditions
Define the claims
Decide the significance level
Calculate the test statistic
Conclusion
For example:

Population: Nobel Prize winners
Category: Born in the United States of America
And we want to check the claim:

"Less than 45% of Nobel Prize winners were born in the US"

By taking a sample of 40 randomly selected Nobel Prize winners we could find that:

10 out of 40 Nobel Prize winners in the sample were born in the US

The sample proportion is then: 
 
, or 25%.

From this sample data we check the claim with the steps below.

1. Checking the Conditions
The conditions for calculating a confidence interval for a proportion are:

The sample is randomly selected
There is only two options:
Being in the category
Not being in the category
The sample needs at least:
5 members in the category
5 members not in the category
In our example, we randomly selected 10 people that were born in the US.

The rest were not born in the US, so there are 30 in the other category.

The conditions are fulfilled in this case.

Note: It is possible to do a hypothesis test without having 5 of each category. But special adjustments need to be made.

2. Defining the Claims
We need to define a null hypothesis (
) and an alternative hypothesis (
) based on the claim we are checking.

The claim was:

"Less than 45% of Nobel Prize winners were born in the US"

In this case, the parameter is the proportion of Nobel Prize winners born in the US (
).

The null and alternative hypothesis are then:

Null hypothesis: 45% of Nobel Prize winners were born in the US.

Alternative hypothesis: Less than 45% of Nobel Prize winners were born in the US.

Which can be expressed with symbols as:

: 

: 

This is a 'left tailed' test, because the alternative hypothesis claims that the proportion is less than in the null hypothesis.

If the data supports the alternative hypothesis, we reject the null hypothesis and accept the alternative hypothesis.

3. Deciding the Significance Level
The significance level (
) is the uncertainty we accept when rejecting the null hypothesis in a hypothesis test.

The significance level is a percentage probability of accidentally making the wrong conclusion.

Typical significance levels are:

 (10%)
 (5%)
 (1%)
A lower significance level means that the evidence in the data needs to be stronger to reject the null hypothesis.

There is no "correct" significance level - it only states the uncertainty of the conclusion.

Note: A 5% significance level means that when we reject a null hypothesis:

We expect to reject a true null hypothesis 5 out of 100 times.

4. Calculating the Test Statistic
The test statistic is used to decide the outcome of the hypothesis test.

The test statistic is a standardized value calculated from the sample.

The formula for the test statistic (TS) of a population proportion is:

 

 is the difference between the sample proportion (
) and the claimed population proportion (
).

 is the sample size.

In our example:

The claimed (
) population proportion (
) was 

The sample proportion (
) was 10 out of 40, or: 
 

The sample size (
) was 

So the test statistic (TS) is then:

 
 
 
 
 
 

You can also calculate the test statistic using programming language functions:

ExampleGet your own Python Server
With Python use the scipy and math libraries to calculate the test statistic for a proportion.

import scipy.stats as stats
import math

# Specify the number of occurrences (x), the sample size (n), and the proportion claimed in the null-hypothesis (p)
x = 10
n = 40
p = 0.45

# Calculate the sample proportion
p_hat = x/n

# Calculate and print the test statistic
print((p_hat-p)/(math.sqrt((p*(1-p))/(n))))
Example
With R use the built-in math functions to calculate the test statistic for a proportion.

# Specify the sample occurrences (x), the sample size (n), and the null-hypothesis claim (p)
x <- 10
n <- 40
p <- 0.45

# Calculate the sample proportion
p_hat = x/n

# Calculate and output the test statistic
(p_hat-p)/(sqrt((p*(1-p))/(n)))
5. Concluding
There are two main approaches for making the conclusion of a hypothesis test:

The critical value approach compares the test statistic with the critical value of the significance level.
The P-value approach compares the P-value of the test statistic and with the significance level.
Note: The two approaches are only different in how they present the conclusion.

The Critical Value Approach
For the critical value approach we need to find the critical value (CV) of the significance level (
).

For a population proportion test, the critical value (CV) is a Z-value from a standard normal distribution.

This critical Z-value (CV) defines the rejection region for the test.

The rejection region is an area of probability in the tails of the standard normal distribution.

Because the claim is that the population proportion is less than 45%, the rejection region is in the left tail:

Standard Normal Distribution with a left tail area (rejection region) denoted as the greek symbol alpha

The size of the rejection region is decided by the significance level (
).

Choosing a significance level (
) of 0.01, or 1%, we can find the critical Z-value from a Z-table, or with a programming language function:

Example
With Python use the Scipy Stats library norm.ppf() function find the Z-value for an 
 = 0.01 in the left tail.

import scipy.stats as stats
print(stats.norm.ppf(0.01))
Example
With R use the built-in qnorm() function to find the Z-value for an 
 = 0.01 in the left tail.

qnorm(0.01)
Using either method we can find that the critical Z-value is  
 
 

For a left tailed test we need to check if the test statistic (TS) is smaller than the critical value (CV).

If the test statistic is smaller than the critical value, the test statistic is in the rejection region.

When the test statistic is in the rejection region, we reject the null hypothesis (
).

Here, the test statistic (TS) was  
 
 
 and the critical value was  
 
 

Here is an illustration of this test in a graph:

Standard Normal Distribution with a left tail area (rejection region) equal to 0.01, a critical value of -2.3263, and a test statistic of -2.543

Since the test statistic was smaller than the critical value we reject the null hypothesis.

This means that the sample data supports the alternative hypothesis.

And we can summarize the conclusion stating:

The sample data supports the claim that "less than 45% of Nobel Prize winners were born in the US" at a 1% significance level.

The P-Value Approach
For the P-value approach we need to find the P-value of the test statistic (TS).

If the P-value is smaller than the significance level (
), we reject the null hypothesis (
).

The test statistic was found to be  
 
 

For a population proportion test, the test statistic is a Z-Value from a standard normal distribution.

Because this is a left tailed test, we need to find the P-value of a Z-value smaller than -2.543.

We can find the P-value using a Z-table, or with a programming language function:

Example
With Python use the Scipy Stats library norm.cdf() function find the P-value of a Z-value smaller than -2.543:

import scipy.stats as stats
print(stats.norm.cdf(-2.543))
Example
With R use the built-in pnorm() function find the P-value of a Z-value smaller than -2.543:

pnorm(-2.543)
Using either method we can find that the P-value is  
 
 

This tells us that the significance level (
) would need to be bigger than 0.0055, or 0.55%, to reject the null hypothesis.

Here is an illustration of this test in a graph:



This P-value is smaller than any of the common significance levels (10%, 5%, 1%).

So the null hypothesis is rejected at all of these significance levels.

And we can summarize the conclusion stating:

The sample data supports the claim that "less than 45% of Nobel Prize winners were born in the US" at a 10%, 5%, and 1% significance level.

Calculating a P-Value for a Hypothesis Test with Programming
Many programming languages can calculate the P-value to decide outcome of a hypothesis test.

Using software and programming to calculate statistics is more common for bigger sets of data, as calculating manually becomes difficult.

The P-value calculated here will tell us the lowest possible significance level where the null-hypothesis can be rejected.

Example
With Python use the scipy and math libraries to calculate the P-value for a left tailed hypothesis test for a proportion.

Here, the sample size is 40, the occurrences are 10, and the test is for a proportion smaller than 0.45.

import scipy.stats as stats
import math

# Specify the number of occurrences (x), the sample size (n), and the proportion claimed in the null-hypothesis (p)
x = 10
n = 40
p = 0.45

# Calculate the sample proportion
p_hat = x/n

# Calculate the test statistic
test_stat = (p_hat-p)/(math.sqrt((p*(1-p))/(n)))

# Output the p-value of the test statistic (left tailed test)
print(stats.norm.cdf(test_stat))
Example
With R use the built-in prop.test() function find the P-value for a left tailed hypothesis test for a proportion.

Here, the sample size is 40, the occurrences are 10, and the test is for a proportion bigger than 0.45.

# Specify the sample occurrences (x), the sample size (n), and the null-hypothesis claim (p)
x <- 10
n <- 40
p <- 0.45

# P-value from left-tail proportion test at 0.01 significance level
prop.test(x, n, p, alternative = c("less"), conf.level = 0.99, correct = FALSE)$p.value
Note: The conf.level in the R code is the reverse of the significance level.

Here, the significance level is 0.01, or 1%, so the conf.level is 1-0.01 = 0.99, or 99%.

Left-Tailed and Two-Tailed Tests
This was an example of a left tailed test, where the alternative hypothesis claimed that parameter is smaller than the null hypothesis claim.

You can check out an equivalent step-by-step guide for other types here:

Right-Tailed Test
Two-Tailed Test

## Statistics - Hypothesis Testing a Proportion (Two Tailed)
A population proportion is the share of a population that belongs to a particular category.

Hypothesis tests are used to check a claim about the size of that population proportion.

Hypothesis Testing a Proportion
The following steps are used for a hypothesis test:

Check the conditions
Define the claims
Decide the significance level
Calculate the test statistic
Conclusion
For example:

Population: Nobel Prize winners
Category: Women
And we want to check the claim:

"The share of Nobel Prize winners that are women is not 50%"

By taking a sample of 100 randomly selected Nobel Prize winners we could find that:

10 out of 100 Nobel Prize winners in the sample were women

The sample proportion is then: 
 
, or 10%.

From this sample data we check the claim with the steps below.

1. Checking the Conditions
The conditions for calculating a confidence interval for a proportion are:

The sample is randomly selected
There is only two options:
Being in the category
Not being in the category
The sample needs at least:
5 members in the category
5 members not in the category
In our example, we randomly selected 10 people that were women.

The rest were not women, so there are 90 in the other category.

The conditions are fulfilled in this case.

Note: It is possible to do a hypothesis test without having 5 of each category. But special adjustments need to be made.

2. Defining the Claims
We need to define a null hypothesis (
) and an alternative hypothesis (
) based on the claim we are checking.

The claim was:

"The share of Nobel Prize winners that are women is not 50%"

In this case, the parameter is the proportion of Nobel Prize winners that are women (
).

The null and alternative hypothesis are then:

Null hypothesis: 50% of Nobel Prize winners were women.

Alternative hypothesis: The share of Nobel Prize winners that are women is not 50%

Which can be expressed with symbols as:

: 

: 

This is a 'two-tailed' test, because the alternative hypothesis claims that the proportion is different (larger or smaller) than in the null hypothesis.

If the data supports the alternative hypothesis, we reject the null hypothesis and accept the alternative hypothesis.

3. Deciding the Significance Level
The significance level (
) is the uncertainty we accept when rejecting the null hypothesis in a hypothesis test.

The significance level is a percentage probability of accidentally making the wrong conclusion.

Typical significance levels are:

 (10%)
 (5%)
 (1%)
A lower significance level means that the evidence in the data needs to be stronger to reject the null hypothesis.

There is no "correct" significance level - it only states the uncertainty of the conclusion.

Note: A 5% significance level means that when we reject a null hypothesis:

We expect to reject a true null hypothesis 5 out of 100 times.

4. Calculating the Test Statistic
The test statistic is used to decide the outcome of the hypothesis test.

The test statistic is a standardized value calculated from the sample.

The formula for the test statistic (TS) of a population proportion is:

 

 is the difference between the sample proportion (
) and the claimed population proportion (
).

 is the sample size.

In our example:

The claimed (
) population proportion (
) was 

The sample proportion (
) was 10 out of 100, or: 
 

The sample size (
) was 

So the test statistic (TS) is then:

 
 
 
 
 
 

You can also calculate the test statistic using programming language functions:

ExampleGet your own Python Server
With Python use the scipy and math libraries to calculate the test statistic for a proportion.

import scipy.stats as stats
import math

# Specify the number of occurrences (x), the sample size (n), and the proportion claimed in the null-hypothesis (p)
x = 10
n = 100
p = 0.5

# Calculate the sample proportion
p_hat = x/n

# Calculate and print the test statistic
print((p_hat-p)/(math.sqrt((p*(1-p))/(n))))
Example
With R use the built-in math functions to calculate the test statistic for a proportion.

# Specify the sample occurrences (x), the sample size (n), and the null-hypothesis claim (p)
x <- 10
n <- 100
p <- 0.5

# Calculate the sample proportion
p_hat = x/n

# Calculate and output the test statistic
(p_hat-p)/(sqrt((p*(1-p))/(n)))
5. Concluding
There are two main approaches for making the conclusion of a hypothesis test:

The critical value approach compares the test statistic with the critical value of the significance level.
The P-value approach compares the P-value of the test statistic and with the significance level.
Note: The two approaches are only different in how they present the conclusion.

The Critical Value Approach
For the critical value approach we need to find the critical value (CV) of the significance level (
).

For a population proportion test, the critical value (CV) is a Z-value from a standard normal distribution.

This critical Z-value (CV) defines the rejection region for the test.

The rejection region is an area of probability in the tails of the standard normal distribution.

Because the claim is that the population proportion is different from 50%, the rejection region is split into both the left and right tail:

Standard Normal Distribution with a left and right tail area (rejection region) denoted as the greek symbol alpha

The size of the rejection region is decided by the significance level (
).

Choosing a significance level (
) of 0.01, or 1%, we can find the critical Z-value from a Z-table, or with a programming language function:

Note: Because this is a two-tailed test the tail area (
) needs to be split in half (divided by 2).

Example
With Python use the Scipy Stats library norm.ppf() function find the Z-value for an 
/2 = 0.005 in the left tail.

import scipy.stats as stats
print(stats.norm.ppf(0.005))
Example
With R use the built-in qnorm() function to find the Z-value for an 
 = 0.005 in the left tail.

qnorm(0.005)
Using either method we can find that the critical Z-value in the left tail is  
 
 

Since a normal distribution i symmetric, we know that the critical Z-value in the right tail will be the same number, only positive:  
 
 

For a two-tailed test we need to check if the test statistic (TS) is smaller than the negative critical value (-CV), or bigger than the positive critical value (CV).

If the test statistic is smaller than the negative critical value, the test statistic is in the rejection region.

If the test statistic is bigger than the positive critical value, the test statistic is in the rejection region.

When the test statistic is in the rejection region, we reject the null hypothesis (
).

Here, the test statistic (TS) was  
 
 
 and the critical value was  
 
 

Here is an illustration of this test in a graph:

Standard Normal Distribution with a left tail area (rejection region) equal to 0.01, a critical value of -2.3263, and a test statistic of -2.543

Since the test statistic was smaller than the negative critical value we reject the null hypothesis.

This means that the sample data supports the alternative hypothesis.

And we can summarize the conclusion stating:

The sample data supports the claim that "The share of Nobel Prize winners that are women is not 50%" at a 1% significance level.

The P-Value Approach
For the P-value approach we need to find the P-value of the test statistic (TS).

If the P-value is smaller than the significance level (
), we reject the null hypothesis (
).

The test statistic was found to be  
 
 

For a population proportion test, the test statistic is a Z-Value from a standard normal distribution.

Because this is a two-tailed test, we need to find the P-value of a Z-value smaller than -8 and multiply it by 2.

We can find the P-value using a Z-table, or with a programming language function:

Example
With Python use the Scipy Stats library norm.cdf() function find the P-value of a Z-value smaller than -8 for a two tailed test:

import scipy.stats as stats
print(2*stats.norm.cdf(-8))
Example
With R use the built-in pnorm() function find the P-value of a Z-value smaller than -8 for a two tailed test:

2*pnorm(-8)
Using either method we can find that the P-value is  
 
 
 or 

This tells us that the significance level (
) would need to be bigger than 0.000000000000125%, to reject the null hypothesis.

Here is an illustration of this test in a graph:



This P-value is smaller than any of the common significance levels (10%, 5%, 1%).

So the null hypothesis is rejected at all of these significance levels.

And we can summarize the conclusion stating:

The sample data supports the claim that "The share of Nobel Prize winners that are women is not 50%" at a 10%, 5%, and 1% significance level.

Calculating a P-Value for a Hypothesis Test with Programming
Many programming languages can calculate the P-value to decide outcome of a hypothesis test.

Using software and programming to calculate statistics is more common for bigger sets of data, as calculating manually becomes difficult.

The P-value calculated here will tell us the lowest possible significance level where the null-hypothesis can be rejected.

Example
With Python use the scipy and math libraries to calculate the P-value for a two-tailed tailed hypothesis test for a proportion.

Here, the sample size is 100, the occurrences are 10, and the test is for a proportion different from than 0.50.

import scipy.stats as stats
import math

# Specify the number of occurrences (x), the sample size (n), and the proportion claimed in the null-hypothesis (p)
x = 10
n = 100
p = 0.5

# Calculate the sample proportion
p_hat = x/n

# Calculate the test statistic
test_stat = (p_hat-p)/(math.sqrt((p*(1-p))/(n)))

# Output the p-value of the test statistic (two-tailed test)
print(2*stats.norm.cdf(test_stat))
Example
With R use the built-in prop.test() function find the P-value for a left tailed hypothesis test for a proportion.

Here, the sample size is 100, the occurrences are 10, and the test is for a proportion different from 0.50.

# Specify the sample occurrences (x), the sample size (n), and the null-hypothesis claim (p)
x <- 10
n <- 100
p <- 0.5

# P-value from left-tail proportion test at 0.01 significance level
prop.test(x, n, p, alternative = c("two.sided"), conf.level = 0.99, correct = FALSE)$p.value
Note: The conf.level in the R code is the reverse of the significance level.

Here, the significance level is 0.01, or 1%, so the conf.level is 1-0.01 = 0.99, or 99%.

Left-Tailed and Two-Tailed Tests
This was an example of a two tailed test, where the alternative hypothesis claimed that parameter is different from the null hypothesis claim.

You can check out an equivalent step-by-step guide for other types here:

Right-Tailed Test
Left-Tailed Test

## Statistics - Hypothesis Testing a Mean (Left Tailed)
A population mean is an average of value a population.

Hypothesis tests are used to check a claim about the size of that population mean.

Hypothesis Testing a Mean
The following steps are used for a hypothesis test:

Check the conditions
Define the claims
Decide the significance level
Calculate the test statistic
Conclusion
For example:

Population: Nobel Prize winners
Category: Age when they received the prize.
And we want to check the claim:

"The average age of Nobel Prize winners when they received the prize is less than 60"

By taking a sample of 30 randomly selected Nobel Prize winners we could find that:

The mean age in the sample (
) is 62.1

The standard deviation of age in the sample (
) is 13.46

From this sample data we check the claim with the steps below.

1. Checking the Conditions
The conditions for calculating a confidence interval for a proportion are:

The sample is randomly selected
And either:
The population data is normally distributed
Sample size is large enough
A moderately large sample size, like 30, is typically large enough.

In the example, the sample size was 30 and it was randomly selected, so the conditions are fulfilled.

Note: Checking if the data is normally distributed can be done with specialized statistical tests.

2. Defining the Claims
We need to define a null hypothesis (
) and an alternative hypothesis (
) based on the claim we are checking.

The claim was:

"The average age of Nobel Prize winners when they received the prize is less than 60"

In this case, the parameter is the mean age of Nobel Prize winners when they received the prize (
).

The null and alternative hypothesis are then:

Null hypothesis: The average age was 60.

Alternative hypothesis: The average age was less than 60.

Which can be expressed with symbols as:

: 

: 

This is a 'left tailed' test, because the alternative hypothesis claims that the proportion is less than in the null hypothesis.

If the data supports the alternative hypothesis, we reject the null hypothesis and accept the alternative hypothesis.

3. Deciding the Significance Level
The significance level (
) is the uncertainty we accept when rejecting the null hypothesis in a hypothesis test.

The significance level is a percentage probability of accidentally making the wrong conclusion.

Typical significance levels are:

 (10%)
 (5%)
 (1%)
A lower significance level means that the evidence in the data needs to be stronger to reject the null hypothesis.

There is no "correct" significance level - it only states the uncertainty of the conclusion.

Note: A 5% significance level means that when we reject a null hypothesis:

We expect to reject a true null hypothesis 5 out of 100 times.

4. Calculating the Test Statistic
The test statistic is used to decide the outcome of the hypothesis test.

The test statistic is a standardized value calculated from the sample.

The formula for the test statistic (TS) of a population mean is:

 

 is the difference between the sample mean (
) and the claimed population mean (
).

 is the sample standard deviation.

 is the sample size.

In our example:

The claimed (
) population mean (
) was 

The sample mean (
) was 

The sample standard deviation (
) was 

The sample size (
) was 

So the test statistic (TS) is then:

 
 
 
 

You can also calculate the test statistic using programming language functions:

ExampleGet your own Python Server
With Python use the scipy and math libraries to calculate the test statistic.

import scipy.stats as stats
import math

# Specify the sample mean (x_bar), the sample standard deviation (s), the mean claimed in the null-hypothesis (mu_null), and the sample size (n)
x_bar = 62.1
s = 13.46
mu_null = 60
n = 30

# Calculate and print the test statistic
print((x_bar - mu_null)/(s/math.sqrt(n)))
Example
With R use built-in math and statistics functions to calculate the test statistic.

# Specify the sample mean (x_bar), the sample standard deviation (s), the mean claimed in the null-hypothesis (mu_null), and the sample size (n)
x_bar <- 62.1
s <- 13.46
mu_null <- 60
n <- 30

# Output the test statistic
(x_bar - mu_null)/(s/sqrt(n))
5. Concluding
There are two main approaches for making the conclusion of a hypothesis test:

The critical value approach compares the test statistic with the critical value of the significance level.
The P-value approach compares the P-value of the test statistic and with the significance level.
Note: The two approaches are only different in how they present the conclusion.

The Critical Value Approach
For the critical value approach we need to find the critical value (CV) of the significance level (
).

For a population mean test, the critical value (CV) is a T-value from a student's t-distribution.

This critical T-value (CV) defines the rejection region for the test.

The rejection region is an area of probability in the tails of the standard normal distribution.

Because the claim is that the population mean is less than 60, the rejection region is in the left tail:

Student's T-Distribution with a left tail area (rejection region) denoted as the greek symbol alpha

The size of the rejection region is decided by the significance level (
).

The student's t-distribution is adjusted for the uncertainty from smaller samples.

This adjustment is called degrees of freedom (df), which is the sample size 

In this case the degrees of freedom (df) is:  
 
 

Choosing a significance level (
) of 0.05, or 5%, we can find the critical T-value from a T-table, or with a programming language function:

Example
With Python use the Scipy Stats library t.ppf() function find the T-Value for an 
 = 0.05 at 29 degrees of freedom (df).

import scipy.stats as stats
print(stats.t.ppf(0.05, 29))
Example
With R use the built-in qt() function to find the t-value for an 
 = 0.05 at 29 degrees of freedom (df).

qt(0.05, 29)
Using either method we can find that the critical T-Value is  
 
 

For a left tailed test we need to check if the test statistic (TS) is smaller than the critical value (CV).

If the test statistic is smaller the critical value, the test statistic is in the rejection region.

When the test statistic is in the rejection region, we reject the null hypothesis (
).

Here, the test statistic (TS) was  
 
 
 and the critical value was  
 
 

Here is an illustration of this test in a graph:

Student's T-Distribution with a left tail area (rejection region) equal to 0.01, a critical value of 2.462, and a test statistic of 2.889

Since the test statistic was bigger than the critical value we keep the null hypothesis.

This means that the sample data does not support the alternative hypothesis.

And we can summarize the conclusion stating:

The sample data does not support the claim that "The average age of Nobel Prize winners when they received the prize is less than 60" at a 5% significance level.

The P-Value Approach
For the P-value approach we need to find the P-value of the test statistic (TS).

If the P-value is smaller than the significance level (
), we reject the null hypothesis (
).

The test statistic was found to be  
 
 

For a population proportion test, the test statistic is a T-Value from a student's t-distribution.

Because this is a left tailed test, we need to find the P-value of a t-value smaller than 0.855.

The student's t-distribution is adjusted according to degrees of freedom (df), which is the sample size  
 
 

We can find the P-value using a T-table, or with a programming language function:

Example
With Python use the Scipy Stats library t.cdf() function find the P-value of a T-value smaller than 0.855 at 29 degrees of freedom (df):

import scipy.stats as stats
print(stats.t.cdf(0.855, 29))
Example
With R use the built-in pt() function find the P-value of a T-Value smaller than 0.855 at 29 degrees of freedom (df):

pt(0.855, 29)
Using either method we can find that the P-value is  
 
 

This tells us that the significance level (
) would need to be smaller 0.80, or 80%, to reject the null hypothesis.

Here is an illustration of this test in a graph:



This P-value is far bigger than any of the common significance levels (10%, 5%, 1%).

So the null hypothesis is kept at all of these significance levels.

And we can summarize the conclusion stating:

The sample data does not support the claim that "The average age of Nobel Prize winners when they received the prize is less than 60" at a 10%, 5%, or 1% significance level.

Calculating a P-Value for a Hypothesis Test with Programming
Many programming languages can calculate the P-value to decide outcome of a hypothesis test.

Using software and programming to calculate statistics is more common for bigger sets of data, as calculating manually becomes difficult.

The P-value calculated here will tell us the lowest possible significance level where the null-hypothesis can be rejected.

Example
With Python use the scipy and math libraries to calculate the P-value for a left tailed hypothesis test for a mean.

Here, the sample size is 30, the sample mean is 62.1, the sample standard deviation is 13.46, and the test is for a mean smaller 60.

import scipy.stats as stats
import math

# Specify the sample mean (x_bar), the sample standard deviation (s), the mean claimed in the null-hypothesis (mu_null), and the sample size (n)
x_bar = 62.1
s = 13.46
mu_null = 60
n = 30

# Calculate the test statistic
test_stat = (x_bar - mu_null)/(s/math.sqrt(n))

# Output the p-value of the test statistic (left tailed test)
print(stats.t.cdf(test_stat, n-1))
Example
With R use built-in math and statistics functions find the P-value for a left tailed hypothesis test for a mean.

Here, the sample size is 30, the sample mean is 62.1, the sample standard deviation is 13.46, and the test is for a mean smaller 60.

# Specify the sample mean (x_bar), the sample standard deviation (s), the mean claimed in the null-hypothesis (mu_null), and the sample size (n)
x_bar <- 62.1
s <- 13.46
mu_null <- 60
n <- 30

# Calculate the test statistic
test_stat = (x_bar - mu_null)/(s/sqrt(n))

# P-value the p-value of the test statistic (left tailed test)
pt(test_stat, n-1)
Left-Tailed and Two-Tailed Tests
This was an example of a left tailed test, where the alternative hypothesis claimed that parameter is smaller than the null hypothesis claim.

You can check out an equivalent step-by-step guide for other types here:

Right-Tailed Test
Two-Tailed Test


## Statistics - Hypothesis Testing a Mean (Two Tailed)
A population mean is an average of value a population.

Hypothesis tests are used to check a claim about the size of that population mean.

Hypothesis Testing a Mean
The following steps are used for a hypothesis test:

Check the conditions
Define the claims
Decide the significance level
Calculate the test statistic
Conclusion
For example:

Population: Nobel Prize winners
Category: Age when they received the prize.
And we want to check the claim:

"The average age of Nobel Prize winners when they received the prize is not 60"

By taking a sample of 30 randomly selected Nobel Prize winners we could find that:

The mean age in the sample (
) is 62.1
The standard deviation of age in the sample (
) is 13.46
From this sample data we check the claim with the steps below.

1. Checking the Conditions
The conditions for calculating a confidence interval for a proportion are:

The sample is randomly selected
And either:
The population data is normally distributed
Sample size is large enough
A moderately large sample size, like 30, is typically large enough.

In the example, the sample size was 30 and it was randomly selected, so the conditions are fulfilled.

Note: Checking if the data is normally distributed can be done with specialized statistical tests.

2. Defining the Claims
We need to define a null hypothesis (
) and an alternative hypothesis (
) based on the claim we are checking.

The claim was:

"The average age of Nobel Prize winners when they received the prize is not 60"

In this case, the parameter is the mean age of Nobel Prize winners when they received the prize (
).

The null and alternative hypothesis are then:

Null hypothesis: The average age was 60.

Alternative hypothesis: The average age is not 60.

Which can be expressed with symbols as:

: 

: 

This is a 'two-tailed' test, because the alternative hypothesis claims that the proportion is different from the null hypothesis.

If the data supports the alternative hypothesis, we reject the null hypothesis and accept the alternative hypothesis.

3. Deciding the Significance Level
The significance level (
) is the uncertainty we accept when rejecting the null hypothesis in a hypothesis test.

The significance level is a percentage probability of accidentally making the wrong conclusion.

Typical significance levels are:

 (10%)
 (5%)
 (1%)
A lower significance level means that the evidence in the data needs to be stronger to reject the null hypothesis.

There is no "correct" significance level - it only states the uncertainty of the conclusion.

Note: A 5% significance level means that when we reject a null hypothesis:

We expect to reject a true null hypothesis 5 out of 100 times.

4. Calculating the Test Statistic
The test statistic is used to decide the outcome of the hypothesis test.

The test statistic is a standardized value calculated from the sample.

The formula for the test statistic (TS) of a population mean is:

 

 is the difference between the sample mean (
) and the claimed population mean (
).

 is the sample standard deviation.

 is the sample size.

In our example:

The claimed (
) population mean (
) was 

The sample mean (
) was 

The sample standard deviation (
) was 

The sample size (
) was 

So the test statistic (TS) is then:

 
 
 
 

You can also calculate the test statistic using programming language functions:

ExampleGet your own Python Server
With Python use the scipy and math libraries to calculate the test statistic.

import scipy.stats as stats
import math

# Specify the sample mean (x_bar), the sample standard deviation (s), the mean claimed in the null-hypothesis (mu_null), and the sample size (n)
x_bar = 62.1
s = 13.46
mu_null = 60
n = 30

# Calculate and print the test statistic
print((x_bar - mu_null)/(s/math.sqrt(n)))
Example
With R use built-in math and statistics functions to calculate the test statistic.

# Specify the sample mean (x_bar), the sample standard deviation (s), the mean claimed in the null-hypothesis (mu_null), and the sample size (n)
x_bar <- 62.1
s <- 13.46
mu_null <- 60
n <- 30

# Output the test statistic
(x_bar - mu_null)/(s/sqrt(n))
5. Concluding
There are two main approaches for making the conclusion of a hypothesis test:

The critical value approach compares the test statistic with the critical value of the significance level.
The P-value approach compares the P-value of the test statistic and with the significance level.
Note: The two approaches are only different in how they present the conclusion.

The Critical Value Approach
For the critical value approach we need to find the critical value (CV) of the significance level (
).

For a population mean test, the critical value (CV) is a T-value from a student's t-distribution.

This critical T-value (CV) defines the rejection region for the test.

The rejection region is an area of probability in the tails of the standard normal distribution.

Because the claim is that the population proportion is different from 60, the rejection region is split into both the left and right tail:

Student's T-Distribution with a left and right tail areas (rejection region) denoted as the greek symbol alpha

The size of the rejection region is decided by the significance level (
).

The student's t-distribution is adjusted for the uncertainty from smaller samples.

This adjustment is called degrees of freedom (df), which is the sample size 

In this case the degrees of freedom (df) is:  
 
 

Choosing a significance level (
) of 0.05, or 5%, we can find the critical T-value from a T-table, or with a programming language function:

Note: Because this is a two-tailed test the tail area (
) needs to be split in half (divided by 2).

Example
With Python use the Scipy Stats library t.ppf() function find the T-Value for an 
/2 = 0.025 at 29 degrees of freedom (df).

import scipy.stats as stats
print(stats.t.ppf(0.025, 29))
Example
With R use the built-in qt() function to find the t-value for an 
/ = 0.025 at 29 degrees of freedom (df).

qt(0.025, 29)
Using either method we can find that the critical T-Value is  
 
 

For a two-tailed test we need to check if the test statistic (TS) is smaller than the negative critical value (-CV), or bigger than the positive critical value (CV).

If the test statistic is smaller than the negative critical value, the test statistic is in the rejection region.

If the test statistic is bigger than the positive critical value, the test statistic is in the rejection region.

When the test statistic is in the rejection region, we reject the null hypothesis (
).

Here, the test statistic (TS) was  
 
 
 and the critical value was  
 
 

Here is an illustration of this test in a graph:

Student's T-Distribution with a left and right tail area (rejection region) equal to 0.05, a critical value of 2.045, and a test statistic of 0.855

Since the test statistic is between the critical values we keep the null hypothesis.

This means that the sample data does not support the alternative hypothesis.

And we can summarize the conclusion stating:

The sample data does not support the claim that "The average age of Nobel Prize winners when they received the prize is not 60" at a 5% significance level.

The P-Value Approach
For the P-value approach we need to find the P-value of the test statistic (TS).

If the P-value is smaller than the significance level (
), we reject the null hypothesis (
).

The test statistic was found to be  
 
 

For a population proportion test, the test statistic is a T-Value from a student's t-distribution.

Because this is a two-tailed test, we need to find the P-value of a T-value bigger than 0.855 and multiply it by 2.

The student's t-distribution is adjusted according to degrees of freedom (df), which is the sample size  
 
 

We can find the P-value using a T-table, or with a programming language function:

Example
With Python use the Scipy Stats library t.cdf() function find the P-value of a T-value bigger than 0.855 for a two tailed test at 29 degrees of freedom (df):

import scipy.stats as stats
print(2*(1-stats.t.cdf(0.855, 29)))
Example
With R use the built-in pt() function find the P-value of a T-Value bigger than 0.855 for a two tailed test at 29 degrees of freedom (df):

2*(1-pt(0.855, 29))
Using either method we can find that the P-value is  
 
 

This tells us that the significance level (
) would need to be smaller 0.3996, or 39.96%, to reject the null hypothesis.

Here is an illustration of this test in a graph:



This P-value is bigger than any of the common significance levels (10%, 5%, 1%).

So the null hypothesis is kept at all of these significance levels.

And we can summarize the conclusion stating:

The sample data does not support the claim that "The average age of Nobel Prize winners when they received the prize is not 60" at a 10%, 5%, or 1% significance level.

Calculating a P-Value for a Hypothesis Test with Programming
Many programming languages can calculate the P-value to decide outcome of a hypothesis test.

Using software and programming to calculate statistics is more common for bigger sets of data, as calculating manually becomes difficult.

The P-value calculated here will tell us the lowest possible significance level where the null-hypothesis can be rejected.

Example
With Python use the scipy and math libraries to calculate the P-value for a two tailed hypothesis test for a mean.

Here, the sample size is 30, the sample mean is 62.1, the sample standard deviation is 13.46, and the test is for a mean different from 60.

import scipy.stats as stats
import math

# Specify the sample mean (x_bar), the sample standard deviation (s), the mean claimed in the null-hypothesis (mu_null), and the sample size (n)
x_bar = 62.1
s = 13.46
mu_null = 60
n = 30

# Calculate the test statistic
test_stat = (x_bar - mu_null)/(s/math.sqrt(n))

# Output the p-value of the test statistic (two tailed test)
print(2*(1-stats.t.cdf(test_stat, n-1)))
Example
With R use built-in math and statistics functions find the P-value for a two tailed hypothesis test for a mean.

Here, the sample size is 30, the sample mean is 62.1, the sample standard deviation is 13.46, and the test is for a mean different from 60.

# Specify the sample mean (x_bar), the sample standard deviation (s), the mean claimed in the null-hypothesis (mu_null), and the sample size (n)
x_bar <- 62.1
s <- 13.46
mu_null <- 60
n <- 30

# Calculate the test statistic
test_stat = (x_bar - mu_null)/(s/sqrt(n))

# P-value the p-value of the test statistic (two tailed test)
2*(1-pt(test_stat, n-1))
Left-Tailed and Two-Tailed Tests
This was an example of a left tailed test, where the alternative hypothesis claimed that parameter is smaller than the null hypothesis claim.

You can check out an equivalent step-by-step guide for other types here:

Right-Tailed Test
Two-Tailed Test







<img width="200" alt="" src="">
<img width="200" alt="" src="">
 