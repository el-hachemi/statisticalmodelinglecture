10 Total and Partial Change
================
Boukara Ahmed El-Hachemi
15/07/2020

One of the most important ideas in science is ***experiment***. In a
simple, ideal form of an experiment, you cause one explanatory factor to
vary, hold all the other conditions constant, and observe the response.

For non-experimentalists – people who study data collected through
observation, without doing an experiment – a central question is whether
there is a way to mimic “holding all other conditions constant.” Is
there a way to analyze data so that you can separate the influences of
these different factors, examining one factor while, through analysis if
not through experiment, holding the others constant?

In this chapter you’ll see how models can be used to examine data as if
some variables were being held constant. Perhaps the most important
message of the chapter is that there is no point hiding your head in the
sand; simply ignoring a variable is not at all the same thing as holding
that variable constant. By including multiple variables in a model you
make it possible to interpret that model in terms of holding the
variables constant. But there is no methodological magic at work here.
The results of modeling can be misleading if the model does not reflect
the reality of what is happening in the system under study.
Understanding how and when models can be used effectively, and when they
can be misleading, will be a major theme of the remainder of the book.

## 1 Total and Partial Relationships

The common phrase “all other things being equal” is an important
qualifier in describing relationships.

In fields such as economics, the Latin equivalent of “all other things
being equal” is sometimes used: ***ceteris paribus***. So, the economics
claim would be, “higher prices are associated with lower demand,
*ceteris paribus*.”

Although the phrase “all other things being equal” has a logical
simplicity, it’s impractical to implement “all.” Instead of the blanket
“all other things,” it’s helpful to be able to consider just “some
other things” to be held constant, being explicit about what those
things are. Other phrases along these lines are “taking into account …”
and “controlling for ….” Such phrases apply when you want to examine the
relationship between two variables, but there are additional variables
that may be coming into play. The additional variables are called
***covariates*** or ***confounders***.

A covariate is just an ordinary variable. The use of the word
“covariate” rather than “variable” highlights the interest in
holding this variable constant, to indicate that it’s not a variable of
primary interest.

## 2 Example: Covariates and Death

In evaluating the drug, it’s best to examine its effects holding other
factors constant. So, even though the data directly show a 64% increase
in the death rate, 48% is a more meaningful number since it adjusts for
covariates such as patient sickness.

-----

The term ***partial relationship*** describes a relationship with one or
more covariates being held constant.

In contrast to a partial relationship where certain variables are being
held constant, there is also a ***total relationship***: how an
explanatory variable is related to a response variable letting those
other explanatory variables change as they will. (The corresponding
Latin phrase is ***mutatis mutandis***.)

Whether you wish to study a partial or a total relationship is largely
up to you and the context of your work. But certainly you need to know
which relationship you are studying.

### Example: Used Car Prices

A simple linear model: `price` \~ `mileage`. Fitting such a model gives
this model formula

*price* = 20770 - 0.10 × `mileage`.

The price of these Honda Accords typically falls by about 10 cents per
mile driven.

As the cars are being driven, other things are happening to them. They
are wearing out, they are being involved in minor accidents, and they
are getting older. The relationship in the model takes none of these
into account. As mileage changes, the other variables such as age are
changing as they will: a total relationship.

In contrast to the total relationship, the `partial` relationship
between price and mileage holding age constant tells you something
different than the total relationship. The partial relationship would be
relevant, for instance, if you were interested in the cost of driving a
car. This cost includes gasoline, insurance, repairs, and depreciation
of the car’s value. The car will age whether or not you drive it; the
extra depreciation due to driving it will be indicated by the partial
relationship between price and mileage holding age constant.

The most intuitive way to hold age constant is to look at the
relationship between price and mileage for a subset of the cars; include
only those cars of a given age. Instead of the price falling by about 10
cents per mile as it does for all the cars combined, within the 4-8 year
old group the price decrease is only about 7 cents per mile, and only 3
cents per mile for cars older than 8 years.

By looking at the different age groups individually, you are holding age
approximately constant in your model. The relationship you find in this
way between price and mileage is a partial relationship. Of course,
there are other variables that you didn’t hold constant. So, to be
precise, you should describe the relationship you found as a partial
relationship *with respect to age*.

## 3 Models and Partial Relationships

Models make it easy to estimate the partial relationship between a
response variable and an explanatory variable, holding one or more
covariates constant.

The first step is to fit a model using both the explanatory variable and
the covariates that you want to hold constant. For example, to find the
partial relationship between car price and miles driven, holding age
constant, fit the model `price` \~ `mileage`+`age`. For the car-price
data, this gives the model formula

*price* = 21330 - 0.077 × `mileage` - 538 × `age`

The second step is to interpret this model as a partial relationship
between `price` and `mileage` holding `age` constant. A simple way to do
this is to plug in some particular value for `age`, say 1 year. With
this value plugged in, the formula for `price` as a function of
`mileage` becomes

*price* = 21330 - 0.077 × `mileage` - 538 × 1 = 20792 - 0.077 ×
`mileage`

The partial relationship is that `price` goes down by 0.077 dollars per
mile, holding `age` constant.

Note the use of the phrase “estimate the partial relationship” in the
first paragraph of this section. The model you fit creates a
representation of the system you are studying that incorporates both the
variable of interest and the covariates in explaining the response
values. In this mathematical representation, it’s easy to hold the
covariates constant. If you don’t include the covariate in the model,
you can’t hold it constant and so you can’t estimate the partial
relationship between the response and the variable of interest while
holding the covariate constant. But even when you do include the
covariates in your model, there is a legitimate question of whether your
model is a faithful reflection of reality; holding a covariate constant
in a model is not the same thing as holding it constant in the real
world. These issues, which revolve around the idea of the causal
relationship between the covariate and the response, are discussed in
Chapter 18.

### Aside: Partial change and partial derivatives

If you are familiar with calculus and ***partial derivatives***, you may
notice that this rate is the partial derivative of `price` with respect
to `mileage`. Using partial derivatives allows one to interpret more
complicated models relatively easily. For example, the `price` vs
`mileage` lines have different slopes for different age group. To
capture this in your model, you might choose to include an interaction
term between `mileage` and `age`. This gives a model with four terms:

*price* = 22140 - 0.094 × `mileage` - 750× `age` + 0.0034 × `mileage` ×
`age`

For this model, the partial relationship between `price` and `mileage`
is not just the coefficient on `mileage`. Instead it is the partial
derivative of `price` with respect to `mileage`, or:

∂`price` / ∂`mileage` = −0.094 + 0.0034 × `age`

Taking into account the units of the variables, this means that for a
new car (`age` = 0), the price declines by $0.09/mile, that is, 9.4
cents per mile. But for a 10-year old car, the decline is less rapid:
−0.094 + 10×0.0034 = −0.060 – only six cents a mile.

## 4 Adjustment

We have data on professional and sales employees of a large mid-western
US trucking company: the annual earnings in 2007, sex, age, job title,
how many years of employment with the company. Data such as these are
sometimes used to establish whether or not employers discriminate on the
basis of sex.

Fitting the model earnings \~ sex indicates the average difference in
earnings between men and women:

*earnings* = 35501 + 4735 `sexM`.

Since `earnings` are in dollars per year, Men are being paid, on
average, $4735 more per year than women. This difference reflects the
*total* relationship between earnings and sex, letting other variables
change as they will.

Notice from the boxplot that even within the male or female groups,
there is considerable variability in annual earnings from person to
person. Evidently, there is something other than sex that influences the
wages.

An important question is whether you should be interested in the total
relationship between earnings and sex, or the partial relationship,
holding other variables constant. This is a difficult issue. Clearly
there are some legitimate reasons to pay people differently, for example
different levels of skill or experience or different job descriptions,
but it’s always possible that these legitimate factors are being used to
mask discrimination.

For the moment, take as a covariate something that can stand in as a
proxy for experience: the employee’s age. Unlike job title, age is
hardly something that can be manipulated to hide discrimination. Figure
shows the employees’ earnings plotted against age. Also shown are the
fitted model values of wages against age, fitted separately for men and
women. It’s evident that for both men and women, earnings tend to
increase with age. The model design imposes a straight line structure on
the fitted model values. The formulas for the two lines are:

  - For Women Earnings = 17178 + 530 `age`  
  - For Men: Earnings = 16735 + 609 `age`

From the graph, you can see the partial relationship between earnings
and sex, holding age constant. Pick an age, say 30 years. At 30 years,
according to the model, the difference in annual earnings is $1931, with
men making more. At 40 years of age, the difference between the sexes is
even more ($2722), at 20 years of age, the difference is less ($1140).
All of these partial differences (holding age constant) are
substantially less than the difference when age is not taken into
account ($4735).

One way to summarize the differences in earnings between men and women
is to answer this question: How would the earnings of the men have been
different if the men were women? Of course you can’t know all the
changes that might occur if the men were somehow magically transformed,
but you can use the model to calculate the change assuming that all
other variables except sex are held constant. This process is called
***adjustment***.

To find the men’s wages adjusted as if they were women, take the age
data for the men and plug them into the model formula for women. The
difference between the earnings of men and women, adjusting for age, is
$2125. This is much smaller than the difference, $4735, when earnings
are not adjusted for age. Differences in age between the men and women
in the data set appear to account for more than half of the overall
earnings difference between men and women.

Of course, before you draw any conclusions, you need to know how precise
these coefficients are. For instance, it’s a different story if the sex
difference is 2125 ± 10 or if it is 2125 ± 5000. In the latter case, it
would be sensible to conclude only that the data leave the matter of
wage difference undecided. Later chapters in this book describe how to
characterize the precision of an estimate.

Another key matter is that of causation. $2125 indicates a difference,
but doesn’t say completely where the difference comes from. By adjusting
for age, the model disposes of the possibility that the earnings
difference reflects differences in the typical ages of male and female
workers. It remains to be found out whether the earnings difference
might be due to different skill sets, discrimination, or other factors.

## 5 Simpson’s Paradox

Sometimes the total relationship is the opposite of the partial
relationship. This is ***Simpson’s paradox***.

One of the most famous examples involves graduate admissions at the
University of California in Berkeley. It was observed that graduate
admission rates were lower for women than for men overall. This reflects
the total relationship between admissions and sex. But, on a
department-by-department basis, admissions rates for women were
consistently as high or higher than for men. The partial relationship,
taking into account the differences between departments, was utterly
different from the total relationship.

### Example: Cancer Rates Increasing?

Consider another example of partial versus total relationships. In 1962,
naturalist author Rachel Carson published Silent Spring (Carson 1962), a
powerful indictment of the widespread use of pesticides such as DDT.
Carson pointed out the links between DDT and dropping populations of
birds such as the bald eagle. She also speculated that pesticides were
the cause of a recent increase in the number of human cancer cases. The
book’s publication was instrumental in the eventual banning of DDT.

The increase in deaths from cancer over time is a total relationship
between cancer deaths and time. It’s relevant to consider a partial
relationship between the number of cancer deaths and time, holding the
population constant. This partial relationship can be indicated by a
death *rate*: say, the number of cancer deaths per 100,000 people. It
seems obvious that the covariate of population size ought to be held
constant. But there are still other covariates to be held constant. The
decades before Silent Spring had seen a strong decrease in deaths at
young ages from other non-cancer diseases which now were under greater
control. It had also seen a strong increase in smoking. When adjusting
for these covariates, the death rate from cancer was actually falling,
not increasing as Carson claimed.(Tierney 2007)

## 6 Explicitly Holding Covariates Constant

The distinction between explanatory variables and covariates is in the
modeler’s mind. When it comes to fitting a model, both sorts of
variables are considered on an equal basis when calculating the
residuals and choosing the best fitting model to produce a model
function. The way that you choose to interpret and analyze the model
function is what determines whether you are examining partial change or
total change.

The intuitive way to hold a covariate constant is to do just that.
Experimentalists arrange their experimental conditions so that the
covariates are the same. Think of Galileo using balls of the same
diameter and varying only the mass. In a clinical trial of a new drug,
perhaps you would test the drug only on women so that you don’t have to
worry about the covariate sex.

When you are not doing an experiment but rather working with
observational data, you can hold a covariate constant by throwing out
data. Do you want to see the partial relationship between `price` and
`mileage` while holding `age` constant? Then restrict your analysis to
cars that are all the same age, say 3 years old. Want to know the
relationship between breath-holding time and body size holding `sex`
constant? Then study the relationship in just women or in just men.

Dividing data up into groups of similar cases, as in Chapter 4, is an
intuitive way to study partial relationships. It can be effective, but
it is not a very efficient way to use data.

The problem with dividing up data into groups is that the individual
groups may not have many cases.

Modeling provides a powerful and efficient way to study partial
relationships that does not require studying separate subsets of data.
Just include multiple explanatory variables in the model. Whenever you
fit a model with multiple explanatory variables, the model gives you
information about the partial relationship between the response and each
explanatory variable *with respect to each of the other explanatory
variables*.

### Example: SAT Scores and School Spending

chapter 7 showed some models relating school expenditures to SAT scores.
The model `sat` \~ 1 + `expend` produced a negative coefficient on
`expend`, suggesting that higher expenditures are associated with lower
test scores. Including another variable, the fraction of students who
take the SAT (variable `frac`) reversed this relationship.

The model `sat` \~ 1 + `expend` + `frac` attempts to capture how SAT
scores depend both on `expend` and `frac`. In interpreting the model,
you can look at how the SAT scores would change with `expend` while
holding `frac` constant. That is, from the model formula, you can study
the partial relationship between SAT and `expend` while holding `frac`
constant.

The example also looked at a couple of other fiscally related variables:
student-teacher ratio and teachers’ salary. The total relationship
between each of the fiscal variables and SAT was negative – for
instance, higher salaries were associated with lower SAT scores. But the
partial relationship, holding `frac` constant, was the opposite:
Simpson’s Paradox.

For a moment, take at face value the idea that higher teacher salaries
and smaller class sizes are associated with better SAT scores as
indicated by the following models:

*sat* = 988 + 2.18 `salary` - 2.78 `frac`

*sat* = 1119 - 3.73 `ratio` - 2.55 `frac`

In thinking about the impact of an intervention – changing teachers’
salaries or changing the student-teacher ratio – it’s important to think
about what other things will be changing during the intervention. For
example, one of the ways to make student-teacher ratios smaller is to
hire more teachers. This is easier if salaries are held low. Similarly,
salaries can be raised if fewer teachers are hired: increasing class
size is one way to do this. So, salaries and student-teacher ratio are
in conflict with each other.

If you want to anticipate what might be the effect of a change in
teacher salary while holding student-teacher ratio constant, then you
should include `ratio` in the model along with `salary` (and `frac`,
whose dominating influence remains confounded with the other variables
if it is left out of the model):

*sat* = 1058 + 2.55 `salary` - 4.64 `ratio` - 2.91 `frac`

Comparing this model to the previous ones gives some indication of the
trade-off between salaries and student-teacher ratios. When `ratio` is
included along with `salary`, the salary coefficient is somewhat bigger:
2.55 versus 2.18. This suggests that if salary is increased while
holding constant the student-teacher ratio, salary has a stronger
relationship with SAT scores than if salary is increased while allowing
student-teacher ratio to vary in the way it usually does, accordingly.

Of course, you still need to have some way to determine whether the
precision in the estimate of the coefficients is adequate to judge
whether the detected difference in the `salary` coefficient is real –
2.18 in one model and 2.55 in the other. Such issues are introduced in
Chapter 12.

### Aside: Divide and Be Conquered\!

Efficiency starts to be a major issue when there are many covariates.
Consider a study of the partial relationship between lung capacity and
smoking, holding constant all these covariates: sex, body size, smoking
status, age, physical fitness. There are two sexes and perhaps three or
more levels of body size (e.g., small, medium, large). You might divide
age into five different groups (e.g., pre-teens, teens, young adults,
middle aged, elderly) and physical fitness into three levels (e.g.,
never exercise, sometimes, often). Taking the variables altogether,
there are now 2 × 3 × 5 × 3 = 90 groups. It’s very inefficient to treat
these 90 groups completely separately, as if none of the groups had
anything to say about the others. A model of the form

`lung capacity` \~ `body size` + `sex` + `smoking status` + `age` +
`fitness`

can not only do the job more efficiently, but avoids the need to divide
quantitative variables such as `body size` or `age` into categories.

To illustrate, consider this news report:

> Higher vitamin D intake has been associated with a significantly
> reduced risk of pancreatic cancer, according to a study released last
> week.

> Researchers combined data from two prospective studies that included
> 46,771 men ages 40 to 75 and 75,427 women ages 38 to 65. They
> identified 365 cases of pancreatic cancer over 16 years.

> Before their cancer was detected, subjects filled out dietary
> questionnaires, including information on vitamin supplements, and
> researchers calculated vitamin D intake. After statistically adjusting
> for \[that is, holding constant\] age, smoking, level of physical
> activity, intake of calcium and retinol and other factors, the
> association between vitamin D intake and reduced risk of pancreatic
> cancer was still significant.

> Compared with people who consumed less than 150 units of vitamin D a
> day, those who consumed more than 600 units reduced their risk by 41
> percent. - New York Times, 19 Sept. 2006, p. D6.

There are more than 125,000 cases in this study, but only 365 of them
developed pancreatic cancer. If those 365 cases had been scattered
around dozens or hundreds of groups and analyzed separately, there would
be so little data in each group that no pattern would be discernible.

## 7 Adjustment and Truth

It’s tempting to think that including covariates in a model is a way to
reach the truth: a model that describes how the real world works, a
model that can correctly anticipate the consequences of interventions
such as medical treatments or changes in policy, etc. This overstates
the power of models.

A model design – the response variable and explanatory terms – is a
statement of a hypothesis about how the world works. If this hypothesis
happens to be right, then under ideal conditions the coefficients from
the fitted model will approximate how the real world works. But if the
hypothesis is wrong, for example if an important covariate has been left
out, then the coefficients may not correctly describe how the world
works.

In certain situations – the idealized ***experiment*** – researchers can
create a world in which their modeling hypothesis is correct. In such
situations there can be good reason to take the model results as
indicating how the world works. For this reason, the results from
studies based on experiments are generally taken as more reliable than
results from non-experimental studies. But even when an experiment has
been done, the situation may not be ideal; experimental subjects don’t
always do what the experimenter tells them to and uncontrolled
influences can sometimes remain at play.

It’s appropriate to show some humility about models and recognize that
they can be no better than the assumptions that go into them. Useful
object lessons are given by the episodes where conclusions from modeling
(with careful adjustment for covariates) can be compared to experimental
results. Some examples (from (Freedman 2008)):

  - Does it help to use telephone canvassing to get out the vote? Models
    suggest it does, but experiments indicate otherwise.  
  - Is a diet rich in vitamins, fruits, vegetables and low in fat
    protective against cancer, heart disease or cognitive decline?
    Models suggest yes, but experiments generally do not.

The divergence between models and experiment suggests that an important
covariate has been left out of the models.

## 8 The Geometry of Covariates and Adjustment

?????

### Aside: Interaction terms and partial derivatives

Earlier, the idea of measuring effect size using a partial derivative
was introduced. Partial derivatives also provide a way to think about
interaction terms.

To measure the effect size of an explanatory variable, consider the
partial derivative of the response variable with respect to the
explanatory. Writing the response as z and the explanatory variables as
x and y, the effect size of x corresponds to ∂z/∂x.

An interaction – how one explanatory variable modulates the effect of
another on the response variable – corresponds to a mixed second-order
partial derivative. For instance, the size of an interaction between x
and y on response z corresponds to ∂²z / ∂x∂y.

A theorem in calculus shows that mixed partials have the same value
regardless of the order in which the derivatives are taken. In other
words, ∂²z / ∂x ∂y = ∂²z / ∂y∂x. This is the mathematical way of stating
that the way x modulates the effect of y on z is the same thing as the
way that y modulates the effect of x on z.

-----

## Computational Technique

### 1 Adjustment

There are two basic approaches to adjusting for covariates.
Conceptually, the simplest one is to hold the covariates constant at
some level when collecting data or by extracting a subset of data which
holds those covariates constant. The other approach is to include the
covariates in your models.

For example, suppose you want to study the differences in the wages of
male and females. The very simple model `wage` \~ `sex` might give some
insight, but it attributes to `sex` effects that might actually be due
to level of education, age, or the sector of the economy in which the
person works. Here’s the result from the simple model:

``` r
cps <- CPS85
mod0 <- lm(wage ~ sex, data = cps)
summary(mod0)
```

    ## 
    ## Call:
    ## lm(formula = wage ~ sex, data = cps)
    ## 
    ## Residuals:
    ##    Min     1Q Median     3Q    Max 
    ## -8.995 -3.529 -1.072  2.394 36.621 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)   7.8789     0.3216   24.50  < 2e-16 ***
    ## sexM          2.1161     0.4372    4.84  1.7e-06 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 5.034 on 532 degrees of freedom
    ## Multiple R-squared:  0.04218,    Adjusted R-squared:  0.04038 
    ## F-statistic: 23.43 on 1 and 532 DF,  p-value: 1.703e-06

The coefficients indicate that a typical male makes $2.12 more per hour
than a typical female. (Notice that \(R^2\)=0.0422 is very small: `sex`
explains hardly any of the person-to-person variability in wage.)

By including the variables `age`, `educ`, and `sector` in the model, you
can adjust for these variables:

``` r
mod1 <- lm(wage ~ age + sex + educ + sector, data = cps)
summary(mod1)
```

    ## 
    ## Call:
    ## lm(formula = wage ~ age + sex + educ + sector, data = cps)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -11.198  -2.695  -0.465   2.066  35.159 
    ## 
    ## Coefficients:
    ##               Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)   -4.69411    1.53776  -3.053 0.002384 ** 
    ## age            0.10221    0.01657   6.167 1.39e-09 ***
    ## sexM           1.94172    0.42285   4.592 5.51e-06 ***
    ## educ           0.61556    0.09439   6.521 1.65e-10 ***
    ## sectorconst    1.43552    1.13120   1.269 0.204999    
    ## sectormanag    3.27105    0.76685   4.266 2.37e-05 ***
    ## sectormanuf    0.80627    0.73115   1.103 0.270644    
    ## sectorother    0.75838    0.75918   0.999 0.318286    
    ## sectorprof     2.24777    0.66976   3.356 0.000848 ***
    ## sectorsales   -0.76706    0.84202  -0.911 0.362729    
    ## sectorservice -0.56871    0.66602  -0.854 0.393556    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 4.334 on 523 degrees of freedom
    ## Multiple R-squared:  0.3022, Adjusted R-squared:  0.2888 
    ## F-statistic: 22.65 on 10 and 523 DF,  p-value: < 2.2e-16

The adjusted difference between the sexes is $1.94 per hour. (The
\(R^2\)=0.30 from this model is considerably larger than for `mod0`, but
still a lot of the person-to-person variation in wages has not be
captured.)

It would be wrong to claim that simply including a covariate in a model
guarantees that an appropriate adjustment has been made. The
effectiveness of the adjustment depends on whether the model design is
appropriate, for instance whether appropriate interaction terms have
been included. However, it’s certainly the case that if you **don’t**
include the covariate in the model, you have **not** adjusted for it.

The other approach is to subsample the data so that the levels of the
covariates are approximately constant. For example, here is a subset
that considers workers between the ages of 30 and 35 with between 10 to
12 years of education and working in the sales sector of the economy:

``` r
small <- subset(cps, 
  age <= 35 & age >= 30 &
    educ >= 10 & educ <= 12 & 
    sector == "sales"
)
```
