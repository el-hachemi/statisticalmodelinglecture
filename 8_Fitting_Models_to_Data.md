8 Fitting Models to Data
================
Boukara Ahmed El-Hachemi
14/07/2020

This chapter is about a technical matter: ***fitting***, how to find the
coefficients that best match the model you choose to the data you have
collected.

Fitting a model – once you have specified the design – is an entirely
automatic process that requires no human decision making. Nevertheless,
it’s important to understand the way in which the computer finds the
coefficients.

Depending on your data and your model design, you may introduce
ambiguities into your model that make the model less reliable than it
could be. These ambiguities, which stem from ***redundancy*** and
***multicollinearity***, are revealed by the fitting process.

## 1 The Least Squares Criterion

Fitting a model is somewhat like buying clothes. the style of clothing
is the model design – you choose this. Your body shape is like the data
– you’re pretty much stuck with what you’ve got.

When you are in the fitting room of a store, you try on different items
of clothing with a range of values of the coefficients.

Unlike clothing, however, there is a very simple, entirely objective
criterion for judging the overall fit called the ***least squares***
criterion.

It is not uncommon in comparing two formulas to find, as in this model,
one formula is better for some cases and the other formula is better for
other cases. This is not so different from clothing, where one item may
be too snug in the waist but just right in the leg, and another item may
be perfect in the waist but too long in the leg.

What’s needed is a way to judge the *overall* fit. In modeling, the
overall fit of a model formula is measured by a single number: the sum
of squares of the residuals.

To find the **best** fit, keep trying different formulas until one is
found that gives the least sum of square residuals: in short, the
***least squares***.

It makes sense to compare the sum of square residuals for two model
formulas only when the two formulas have the same design and are fitted
with the same data. So don’t try to use the sum of square residuals to
decide which of two different designs are better. Tools to do that will
be introduced in later chapters.

### Aside: Why Square Residuals?

In the late 18th century, three different criteria were competing, each
of which made sense:

1.  The least squares criterion, which seeks to minimize the sum of
    square residuals.
2.  The least absolute value criterion. That is, rather than the sum of
    square residuals, one looks at the sum of absolute values of the
    residuals.
3.  Make the absolute value of the residual as small as possible for the
    single worst case.

Computationally, the least squares criterion leads to simpler procedures
than the least absolute value criterion. In the 18th century, when
computing was done by hand, this was a very important issue. It’s no
longer so, and there can be good statistical reasons to favor a least
absolute value criterion when it is thought that the data may contain
outliers.

The least squares criterion is best justified when variables have a
bell-shaped distribution. Insofar as this is the situation – and it
often is – the least squares criterion is arguably better than least
absolute value.

Another key advantage of the least squares criterion is in
interpretation, as you’ll see in Section 8.

## 2 Partitioning Variation

A model is intended to explain the variation in the response variable
using the variation in the explanatory variables. It’s helpful in
quantifying the success of this to be able to measure how much variation
there is in the response variable, how much has been explained, and how
much remains unexplained. This is a ***partitioning*** of variation into
parts.

Section 4.2 introduced the idea of partitioning variation in the context
of simple group-wise models. There, it was shown that the variance – the
square of the standard deviation – is a useful way to quantify variation
because it has the property of exactly dividing total variation into
parts: the variation of model values and the variation of the residuals.

The variance has this same useful partitioning property with
least-squares models. Chapter 9 describes how the variance is used to
construct a simple measure, called R², of the quality of fit of a model.

### Aside: Partitioning and the Sum of Squares

Another partitioning statistic is the ***sum of squares***. The sum of
squares is deceptively simple. To find the sum of squares of the
response variable, just square the value for each case and add them up.
Similarly, you can find the sum of squares of the fitted model values
and the sum of squares of the residuals. The partitioning property is
that the sum of squares of the response variable exactly equals the sum
of squares of the fitted model values plus the sum of squares of the
residuals.

## 3 The Geometry of Least Squares Fitting

Consider a very simple model, A \~ B. Each of the vectors involved, A
and B, has a length and a direction, For instance, the vector c(3, 4),
when plotted in the usual Cartesian coordinate plane, points to the
north-northeast and has square-length 3² + 4² = 5².

The process of least-squares fitting amounts to finding the point on the
“subspace defined by B” that is as close as possible to A. You can do
this by eye, if you like. Move your finger along the line that is the
subspace defined by B to the point on that line that is as close as you
can get to the tip of vector A.

The vector that connects them is the ***residual vector***.

Notice that choosing the fitted value as the closest point to A on the
subspace defined by B means that the residual vector will be
***perpendicular*** to B. In statistics, the term that’s used for
“perpendicular” is ***orthogonal***.

One consequence of the orthogonality is that the three vectors involved
– A, B, and the residual – form a right triangle. This is why the
Pythagorean theorem applies and why it’s square quantities – the
variance and the sum of squares – that have the partitioning property.

## 4 Redundancy

consider the following data collected in 2009 on prices of used cars
(the Ford Taurus model), the year the car was built, and the number of
miles the car has been driven.

A group of students thought to see how price depends on year and
mileage. After collecting a sample of 635 cars advertised on the
Internet, they fit a model price \~ mileage + year. The coefficients
came out to be:

| Term      |   Coefficient | Units        |
| :-------- | ------------: | :----------- |
| Intercpet | \-1136311.500 | dollars      |
| milage    |       \-0.069 | dollars/mile |
| year      |       573.500 | dollars/year |

The coefficient on `mileage` is straightforward enough; according to the
model the price of these cars typically decreases by 6.9 cents per mile.
But the intercept seems strange: very big and negative. Of course this
is because the intercept tells the model value at zero mileage in the
year zero\! They checked the plausibility of the model by plugging in
values for a 2006 car with 50,000 miles: −1136312 − 0.069 × 50000 + 2006
× 573.50 giving $10679.50 – a reasonable sounding price for such a car.

The students thought that the coefficients would make more sense if they
were presented in terms of the `age` of the car rather than the model
year. Since their data was from 2009, they calculated the `age` by
taking 2009 − `year`. Then they fit the model `price` \~ `mileage` +
`age`. Of course, there is no new information in the `age` variable that
isn’t already in the `year` variable. Even so, the information is
provided in a new way and so the coefficients in the new model are
somewhat different.

| Term      | Coefficient | Units        |
| :-------- | ----------: | :----------- |
| Intercpet |   15850.000 | dollars      |
| milage    |     \-0.069 | dollars/mile |
| age       |   \-573.500 | dollars/year |

From the table, you can see that the `mileage` coefficient is unchanged,
but now the intercept term looks much more like a real price: the price
of a hypothetical brand new car with zero miles. The `age` coefficient
makes sense; typically the cars decrease in price by $573.50 per year of
age. Again, the students calculated the model for a 2006 car (thus age 3
years in 2009) with 50,000 miles: $10679.50, the same as before.

At first, the students were surprised by the differences between the two
sets of coefficients. Then they realized that the two different model
formulas give exactly the same model value for every car. This makes
sense. The two models are based on exactly the same information. The
only difference is that in one model the age is given by the model year
of the car, in the other by the age itself.

The students decided to experiment. “What happens if we include both
`age` and `year` in the model?” The started with the model `price` \~
`mileage` + `year` + `age`. They got these coefficients:

| Term      |   Coefficient | Units        |
| :-------- | ------------: | :----------- |
| Intercpet | \-1136311.000 | dollars      |
| milage    |       \-0.069 | dollars/mile |
| year      |       573.500 | dollars/year |
| age       |            NA | dollars/year |

The model is effectively disregarding the age variable, reporting the
coefficient as “NA”, not available.

The dual identity of age and year is ***redundancy***. (The mathematical
term is “***linear dependence***.”) It arises whenever an explanatory
model vector can be modeled exactly in terms of the other explanatory
vectors.

In order to avoid this ambiguity, modeling software is written to spot
any redundancy and drop the redundant model vectors from the model. One
possibility would be to report a coefficient of zero for the redundant
vector. But this could be misleading. For instance, the user might
interpret the zero coefficient on Set 1 above as meaning that year isn’t
associated with price. But that would be wrong; year is a very important
determinant of price, it’s just that all the relationship is represented
by the coefficient on age in Set 1. Rather than report a coefficient of
zero, it’s helpful when software reports the redundancy by displaying a
NA. This makes it clear that it is redundancy that is the issue and not
that a coefficient is genuinely zero.

When model vectors are redundant, modeling software can spot the
redundancy and do the right thing. But sometimes, the redundancy is only
approximate, a situation called ***multi-collinearity***. In such cases
it’s important for you to be aware of the potential for problems; they
will not be clearly marked by NA as happens with exact redundancy.

### Example: Almost redundant

In collecting the Current Population Survey wage data, interviewers
asked people their age and the number of years of education they had.
From this, they computed the number of years of experience. They
presumed that kids spend six years before starting school. So a 40-year
old with 12 years of education would have 22 years of experience: 6 + 12
+ 22 = 40. This creates redundancy of `experience` with `age` and
`education`. Ordinarily, the computer could identify such a situation.
However, there is a mistake in the CPS data. Case 350 is an 18-year old
woman with 16 years of education. This seems hard to believe since very
few people start their education at age 2. Presumably, either the age or
education were mis-recorded. But either way, this small mistake in one
case means that the redundancy among `experience`, `age`, and
`education` is not exact. It also means that standard software doesn’t
spot the problem when all three of these variables are included in a
model. As a result, coefficients on these variables are highly
unreliable.

With such multi-collinearity, as opposed to exact redundancy, there is a
unique least-squares fit of the model to the data. However, this
uniqueness is hardly a blessing. What breaks the tie to produce a unique
best fitting set of coefficients are the small deviations from exact
redundancy. These are often just a matter of random noise, arithmetic
round-off, or mistakes as with case 350 in the Current Population Survey
data. As a result, the choice of the winning set of coefficients is to
some extent arbitrary and potentially misleading.

The costs of multi-collinearity can be measured when fitting a model.
(See Section 12.6.) When the costs of multi-collinearity are too high,
the modeler often chooses to take terms out of the model.

### Aside: Redundancy – (Almost) Anything Goes

Even with the duplicate information in `year` and `age`, there is no
mathematical reason why the computer could not have given coefficients
for all four model terms in the model `price` \~ `mileage` + `year` +
`age`. For example, any of the following sets of coefficients would give
exactly the same model values for any inputs of `year` and `mileage`,
with `age` being appropriately calculated from `year`.

| Term      |      Set1 |         Set2 |         Set3 |          Set4 |
| :-------- | --------: | -----------: | -----------: | ------------: |
| Intercpet | 15850.000 | \-185050.000 | \-734511.500 | \-1136311.500 |
| milage    |   \-0.069 |      \-0.069 |      \-0.069 |         0.069 |
| year      |     0.000 |      100.000 |      373.500 |       573.500 |
| age       | \-573.500 |    \-473.500 |    \-200.000 |         0.000 |

The overall pattern is that the coefficient on `age` minus the
coefficient on `year` has to be −573.5. This works because `age` and
`year` are basically the same thing since `age` = 2009 − `year`.

-----

## Computational Technique

Computing the fitted model values and the residuals is done with the
`fitted` and `resid`. These operators take a model as an input. To
illustrate:

``` r
swim <- SwimRecords
mod1 <- lm(time ~ year + sex, data = swim)
coef(mod1)
```

    ## (Intercept)        year        sexM 
    ## 555.7167834  -0.2514637  -9.7979615

Once you have constructed the model, you can use `fitted` and `resid`:

``` r
modvals <- fitted(mod1)
head(modvals)
```

    ##        1        2        3        4        5        6 
    ## 66.88051 66.12612 65.62319 65.12026 63.61148 63.10855

### Sum of squares

Computations can be performed on the fitted model values and the
residuals, just like any other quantity:

``` r
mean(fitted(mod1))
```

    ## [1] 59.92419

``` r
var(resid(mod1))
```

    ## [1] 15.34147

``` r
sd(resid(mod1))
```

    ## [1] 3.916818

``` r
summary(resid(mod1))
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ## -4.7027 -2.7027 -0.5968  0.0000  1.2796 19.0759

Sums of squares are very important in statistics. Here’s how to
calculate them for the response values, the fitted model values, and the
residuals:

``` r
sum(swim$time^2)
```

    ## [1] 228635

``` r
sum(fitted(mod1)^2)
```

    ## [1] 227699.2

``` r
sum(resid(mod1)^2)
```

    ## [1] 935.8294

The partitioning of variation by models is seen by the way the sum of
squares of the fitted and the residuals add up to the sum of squares of
the response:

``` r
227699.2 + 935.8294
```

    ## [1] 228635

Don’t forget the squaring stage of the operation\! The sum of the
residuals (without squaring) is very different from the sum of squares
of the residuals:

``` r
sum(resid(mod1))
```

    ## [1] 1.848521e-14

``` r
sum(resid(mod1)^2)
```

    ## [1] 935.8294

Take care in reading numbers formatted like 1.849e-14. The notation
stands for 1.849×10−14 . That number, 0.00000000000001849 , is
effectively zero compared to the residuals themselves\!

### 2 Redundancy

The `lm` operator will automatically detect redundancy and deal with it
by leaving the redundant terms out of the model.

To see how redundancy is handled, here is an example with a constructed
redundant variable in the swimming dataset.  
The following statement adds a new variable to the dataframe counting
how many years after the end of World War II each record was
established:

``` r
swim$afterwar <- swim$year - 1945
```

Here is a model that doesn’t involve redundancy

``` r
mod2 <- lm(time ~ year + sex, data = swim)
coefficients(mod2)
```

    ## (Intercept)        year        sexM 
    ## 555.7167834  -0.2514637  -9.7979615

When the redundant variable is added in, lm successfully detects the
redundancy and handles it. This is indicated by a coefficient of NA on
the redundant variable.

``` r
mod2 <- lm(time ~ year + sex + afterwar, data = swim)
coef(mod2)
```

    ## (Intercept)        year        sexM    afterwar 
    ## 555.7167834  -0.2514637  -9.7979615          NA

In the absence of redundancy, the model coefficients don’t depend on the
order in which the model terms are specified. But this is not the case
when there is redundancy, since any redundancy is blamed on the later
variables. For instance, here `afterwar` has been put first in the
explanatory terms, so `lm` identifies `year` as the redundant variable:

``` r
mod3 <- lm( time ~ afterwar + year + sex, data = swim)
coef(mod3)
```

    ## (Intercept)    afterwar        year        sexM 
    ##  66.6199228  -0.2514637          NA  -9.7979615

Even though the coefficients are different, the fitted model values and
the residuals are exactly the same (to within computer round-off)
regardless of the order of the model terms.

``` r
head(fitted(mod2))
```

    ##        1        2        3        4        5        6 
    ## 66.88051 66.12612 65.62319 65.12026 63.61148 63.10855

``` r
head(fitted(mod3))
```

    ##        1        2        3        4        5        6 
    ## 66.88051 66.12612 65.62319 65.12026 63.61148 63.10855

Note that whenever you use a categorical variable and an intercept term
in a model, there is a redundancy. This is not shown explicitly. For
example, here is a model with no intercept term, and both levels of the
categorical variable sex show up with coefficients:

``` r
mod <- lm( time ~ sex - 1, data = swim)
coef(mod)
```

    ##     sexF     sexM 
    ## 65.19226 54.65613

If the intercept term is included (as it is by default unless -1 is used
in the model formula), one of the levels is simply dropped in the
report:

``` r
mod <- lm( time ~ sex, data = swim)
coef(mod)
```

    ## (Intercept)        sexM 
    ##    65.19226   -10.53613

Remember that this coefficient report implicitly involves a redundancy.
