2 Data: Cases, Variables, Samples
================
Boukara Ahmed El-Hachemi
07/07/2020

> The tendency of the casual mind is to pick out or stumble upon a
> sample which supports or defies its prejudices, and then to make it
> the representative of a whole class. – Walter Lippmann (1889-1974),
> journalist

Statistics is, at its heart, about variability: how things differ from
one another.

Any data set consists of **cases**: the objects in the collection. Each
case has one or more attributes or qualities, called **variables**. The
researcher measures or observes the value of each variable for each
case. The result is a **table**, also known as a **data frame**. Within
the data table, each row refers to one case, each column to one
variable.

Each case has a case number that identifies it, these case numbers are
arbitrary; the position of each case in the table – first, second,
tenth, and so on – is of no significance. The point of assigning an
identifying case number is just to make it easier to refer to individual
cases later on.

If the data table had been a collection of people, the person’s name or
another identifying label could be used to identify the case.

## 1 Kinds of Variables

The two basic types of data are:

1.  **Quantitative**: Naturally represented by a number.  
2.  **Categorical**: A description that can be put simply into words or
    categories. The value for each case is selected from a fixed set of
    possibilities. This set of possibilities are the **levels** of the
    categorical variable.

Quantitative variables are numerical but they often have units attached
to them. The information about the units is kept in a separate place
called a **code book**.

The code book contains a short description of each variable.

On the computer, a data frame is usually stored as a spreadsheet file,
while the corresponding code book can be stored separately as a text
file.

Sometimes quantitative information is represented by categories. Almost
always, the genuinely quantitative form is to be preferred. It conveys
more information even if it is not correct to the last digit.

Both quantitative and categorical variables can be described as simple
variables because each consists of one number or a short text phrase for
each case. One can also think of compound variables: an image is a set
of many pixels, a color might be represented as a red/green/blue triplet
of numbers, a location might be a latitude/longitude pair. This book
considers only simple variables.

The distinction between quantitative and categorical data is essential,
but there are other distinctions that can be helpful even if they are
less important.

Some categorical variables have levels that have a natural order.
Variables like this are called **ordinal**.

For the most part, this book will treat ordinal variables like any other
form of categorical variable. But it’s worthwhile to pay attention to
the natural ordering of an ordinal variable. Indeed, sometimes it can be
appropriate to treat an ordinal variable as if it were quantitative.

## 2 Data Frames and the Unit of Analysis

When collecting and organizing data, it’s important to be clear about
what is a case.

A key idea is the **unit of analysis**.

Once you choose the unit of analysis, you combine information from the
different data frames to carry out the data analysis, generating a
single data frame in which cases are your chosen unit of analysis. The
choice of the unit of analysis can be determined by many things, such as
the availability of data. As a general rule, it’s best to make the unit
of analysis as small as possible. But there can be obstacles to doing
this. You might find, for instance, that for privacy reasons (or less
legitimate reasons of secrecy) the school district is unwilling to
release the data at the individual student level, or even to release
data on individual classes.

In the past, limitations in data analysis techniques and computational
power provided a reason to use a coarse unit of analysis. Nowadays these
reasons are obsolete. Standard personal computers have plenty of power
to perform the required calculations.

## 3 Populations and Samples

A data frame is a collection. A ***population*** is the set of all the
possible objects or units which might have been included in the
collection.

A ***sample*** is a selection of cases from the population. The
***sample size*** is the number of cases in the sample.

A ***census*** is a sample that contains the entire population. The most
familiar sort of census is the kind to count the people living in a
country. The United States and the United Kingdom have a census every
ten years. Countries such as Canada, Australia, and New Zealand hold a
census every five years.

Almost always, the sample is just a small fraction of the population.
There are good reasons for this. It can be expensive or damaging to take
a sample: Imagine a biologist who tried to use all the laboratory rats
in the world for his or her work\! Still, when you draw a sample, it is
generally because you are interested in finding out something about the
population rather than just the sample at hand. That is, you want the
sample to be genuinely representative of the population. (In some
fields, the ability to draw conclusions from a sample that can be
generalized is referred to as external validity or transferability.)

The process by which the sample is taken is important because it
controls what sorts of conclusions can legitimately be drawn from the
sample. One of the most important ideas of statistics is that a sample
will be representative of the population if the sample is collected at
random. In a ***simple random sample***, each member of the population
is equally likely to be included in the sample.

Ironically, taking a random sample, even from a single spot on the
beach, requires organization and planning. The sea shells were collected
haphazardly, but this is not a genuinely random sample. The bigger
shells are much easier to see and pick up than the very small ones, so
there is reason to think that the small shells are under-represented:
the collection doesn’t have as big a proportion of them as in the
population. To make the sample genuinely random, you need to have access
in some way to the entire population so that you can pick any member
with equal probability. For instance, if you want a sample of students
at a particular university, you can get a list of all the students from
the university registrar and use a computer to pick randomly from the
list. Such a list of the entire set of possible cases is called a
***sampling frame***.

In a sense, the sampling frame is the definition of the population for
the purpose of drawing conclusions from the sample. For instance, a
researcher studying cancer treatments might take the sampling frame to
be the list of all the patients who visit a particular clinic in a
specified month. A random sample from that sampling frame can reasonably
be assumed to represent that particular population, but not necessarily
the population of all cancer patients.

You should always be careful to define your sampling frame precisely. If
you decide to sample university students by picking randomly from those
who enter the front door of the library, you will get a sample that
might not be typical for all university students. There’s nothing wrong
with using the library students for your sample, but you need to be
aware that your sample will be representative of just the library
students, not necessarily all students.

When sampling at random, use formal random processes. For example, if
you are sampling students who walk into the library, you can flip a coin
to decide whether to include that student in your sample. When your
sampling frame is in the form of a list, it’s wise to use a computer
random number generator to select the cases to include in the sample.

A ***convenience sample*** is one where the sampling frame is defined
mainly in a way that makes it easy for the researcher. For example,
during lectures I often sample from the set of students in my class.
These students – the ones who take statistics courses from me – are not
necessarily representative of all university students. It might be fine
to take a convenience sample in a quick, informal, preliminary study.
But don’t make the mistake of assuming that the convenience sample is
representative of the population. Even if you believe it yourself, how
will you convince the people who are skeptical about your results?

When cases are selected in an informal way, it’s possible for the
researcher to introduce a non-representativeness or ***sampling bias***.
For example, in deciding which students to interview who walk into the
library, you might consciously or subconsciously select those who seem
most approachable or who don’t seem to be in a hurry.

There are many possible sources of sampling bias. In surveys, sampling
bias can come from non-response or self-selection. Perhaps some of the
students who you selected randomly from the people entering the library
have declined to participate in your survey. This ***non-response*** can
make your sample non-representative. Or, perhaps some people who you
didn’t pick at random have walked up to you to see what you are up to
and want to be surveyed themselves. Such ***self-selected*** people are
often different from people who you would pick at random.

In an example of self-selection bias, the newspaper columnist Ann
Landers asked her readers, “If you had it to do over again, would you
have children?” Over 70% of the respondents who wrote in said “No.” This
result is utterly different from what was found in surveys on the same
question done with a random sampling methodology: more than 90% said
“Yes.” Presumably the people who bothered to write were people who had
had a particularly bad experience as parents whereas the randomly
selected parents are representative of the whole population. Or, as Ann
Landers wrote, “\[T\]he hurt, angry, and disenchanted tend to write more
readily than the contented ….”

Non-response is often a factor in political polls, where people don’t
like to express views that they think will be unpopular.

It’s hard to take a genuinely random sample. But if you don’t, you have
no guarantee that your sample is representative. Do what you can to
define your sampling frame precisely and to make your selections as
randomly as possible from that frame. By using formal selection
procedures (e.g., coin flips, computer random number generators) you
have the opportunity to convince skeptics who might otherwise wonder
what hidden biases were introduced by informal selections. If you
believe that your imperfect selection may have introduced biases be
up-front and honest about it. In surveys, you should keep track of the
non-response rate and include that in whatever report you make of your
study.

Good researchers take great effort to secure a random sample. One
evening I received a phone call at home from the state health
department. They were conducting a survey of access to health care, in
particular how often people have illnesses for which they don’t get
treatment. The person on the other end of the phone told me that they
were dialing numbers randomly, checked to make sure that I live in the
area of interest, and asked how many adults over age 18 live in the
household. “Two,” I replied, “Me and my wife.” The researcher asked me
to hold a minute while she generated a random number. Then the
researcher asked to speak to my wife. “She isn’t home right now, but
I’ll be happy to help you,” I offered. No deal.

The sampling frame was adults over age 18 who live in a particular area.
Once the researcher had made a random selection, as she did after asking
how many adults are in my household, she wasn’t going to accept any
substitutes. It took three follow-up phone calls over a few days – at
least that’s how many I answered, who knows how many I wasn’t home for –
before the researcher was able to contact my wife. The researcher
declined to interview me in order to avoid self-selection bias and
worked hard to contact my wife – the randomly selected member of our
household – in order to avoid non-response bias.

## 4 Longitudinal and Cross-Sectional Samples

Data are often collected to study the links between different traits.

For example, this data are a small part of a larger data set of the
speeds of runners in a ten-mile race held in Washington, D.C. in 2005.
The variable time gives the time from the start gun to the finish line,
in seconds.

| state | time | net  | age | sex |
| :---: | :--: | :--: | :-: | :-: |
|  VA   | 6060 | 5978 | 12  |  M  |
|  MD   | 4515 | 4457 | 13  |  M  |
|  VA   | 5026 | 4928 | 13  |  M  |

A few entries from the `TenMileRace` data table in the `MosaicData`
package

Such data might be used to study the link between age and speed, for
example to find out at what age people run the fastest and how much they
slow down as they age beyond that.

This sample is a ***cross section*** , a snapshot of the population that
includes people of different ages. Each person is included only once.

Another type of sample is ***longitudinal***, where the cases are
tracked over time, each person being included more than once in the data
frame. For example A longitudinal data set showing of runners’ times in
races over several years. The ID is a unique identifier given to each
runner. The individual runners have been tracked from year to year, so
each individual person shows up in multiple rows.

If your concern is to understand how individual change as they age, it’s
best to collect data that show such change in individuals. Using
cross-sectional data to study a longitudinal problem is risky. Suppose,
as seems likely, that younger runners who are slow tend to drop out of
racing as they age, so the older runners who do participate are those
who tend to be faster. This could bias your estimate of how running
speed changes with age.
