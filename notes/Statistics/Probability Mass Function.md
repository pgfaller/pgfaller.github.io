Probability Mass Function

Another way to represent a distribution is a probability mass function (PMF), which
maps from each value to its probability. A probability is a frequency expressed as a
fraction of the sample size, $n$ . To get from frequencies to probabilities, we divide through by $n$ , which is called normalization.
Given a Hist, we can make a dictionary that maps from each value to its probability:

``` python
n = hist.Total()
d = {}
for x, freq in hist.Items():
    d[x] = freq / n
```
