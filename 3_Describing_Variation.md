3 Describing Variation
================
Boukara Ahmed El-Hachemi
08/07/2020

A statistical model partitions variation. People describe the
partitioning in different ways depending on their purposes and the
conventions of the field in which they work: explained variation versus
unexplained variation; described variation versus undescribed; predicted
variation versus unpredicted; signal versus noise; common versus
individual. This chapter describes ways to quantify variation in a
single variable. Once you can quantify variation, you can describe how
models divide it up.

In the 1880s, Francis Galton, one of the pioneers of statistics,
collected data on the heights of about 900 adult children and their
parents in London.

Galton was interested in studying the relationship between a full-grown
child’s height and his or her mother’s and father’s height. One way to
study this relationship is to build a model that accounts for the
child’s height – the ***response variable*** – by one or more
***explanatory variables*** such as mother’s height or father’s height
or the child’s sex. In later chapters you will construct such models.
For now, though, the objective is to describe and quantify how the
response variable varies across children without taking into
consideration any explanatory variables.

One way to describe variation is by the ***range of extremes***: an
interval that includes every case from the smallest to the largest.

What’s nice about describing variation through the extremes is that the
range includes every case. But there are disadvantages. First, you
usually don’t always have a ***census***, measurements on the entire
population. Instead of a census, you typically have only a ***sample***,
a subset of the population.

A second disadvantage of using the extremes is that it can give a
picture that is untypical. Giving a comprehensive range would be
misleading in important ways, even if it were literally correct.

A third disadvantage of using the extremes is that even a single case
can have a strong influence on your description.

It’s natural for people to think about variation in terms of records and
extremes. In statistics, however, the focus is usually on the
unexceptional cases, the typical cases. With such a focus, it’s
important to think about ***typical variation*** rather than extreme
variation.

## 1 Coverage Intervals

One way to describe typical variation is to specify a fraction of the
cases that are regarded as typical and then give the ***coverage
interval*** or range that includes that fraction of the cases.

Imagine arranging all of the people in Galton’s sample of 900 into
order, the way a school-teacher might, from shortest to tallest. Now
walk down the line, starting at the shortest, counting heads. At some
point you will reach the person at position 225. This position is
special because one quarter of the 900 people in line are shorter and
three quarters are taller. The height of the person at position 225 –
64.0 inches – is the 25th ***percentile*** of the height variable in the
sample.

Continue down the line until you reach the person at position 675. The
height of this person – 69.7 inches – is the 75th percentile of height
in the sample.

The range from 25th to 75th percentile is the ***50% coverage
interval*** : 64.0 to 69.7 inches in Galton’s data. Within this interval
is 50% of the cases.

For most purposes, a 50% coverage interval excludes too much; half the
cases are outside of the interval.

Scientific practice has established a convention, the ***95-percent
coverage interval*** that is more inclusive than the 50% interval but
not so tied to the extremes as the 100% interval. The 95% coverage
interval includes all but 5% of the cases, excluding the shortest 2.5%
and the tallest 2.5%.

To calculate the 95% coverage interval, find the 2.5 percentile and the
97.5 percentile. In Galton’s height data, these are 60 inches and 73
inches, respectively.

There is nothing magical about using the coverage fractions 50% or 95%.
They are just conventions that make it easier to communicate clearly.
But they are important and widely used conventions.

In translating the position in the sorted list to a percentile,
convention puts the smallest case at the 0th percentile and the largest
case at the 100th percentile. For the kth position in the sorted list of
n cases, the percentile is taken to be (k-1)/(n-1).

With n=11 cases in the sample, the sorted cases themselves stand for the
0th, 10th, 20th, …, 90th, and 100th percentiles. If you want to
calculate a percentile that falls in between these values, you (or the
software) interpolate between the samples. For instance, the 75th
percentile would, for n=11, be taken as half-way between the values of
the 70th and 80th percentile cases.

Coverage intervals are found from the tabulated percentiles. The 50%
coverage interval runs from the 25th to the 75th percentile. Those exact
percentiles happen not be be in the table, but you can estimate them.
Take the 25th percentile to be half way between the 20th and 30th
percentiles: 62.5 inches (I calculated (63+66)/2 = 64.5). Similarly,
take the 75th percentile to be half way between the 70th and 80th
percentiles: 70.5 inches.(I calculated (70+70.5)/2 = 70.25)

This small N=11 subset of Galton’s data illustrates a potential
difficulty of a 95% coverage interval: The values of the 2.5th and
97.5th percentiles in a small data set depend heavily on the extreme
cases, since interpolation is needed to find the percentiles. In larger
data sets, this is not so much of a problem.

A reasonable person might object that the 0th percentile of the sample
is probably not the 0th percentile of the population; a small sample
almost certainly does not contain the shortest person in the population.
There is no good way to know whether the population extremes will be
close to the sample extremes and therefore you cannot demonstrate that
the estimates of the extremes based on the sample are valid for the
population. The ability to draw demonstrably valid inferences from
sample to population is one of the reasons to use a 50% or 95% coverage
interval rather than the range of extremes.

Different fields have varying conventions for dividing groups into
parts. In the various literatures, one will read about ***quintiles***
(division into 5 equally sized groups, common in giving economic data),
***stanines*** (division into 9 unevenly sized groups, common in
education testing), and so on.

In general-purpose statistics, it’s conventional to divide into four
groups: ***quartiles*** . The dividing point between the first and
second quartiles is the 25th percentile. For this reason, the 25th
percentile is often called the “first quartile.” Similarly, the 75th
percentile is called the “third quartile.”

The most famous percentile is the 50th: the ***median***, which is the
value that half of the cases are above and half below. The median gives
a good representation of a typical value. In this sense, it is much like
the ***mean***: the average of all the values.

Neither the median nor the mean describes the variation. For example,
knowing that the median of Galton’s sample of heights is 66 inches does
not give you any indication of what is a typical range of heights. In
the next section, however, you’ll see how the mean can be used to set up
an important way of measuring variation: the typical distance of cases
from the mean.

## Aside: What’s Normal?

People frequently confuse “normal” in the sense of “inside a 95%
coverage interval” with “normal” in the sense of “functions properly.”

## 2 The Variance and Standard Deviation

The 95% and 50% coverage intervals are important descriptions of
variation. For constructing models, however, another format for
describing variation is more widely used: the variance and standard
deviation.

Any given individual case will likely deviate from a single model value.
The value of an individual can be written in a way that emphasizes the
common model value shared by all the cases and the deviation from that
value of each individual:

individual case = model value + deviation of that case

As the single model value of the variable, it’s reasonable to choose the
mean. Another equally good choice would be the median. (Chapter 8 deals
with the issue of how to choose the “best” model value, and how to
define “best.”)

Once you have chosen the model value, you can find how much each case
deviates from the model.

The word ***residual*** provides a more neutral term than “deviation” or
“error” to describe how each individual differs from the model value. It
refers to what is left over when the model value is taken away from the
individual case. The word “deviation” survives in statistics in a
technical terms such as ***standard deviation***, and ***deviance***.
Similarly, “error” shows up in some technical terms such as ***standard
error***.

In practice, instead of the coverage intervals, a very simple, powerful,
and perhaps unexpected measure is used: the ***mean square*** of the
residuals. To produce this measure, add up the square of the residuals
for the individual cases. This gives the ***sum of squares*** of the
residuals Such sums of squares will show up over and over again in
statistical modeling.

It may seem strange to square the residuals. Squaring the residuals
changes their units. If you just added up the raw residuals, negative
residuals would tend to cancel out positive residuals. By squaring, all
the negative residuals become positive square-residuals. It would also
be reasonable do this by taking an absolute value rather than squaring,
but the operation of squaring captures in a special way important
properties of the potential randomness of the residuals.

Finding the sum of squares is an intermediate step to calculating an
important measure of variation: the mean square. The ***mean square***
is intended to report a typical square residual for each case. The
obvious way to get this is to divide the sum of squares by the number of
cases, N. This is not exactly what is done by statisticians. For reasons
that you will see later, they divide by N−1 instead. (When N is big,
there is no practical difference between using N and N−1).

Later in this book, mean squares will be applied to all sorts of models
in various ways. But for the very simple situation here – the
every-case-the-same model – the mean square has a special name that is
universally used: the ***variance***.

The variance provides a compact description of how far cases are, on
average, from the mean. As such, it is a simple measure of variation. It
is undeniable that the unfamiliar units of the variance – squares of the
natural units – make it hard to interpret. There is a simple cure,
however: take the square root of the variance. This is called,
infamously to many students of statistics, the ***standard deviation***.

The term “standard deviation” might be better understood if “standard”
were replaced by a more contemporary equivalent word: “typical.” The
standard deviation is a measure of how far cases typically deviate from
the mean of the group.

Historically, part of the appeal of using the standard deviation to
describe variation comes from the ease of calculating it using
arithmetic. Percentiles require more tedious sorting operations.
Nowadays, computers make it easy to calculate 50% or 95% intervals
directly from data. Still, standard deviations remain an important way
of describing variation both because of historical convention and, more
important for this book, because of its connection to concepts of
modeling and randomness encountered in later chapters.

## 3 Displaying Variation

One of the best ways to depict variation is graphically. This takes
advantage of the human capability to capture complicated patterns at a
glance and to discern detail. There are several standard formats for
presenting variation; each has its own advantages and disadvantages.

A simple but effective display plots out each case as a point along a
number line. This ***rug plot*** is effectively a graphical listing of
the values of the variable, case-by-case.

Another simple display, the ***histogram***, avoids this overlap by
using two different axes. As in the rug plot, one of the axes shows the
variable. The other axis displays the number of individual cases within
set ranges, or “bins,” of the variable.

Histograms have been a standard graphical format for more than a
century, but even so they are often not interpreted correctly. Many
people wrongly believe that variation in the data is reflected by the
uneven height of the bars. Rather, the variation is represented by the
width of the spread measured from side to side, not from bottom to top.

A more modern format for displaying distributions is a ***density
plot***. To understand a density plot, start with the idea of a rug
plot, The “density” of points in the rug plot reflects how close
together the cases are. In places where the cases are very close, the
density is high. Where the cases are spread out far from one another,
the density is low. In the density plot, a smooth curve is used to trace
how the density varies from place to place. Unlike the histogram, the
density plot does not divide the cases into rigid bins.

The height of the density-plot curve is scaled so that the overall area
under the curve is always exactly 1. This choice makes it possible to
interpret the area under a part of the curve as the fraction of cases
that lie in that plot.

Since the density plot is a smooth curve, and since the area is scaled
to 1, it’s feasible to compare different groups.

Since the long “tail” of the distribution runs to the right, the
distribution is called ***skew right***. When the distribution is peaked
in the center and falling off similarly both to the left and the right,
than it is symmetric. It takes a bit of thought to understand the units
of measuring density. In general, the word “density” refers to an amount
per unit length, or area, or volume. In general, the word “density”
refers to an amount per unit length, or area, or volume. For example,
the mass-volume density of water is the mass of water per unit of
volume, typically given as kilograms per liter. The sort of density used
for density plots is the fraction-of-cases per unit of the measured
variable.

## 4 Shapes of Distributions

A very common form for the density of variables is the bell-shaped
pattern: the individuals are distributed with most near the center and
fewer and fewer near the edges. The pattern is so common that a
mathematical idealization of it is called the ***normal distribution***.

Don’t be mislead by the use of the word “normal.” Although the
bell-shaped distribution is common, other shapes of distributions also
often occur, such as the ***right skew*** distribution.

Usually, distributions are examined for their gross or coarse
characteristics: the location of their center, their width, whether they
are skew or symmetric, etc. A nice graphical device for emphasizing such
broad characteristics is the violin plot. The ***violin plot*** puts
displays of density side by side. Within the “violin”, the lines show
the first quartile, median, and third quartile.

### 4.1 Categorical Variables

All of the measures of variation encountered so far are for quantitative
variables; the kind of variable for which it’s meaningful to average or
sort.

Categorical variables are a different story. One thing to do is to
display the variation using tables and bar charts.

### 4.2 Quantifying Categorical Variation

For a quantitative variable, there are several good choices for
describing the variation:

1.  The standard deviation.
2.  The variance, which is just the square of the standard deviation.
3.  The interquartile interval.

But when it comes to categorical variables, giving a numerical summary
for variation is a more difficult matter. Recall that for quantitative
variables, one can define a “typical” value, e.g., the mean or the
median. It makes sense to measure residuals as how far an individual
value is from the typical value, and to quantify variation as the
average size of a residual. This led to the variance and the standard
deviation as measures of variation.

For a categorical variable like sex, concepts of mean or median or
distance or size don’t apply. Neither F nor M is typical and in-between
doesn’t really make sense. Even if you decided that, say, M is typical –
there are somewhat more of them in Galton’s data – how can you say what
the “distance” is between F and M?

Statistics textbooks hardly ever give a quantitative measure of
variation in categorical variables. That’s understandable for the
reasons described above. But it’s also a shame because many of the
methods used in statistical modeling rely on quantifying variation in
order to evaluate the quality of models.

There are quantitative notions of variation in categorical variables.
You won’t have use for them directly, but they are used in the software
that fits models of categorical variables.

Solely for the purposes of illustration, here is one measure of
variation in categorical variables with two levels, say F and M as in
sex in Galton’s data. Two-level variables are important in lots of
settings, for example diagnostic models of whether or not a patient has
cancer or models that predict whether a college applicant will be
accepted.

Imagine that altogether you have N cases, with k being level F and N-k
being level M. (In Galton’s data, N is 898, while k=433 and N-k=465.) A
simple measure of variation in two-level categorical variables is
called, somewhat awkwardly, the unalikeability. This is

\[unalikeability = 2 \frac{k}{N} \frac{N−k}{N}.\].

Or, more simply, if you write the prop

\[unalikeability = 2 p_{F} (1-p_{F}).\].

For instance, in the variable sex, p\_F = 433 / 898 = 0.482. The
unalikeability is therefore 2 × 0.482 × 0.518 = 0.4993.

Some things to notice about unalikeability: If all of the cases are the
same (e.g., all are F), then the unalikeability is zero – no variation
at all. The highest possible level of unalikeability occurs when there
are equal numbers in each level; this gives an unalikeability of 0.5.

Where does the unalikeability come from? One way to think about
unalikeability is as a kind of numerical trick. Pretend that the level F
is 1 and the level M is 0 – turn the categorical variable into a
quantitative variable. With this transformation, `sex` looks like
`0 1 1 1 0 0 1 1 0 1 0` and so on. Now you can quantify variation in the
ordinary way, using the variance. It turns out that the unalikeability
is exactly twice the variance.

Here’s another way to think about unalikeability: although you can’t
really say how far F is from M, you can certainly see the difference.
Pick two of the cases at random from your sample. The unalikeability is
the probability that the two cases will be different: one an M and the
other an F.

There is a much more profound interpretation of unalikeability that is
introduced in Chapter 16, which covers modeling two-level categorical
variables. For now, just keep in mind that you can measure variation for
any kind of variable and use that measure to calculate how much of the
variation is being captured by your models.
