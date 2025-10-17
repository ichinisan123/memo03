# Stat 001

## Statistics - Populations and Samples

- The terms 'population' and 'sample' are important in statistics and refer to key concepts that are closely related.
- Population: Everything in the group that we want to learn about.
- Sample: A part of the population.

| Population                      | Sample                   |
| ------------------------------- | ------------------------ |
| All of the people in Germany    | 500 Germans              |
| All of the customers of Netflix | 300 Netflix customers    |
| Every car manufacturer          | Tesla, Toyota, BMW, Ford |

- For good statistical analysis, the sample needs to be as "similar" as possible to the population. If they are similar enough, we say that the sample is representative of the population.
- The sample is used to make conclusions about the whole population. If the sample is not similar enough to the whole population, the conclusions could be useless.
- Many words have specific meanings in statistics.
- The word 'population' normally refers to a group of people. In statistics, it is any specific group that we are interested in learning about.

## Statistics - Mean

- The mean is a type of average value, which describes where center of the data is located.
- The mean is usually referred to as 'the average'.
- The mean is the sum of all the values in the data divided by the total number of values in the data.
- The mean is calculated for numerical variables. A variable is something in the data that can vary, like:
  - Age
  - Height
  - Income
- There are multiple types of mean values. The most common type of mean is the arithmetic mean.

### Calculating the Mean

- You can calculate the mean for both the population and the sample.
- The formulas are the same and uses different symbols to refer to the population mean ($\mu$) and sample mean ($\bar{x}$).
- Calculating the population mean ($\mu$) is done with this formula:

$$\mu = \frac{\sum x_{i}}{n}$$

- Calculating the sample mean ($\bar{x}$) is done with this formula:

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
  4. Standard Deviation
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

## Statistics - 4 Standard Deviation

- Standard deviation is the most used measure of variation.
- Standard deviation (σ) measures how far a 'typical' observation is from the average of the data (μ).
- Standard deviation is important for many statistical methods.

<img width="500" alt="Variation4" src="https://www.w3schools.com/statistics/img_histogram_std.svg">

- Each dotted line in the histogram shows a shift of one extra standard deviation.
- If the data is normally distributed:
- Roughly 68.3% of the data is within 1 standard deviation of the average (from μ-1σ to μ+1σ)
- Roughly 95.5% of the data is within 2 standard deviations of the average (from μ-2σ to μ+2σ)
- Roughly 99.7% of the data is within 3 standard deviations of the average (from μ-3σ to μ+3σ)
- A normal distribution has a "bell" shape and spreads out equally on both sides.

### Calculating the Standard Deviation

- You can calculate the standard deviation for both the population and the sample.
- The formulas are the almost same and uses different symbols to refer to the standard deviation ($\sigma$) and sample standard deviation ($s$).
- Calculating the standard deviation ($\sigma$) is done with this formula:

$$\sigma =\sqrt{\frac{\sum(x_{i} - \mu)^{2}}{n}}$$

- Calculating the sample standard deviation ($s$) is done with this formula:

$$s =\sqrt{\frac{\sum(x_{i} - \bar{x})^{2}}{n - 1}}$$

- $n$ is the total number of observations.
- $\sigma$ is the symbol for adding together a list of numbers.
- $x_{i}$ is the list of values in the data: $x_{1}, x_{2}, x_{3}, ...$
- $\mu$ is the population mean and $\bar{x}$ is the sample mean (average value).
- $(x_{i} - \mu)$ and $(x_{i} - \bar{x})$ are the differences between the values of the observations ($x_{i}$) and the mean.
- Each difference is squared and added together.
- Then the sum is divided by $n$ or $(n - 1)$ and then we find the square root.
- Using these 4 values for calculating the population standard deviation:

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

- So, the standard deviation of the values is roughly: 

### Calculating the Standard Deviation with Programming

- Population Standard Deviation

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

- Sample Standard Deviation

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

An example could be a confidence interval for the number of bicycles a Dutch person owns:

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
- The normal distribution is described by the mean ($\mu$) and the standard deviation ($\sigma$).
- The normal distribution is often referred to as a 'bell curve' because of it's shape:
  - Most of the values are around the center ($\mu$)
  - The median and mean are equal
  - It has only one mode
  - It is symmetric, meaning it decreases the same amount on the left and the right of the center
- The area under the curve of the normal distribution represents probabilities for the data.

The area under the whole curve is equal to 1, or 100%

Here is a graph of a normal distribution with probabilities between standard deviations (
):

Normal Distributions with indicated probabilities.

Roughly 68.3% of the data is within 1 standard deviation of the average (from μ-1σ to μ+1σ)
Roughly 95.5% of the data is within 2 standard deviations of the average (from μ-2σ to μ+2σ)
Roughly 99.7% of the data is within 3 standard deviations of the average (from μ-3σ to μ+3σ)
Note: Probabilities of the normal distribution can only be calculated for intervals (between two values).

Different Mean and Standard Deviations
The mean describes where the center of the normal distribution is.

Here is a graph showing three different normal distributions with the same standard deviation but different means.

Normal Distributions with different means.

The standard deviation describes how spread out the normal distribution is.

Here is a graph showing three different normal distributions with the same mean but different standard deviations.

Normal Distributions with different standard deviations.

The purple curve has the biggest standard deviation and the black curve has the smallest standard deviation.

The area under each of the curves is still 1, or 100%.

A Real Data Example of Normally Distributed Data
Real world data is often normally distributed.

Here is a histogram of the age of Nobel Prize winners when they won the prize:

Histogram of the age of Nobel Prize winners when they won the prize and normal distribution fitted to the data.

The normal distribution drawn on top of the histogram is based on the population mean (
) and standard deviation (
) of the real data.

We can see that the histogram close to a normal distribution.

Examples of real world variables that can be normally distributed:

Test scores
Height
Birth weight
Probability Distributions
Probability distributions are functions that calculates the probabilities of the outcomes of random variables.

Typical examples of random variables are coin tosses and dice rolls.

Here is an graph showing the results of a growing number of coin tosses and the expected values of the results (heads or tails).

The expected values of the coin toss is the probability distribution of the coin toss.

Simulated coin tosses and expected values.

Notice how the result of random coin tosses gets closer to the expected values (50%) as the number of tosses increases.

Similarly, here is a graph showing the results of a growing number of dice rolls and the expected values of the results (from 1 to 6).

Simulated dice rolls and expected values.

Notice again how the result of random dice rolls gets closer to the expected values (1/6, or 16.666%) as the number of rolls increases.

When the random variable is a sum of dice rolls the results and expected values take a different shape.

The different shape comes from there being more ways of getting a sum of near the middle, than a small or large sum.

Simulated sum of two dice rolls and expected values.

As we keep increasing the number of dice for a sum the shape of the results and expected values look more and more like a normal distribution.

Simulated sum of 3 dice rolls and expected values.Simulated sum of 5 dice rolls and expected values.

Many real world variables follow a similar pattern and naturally form normal distributions.

Normally distributed variables can be analyzed with well-known techniques.

You will learn about some of the most common and useful techniques in the following pages.


## Statistics - Standard Normal Distribution
The standard normal distribution is a normal distribution where the mean is 0 and the standard deviation is 1.

Standard Normal Distribution
Normally distributed data can be transformed into a standard normal distribution.

Standardizing normally distributed data makes it easier to compare different sets of data.

The standard normal distribution is used for:

Calculating confidence intervals
Hypothesis tests
Here is a graph of the standard normal distribution with probability values (p-values) between the standard deviations:

Standard Normal Distribution with indicated probabilities.

Standardizing makes it easier to calculate probabilities.

The functions for calculating probabilities are complex and difficult to calculate by hand.

Typically, probabilities are found by looking up tables of pre-calculated values, or by using software and programming.

The standard normal distribution is also called the 'Z-distribution' and the values are called 'Z-values' (or Z-scores).

Z-Values
Z-values express how many standard deviations from the mean a value is.

The formula for calculating a Z-value is:

 

 is the value we are standardizing, 
 is the mean, and 
 is the standard deviation.

For example, if we know that:

The mean height of people in Germany is 170 cm (
)

The standard deviation of the height of people in Germany is 10 cm (
)

Bob is 200 cm tall (
)

Bob is 30 cm taller than the average person in Germany.

30 cm is 3 times 10 cm. So Bob's height is 3 standard deviations larger than mean height in Germany.

Using the formula:

 
 
 
 

The Z-value of Bob's height (200 cm) is 3.

Finding the P-value of a Z-Value
Using a Z-table or programming we can calculate how many people Germany are shorter than Bob and how many are taller.

ExampleGet your own Python Server
With Python use the Scipy Stats library norm.cdf() function find the probability of getting less than a Z-value of 3:

import scipy.stats as stats
print(stats.norm.cdf(3))
Example
With R use the built-in pnorm() function find the probability of getting less than a Z-value of 3:

pnorm(3)
Using either method we can find that the probability is 
, or 

Which means that Bob is taller than 99.87% of the people in Germany.

Here is a graph of the standard normal distribution and a Z-value of 3 to visualize the probability:

Standard Normal Distribution with indicated probability for a z-value of 3.

These methods find the p-value up to the particular z-value we have.

To find the p-value above the z-value we can calculate 1 minus the probability.

So in Bob's example, we can calculate 1 - 0.9987 = 0.0013, or 0.13%.

Which means that only 0.13% of Germans are taller than Bob.

Finding the P-Value Between Z-Values
If we instead want to know how many people are between 155 cm and 165 cm in Germany using the same example:

The mean height of people in Germany is 170 cm (
)

The standard deviation of the height of people in Germany is 10 cm (
)

Now we need to calculate Z-values for both 155 cm and 165 cm:


 
 
 
 
 

The Z-value of 155 cm is -1.5


 
 
 
 
 

The Z-value of 165 cm is -0.5


Using the Z-table or programming we can find that the p-value for the two z-values:

The probability of a z-value smaller than -0.5 (shorter than 165 cm) is 30.85%
The probability of a z-value smaller than -1.5 (shorter than 155 cm) is 6.68%
Subtract 6.68% from 30.85% to find the probability of getting a z-value between them.

30.85% - 6.68% = 24.17%

Here is a set of graphs illustrating the process:

Standard Normal Distribution with indicated probability for a z-value of 3.

Finding the Z-value of a P-Value
You can also use p-values (probability) to find z-values.

For example:

"How tall are you if you are taller than 90% of Germans?"

The p-value is 0.9, or 90%.

Using a Z-table or programming we can calculate the z-value:

Example
With Python use the Scipy Stats library norm.ppf() function find the z-value separating the top 10% from the bottom 90%:

import scipy.stats as stats
print(stats.norm.ppf(0.9))
Example
With R use the built-in qnorm() function find the z-value separating the top 10% from the bottom 90%:

qnorm(0.9)
Using either method we can find that the Z-value is 

Meaning that a person that is 1.281 standard deviations taller than the mean height of Germans is taller than 90% of Germans.

We then use the formula to calculate the height (
) based on a mean (
) of 170 cm and standard deviation (
) of 10 cm:

 

 




 
 

So we can conclude that:

"You have to be at least 182.81 cm tall to be taller than 90% of Germans"




<img width="200" alt="" src="">
<img width="200" alt="" src="">
