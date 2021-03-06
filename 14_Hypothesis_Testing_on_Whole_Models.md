14 Hypothesis Testing on Whole Models
================
Boukara Ahmed El-Hachemi
23/07/2020

It’s important to remember that in a hypothesis test, the null
hypothesis is about the **population**. The null hypothesis claims that
in the population the explanatory variables are unlinked to the response
variable. Such a hypothesis does not rule out the possibility that, in
the sample, the explanatory variables are aligned with the response
variable. The hypothesis merely claims that any such alignment is
accidental, due to the randomness of the sampling process.

## 1 The Permutation Test

The null hypothesis is that the explanatory variables are unlinked with
the response variable. One way to see how big a test statistic will be
in a world where the null hypothesis holds true is to randomize the
explanatory variables in the sample to destroy any relationship between
them and the response variable.

Imagine that the table has been cut into horizontal slips with one case
on each slip. The response variable – say, A – has been written to the
left of a dotted line. The explanatory variables B and C are on the
right of the dotted line:

To randomize the cases, tear each sheet along the dotted line. Place the
right sides – the explanatory variables – on a table in their original
order. Then, randomly shuffle the left halves – the response variable –
and attach each to a right half.

None of the cases in the shuffle are genuine cases, except possibly by
chance. Yet each of the shuffled explanatory variables is true to its
distribution in the original sample and the relationships among
explanatory variables – collinearity and multi-collinearity – are also
authentic.

Each possible order for the left halves of the cards is called a
**permutation**. A hypothesis test conducted in this way is called a
***permutation test***.

The logic of a permutation test is straightforward. To set up the test,
you need to choose a test statistic that reflects some aspect of the
system of interest to you.

Here are the steps involved in permutation test:

  - Step 1. Calculate the value of the test statistic on the original
    data.
  - Step 2. Permute the data and calculate the test statistic again.
    Repeat this many times, collecting the results. This gives the
    distribution of the test statistic under the null hypothesis.
  - Step 3. Read off the p-value as the fraction of the results in (2)
    that are more extreme than the value in (1).

## 2 R² and the F Statistic

The coefficient of determination R² measures what fraction of the
variance of the response variable is “explained” or “accounted for” or –
to put it simply – “modeled” by the explanatory variables. R² is a
comparison of two quantities: the variance of the fitted model values to
the variance of the response variable. R² is a single number that puts
the explanation in the context of what remains unexplained. It’s a good
test statistic for a hypothesis test.

Using R² as the test statistic in a permutation test would be simple
enough. There are advantages, however, to thinking about things in terms
of a closely related statistic invented by Fisher and named in honor of
him: the ***F statistic***.

Like R², the F statistic compares the size of the fitted model values to
the size of the residuals. But the notion of “size” is somewhat
different. Rather than measuring size directly by the variance or by the
sum of squares, the F statistic takes into account the number of model
vectors.

To see where F comes from, consider the ***random model walk*** . In a
regular random walk, each new step is taken in a random direction. In a
random model walk, each “step” consists of adding a new random
explanatory term to a model. The “position” is measured as the R² from
the model.

The starting point of the random model walk is the simple model A \~ 1
with just m=1 model vector. This model always produces R² = 0 because
the all-cases-the-same model can’t account for any variance. Taking a
“step” means adding a random model vector, x₁, giving the model A \~
1+x₁. Each new step adds a new random vector to the model.

All the random walks start at R² = 0 for m=1. All of them reach R² = 1
when m=n. Adding any more vectors beyond m=n simply creates redundancy;
R² = 1 is the best that can be done.

Notice that each step increases R² – none of the random walks goes down
in value as m gets bigger.

The F statistic is the ratio of these two slopes:

\[F = \frac{\mbox{slope of model segment}}{\mbox{slope of residual segment}} = \frac{R^2}{m-1} / \frac{1-R^2}{n-m}\]

In interpreting the F statistic, keep in mind that if the model vectors
were no better than random, F should be near 1. When F is much bigger
than 1, it indicates that the model terms explain more than would be
expected at random. The p-value provides an effective way to identify
when F is “much bigger than 1.” Calculating the p-value involves knowing
the exact shape of the F distribution. In practice, this is done with
software.

The number m-1 in the numerator of F counts how many model terms there
are other than the intercept. In standard statistical nomenclature, this
is called the ***degrees of freedom of the numerator*** . The number n−m
in the denominator of F counts how many random terms would need to be
added to make a “perfect” fit to the response variable. This number is
called the ***degrees of freedom of the denominator*** .

### Example: Marriage and Astrology

Does your astrological sign predict when you will get married? To test
this possibility, consider a small set of data collected from an on-line
repository of marriage licenses in Mobile County, Alabama in the US. The
licenses contain a variety of information: age at marriage, years of
college, date of birth, date of the wedding and so on.

There are, of course, 12 different astrological signs, so the model
`Age` \~ `Sign` has m=12. With the intercept term, that leaves 11
vectors to represent `Sign`. Fitting the model produces R² = 0.070. To
generate a p-value, this can be compared to the distribution of R² for
random vectors with n=98 and m=12, giving p=0.885. This large value is
consistent with the null hypothesis that `Sign` is unlinked with `Age`.

The pair m=12, R² = 0.070 gives one point on a model walk. The 11
indicator vectors that arise from the 12 levels of Sign do not
contribute more to R² than would be expected from 11 random vectors.

Now consider a different model, `Age` \~ `College`. This model
undertakes to explain age at marriage by whether the person went to
college. The R² from this model is only 0.065 – the `College` variable
accounts for somewhat less of the variability in `Age` than astrological
`Sign`. Yet this small R² is statistically significant – p=0.017. The
reason is that `College` accomplishes its explanation using only a
single model vector, compared to the 11 vectors in `Sign`. The model
walk for the `College` model starts with a steep increase because the
whole gain of 0.065 is accomplished with just one model vector, rather
than being achieved using 11 vectors as in `Sign`.

## 3 The ANOVA Report

The F statistic compares the variation that is explained by the model to
the variation that remains unexplained. Doing this involves taking apart
the variation; partitioning it into a part associated with the model and
a part associated with the residuals.

Such partitioning of variation is fundamental to statistical methods.
When done in the context of linear models, this partitioning is given
the name ***analysis of variance*** ANOVA for short. This name stays
close to the dictionary definition of “analysis” as “the process of
separating something into its constituent elements.” (“New Oxford
American Dictionary” 2015)

The analysis of variance is often presented in a standard way: the
***ANOVA report*** . For example, here is the ANOVA report for the
marriage-astrology model `Age` \~ `Sign`:

|           | Df | Sum.Sq | Mean.Sq | F value | p-value |
| :-------- | -: | -----: | ------: | ------: | ------: |
| Sign      | 11 |   1402 |     127 |    0.59 |  0.8359 |
| Residuals | 86 |  18724 |     218 |         |         |

There are two rows in this ANOVA report. The first refers to the
explanatory variable, the second to the residual.

Since ANOVA is about variance, the mean of the response variable is
subtracted out before the analysis is performed, just as it would be
when calculating a variance. The column labeled “Sum Sq” gives the sum
of squares of the fitted model values and the residual vector. The
column headed “Df” is the degrees of freedom of the term. This is simply
the number of model vectors associated with that term or, for the
residual, the total number of cases minus the number of explanatory
vectors. For a categorical variable, the number of explanatory vectors
is the number of levels of that variable minus one for each redundant
vector. (For instance, every categorical variable has one degree of
redundancy with the intercept). Because there are 12 levels in `Sign`,
the 12 astrological signs, the `Sign` variable has 11 degrees of
freedom.

The degrees of freedom of the residuals is the number of cases n minus
the number of model terms m.

### Aside: F and R²

The R² doesn’t appear explicitly in the ANOVA report, but it’s easy to
calculate since the report does give the square lengths of the two legs
of the model triangle. In the above ANOVA report for `Age` \~ `Sign`,
the square length of the hypotenuse is, through the pythagorean
relationship, simply the sum of the two legs: in this report, 1402 +
18724 = 20126. The model’s R² is the square length of the
fitted-model-value leg divided into the square length of the hypotenuse:
1402 / 20126 = 0.070.

The ***mean square*** in each row is the sum of squares divided by the
degrees of freedom. The table’s F value is the ratio of the mean square
of the fitted model values to the mean square of the residuals: 127 /
218 = 0.585 in this example. This is the same as given by Equation 14.1,
but the calculations are being done in a different order.

Finally, the F value is converted to a p-value by look-up in the
appropriate F distribution with the indicated degrees of freedom in the
numerator and the denominator.

### Example: Is height genetically determined?

The report summarizes the extent to which `height` is associated with
inheritance from the `mother` and the `father` and by the genetic trait
`sex`, using the model `height` \~ 1 + `sex` + `mother` + `father`.

|               |  Df | Sum.Sq | Mean.Sq | F.value | p-value |
| :------------ | --: | -----: | ------: | ------: | ------: |
| Genetic Terms |   3 |   7366 |    2455 |     529 |       0 |
| Residuals     | 894 |   4159 |       5 |         |         |

The F value is huge and accordingly the p-value is very small: the
genetic variables are clearly explaining much more of `height` than
random vectors.

If Galton had access to modern statistical approaches – even those from
as long ago as the middle of the twentieth century – he might have
wondered how to go further, for example how to figure out whether the
mother and father each contribute to height, or whether it is a trait
that comes primarily from one parent. Answering such questions involves
partitioning the variance not merely between the model terms and the
residual but *among* the individual model terms. This is the subject of
Chapter 15.

### Aside: The shape of F

The shape of the F distribution depends on both n and m. Despite slight
differences, the F distributions are all centered on 1. (In contrast,
distributions of R² change shape substantially with m and n.) This
steadiness in the F distribution makes it easy to interpret an F
statistic by eye since a value near 1 is a plausible outcome from the
null hypothesis. (The meaning of “near” reflects the width of the
distribution: When n is much bigger than m, the the F distribution has
mean 1 and standard deviation that is roughly √(2/m).)

Presenting F with m and n as the parameters violates a convention. The F
distribution is always specified in terms of the degrees of freedom of
the numerator m-1 and the degrees of freedom of the denominator n-m.

### Example: F and Astrology

The model `Age` \~ `Sign` produced R² = 0.070 with m=12 model vectors
and n=98 cases. The F statistic is therefore (0.070/11)/(0.930/86) =
0.585. Since F is somewhat less than 1, there is no reason to think that
the `Sign` vectors are more effective than random vectors in explaining
`Age`. Finding a p-value involves looking up the value F=0.585 in the F
distribution with m-1=11 degrees of freedom in the numerator and n-m=86
degrees of freedom in the denominator.

The p-value is the probability of seeing an F value from this
distribution that is larger than the observed value of F=0.585. From the
figure, it’s easy to see that p is more than one-half since a majority
of the distribution falls to the right of 0.585. Calculating it exactly
using software gives p=0.836.

## 4 Interpreting the p-value

The p-value is a useful format for summarizing the strength of evidence
that the data provide. But statistical evidence, like any other form of
evidence, needs to be interpreted in context.

### Multiple Comparisons

Keep in mind that a hypothesis test, particularly when p is near the
conventional p\<0.05 threshold for rejection of the null, is a very weak
standard of evidence. Failure to reject the null may just mean that
there isn’t enough data to reveal the patterns, or that important
explanatory variables have not been included in the model.

But even when the p-value is below 0.05, it needs to be interpreted in
the context within which the tested hypothesis was generated. Often,
models are used to explore data, looking for relationships among
variables. The hypothesis tests that stem from such an exploration can
give misleadingly low p-values. To illustrate, consider an analogous
situation in the world of crime. Suppose there were 20 different genetic
markers evenly distributed through the population. A crime has been
committed and solid evidence found on the scene shows that the
perpetrator has a particular genetic marker, M, found in only 5% of the
population. The police fan out through the city, testing passersby for
the M marker. A man with M is quickly found and arrested.

Should he be convicted based on this evidence? Of course not. That this
specific man should match the crime marker is unlikely, a probability of
only 5%. But by testing large numbers of people who have no particular
connection to the crime, it’s a guarantee that someone who matches will
be found.

Now suppose that eyewitnesses had seen the crime at a distance. The
police arrived at the scene and quickly cordoned off the area. A man,
clearly nervous and disturbed, was caught trying to sneak through the
cordon. Questioning by the police revealed that he didn’t live in the
area. His story for why he was there did not hold up. A genetic test
shows he has marker M. This provides much stronger, much more credible
evidence. The physical datum of a match is just the same as in the
previous scenario, but the context in which that datum is set is much
more compelling.

The lesson here is that the p-value needs to be interpreted in context.
The p-value itself doesn’t reveal that context. Instead, the story of
the research project come into play. Have many different models been
fitted to the data? If so, then it’s likely that one or more of them may
have p \< 0.05 even if the explanatory variables are not linked to the
response.

It’s a grave misinterpretation of hypothesis testing to treat the
p-value as the probability that the null hypothesis is true. Remember,
the p-value is based on the assumption that the null hypothesis is true.
A low p-value may call that assumption into doubt, but that doubt needs
to be placed into the context of the overall situation.

Consider the unfortunate researcher who happens to work in a world where
the null hypothesis is always true. In this world, each study that the
researcher performs will produce a p-value that is effectively a random
number equally likely to be anywhere between 0 and 1. If this researcher
performs many studies, it’s highly likely that one or more of them will
produce a p-value less than 0.05 even though the null is true.

Tempting though it may be to select a single study from the overall set
based on its low p-value, it’s a mistake to claim that this isolated
p-value accurately depicts the probability of the null hypothesis.
Statistician David Freedman writes, “Given a significant finding … the
chance of the null hypothesis being true is ill-defined – especially
when publication is driven by the search for significance.”

One approach to dealing with multiple tests is to adjust the threshold
for rejection of the null to reflect the multiple possibilities that
chance has to produce a small p-value. A simple and conservative method
for adjusting for multiple tests is the ***Bonferroni correction***.
Suppose you perform k different tests. The Bonferroni correction adjusts
the threshold for rejection downward by a factor of 1/k. For example, if
you perform 15 hypothesis tests, rather than rejecting the null at a
level of 0.05, your threshold for rejection should be 0.05/15 = 0.0033.

Another strategy is to treat multiple testing situations as “hypothesis
generators.” Tests that produce low p-values are not to be automatically
deemed as significant but as worthwhile candidates for further
testing.(Saville 1990). Go out and collect a new sample, independent of
the original one. Then use this sample to perform exactly one hypothesis
test: re-testing the model whose low p-value originally prompted your
interest. This common-sense procedure is called an ***out-of-sample***
test, since the test is performed on data outside the original sample
used to form the hypothesis. In contrast, tests conducted on the data
used to form the hypothesis are called ***in-sample*** tests. It’s
appropriate to be skeptical of in-sample tests.

When reading work from others, it can be hard to know for sure whether a
test is in-sample or out-of-sample. For this reason, researchers value
***prospective studies***, where the data are collected after the
hypothesis has been framed. Obviously, data from a prospective study
must be out-of-sample. In contrast, in ***retrospective studies***,
where data that have already been collected are used to test the
hypothesis, there is a possibility that the same data used to form the
hypothesis are also being used to test it. Retrospective studies are
often disparaged for this reason, although really the issue is whether
the data are in-sample or out-of-sample. (Retrospective studies also
have the disadvantage that the data being analyzed might not have been
collected in a way that optimally addresses the hypothesis. For example,
important covariates might have been neglected.)

### Example: Multiple Jeopardy

You might be thinking: Who would conduct multiple tests, effectively
shopping around for a low p-value? It happens all the time, even in
situations where wrong conclusions have important implications.\[1\].

To illustrate, consider the procedures adopted by the US Government’s
Office of Federal Contract Compliance Programs when auditing government
contractors to see if they discriminate in their hiring practices. The
OFCCP requires contractors to submit a report listing the number of
applicants and the number of hires broken down by sex, by several
racial/ethnic categories, and by job group. In one such report, there
were 9 job groups (manager, professional, technical, sales workers,
office/clerical, skilled crafts, operatives, laborers, service workers)
and 6 discrimination categories (Black, Hispanic, Asian/Pacific
Islander, American Indian/American Native, females, and people with
disabilities).

According to the OFCCP operating procedures (Federal Contract Compliance
Programs, n.d.), a separate hypothesis test with a rejection threshold
of about 0.05 is to be undertaken for each job group and for each
discrimination category, for example, discrimination against Black
managers or against female sales workers. This corresponds to 54
different hypothesis tests. Rejection of the null in any one of these
tests triggers punitive action by the OFCCP. Audits can occur annually,
so there is even more potential for repeated testing.

Such procedures are not legitimately called hypothesis tests; they
should be treated as ***screening tests*** meant to identify potential
problem areas which can then be confirmed by collecting more data. A
legitimate hypothesis test would require that the threshold be adjusted
to reflect the number of tests conducted, or that a pattern identified
by screening in one year has to be confirmed in the following year.

### Significance vs Substance

It’s very common for people to misinterpret the p-value as a measure of
the strength of a relationship, rather than as a measure for the
*evidence* that the data provide. Even when a relationship is very
slight, as indicated by model coefficients or an R², the evidence for it
can be very strong so long as there are enough cases.

Suppose, for example, that you are studying how long patients survive
after being diagnosed with a particular disease. The typical survival
time is 10 years, with a standard deviation of 5 years. In your
research, you have identified a genetic trait that explains some of the
survival time: modeling survival by the genetics produces an R² of 0.01.
Taking this genetic trait into account makes the survival time more
predictable; it reduces the standard deviation of survival time from 5
years to 4.975 years. Big deal\! The fact is, an R² of 0.01 does not
reduce uncertainty very much; it leaves 99 percent of the variance
unaccounted for.

To see how the F statistic stems from both R² = 0.01 and the sample size
n, re-write the formula for F

\[ F = \frac{R²}{m-1} \Biggm/ \frac{1-R²}{n-m}\]
\[\ \ \ \ = \left( \frac{n-m}{m-1} \right) \ \frac{R²}{1-R²}\] The ratio
R²/(1-R²) is a reasonable way to measure the substance of the result:
how forceful the relationship is. The ratio (n-m)/(m-1) reflects the
amount of data. Any relationship, even one that lacks practical
substance, can be made to give a large F value so long as n is big
enough. For example, taking m=2 in your genetic trait model, a small
study with n=100 gives an F value of approximately 1: not significant.
But if n=1000 cases were collected, the F value would become a hugely
significant F=10. When used in a statistical sense to describe a
relationship, the word “significant” does not mean important or
substantial. It merely means that there is evidence that the
relationship did not arise purely by accident from random variation in
the sample.

### Example: The Significance of Finger Lengths

The example in Section 14.4 commented on a study that found R² = 0.044
for the relationship between finger-length ratios and aggressiveness.
The relationship was hyped in the news media as the “key to aggression.”
(BBC News, 2005/03/04) The researchers who published the study(Bailey
and Hurd 2005) didn’t characterize their results in this dramatic way.
They reported merely that they found a statistically significant result,
that is, p-value of 0.028. The small p-value stems not from a forceful
correlation but from number of cases; their study, at n=134, was large
enough to produce a value of F bigger than 4 even though the
“substance”, R²/(1−R²), is only 0.046.

The researchers were careful in presenting their results and gave a
detailed presentation of their study. They described their use of four
different ways of measuring aggression: physical, hostility, verbal, and
anger. These four scales were each used to model finger-length ratio for
men and women separately. Here are the p-values they report:

| Sex     | Scale     |    R² | p-value |
| :------ | :-------- | ----: | ------: |
| Males   | Physical  | 0.044 |   0.028 |
|         | Hostility | 0.016 |   0.198 |
|         | Verbal    | 0.008 |   0.347 |
|         | Anger     | 0.001 |   0.721 |
| Females | Physical  | 0.010 |   0.308 |
|         | Hostility | 0.001 |   0.670 |
|         | Verbal    | 0.001 |   0.778 |
|         | Anger     | 0.000 |   0.887 |

Notice that only one of the eight p-values is below the 0.05 threshold.
The others seem randomly scattered on the interval 0 to 1, as would be
expected if there were no relationship between the finger-length ratio
and the aggressiveness scales. A Bonferroni correction to account for
the eight tests gives a rejection threshold of 0.05/8 = 0.00625. None of
the tests satisfies this threshold.

1.  See Section 13.9 for another example
