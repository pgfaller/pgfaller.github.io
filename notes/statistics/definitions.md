---
layout: maths
---

# Statistics

## Mean

If you have a sample of
$$n$$
values
$$x_i$$
then the mean
$$\bar{x}$$
is the sum of the values divided by the number of values:

$$\bar{x}=\frac{1}{n}\sum_{i}x_i$$

## Variance and Standard Deviation

Variance is a summary statistic intended to describe the variability or spread of a distribution. The variance of a set of values is:

$$S^2=\frac{1}{n}\sum_{i} (x_i - \bar{x})^2$$

The square root of Variance, S, is the standard deviation.

## Correlation

Statisticians use the correlation coefficient to measure the strength and direction of the linear relationship between two numerical variables X and Y. The correlation coefficient for a sample of data is denoted by _r_.

$$
r=\frac{1}{n-1}(\frac{\sum_{x}\sum_{y}(x-\bar{x})(y-\bar{y})}{s_xs_y})
$$

where
$$s_x, s_y$$
are the standard deviation of the _x_ and _y_ values.

## Probability Mass Function

Another way to represent a distribution is a probability mass function (PMF), which
maps from each value to its probability. A probability is a frequency expressed as a
fraction of the sample size, _n_ . To get from frequencies to probabilities, we divide through by _n_ , which is called normalization.
Given a Hist, we can make a dictionary that maps from each value to its probability:

```python
n = hist.Total()
d = {}
for x, freq in hist.Items():
    d[x] = freq / n
```

## Cohen's Effect Size

Another way to convey the size of the effect is to compare the difference between groups to the variability within groups.
Cohen’s _d_ is a statistic intended to do that; it is defined as

$$d = \frac{\bar{x_1}-\bar{x_2}}{s}$$

where
$$\bar{x_1}$$
and
$$\bar{x_2}$$
are the means of the groups and _s_ is the “pooled standard deviation”.
