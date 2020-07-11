4 Groupwise Models
================
Boukara Ahmed El-Hachemi
09/07/2020

> Seek simplicity and distrust it. – Alfred North Whitehead (1861-1947),
> mathematician and philosopher

This chapter introduces a simple form of statistical model based on
separating the cases in your data into different groups. Such models are
very widely used and will seem familiar to you, even obvious. They can
be useful in very simple situations, but can be utterly misleading in
others. Part of the objective of this chapter is to guide you to
understand the serious limitations of such models and to critique the
inappropriate, though all too common, use of group-wise models.

## 1 Grand and Group-wise Models

***grand mean*** form that puts everyone into the same group, or
***group-wise mean*** form where people are divided up into several
groups.

## 2 Accounting for Variation

It’s helpful to have a way to measure the “amount” of variation in a
quantity so that you can describe how much of the overall variation a
model accounts for. There are several such standard measures:

  - the standard deviation
  - the variance (which is just the standard deviation squared)
  - the inter-quartile interval
  - the range (from minimum to maximum)
  - coverage intervals, such as the 95% coverage intervals

Each of these ways of measuring variation has advantages and
disadvantages.

The variance has a property that is extremely advantageous for
describing how much variation a model accounts for: the variance
***partitions the variation*** between that explained or accounted for
by a model, and the remaining variation that remains unexplained or
unaccounted for. This latter is called the ***residual variation***.

To illustrate, consider the simple group-wise mean model, “Women are
64.1 inches tall, while men are 69.2 inches tall.” How does this model
account for variation?

Measuring the person-to-person variation in height by the variance,
gives a variation of 12.8 square-inches. That’s the total variation to
be accounted for.

Now imagine creating a new data set that replaces each person’s actual
height with what the model says. So all men would be listed at a height
of 69.2 inches, and all women at a height of 64.1 inches. Those model
values also have a variation, which can be measured by their variance:
6.5 square inches.

Now consider the residual, the difference between the actual height and
the heights according to the model. A women who is 67 inches tall would
have a residual of 2.9 inches – she’s taller by 2.9 inches than the
model says. Each person has his or her own residual in a model. Since
these vary from person to person, they also have a variance, which turns
out to be 6.3 inches for this group-wise model of heights.

Notice the simple relationship among the three variances:

Overall Model Residual 12.8 = 6.5 + 6.3

To be precise about the variance and partitioning … the variance has
this property of partitioning for a certain kind of model – group-wise
means and the generalization of that called ***linear, least-squares
models*** that are the subject of later chapters – but those models are
by far the most important. For other kinds of models, such as
***logistic models*** described in Chapter 16 there are other measures
of variation that have the partitioning property.

## Aside: The geometry of partitioning

One way to think of this is in terms of a triangle: the model value is
one side of the triangle, the residual is another side, and the actual
values are the third side.

it turns out that this triangle involves a right angle between the
residuals and the model values. As such, the Pythagorean theorem applies
and the square of the triangle side lengths add in the familiar way:

Model values² + Residuals² = Actual values² .

## 3 Group-wise Proportions

It’s often useful to consider proportions broken down, group by group.
For example, In examining employment patterns for workers, it makes
sense to consider mean or median wages in different groups, mean or
median ages, and so on. But when the question has to do with employment
termination – whether or not a person was fired – the appropriate
quantity is the proportion of workers in each group who were terminated.

## 4 What’s the Precision?

The main point of constructing group-wise models is to be able to
support a claim that the groups are different, or perhaps to refute such
a claim. In thinking about differences, it’s helpful to distinguish
between two sorts of criteria:

1.  Whether the difference is substantial or important in terms of the
    phenomenon that you are studying.  
2.  How much evidence there is for any difference at all. This is a more
    subtle point.

Quantifying and interpreting this ***sampling variability*** is an
important component of statistical reasoning. The techniques to do so
are introduced in Chapter 5 and then expanded in later chapters. But
before moving on to the techniques for quantifying sampling variability,
consider the common format for presenting it: the ***confidence
interval***.

A confidence interval is a way of expressing the precision or
repeatability of a statistic, how much variation would likely be present
across the possible different random samples from the population. In
format, it is a form of coverage interval, typically taken at the 95%
level, and looks like this:

68.6 ± 3.3

The first number, 68.6 here, is called the ***point estimate***, and is
the statistic itself. The second number, the ***margin of error***,
reflects how precise the point estimate is. There is a third number,
sometimes stated explicitly, sometimes left implicit, the ***confidence
level***, which is the level of the coverage interval, typically 95%.

Like other coverage intervals, a confidence interval leaves out the
extremes. You can think of this as arranging the confidence interval to
reflect what *plausibly* might happen, rather than the full extent of
the possibilities, no matter how extreme or unlikely.

## 5 Misleading Group-wise Models

You will often see news reports or political claims that attempt to
account for or dismiss differences by appealing to “other factors.” This
is a valuable form of argument, but it ought to be supported by
quantitative evidence, not just an intuitive sense of “small” or “big.”
The modeling techniques introduced in the following chapters enable you
to do consider multiple factors in a quantitative way.

A relatively simple modeling method called ***stratification*** (or
disaggregation) can illustrate how this is possible.
