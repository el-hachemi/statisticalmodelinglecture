9 Correlation and Partitioning of Variance
================
Boukara Ahmed El-Hachemi
15/07/2020

> The invalid assumption that correlation implies cause is probably
> among the two or three most serious and common errors of human
> reasoning. – Stephen Jay Gould (1941-2002), paleontologist and
> historian of science

> “Co-relation or correlation of structure” is a phrase much used … but
> I am not aware of any previous attempt to define it clearly, to trace
> its mode of action in detail, or to show how to measure its degree. –
> Francis Galton (1822-1911), statistician

The partition property of the variance offers a simple way to summarize
a model: the proportion of the total variation in the response variable
that is accounted for by the model. This description is called the R²
(“**R-Squared**”) of the model. It is a ratio:

\(R^2 = \frac {\mbox {variance of fitted model values}}{\mbox {variance of response values}}\)

Another name for R² is the ***coefficient of determination*** , but this
is not a coefficient in the same sense used to refer to a multiplier in
a model formula.

## 1 Properties of R²

R² has a nice property that makes it easy to interpret: its value is
always between zero and one. When R² = 0, the model accounts for none of
the variance of the response values: the model is useless. When R² = 1,
the model captures all of the variance of the response values: the model
values are exactly on target. Typically, R² falls somewhere between zero
and one, meaning that the model accounts for some, but not all, of the
variance in the response values.

From the linear model height \~ 1 + mother + sex that includes both
mother’s height and child’s sex as explanatory variables. the R²
statistic is

\(R^2 = \frac {\mbox{7.21}}{\mbox{12.84}} = 0.56\)

One nice feature of R² is that the hard-to-interpret units of variance
disappear; by any standard, square-inches is a strange way to describe
height\! Since R² is the ratio of two variances, the units cancel out.
R² is unitless.

### Example: Quantifying the capture of variation

Back in Chapter 6, a model of natural gas usage and a model of wages
were presented. It was claimed that the natural gas model captured more
of the variation in natural gas usage than the wage model captured in
the hourly wages of workers. At one level, such a claim is absurd. How
can you compare natural gas usage to hourly wages? If nothing else, they
have completely different units.

R² is what enables this to be done. For any model, R² describes the
fraction of the variance in the response variable that is accounted for
by the model. Here are the R² for the two models:

  - `wage` \~ `sex` × `married`: R² = 0.07
  - `ccf` \~ `temp`: R² = 0.91

Sex and marital status explain only a small fraction of the variation in
wages. Temperature explains the large majority of the variation in
natural gas usage (`ccf`).

## 2 Simple Correlation

The idea Galton introduced in 1888 is that the relationship between two
variables – “co-relation” as he phrased it – can be described with a
single number. This is now called the ***correlation coefficient***,
written r and pronounced *r*.

The correlation coefficient is still very widely used. Part of the
reason for this is that the single number describes an important
mathematical aspect of the relationship between two variables: the
extent to which they are aligned or ***collinear***.

The correlation coefficient r is the square root of R² for the simple
straight-line model: response \~ explanatory variable. As with all
square roots, there is a choice of negative or positive. The sign of the
r is chosen to indicate the positive or negative slope of the model
line.

It may seem very limiting, in retrospect, to define correlation in terms
of such a simple model. But Galton was motivated by a wonderful symmetry
involved in the correlation coefficient: the R² from the straight-line
model of A versus B is the same as that from the straight-line model of
B versus A. In this sense, the correlation coefficient describes the
relationship between the two variables and not merely the dependence of
one variable on another. Of course, a more modern perspective on
relationships accepts that additional variables can be involved as well
as interaction and transformation terms.

### Example: Relationships without Correlation

Consider how the temperature varies over the course of the year. In most
places, temperature changes predictably from month to month: a very
strong relationship.  
A very simple straight-line model: `temperature` \~ `month`. This model
doesn’t capture very well the relationship between the two variables.
Since the response values have a variance of 409.3°F² and the fitted
model values have a variance of 25.6°F² the R² = 25.6 / 409.3 = 0.0624.

As a way to describe the overall relationship between variables, r is
limited. Although r is often described as measuring the relationship
between two variables, it’s more accurate to say that r quantifies a
particular model rather than “the relationship” between two variables.

But not all relationships are linear. The simple correlation coefficient
r does not reflect any nonlinear relationship in the data.

### Example: R versus R²

The correlation coefficient r is often reported in squared form: r².
However, the coefficient of determination is R². You will occasionally
see reports of the square root of the coefficient of determination: R =
√R². Perhaps this is because it seems unnatural to report squares,
just as the variance seem less natural than standard deviation. It’s
hard to claim that R² is right and R is wrong, but do make sure that you
know what you are reading about. What’s wrong is to read an R value and
interpret it as R².

## 3 The Geometry of Correlation

The correlation coefficient r is the cosine of the angle between the two
quantitative variable vectors, after the mean of each variable has been
subtracted.

This means that a perfect correlation, r = 1 corresponds to exact
alignment of A and B: the angle ϑ = 0. No correlation at all, r = 0
corresponds to A and B being at right angles: ϑ = 90°. A negative
correlation, r \< 0, corresponds to A and B pointing in opposite
directions.

## 4 Nested Models

Models are often built up in stages; start with an existing model and
then add a new model term. This process is important in deciding whether
the new term contributes to the explanation of the reponse variable. If
the new, extended model is substantially better than that old one,
there’s reason to think that the new term is contributing.

You can use R² to measure how much better the new model is than the old
model. But be careful. It turns out that whenever you add a new term to
a model, R² can increase. It’s never the case that the new term will
cause R² to go down. Even a random variable, one that’s utterly
unrelated to the response variable, can cause an increase in R² when
it’s added to a model.

This raises an important question: When is an increase in R² big enough
to justify concluding that the added explanatory term is genuinely
contributing to the model? Answering this question will require concepts
that will be introduced in later chapters.

An important idea is that of ***nested models***. Consider two models: a
“small” one and a “large” one that includes all of the explanatory terms
in the small one. The small model is said to be nested in the large
model.

To illustrate, consider a series of models of the Galton height data.
Each model will take child’s height as the response variable, but the
different models will include different variables and model terms
constructed from these variables.

  - **Model A**: `height` \~ 1
  - **Model B**: `height` \~ 1 + `mother`
  - **Model C**: `height` \~ 1 + `mother` + `sex`
  - **Model D**: `height` \~ 1 + `mother` + `sex` + `mother`:`sex`

Model B includes all of the explanatory terms that are in Model A. So,
Model A is nested in Model B. Similarly, A and B are both nested in
Model C. Model D is even more comprehensive; A, B, and C are all nested
in D.

When one model is nested inside another, the variance of the fitted
model values from the smaller model will be less than the variance of
the fitted model values from the larger model. The same applies to R²,
since R² is proportional to the variance of the fitted model values.

In the four nested models listed above, for example, the increase in
fitted variance and R² is this:

| Model                    | A |      B |      C |      D |
| :----------------------- | -: | -----: | -----: | -----: |
| Variance of model values | 0 | 0.5200 | 7.2100 | 7.2200 |
| R²                       | 0 | 0.0407 | 0.5618 | 0.5621 |

Notice that the variance of the fitted model values for Model A is
exactly zero. This is because Model A has only the intercept term 1 as
an explanatory term. This simple model treats all cases as the same and
so there is no variation at all in the fitted model values: the variance
and R² are zero.

### Example: R² Out of the Headlines

Consider this headline from the BBC News: “Finger length \`key to
aggression.’” The length of a man’s fingers can reveal how physically
aggressive he is.

Or, from Time magazine, a summary of the same story: “The shorter a
man’s index finger is relative to his ring finger, the more aggressive
he is likely to be (this doesn’t apply to women).”

These news reports were based on a study examining the relationship
between finger-length ratios and aggressiveness.(Bailey and Hurd 2005)
It has been noticed for years that men tend to have shorter index
fingers compared to ring fingers, while women tend the opposite way. The
study authors hypothesized that a more “masculine finger ratio” might be
associated with other masculine traits, such as aggressiveness. The
association was found and reported in the study: R² = 0.04.

As always, R² gives the fraction of the variance in the response
variable that is accounted for by the model. This means that of all the
variation in aggressiveness among the men involved in the study, 4% was
accounted for, leaving 96% unexplained by the models. This suggests that
finger length is no big deal.

Headline words like “key” and “reveal” are vague but certainly suggest a
strong relationship. The news media got it wrong.

## 5 The Geometry of R²

Consider the model A \~ B + C. Since there are two explanatory vectors
involved, there is an ambiguity: which is the angle to consider: the
angle A to B or the angle A to C?

The response is projected down onto the space that holds both of them,
the ***model subspace***. There is still a vector of fitted model values
and a residual vector. The three vectors taken together – response
variable, fitted model values, and residual – form a right triangle. The
angle between the response variable and the fitted model values is the
one of interest. R is the cosine of that angle.

Because the vectors B and C could be oriented in any direction relative
to one another, there’s no sense in worrying about whether the angle is
acute (less than 90°) or obtuse. For this reason, R² is used – there’s
no meaning in saying that R is negative.

-----

## Computational Technique

The coefficient of determination, R2 , compares the variation in the
response variable to the variation in the fitted model value. It can be
calculated as a ratio of variances:

``` r
Swim <- SwimRecords # from mosaicData
mod <- lm( time ~ year + sex, data = Swim)
var(fitted(mod)) / var(Swim$time)
```

    ## [1] 0.8439936

The convenience function `rsquared()` does the calculation for you:

``` r
rsquared(mod)
```

    ## [1] 0.8439936

The regression report is a standard way of summarizing models. Such a
report is produced by most statistical software packages and used in
many fields. The first part of the table contains the coefficients —
labeled “Estimate” — along with other information that will be
introduced later. The \(R^2\) statistic is a standard part of the
report; look at the second line from the bottom.

``` r
summary(mod)
```

    ## 
    ## Call:
    ## lm(formula = time ~ year + sex, data = Swim)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -4.7027 -2.7027 -0.5968  1.2796 19.0759 
    ## 
    ## Coefficients:
    ##              Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept) 555.71678   33.79991  16.441  < 2e-16 ***
    ## year         -0.25146    0.01732 -14.516  < 2e-16 ***
    ## sexM         -9.79796    1.01287  -9.673 8.79e-14 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 3.983 on 59 degrees of freedom
    ## Multiple R-squared:  0.844,  Adjusted R-squared:  0.8387 
    ## F-statistic: 159.6 on 2 and 59 DF,  p-value: < 2.2e-16

Occasionally, you may be interested in the correlation coefficient r
between two quantities.  
You can, of course, compute r by fitting a model, finding R2 , and
taking a square root.

``` r
mod2 <- lm( time ~ year, data = Swim)
coef(mod2)
```

    ## (Intercept)        year 
    ## 567.2420024  -0.2598771

``` r
sqrt(rsquared(mod2))
```

    ## [1] 0.7723752

The `cor()` function computes this directly:

``` r
cor(Swim$time, Swim$year)
```

    ## [1] -0.7723752

Note that the negative sign on \(r\) indicates that record swim `time`
decreases as `year` increases. This information about the direction of
change is contained in the sign of the coefficient from the model. The
magnitude of the coefficient tells how fast the `time` is changing (with
units of seconds per year). The correlation coefficient (like \(R^2\) )
is without units.

Keep in mind that the correlation coefficient r summarizes only the
simple linear model A \~ B where B is quantitative. But the coefficient
of determination, \(R^2\) , summarizes any model; it is much more
useful. If you want to see the direction of change, look at the sign of
the correlation coefficient.
