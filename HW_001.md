KZ\_HW\_001
================

R Markdown Exploration!!
------------------------

Hello! Welcome to my first homework assignment. In this assignment I will be exploring the **gapminder** dataset (wahoo)

Before we begin... if you have any questions about the functions you can use the help funciton. For example if we are wondering what the **install.packages** function does, we add a question mark to the front of the function and run it through the console. Here is an example:

``` r
?install.packages
```

Our first step is to install the gapminder package using the **install.packages("gapminder")** function. I will not include it below as this is a function that you only want to run in your console once, rather than multiple times in your markdown document. You may also want to run an install for the **tidyverse** package in your console. It is a set of packages that may make your life easier in the future if you decide to make your analysis more complex

The next thing we do is load the gapminder dataset. To accomplish this we use the **library** function. We will also load the **tidyverse** package that we just downloaded

``` r
library(gapminder)
library(tidyverse)
```

    ## ── Attaching packages ────────────────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 3.0.0     ✔ purrr   0.2.5
    ## ✔ tibble  1.4.2     ✔ dplyr   0.7.6
    ## ✔ tidyr   0.8.1     ✔ stringr 1.3.1
    ## ✔ readr   1.1.1     ✔ forcats 0.3.0

    ## ── Conflicts ───────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

To get a summary of the dataset we use the **summary** function

``` r
summary(gapminder)
```

    ##         country        continent        year         lifeExp     
    ##  Afghanistan:  12   Africa  :624   Min.   :1952   Min.   :23.60  
    ##  Albania    :  12   Americas:300   1st Qu.:1966   1st Qu.:48.20  
    ##  Algeria    :  12   Asia    :396   Median :1980   Median :60.71  
    ##  Angola     :  12   Europe  :360   Mean   :1980   Mean   :59.47  
    ##  Argentina  :  12   Oceania : 24   3rd Qu.:1993   3rd Qu.:70.85  
    ##  Australia  :  12                  Max.   :2007   Max.   :82.60  
    ##  (Other)    :1632                                                
    ##       pop              gdpPercap       
    ##  Min.   :6.001e+04   Min.   :   241.2  
    ##  1st Qu.:2.794e+06   1st Qu.:  1202.1  
    ##  Median :7.024e+06   Median :  3531.8  
    ##  Mean   :2.960e+07   Mean   :  7215.3  
    ##  3rd Qu.:1.959e+07   3rd Qu.:  9325.5  
    ##  Max.   :1.319e+09   Max.   :113523.1  
    ## 

If you only want a preview of the first bit of the data set you can use the **head** function

``` r
head(gapminder)
```

    ## # A tibble: 6 x 6
    ##   country     continent  year lifeExp      pop gdpPercap
    ##   <fct>       <fct>     <int>   <dbl>    <int>     <dbl>
    ## 1 Afghanistan Asia       1952    28.8  8425333      779.
    ## 2 Afghanistan Asia       1957    30.3  9240934      821.
    ## 3 Afghanistan Asia       1962    32.0 10267083      853.
    ## 4 Afghanistan Asia       1967    34.0 11537966      836.
    ## 5 Afghanistan Asia       1972    36.1 13079460      740.
    ## 6 Afghanistan Asia       1977    38.4 14880372      786.

The **ncol** function tells you how many columns are present while the **nrow** function tells you how many rows are present in your dataset

``` r
ncol(gapminder)
```

    ## [1] 6

``` r
nrow(gapminder)
```

    ## [1] 1704

Now we will dig deeper.

If you only want to see a certain part of the dataset you can use the **select** function. For example if you only want to see the life expectancy per country you will do this

``` r
select(gapminder, country, lifeExp)
```

    ## # A tibble: 1,704 x 2
    ##    country     lifeExp
    ##    <fct>         <dbl>
    ##  1 Afghanistan    28.8
    ##  2 Afghanistan    30.3
    ##  3 Afghanistan    32.0
    ##  4 Afghanistan    34.0
    ##  5 Afghanistan    36.1
    ##  6 Afghanistan    38.4
    ##  7 Afghanistan    39.9
    ##  8 Afghanistan    40.8
    ##  9 Afghanistan    41.7
    ## 10 Afghanistan    41.8
    ## # ... with 1,694 more rows

If we decide that we want to rename a variable in the dataset (say there is a mistake or a repeat) we can use the **rename** function

``` r
rename(gapminder, AgeOfDeath=lifeExp)
```

    ## # A tibble: 1,704 x 6
    ##    country     continent  year AgeOfDeath      pop gdpPercap
    ##    <fct>       <fct>     <int>      <dbl>    <int>     <dbl>
    ##  1 Afghanistan Asia       1952       28.8  8425333      779.
    ##  2 Afghanistan Asia       1957       30.3  9240934      821.
    ##  3 Afghanistan Asia       1962       32.0 10267083      853.
    ##  4 Afghanistan Asia       1967       34.0 11537966      836.
    ##  5 Afghanistan Asia       1972       36.1 13079460      740.
    ##  6 Afghanistan Asia       1977       38.4 14880372      786.
    ##  7 Afghanistan Asia       1982       39.9 12881816      978.
    ##  8 Afghanistan Asia       1987       40.8 13867957      852.
    ##  9 Afghanistan Asia       1992       41.7 16317921      649.
    ## 10 Afghanistan Asia       1997       41.8 22227415      635.
    ## # ... with 1,694 more rows

That is a little dark but we will go with it

If we want to order the dataset in a certain way we can use the **arrange** function. This will order the data by population

``` r
arrange(gapminder, pop)
```

    ## # A tibble: 1,704 x 6
    ##    country               continent  year lifeExp   pop gdpPercap
    ##    <fct>                 <fct>     <int>   <dbl> <int>     <dbl>
    ##  1 Sao Tome and Principe Africa     1952    46.5 60011      880.
    ##  2 Sao Tome and Principe Africa     1957    48.9 61325      861.
    ##  3 Djibouti              Africa     1952    34.8 63149     2670.
    ##  4 Sao Tome and Principe Africa     1962    51.9 65345     1072.
    ##  5 Sao Tome and Principe Africa     1967    54.4 70787     1385.
    ##  6 Djibouti              Africa     1957    37.3 71851     2865.
    ##  7 Sao Tome and Principe Africa     1972    56.5 76595     1533.
    ##  8 Sao Tome and Principe Africa     1977    58.6 86796     1738.
    ##  9 Djibouti              Africa     1962    39.7 89898     3021.
    ## 10 Sao Tome and Principe Africa     1982    60.4 98593     1890.
    ## # ... with 1,694 more rows

If you want this to decrease rather than increase, we use the same function but we make a small tweak

``` r
arrange(gapminder, desc(pop))
```

    ## # A tibble: 1,704 x 6
    ##    country continent  year lifeExp        pop gdpPercap
    ##    <fct>   <fct>     <int>   <dbl>      <int>     <dbl>
    ##  1 China   Asia       2007    73.0 1318683096     4959.
    ##  2 China   Asia       2002    72.0 1280400000     3119.
    ##  3 China   Asia       1997    70.4 1230075000     2289.
    ##  4 China   Asia       1992    68.7 1164970000     1656.
    ##  5 India   Asia       2007    64.7 1110396331     2452.
    ##  6 China   Asia       1987    67.3 1084035000     1379.
    ##  7 India   Asia       2002    62.9 1034172547     1747.
    ##  8 China   Asia       1982    65.5 1000281000      962.
    ##  9 India   Asia       1997    61.8  959000000     1459.
    ## 10 China   Asia       1977    64.0  943455000      741.
    ## # ... with 1,694 more rows

A big perk of R Markdown is the the ease of statistical applications, I find it quite handy for greating plots. for example I can create a **plot** with R Markdown will spit out a visualization of it instantly

``` r
plot(gapminder)
```

![](HW_001_files/figure-markdown_github/unnamed-chunk-10-1.png)

If we want to get REALLY crazy we could do something like this

``` r
plot(gapminder$lifeExp~gapminder$gdpPercap, cex=0.5, pch=16, col=rgb(0,0,0,0.25))
```

![](HW_001_files/figure-markdown_github/unnamed-chunk-11-1.png)

Thanks for checking out my data exploration. These are the basics and are essential when starting with any data set
