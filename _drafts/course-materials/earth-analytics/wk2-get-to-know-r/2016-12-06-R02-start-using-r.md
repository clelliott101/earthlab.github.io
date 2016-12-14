---
layout: single
title: "Get to Know R & RStudio"
excerpt: "This tutorial introduces the R scientific programming language. It is
designed for someone who has not used R before. We will work with precipitation and
stream discharge data for Boulder County."
authors: ['Leah Wasser', 'Data Carpentry']
category: [course-materials]
class-lesson: ['get-to-know-r']
permalink: /course-materials/earth-analytics/start-using-r
nav-title: 'Use R'
dateCreated: 2016-12-13
lastModified: 2016-12-13
sidebar:
  nav:
author_profile: false
comments: false
order: 2
---

.

<div class='notice--success' markdown="1">

# Learning Objectives
At the end of this activity, you will be able to:

* Be able to work with the 4 panes in the RStudio interface
* Understand the basic concept of a function and be able to use a function in your code.
* Know how to use key operator commands in R (<-)

## What You Need

You need R and RStudio to complete this tutorial. Also we recommend have you
have an `earth-analytics` directory setup on your computer with a `/data`
directory with it.

* [How to Setup R / R Studio](/course-materials/setup-r-rstudio)
* [Setup your working directory](/course-materials/setup-working-directory)


</div>

# Basics of R

`R` is a versatile, open source programming/scripting language that's useful both
for statistics but also data science. Inspired by the programming language S.

* Free/Libre/Open Source Software under the [GPL version 2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html).
* Superior (if not just comparable) to commercial alternatives. R has over 7,000
  user contributed packages at this time. It's widely used both in academia and
  industry.
* Available on all platforms.
* Not just for statistics, but also general purpose programming.
* For people who have experience in programmming: R is both an object-oriented
  and a so-called [functional language](http://adv-r.had.co.nz/Functional-programming.html).
* Large and growing community of peers.

## The R syntax


```r

# let's define some variables
my.variable <- (1*2) + 5
my.second.variable <- 7 * 3

# I can sum two variables together using the sum function
sum(my.variable, my.second.variable, na.rm=FALSE)
## [1] 28
```

* Point to the different parts:
  - a function
  - the assignment operator `<-`
  - the `=` for arguments
  - the comments `#` and how they are used to document function and its content
  - the `$` operator
* Point to indentation and consistency in spacing to improve clarity

![Example of a simple R script](img/r_starting_example_script.png)

### Commenting

Use `#` sign is used to add comments to your code. A comment is a way for you 
to DOCUMENT the steps of your code - both for yourself and for others who may
use your script. Anything to the right of a `#` is ignored by `R`,
meaning it won't be executed.

### Assignment operator <-

`<-` is the assignment operator. It is similar to an equalts sign. It assigns 
values on the right to objects on the left. So, after executing `x <- 3`, the 
value of `x` is `3`. The arrow can
be read as 3 **goes into** `x`.  For historical reasons, you can also use `=` for assignments,
but not in every context. Because of the [slight](http://blog.revolutionanalytics.com/2008/12/use-equals-or-arrow-for-assignment.html) [differences](https://web.archive.org/web/20130610005305/https://stat.ethz.ch/pipermail/r-help/2009-March/191462.html) in syntax,
it is good practice to use always `<-` for assignments, except when specifying the values of
arguments in functions, when only `=` should be used, see below.

<i class="fa fa-star"></i> **Data Tip:**  In RStudio, typing <kbd>Alt</kbd> + <kbd>-</kbd> (push <kbd>Alt</kbd> at the
same time as the <kbd>-</kbd> key) will write ` <- ` in a single keystroke.
{: .notice }

### Functions and their arguments

Functions are "canned scripts" that automate something complicated or convenient
or both. Many functions are predefined, or can be made available by importing R
*packages* (more on that later). A function usually gets one or more inputs
called *arguments*. Functions often (but not always) return a *value*. A typical
example would be the function `sqrt()`. The input (the argument) must be a
number, and the return value (in fact, the output) is the square root of that
number. Executing a function ('running it') is called *calling* the function. An
example of a function call is:

`b <- sqrt(a)`

Here, the value of `a` is given to the `sqrt()` function, the `sqrt()` function
calculates the square root, and returns the value which is then assigned to
variable `b`. This function is very simple, because it takes just one argument.

The return 'value' of a function need not be numerical (like that of `sqrt()`),
and it also does not need to be a single item: it can be a set of things, or
even a data set. We'll see that when we read data files in to R.

Arguments can be anything, not only numbers or filenames, but also other
objects. Exactly what each argument means differs per function, and must be
looked up in the documentation (see below). Some functions take arguments which
may either be specified by the user, or if left out, take on a *default* value:
these are called *options*. Options are typically used to alter the way the
function operates, such as whether it ignores 'bad values', or what symbol to
use in a plot.  However, if you want something specific, you can specify a value
of your choice which will be used instead of the default.

Let's run a function that can take multiple arguments: `round()`.


```r

round(3.14159)
## [1] 3
```

Here, we've called `round()` with just one argument, `3.14159`, and it has
returned the value `3`.  That's because the default is to round to the nearest
whole number. If we want more digits we can see how to do that by getting
information about the `round` function.  We can use `args(round)` or look at the
help for this function using `?round`.


```r
args(round)
## function (x, digits = 0) 
## NULL
```


```r
?round
```

We see that if we want a different number of digits, we can
type `digits=2` or however many we want.


```r
round(3.14159, digits=2)
## [1] 3.14
```

If you provide the arguments in the exact same order as they are defined you
don't have to name them:


```r
round(3.14159, 2)
## [1] 3.14
```

And if you do name the arguments, you can switch their order:


```r
round(digits=2, x=3.14159)
## [1] 3.14
```

It's good practice to put the non-optional arguments (like the number you're
rounding) first in your function call, and to specify the names of all optional
arguments.  If you don't, someone reading your code might have to look up
definition of a function with unfamiliar arguments to understand what you're
doing.


## Get Information About A Function 

If you need help with a specific function, let's say `barplot()`, you can type:


```r
?barplot
```

If you just need to remind yourself of the names of the arguments, you can use:


```r
args(lm)
```

## I want to use a function that does X, there must be a function for it but I don't know which one...

If you are looking for a function to do a particular task, you can use
`help.search()` function, which is called by the double question mark `??`.
However, this only looks through the installed packages for help pages with a
match to your search request


```r
??kruskal
```

If you can't find what you are looking for, you can use the
[rdocumention.org](http://www.rdocumentation.org) website that searches through
the help files across all packages available.

## I am stuck... I get an error message that I don't understand

Start by googling the error message. However, this doesn't always work very well
because often, package developers rely on the error catching provided by R. You
end up with general error messages that might not be very helpful to diagnose a
problem (e.g. "subscript out of bounds"). If the message is very generic, you might
also include the name of the function or package you're using in your query.

However, you should check StackOverflow. Search using the `[r]` tag. Most
questions have already been answered, but the challenge is to use the right
words in the search to find the answers:
[http://stackoverflow.com/questions/tagged/r](http://stackoverflow.com/questions/tagged/r)

The [Introduction to R](http://cran.r-project.org/doc/manuals/R-intro.pdf) can
also be dense for people with little programming experience but it is a good
place to understand the underpinnings of the R language.

The [R FAQ](http://cran.r-project.org/doc/FAQ/R-FAQ.html) is dense and technical
but it is full of useful information.


<div class='notice--info' markdown="1">

# Where to Get Help

* Ask your colleagues: if you know someone with more experience than you,
  they might be able to help you.
* [StackOverflow](http://stackoverflow.com/questions/tagged/r): if your question
  hasn't been answered before and is well crafted, chances are you will get an
  answer in less than 5 min. Remember to follow their guidelines on [how to ask
  a good question](http://stackoverflow.com/help/how-to-ask).
* There are also some topic-specific mailing lists (GIS, phylogenetics, etc...),
  the complete list is [here](http://www.r-project.org/mail.html).

## More resources

* The [Posting Guide](http://www.r-project.org/posting-guide.html) for the R
  mailing lists.
* [How to ask for R help](http://blog.revolutionanalytics.com/2014/01/how-to-ask-for-r-help.html)
  useful guidelines
* [This blog post by Jon Skeet](http://codeblog.jonskeet.uk/2010/08/29/writing-the-perfect-question/)
  has quite comprehensive advice on how to ask programming questions.
</div>