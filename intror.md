# Data wrangling

<p>

In this chapter, you'll learn to do three things with a table: filter for particular observations, arrange the observations in a desired order, and mutate to add or change a column.
You'll see how each of these steps allows you to answer questions about your data.

</p>

## The gapminder dataset

### Loading the gapminder and dplyr packages

<div>

<p>

Before you can work with the <code>gapminder</code> dataset, you'll need to load two R packages that contain the tools for working with it, then display the <code>gapminder</code> dataset so that you can see what it contains.

</p>

<p>

To your right, you'll see two windows inside which you can enter code: The <code>script.R</code> window, and the R Console.
All of your code to solve each exercise must go inside <code>script.R</code>.

</p>

<p>

If you hit <em>Submit Answer</em>, your R script is executed and the output is shown in the R Console.
DataCamp checks whether your submission is correct and gives you feedback.
You can hit <em>Submit Answer</em> as often as you want.
If you're stuck, you can ask for a hint or a solution.

</p>

<p>

You can use the R Console interactively by simply typing R code and hitting Enter.
When you work in the console directly, your code will not be checked for correctness so it is a great way to experiment and explore.

</p>

<p>

<em>This course introduces a lot of new concepts, so if you ever need a quick refresher, download the <a href="https://datacamp-community-prod.s3.amazonaws.com/e63a8f6b-2aa3-4006-89e0-badc294b179c">tidyverse for beginners Cheat Sheet</a> and keep it handy!<
/em>

</p>

</div>

::: exercise--instructions__content
<li>

Use the <code>library()</code> function to load the <code>dplyr</code> package, just like we've loaded the <code>gapminder</code> package for you.

</li>


```r
# Load the gapminder package
library(gapminder)

# Load the dplyr package
library(dplyr)
#> 
#> Attaching package: 'dplyr'
#> The following objects are masked from 'package:stats':
#> 
#>     filter, lag
#> The following objects are masked from 'package:base':
#> 
#>     intersect, setdiff, setequal, union
```

<li>

Type <code>gapminder</code>, on its own line, to look at the gapminder dataset.

</li>


```r
# Look at the gapminder dataset
gapminder
#> [90m# A tibble: 1,704 × 6[39m
#>   [1mcountry[22m     [1mcontinent[22m  [1myear[22m [1mlifeExp[22m      [1mpop[22m [1mgdpPercap[22m
#>   [3m[90m<fct>[39m[23m       [3m[90m<fct>[39m[23m     [3m[90m<int>[39m[23m   [3m[90m<dbl>[39m[23m    [3m[90m<int>[39m[23m     [3m[90m<dbl>[39m[23m
#> [90m1[39m Afghanistan Asia       [4m1[24m952    28.8  8[4m4[24m[4m2[24m[4m5[24m333      779.
#> [90m2[39m Afghanistan Asia       [4m1[24m957    30.3  9[4m2[24m[4m4[24m[4m0[24m934      821.
#> [90m3[39m Afghanistan Asia       [4m1[24m962    32.0 10[4m2[24m[4m6[24m[4m7[24m083      853.
#> [90m4[39m Afghanistan Asia       [4m1[24m967    34.0 11[4m5[24m[4m3[24m[4m7[24m966      836.
#> [90m5[39m Afghanistan Asia       [4m1[24m972    36.1 13[4m0[24m[4m7[24m[4m9[24m460      740.
#> [90m6[39m Afghanistan Asia       [4m1[24m977    38.4 14[4m8[24m[4m8[24m[4m0[24m372      786.
#> [90m# … with 1,698 more rows[39m
```
:::

<p class>

Great job!
Notice that you can see the gapminder dataset in the output.
This is called 'printing' a dataset.

</p>

### Understanding a data frame

<div>

<p>

Now that you've loaded the <code>gapminder</code> dataset, you can start examining and understanding it.

</p>

<p>

We've already loaded the <code>gapminder</code> and <code>dplyr</code> packages.
Type <code>gapminder</code> in the console, to display the object.

</p>

<p>

How many observations (rows) are in the dataset?

</p>

</div>

<ul>

<string>

<li>

::: dc-input-radio__text
1704
:::

</li>

</string>

<li>

::: dc-input-radio__text
6
:::

</li>

<li>

::: dc-input-radio__text
1694
:::

</li>

<li>

::: dc-input-radio__text
1952
:::

</li>

</ul>

<p class>

Correct!

</p>

## The filter verb

### Filtering for one year

<div>

<p>

The <code>filter</code> verb extracts particular observations based on a condition.
In this exercise you'll filter for observations from a particular year.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Add a <code>filter()</code> line after the pipe (<code>%\>%</code>) to extract only the observations from the year 1957.
Remember that you use <code>==</code> to compare two values.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)

# Filter the gapminder dataset for the year 1957
gapminder %>%
  filter(year == 1957)
#> [90m# A tibble: 142 × 6[39m
#>   [1mcountry[22m     [1mcontinent[22m  [1myear[22m [1mlifeExp[22m      [1mpop[22m [1mgdpPercap[22m
#>   [3m[90m<fct>[39m[23m       [3m[90m<fct>[39m[23m     [3m[90m<int>[39m[23m   [3m[90m<dbl>[39m[23m    [3m[90m<int>[39m[23m     [3m[90m<dbl>[39m[23m
#> [90m1[39m Afghanistan Asia       [4m1[24m957    30.3  9[4m2[24m[4m4[24m[4m0[24m934      821.
#> [90m2[39m Albania     Europe     [4m1[24m957    59.3  1[4m4[24m[4m7[24m[4m6[24m505     [4m1[24m942.
#> [90m3[39m Algeria     Africa     [4m1[24m957    45.7 10[4m2[24m[4m7[24m[4m0[24m856     [4m3[24m014.
#> [90m4[39m Angola      Africa     [4m1[24m957    32.0  4[4m5[24m[4m6[24m[4m1[24m361     [4m3[24m828.
#> [90m5[39m Argentina   Americas   [4m1[24m957    64.4 19[4m6[24m[4m1[24m[4m0[24m538     [4m6[24m857.
#> [90m6[39m Australia   Oceania    [4m1[24m957    70.3  9[4m7[24m[4m1[24m[4m2[24m569    [4m1[24m[4m0[24m950.
#> [90m# … with 136 more rows[39m
```

<p class>

That's right!
Notice that all the observations in the output have the year 1957.

</p>

### Filtering for one country and one year

<div>

<p>

You can also use the <code>filter()</code> verb to set two conditions, which could retrieve a single observation.

</p>

<p>

Just like in the last exercise, you can do this in two lines of code, starting with <code>gapminder %\>%</code> and having the <code>filter()</code> on the second line.
Keeping one verb on each line helps keep the code readable.
Note that each time, you'll put the pipe <code>%\>%</code> at the end of the first line (like <code>gapminder %\>%</code>); putting the pipe at the beginning of the second line will throw an error.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Filter the <code>gapminder</code> data to retrieve only the observation from China in the year 2002.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)

# Filter for China in 2002
gapminder %>%
  filter(country == "China", year == 2002)
#> [90m# A tibble: 1 × 6[39m
#>   [1mcountry[22m [1mcontinent[22m  [1myear[22m [1mlifeExp[22m        [1mpop[22m [1mgdpPercap[22m
#>   [3m[90m<fct>[39m[23m   [3m[90m<fct>[39m[23m     [3m[90m<int>[39m[23m   [3m[90m<dbl>[39m[23m      [3m[90m<int>[39m[23m     [3m[90m<dbl>[39m[23m
#> [90m1[39m China   Asia       [4m2[24m002    72.0 [4m1[24m280[4m4[24m[4m0[24m[4m0[24m000     [4m3[24m119.
```

<p class>

Good work!
This is a useful way to grab a single observation you're interested in.

</p>

## The arrange verb

### Arranging observations by life expectancy

<div>

<p>

You use <code>arrange()</code> to sort observations in ascending or descending order of a particular variable.
In this case, you'll sort the dataset based on the <code>lifeExp</code> variable.

</p>

</div>

::: exercise--instructions__content
<li>

Sort the <code>gapminder</code> dataset in ascending order of life expectancy (<code>lifeExp</code>).

</li>


```r
library(gapminder)
library(dplyr)

# Sort in ascending order of lifeExp
gapminder %>%
  arrange(lifeExp)
#> [90m# A tibble: 1,704 × 6[39m
#>   [1mcountry[22m      [1mcontinent[22m  [1myear[22m [1mlifeExp[22m     [1mpop[22m [1mgdpPercap[22m
#>   [3m[90m<fct>[39m[23m        [3m[90m<fct>[39m[23m     [3m[90m<int>[39m[23m   [3m[90m<dbl>[39m[23m   [3m[90m<int>[39m[23m     [3m[90m<dbl>[39m[23m
#> [90m1[39m Rwanda       Africa     [4m1[24m992    23.6 7[4m2[24m[4m9[24m[4m0[24m203      737.
#> [90m2[39m Afghanistan  Asia       [4m1[24m952    28.8 8[4m4[24m[4m2[24m[4m5[24m333      779.
#> [90m3[39m Gambia       Africa     [4m1[24m952    30    [4m2[24m[4m8[24m[4m4[24m320      485.
#> [90m4[39m Angola       Africa     [4m1[24m952    30.0 4[4m2[24m[4m3[24m[4m2[24m095     [4m3[24m521.
#> [90m5[39m Sierra Leone Africa     [4m1[24m952    30.3 2[4m1[24m[4m4[24m[4m3[24m249      880.
#> [90m6[39m Afghanistan  Asia       [4m1[24m957    30.3 9[4m2[24m[4m4[24m[4m0[24m934      821.
#> [90m# … with 1,698 more rows[39m
```

<li>

Sort the <code>gapminder</code> dataset in descending order of life expectancy.

</li>


```r
# Sort in descending order of lifeExp
gapminder %>%
  arrange(desc(lifeExp))
#> [90m# A tibble: 1,704 × 6[39m
#>   [1mcountry[22m          [1mcontinent[22m  [1myear[22m [1mlifeExp[22m       [1mpop[22m [1mgdpPercap[22m
#>   [3m[90m<fct>[39m[23m            [3m[90m<fct>[39m[23m     [3m[90m<int>[39m[23m   [3m[90m<dbl>[39m[23m     [3m[90m<int>[39m[23m     [3m[90m<dbl>[39m[23m
#> [90m1[39m Japan            Asia       [4m2[24m007    82.6 127[4m4[24m[4m6[24m[4m7[24m972    [4m3[24m[4m1[24m656.
#> [90m2[39m Hong Kong, China Asia       [4m2[24m007    82.2   6[4m9[24m[4m8[24m[4m0[24m412    [4m3[24m[4m9[24m725.
#> [90m3[39m Japan            Asia       [4m2[24m002    82   127[4m0[24m[4m6[24m[4m5[24m841    [4m2[24m[4m8[24m605.
#> [90m4[39m Iceland          Europe     [4m2[24m007    81.8    [4m3[24m[4m0[24m[4m1[24m931    [4m3[24m[4m6[24m181.
#> [90m5[39m Switzerland      Europe     [4m2[24m007    81.7   7[4m5[24m[4m5[24m[4m4[24m661    [4m3[24m[4m7[24m506.
#> [90m6[39m Hong Kong, China Asia       [4m2[24m002    81.5   6[4m7[24m[4m6[24m[4m2[24m476    [4m3[24m[4m0[24m209.
#> [90m# … with 1,698 more rows[39m
```
:::

<p class>

That's right!
Take a look at the countries with the highest and lowest life expectancy- is it similar to what you expected?

</p>

### Filtering and arranging

<div>

<p>

You'll often need to use the pipe operator (<code>%\>%</code>) to combine multiple dplyr verbs in a row.
In this case, you'll combine a <code>filter()</code> with an <code>arrange()</code> to find the highest population countries in a particular year.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Use <code>filter()</code> to extract observations from just the year 1957, then use <code>arrange()</code> to sort in descending order of population (<code>pop</code>).

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)

# Filter for the year 1957, then arrange in descending order of population
gapminder %>%
  filter(year == 1957) %>%
  arrange(desc(pop))
#> [90m# A tibble: 142 × 6[39m
#>   [1mcountry[22m       [1mcontinent[22m  [1myear[22m [1mlifeExp[22m       [1mpop[22m [1mgdpPercap[22m
#>   [3m[90m<fct>[39m[23m         [3m[90m<fct>[39m[23m     [3m[90m<int>[39m[23m   [3m[90m<dbl>[39m[23m     [3m[90m<int>[39m[23m     [3m[90m<dbl>[39m[23m
#> [90m1[39m China         Asia       [4m1[24m957    50.5 637[4m4[24m[4m0[24m[4m8[24m000      576.
#> [90m2[39m India         Asia       [4m1[24m957    40.2 409[4m0[24m[4m0[24m[4m0[24m000      590.
#> [90m3[39m United States Americas   [4m1[24m957    69.5 171[4m9[24m[4m8[24m[4m4[24m000    [4m1[24m[4m4[24m847.
#> [90m4[39m Japan         Asia       [4m1[24m957    65.5  91[4m5[24m[4m6[24m[4m3[24m009     [4m4[24m318.
#> [90m5[39m Indonesia     Asia       [4m1[24m957    39.9  90[4m1[24m[4m2[24m[4m4[24m000      859.
#> [90m6[39m Germany       Europe     [4m1[24m957    69.1  71[4m0[24m[4m1[24m[4m9[24m069    [4m1[24m[4m0[24m188.
#> [90m# … with 136 more rows[39m
```

<p class>

Great work!
A lot of the exercises in this course will involve combining multiple steps with the %\>% operator.

</p>

## The mutate verb

### Using mutate to change or create a column

<div>

<p>

Suppose we want life expectancy to be measured in months instead of years: you'd have to multiply the existing value by 12.
You can use the <code>mutate()</code> verb to change this column, or to create a new column that's calculated this way.

</p>

</div>

::: exercise--instructions__content
<li>

Use <code>mutate()</code> to change the existing <code>lifeExp</code> column, by multiplying it by 12: <code>12 \* lifeExp</code>.

</li>


```r
library(gapminder)
library(dplyr)

# Use mutate to change lifeExp to be in months
gapminder %>%
  mutate(lifeExp = lifeExp * 12)
#> [90m# A tibble: 1,704 × 6[39m
#>   [1mcountry[22m     [1mcontinent[22m  [1myear[22m [1mlifeExp[22m      [1mpop[22m [1mgdpPercap[22m
#>   [3m[90m<fct>[39m[23m       [3m[90m<fct>[39m[23m     [3m[90m<int>[39m[23m   [3m[90m<dbl>[39m[23m    [3m[90m<int>[39m[23m     [3m[90m<dbl>[39m[23m
#> [90m1[39m Afghanistan Asia       [4m1[24m952    346.  8[4m4[24m[4m2[24m[4m5[24m333      779.
#> [90m2[39m Afghanistan Asia       [4m1[24m957    364.  9[4m2[24m[4m4[24m[4m0[24m934      821.
#> [90m3[39m Afghanistan Asia       [4m1[24m962    384. 10[4m2[24m[4m6[24m[4m7[24m083      853.
#> [90m4[39m Afghanistan Asia       [4m1[24m967    408. 11[4m5[24m[4m3[24m[4m7[24m966      836.
#> [90m5[39m Afghanistan Asia       [4m1[24m972    433. 13[4m0[24m[4m7[24m[4m9[24m460      740.
#> [90m6[39m Afghanistan Asia       [4m1[24m977    461. 14[4m8[24m[4m8[24m[4m0[24m372      786.
#> [90m# … with 1,698 more rows[39m
```

<li>

Use <code>mutate()</code> to add a new column, called <code>lifeExpMonths</code>, calculated as <code>12 \* lifeExp</code>.

</li>


```r
# Use mutate to create a new column called lifeExpMonths
gapminder %>%
  mutate(lifeExpMonths = lifeExp * 12)
#> [90m# A tibble: 1,704 × 7[39m
#>   [1mcountry[22m     [1mcontinent[22m  [1myear[22m [1mlifeExp[22m      [1mpop[22m [1mgdpPercap[22m [1mlifeExpMonths[22m
#>   [3m[90m<fct>[39m[23m       [3m[90m<fct>[39m[23m     [3m[90m<int>[39m[23m   [3m[90m<dbl>[39m[23m    [3m[90m<int>[39m[23m     [3m[90m<dbl>[39m[23m         [3m[90m<dbl>[39m[23m
#> [90m1[39m Afghanistan Asia       [4m1[24m952    28.8  8[4m4[24m[4m2[24m[4m5[24m333      779.          346.
#> [90m2[39m Afghanistan Asia       [4m1[24m957    30.3  9[4m2[24m[4m4[24m[4m0[24m934      821.          364.
#> [90m3[39m Afghanistan Asia       [4m1[24m962    32.0 10[4m2[24m[4m6[24m[4m7[24m083      853.          384.
#> [90m4[39m Afghanistan Asia       [4m1[24m967    34.0 11[4m5[24m[4m3[24m[4m7[24m966      836.          408.
#> [90m5[39m Afghanistan Asia       [4m1[24m972    36.1 13[4m0[24m[4m7[24m[4m9[24m460      740.          433.
#> [90m6[39m Afghanistan Asia       [4m1[24m977    38.4 14[4m8[24m[4m8[24m[4m0[24m372      786.          461.
#> [90m# … with 1,698 more rows[39m
```
:::

<p class>

That's right!

</p>

### Combining filter, mutate, and arrange

<div>

<p>

In this exercise, you'll combine all three of the verbs you've learned in this chapter, to find the countries with the highest life expectancy, in months, in the year 2007.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

In one sequence of pipes on the <code>gapminder</code> dataset:

</li>

<li>

<code>filter()</code> for observations from the year 2007,

</li>

<li>

<code>mutate()</code> to create a column <code>lifeExpMonths</code>, calculated as <code>12 \* lifeExp</code>, and

</li>

<li>

<code>arrange()</code> in descending order of that new column

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)

# Filter, mutate, and arrange the gapminder dataset
gapminder %>%
  filter(year == 2007) %>%
  mutate(lifeExpMonths = 12 * lifeExp) %>%
  arrange(desc(lifeExpMonths))
#> [90m# A tibble: 142 × 7[39m
#>   [1mcountry[22m          [1mcontinent[22m  [1myear[22m [1mlifeExp[22m       [1mpop[22m [1mgdpPercap[22m [1mlifeExpMonths[22m
#>   [3m[90m<fct>[39m[23m            [3m[90m<fct>[39m[23m     [3m[90m<int>[39m[23m   [3m[90m<dbl>[39m[23m     [3m[90m<int>[39m[23m     [3m[90m<dbl>[39m[23m         [3m[90m<dbl>[39m[23m
#> [90m1[39m Japan            Asia       [4m2[24m007    82.6 127[4m4[24m[4m6[24m[4m7[24m972    [4m3[24m[4m1[24m656.          991.
#> [90m2[39m Hong Kong, China Asia       [4m2[24m007    82.2   6[4m9[24m[4m8[24m[4m0[24m412    [4m3[24m[4m9[24m725.          986.
#> [90m3[39m Iceland          Europe     [4m2[24m007    81.8    [4m3[24m[4m0[24m[4m1[24m931    [4m3[24m[4m6[24m181.          981.
#> [90m4[39m Switzerland      Europe     [4m2[24m007    81.7   7[4m5[24m[4m5[24m[4m4[24m661    [4m3[24m[4m7[24m506.          980.
#> [90m5[39m Australia        Oceania    [4m2[24m007    81.2  20[4m4[24m[4m3[24m[4m4[24m176    [4m3[24m[4m4[24m435.          975.
#> [90m6[39m Spain            Europe     [4m2[24m007    80.9  40[4m4[24m[4m4[24m[4m8[24m191    [4m2[24m[4m8[24m821.          971.
#> [90m# … with 136 more rows[39m
```

<p class>

Great work!
Notice how you can combine several <code>dplyr</code> operations to answer a more complicated question like this.

</p>

# Data visualization

<p>

Often a better way to understand and present data as a graph.
In this chapter, you'll learn the essential skills of data visualization using the ggplot2 package, and you'll see how the dplyr and ggplot2 packages work closely together to create informative graphs.

</p>

## Visualizing with ggplot2

### Variable assignment

<div>

<p>

Throughout the exercises in this chapter, you'll be visualizing a subset of the gapminder data from the year 1952.
First, you'll have to load the ggplot2 package, and create a <code>gapminder_1952</code> dataset to visualize.

</p>

<p>

<em>By the way, if you haven't downloaded it already, check out the <a href="https://datacamp-community-prod.s3.amazonaws.com/c1fae72f-d2d7-4646-9dce-dd0f8fb5c5e8">tidyverse for beginners Cheat Sheet</a>.
It includes an overview of the most important concepts, functions and methods and might come in handy if you ever need a quick refresher!<
/em>

</p>

</div>

::: exercise--instructions__content
<li>

Load the <code>ggplot2</code> package after the gapminder and dplyr packages.

</li>


```r
# Load the ggplot2 package as well
library(gapminder)
library(dplyr)
library(ggplot2)
```

<li>

Filter <code>gapminder</code> for observations from the year 1952, and assign it to a new dataset <code>gapminder_1952</code> using the assignment operator (<code>\<-</code>).

</li>


```r
# Create gapminder_1952
gapminder_1952 <- gapminder %>%
  filter(year == 1952)
```
:::

<p class>

Great!
If you typed 'gapminder_1952' now, you'd see the filtered dataset.

</p>

### Comparing population and GDP per capita

<div>

<p>

In the video you learned to create a scatter plot with GDP per capita on the x-axis and life expectancy on the y-axis (the code for that graph has been provided in the exercise code).
When you're exploring data visually, you'll often need to try different combinations of variables and aesthetics.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Change the scatter plot of <code>gapminder_1952</code> so that (<code>pop</code>) is on the x-axis and GDP per capita (<code>gdpPercap</code>) is on the y-axis.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

gapminder_1952 <- gapminder %>%
  filter(year == 1952)

# Change to put pop on the x-axis and gdpPercap on the y-axis
ggplot(gapminder_1952, aes(x = pop, y = gdpPercap)) +
  geom_point()
```

<img src="intror_files/figure-html/unnamed-chunk-13-1.png" width="672" />

<p class>

Great work on your first graph!
Each point represents a country: can you guess which country any of the points are?

</p>

### Comparing population and life expectancy

<div>

<p>

In this exercise, you'll use <code>ggplot2</code> to create a scatter plot from scratch, to compare each country's population with its life expectancy in the year 1952.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Create a scatter plot of <code>gapminder_1952</code> with population (<code>pop</code>) is on the x-axis and life expectancy (<code>lifeExp</code>) on the y-axis.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

gapminder_1952 <- gapminder %>%
  filter(year == 1952)

# Create a scatter plot with pop on the x-axis and lifeExp on the y-axis
ggplot(gapminder_1952, aes(x = pop, y = lifeExp)) +
  geom_point()
```

<img src="intror_files/figure-html/unnamed-chunk-14-1.png" width="672" />

<p class>

Great!
You might notice the points are crowded towards the left side of the plot, making them hard to distinguish.
This next video will help solve that problem.

</p>

## Log scales

### Putting the x-axis on a log scale

<div>

<p>

You previously created a scatter plot with population on the x-axis and life expectancy on the y-axis.
Since population is spread over several orders of magnitude, with some countries having a much higher population than others, it's a good idea to put the x-axis on a log scale.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Change the existing scatter plot (code provided) to put the x-axis (representing population) on a log scale.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

gapminder_1952 <- gapminder %>%
  filter(year == 1952)

# Change this plot to put the x-axis on a log scale
ggplot(gapminder_1952, aes(x = pop, y = lifeExp)) +
  geom_point() +
  scale_x_log10()
```

<img src="intror_files/figure-html/unnamed-chunk-15-1.png" width="672" />

<p class>

Great!
Notice the points are more spread out on the x-axis.
This makes it easy to see that there isn't a correlation between population and life expectancy.

</p>

### Putting the x- and y- axes on a log scale

<div>

<p>

Suppose you want to create a scatter plot with population on the x-axis and GDP per capita on the y-axis.
Both population and GDP per-capita are better represented with log scales, since they vary over many orders of magnitude.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Create a scatter plot with population (<code>pop</code>) on the x-axis and GDP per capita (<code>gdpPercap</code>) on the y-axis.
Put <strong>both</strong> the x- and y- axes on a log scale.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

gapminder_1952 <- gapminder %>%
  filter(year == 1952)

# Scatter plot comparing pop and gdpPercap, with both axes on a log scale
ggplot(gapminder_1952, aes(x = pop, y = gdpPercap)) +
  geom_point() +
  scale_x_log10() +
  scale_y_log10()
```

<img src="intror_files/figure-html/unnamed-chunk-16-1.png" width="672" />

<p class>

Great!
Notice that the y-axis goes from 1e3 (1000) to 1e4 (10,000) to 1e5 (100,000) in equal increments.

</p>

## Additional aesthetics

### Adding color to a scatter plot

<div>

<p>

In this lesson you learned how to use the color aesthetic, which can be used to show which continent each point in a scatter plot represents.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Create a scatter plot with population (<code>pop</code>) on the x-axis, life expectancy (<code>lifeExp</code>) on the y-axis, and with continent (<code>continent</code>) represented by the color of the points.
Put the x-axis on a log scale.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

gapminder_1952 <- gapminder %>%
  filter(year == 1952)

# Scatter plot comparing pop and lifeExp, with color representing continent
ggplot(gapminder_1952, aes(x = pop, y = lifeExp, color = continent)) +
  geom_point() +
  scale_x_log10()
```

<img src="intror_files/figure-html/unnamed-chunk-17-1.png" width="672" />

<p class>

Good work!
What differences can you see between continents, in terms of their population and life expectancy?

</p>

### Adding size and color to a plot

<div>

<p>

In the last exercise, you created a scatter plot communicating information about each country's population, life expectancy, and continent.
Now you'll use the size of the points to communicate even more.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Modify the scatter plot so that the size of the points represents each country's GDP per capita (<code>gdpPercap</code>).

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

gapminder_1952 <- gapminder %>%
  filter(year == 1952)

# Add the size aesthetic to represent a country's gdpPercap
ggplot(gapminder_1952, aes(x = pop, y = lifeExp, color = continent, size = gdpPercap)) +
  geom_point() +
  scale_x_log10()
```

<img src="intror_files/figure-html/unnamed-chunk-18-1.png" width="672" />

<p class>

Good work!
Are you able to guess which point represents your own country?

</p>

## Faceting

### Creating a subgraph for each continent

<div>

<p>

You've learned to use faceting to divide a graph into subplots based on one of its variables, such as the continent.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Create a scatter plot of <code>gapminder_1952</code> with the x-axis representing population (<code>pop</code>), the y-axis representing life expectancy (<code>lifeExp</code>), and faceted to have one subplot per continent (<code>continent</code>).
Put the x-axis on a log scale.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

gapminder_1952 <- gapminder %>%
  filter(year == 1952)

# Scatter plot comparing pop and lifeExp, faceted by continent
ggplot(gapminder_1952, aes(x = pop, y = lifeExp)) +
  geom_point() +
  scale_x_log10() +
  facet_wrap(~ continent)
```

<img src="intror_files/figure-html/unnamed-chunk-19-1.png" width="672" />

<p class>

Great work!
Faceting is a powerful way to understand subsets of your data separately.

</p>

### Faceting by year

<div>

<p>

All of the graphs in this chapter have been visualizing statistics within one year.
Now that you're able to use faceting, however, you can create a graph showing <strong>all</strong> the country-level data from 1952 to 2007, to understand how global statistics have changed over time.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Create a scatter plot of the <code>gapminder</code> data:

</li>

<li>

Put GDP per capita (<code>gdpPercap</code>) on the x-axis and life expectancy (<code>lifeExp</code>) on the y-axis, with continent (<code>continent</code>) represented by color and population (<code>pop</code>) represented by size.

</li>

<li>

Put the x-axis on a log scale

</li>

<li>

Facet by the <code>year</code> variable

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

# Scatter plot comparing gdpPercap and lifeExp, with color representing continent
# and size representing population, faceted by year
ggplot(gapminder, aes(x = gdpPercap, y = lifeExp, color = continent, size = pop)) +
  geom_point() +
  scale_x_log10() +
  facet_wrap(~ year)
```

<img src="intror_files/figure-html/unnamed-chunk-20-1.png" width="672" />

<p class>

Awesome!
That's a lot of information you're now able to share in one graph.

</p>

# Grouping and summarizing

<p>

So far you've been answering questions about individual country-year pairs, but you may be interested in aggregations of the data, such as the average life expectancy of all countries within each year.
Here you'll learn to use the group by and summarize verbs, which collapse large datasets into manageable summaries.

</p>

## The summarize verb

### Summarizing the median life expectancy

<div>

<p>

You've seen how to find the mean life expectancy and the total population across a set of observations, but <code>mean()</code> and <code>sum()</code> are only two of the functions R provides for summarizing a collection of numbers.
Here, you'll learn to use the <code>median()</code> function in combination with <code>summarize()</code>.

</p>

<p>

By the way, <code>dplyr</code> displays some messages when it's loaded that we've been hiding so far.
They'll show up in red and start with:

</p>

```{=html}
<pre><code>Attaching package: 'dplyr'

The following objects are masked from 'package:stats':
</code></pre>
```
<p>

This will occur in future exercises each time you load <code>dplyr</code>: it's mentioning some built-in functions that are overwritten by <code>dplyr</code>.
You won't need to worry about this message within this course.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Use the <code>median()</code> function within a <code>summarize()</code> to find the median life expectancy.
Save it into a column called <code>medianLifeExp</code>.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)

# Summarize to find the median life expectancy
gapminder %>%
  summarize(medianLifeExp = median(lifeExp))
#> [90m# A tibble: 1 × 1[39m
#>   [1mmedianLifeExp[22m
#>           [3m[90m<dbl>[39m[23m
#> [90m1[39m          60.7
```

<p class>

That's right!
Note that this is the median across all countries and all years in the dataset.

</p>

### Summarizing the median life expectancy in 1957

<div>

<p>

Rather than summarizing the entire dataset, you may want to find the median life expectancy for only one particular year.
In this case, you'll find the median in the year 1957.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Filter for the year 1957, then use the <code>median()</code> function within a <code>summarize()</code> to calculate the median life expectancy into a column called <code>medianLifeExp</code>.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)

# Filter for 1957 then summarize the median life expectancy
gapminder %>%
  filter(year == 1957) %>%
  summarize(medianLifeExp = median(lifeExp))
#> [90m# A tibble: 1 × 1[39m
#>   [1mmedianLifeExp[22m
#>           [3m[90m<dbl>[39m[23m
#> [90m1[39m          48.4
```

<p class>

Great!
Just like in Chapter 1, this chapter will often involve performing multiple <code>dplyr</code> steps in a row.

</p>

### Summarizing multiple variables in 1957

<div>

<p>

The <code>summarize()</code> verb allows you to summarize multiple variables at once.
In this case, you'll use the <code>median()</code> function to find the median life expectancy and the <code>max()</code> function to find the maximum GDP per capita.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Find both the median life expectancy (<code>lifeExp</code>) and the maximum GDP per capita (<code>gdpPercap</code>) in the year 1957, calling them <code>medianLifeExp</code> and <code>maxGdpPercap</code> respectively.
You can use the <code>max()</code> function to find the maximum.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)

# Filter for 1957 then summarize the median life expectancy and the maximum GDP per capita
gapminder %>%
  filter(year == 1957) %>%
  summarize(medianLifeExp = median(lifeExp),
            maxGdpPercap = max(gdpPercap))
#> [90m# A tibble: 1 × 2[39m
#>   [1mmedianLifeExp[22m [1mmaxGdpPercap[22m
#>           [3m[90m<dbl>[39m[23m        [3m[90m<dbl>[39m[23m
#> [90m1[39m          48.4      [4m1[24m[4m1[24m[4m3[24m523.
```

<p class>

That's right!
Think about what other kinds of information about countries you might want to summarize within one year.

</p>

## The group_by verb

### Summarizing by year

<div>

<p>

In a previous exercise, you found the median life expectancy and the maximum GDP per capita in the year 1957.
Now, you'll perform those two summaries within each year in the dataset, using the <code>group_by</code> verb.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Find the median life expectancy (<code>lifeExp</code>) and maximum GDP per capita (<code>gdpPercap</code>) <strong>within each year</strong>, saving them into <code>medianLifeExp</code> and <code>maxGdpPercap</code>, respectively.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)

# Find median life expectancy and maximum GDP per capita in each year
gapminder %>%
  group_by(year) %>%
  summarize(medianLifeExp = median(lifeExp),
            maxGdpPercap = max(gdpPercap))
#> [90m# A tibble: 12 × 3[39m
#>    [1myear[22m [1mmedianLifeExp[22m [1mmaxGdpPercap[22m
#>   [3m[90m<int>[39m[23m         [3m[90m<dbl>[39m[23m        [3m[90m<dbl>[39m[23m
#> [90m1[39m  [4m1[24m952          45.1      [4m1[24m[4m0[24m[4m8[24m382.
#> [90m2[39m  [4m1[24m957          48.4      [4m1[24m[4m1[24m[4m3[24m523.
#> [90m3[39m  [4m1[24m962          50.9       [4m9[24m[4m5[24m458.
#> [90m4[39m  [4m1[24m967          53.8       [4m8[24m[4m0[24m895.
#> [90m5[39m  [4m1[24m972          56.5      [4m1[24m[4m0[24m[4m9[24m348.
#> [90m6[39m  [4m1[24m977          59.7       [4m5[24m[4m9[24m265.
#> [90m# … with 6 more rows[39m
```

<p class>

Great!
Interesting: notice that median life expectancy across countries is generally going up over time, but maximum GDP per capita is not.

</p>

### Summarizing by continent

<div>

<p>

You can group by any variable in your dataset to create a summary.
Rather than comparing across time, you might be interested in comparing among continents.
You'll want to do that within one year of the dataset: let's use 1957.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Filter the <code>gapminder</code> data for the year 1957.
Then find the median life expectancy (<code>lifeExp</code>) and maximum GDP per capita (<code>gdpPercap</code>) <strong>within each continent</strong>, saving them into <code>medianLifeExp</code> and <code>maxGdpPercap</code>, respectively.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)

# Find median life expectancy and maximum GDP per capita in each continent in 1957
gapminder %>%
  filter(year == 1957) %>%
  group_by(continent) %>%
  summarize(medianLifeExp = median(lifeExp),
            maxGdpPercap = max(gdpPercap))
#> [90m# A tibble: 5 × 3[39m
#>   [1mcontinent[22m [1mmedianLifeExp[22m [1mmaxGdpPercap[22m
#>   [3m[90m<fct>[39m[23m             [3m[90m<dbl>[39m[23m        [3m[90m<dbl>[39m[23m
#> [90m1[39m Africa             40.6        [4m5[24m487.
#> [90m2[39m Americas           56.1       [4m1[24m[4m4[24m847.
#> [90m3[39m Asia               48.3      [4m1[24m[4m1[24m[4m3[24m523.
#> [90m4[39m Europe             67.6       [4m1[24m[4m7[24m909.
#> [90m5[39m Oceania            70.3       [4m1[24m[4m2[24m247.
```

<p class>

Great work!
Which continent had the highest median life expectancy in 1957?

</p>

### Summarizing by continent and year

<div>

<p>

Instead of grouping just by year, or just by continent, you'll now group by both continent and year to summarize within each.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Find the median life expectancy (<code>lifeExp</code>) and maximum GDP per capita (<code>gdpPercap</code>) <strong>within each combination of continent and year</strong>, saving them into <code>medianLifeExp</code> and <code>maxGdpPercap</code>, respectively.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)

# Find median life expectancy and maximum GDP per capita in each continent/year combination
gapminder %>%
  group_by(continent, year) %>%
  summarize(medianLifeExp = median(lifeExp),
            maxGdpPercap = max(gdpPercap))
#> [1m[22m`summarise()` has grouped output by 'continent'. You can override using the
#> `.groups` argument.
#> [90m# A tibble: 60 × 4[39m
#> [90m# Groups:   continent [5][39m
#>   [1mcontinent[22m  [1myear[22m [1mmedianLifeExp[22m [1mmaxGdpPercap[22m
#>   [3m[90m<fct>[39m[23m     [3m[90m<int>[39m[23m         [3m[90m<dbl>[39m[23m        [3m[90m<dbl>[39m[23m
#> [90m1[39m Africa     [4m1[24m952          38.8        [4m4[24m725.
#> [90m2[39m Africa     [4m1[24m957          40.6        [4m5[24m487.
#> [90m3[39m Africa     [4m1[24m962          42.6        [4m6[24m757.
#> [90m4[39m Africa     [4m1[24m967          44.7       [4m1[24m[4m8[24m773.
#> [90m5[39m Africa     [4m1[24m972          47.0       [4m2[24m[4m1[24m011.
#> [90m6[39m Africa     [4m1[24m977          49.3       [4m2[24m[4m1[24m951.
#> [90m# … with 54 more rows[39m
```

<p class>

Excellent!
In the next chapter, you'll learn to turn this data into an informative graph.

</p>

## Visualizing summarized data

### Visualizing median life expectancy over time

<div>

<p>

In the last chapter, you summarized the gapminder data to calculate the median life expectancy within each year.
This code is provided for you, and is saved (with <code>\<-</code>) as the <code>by_year</code> dataset.

</p>

<p>

Now you can use the ggplot2 package to turn this into a visualization of changing life expectancy over time.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Use the <code>by_year</code> dataset to create a scatter plot showing the change of median life expectancy over time, with <code>year</code> on the x-axis and <code>medianLifeExp</code> on the y-axis.
Be sure to add <code>expand_limits(y = 0)</code> to make sure the plot's y-axis includes zero.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

by_year <- gapminder %>%
  group_by(year) %>%
  summarize(medianLifeExp = median(lifeExp),
            maxGdpPercap = max(gdpPercap))

# Create a scatter plot showing the change in medianLifeExp over time
ggplot(by_year, aes(x = year, y = medianLifeExp)) +
  geom_point() +
  expand_limits(y = 0)
```

<img src="intror_files/figure-html/unnamed-chunk-27-1.png" width="672" />

<p class>

Great!
It looks like median life expectancy across countries is increasing over time.

</p>

### Visualizing median GDP per capita per continent over time

<div>

<p>

In the last exercise you were able to see how the median life expectancy of countries changed over time.
Now you'll examine the median GDP per capita instead, and see how the trend differs among continents.

</p>

</div>

::: exercise--instructions__content
<li>

Summarize the gapminder dataset by continent and year, finding the median GDP per capita (<code>gdpPercap</code>) within each and putting it into a column called <code>medianGdpPercap</code>.
Use the assignment operator <code>\<-</code> to save this summarized data as <code>by_year_continent</code>.

</li>


```r
library(gapminder)
library(dplyr)
library(ggplot2)

# Summarize medianGdpPercap within each continent within each year: by_year_continent
by_year_continent <- gapminder %>%
  group_by(continent, year) %>%
  summarize(medianGdpPercap = median(gdpPercap))
#> [1m[22m`summarise()` has grouped output by 'continent'. You can override using the
#> `.groups` argument.
```

<li>

Create a scatter plot showing the change in <code>medianGdpPercap</code> by continent over time.
Use color to distinguish between continents, and be sure to add <code>expand_limits(y = 0)</code> so that the y-axis starts at zero.

</li>


```r
# Plot the change in medianGdpPercap in each continent over time
ggplot(by_year_continent, aes(x = year, y = medianGdpPercap, color = continent)) +
  geom_point() +
  expand_limits(y = 0)
```

<img src="intror_files/figure-html/unnamed-chunk-29-1.png" width="672" />
:::

<p class>

Great!
You might be wondering how you can connect these points with lines.
You'll learn that in Chapter 4!

</p>

### Comparing median life expectancy and median GDP per continent in 2007

<div>

<p>

In these exercises you've generally created plots that show change over time.
But as another way of exploring your data visually, you can also use ggplot2 to plot summarized data to compare continents within a single year.

</p>

</div>

::: exercise--instructions__content
<li>

Filter the gapminder dataset for the year 2007, then summarize the median GDP per capita and the median life expectancy <strong>within each continent</strong>, into columns called <code>medianLifeExp</code> and <code>medianGdpPercap</code>.
Save this as <code>by_continent_2007</code>.

</li>


```r
library(gapminder)
library(dplyr)
library(ggplot2)

# Summarize the median GDP and median life expectancy per continent in 2007
by_continent_2007 <- gapminder %>%
  filter(year == 2007) %>%
  group_by(continent) %>%
  summarize(medianGdpPercap = median(gdpPercap),
            medianLifeExp = median(lifeExp))
```

<li>

Use the <code>by_continent_2007</code> data to create a scatterplot comparing these summary statistics for continents in 2007, putting the median GDP per capita on the x-axis to the median life expectancy on the y-axis.
Color the scatter plot by <code>continent</code>.
You don't need to add <code>expand_limits(y = 0)</code> for this plot.

</li>


```r
# Use a scatter plot to compare the median GDP and median life expectancy
ggplot(by_continent_2007, aes(x = medianGdpPercap, y = medianLifeExp, color = continent)) +
  geom_point()
```

<img src="intror_files/figure-html/unnamed-chunk-31-1.png" width="672" />
:::

<p class>

Great work!
Scatter plots are a very flexible tool for examining relationships.

</p>

# Types of visualizations

<p>

In this chapter, you'll learn how to create line plots, bar plots, histograms, and boxplots.
You'll see how each plot requires different methods of data manipulation and preparation, and you'll understand how each of these plot types plays a different role in data analysis.

</p>

## Line plots

### Visualizing median GDP per capita over time

<div>

<p>

A line plot is useful for visualizing trends over time.
In this exercise, you'll examine how the median GDP per capita has changed over time.

</p>

</div>

::: exercise--instructions__content
<li>

Use <code>group_by()</code> and <code>summarize()</code> to find the median GDP per capita <strong>within each year</strong>, calling the output column <code>medianGdpPercap</code>.
Use the assignment operator <code>\<-</code> to save it to a dataset called <code>by_year</code>.

</li>


```r
library(gapminder)
library(dplyr)
library(ggplot2)

# Summarize the median gdpPercap by year, then save it as by_year
by_year <- gapminder %>%
  group_by(year) %>%
  summarize(medianGdpPercap = median(gdpPercap))
```

<li>

Use the <code>by_year</code> dataset to create a line plot showing the change in median GDP per capita over time.
<strong>Be sure</strong> to use <code>expand_limits(y = 0)</code> to include 0 on the y-axis.

</li>


```r
# Create a line plot showing the change in medianGdpPercap over time
ggplot(by_year, aes(x = year, y = medianGdpPercap)) +
  geom_line() +
  expand_limits(y = 0)
```

<img src="intror_files/figure-html/unnamed-chunk-33-1.png" width="672" />
:::

<p class>

Great!
Looks like median GDP per capita across countries has gone up over time.

</p>

### Visualizing median GDP per capita by continent over time

<div>

<p>

In the last exercise you used a line plot to visualize the increase in median GDP per capita over time.
Now you'll examine the change within each continent.

</p>

</div>

::: exercise--instructions__content
<li>

Use <code>group_by()</code> and <code>summarize()</code> to find the median GDP per capita <strong>within each year and continent</strong>, calling the output column <code>medianGdpPercap</code>.
Use the assignment operator <code>\<-</code> to save it to a dataset called <code>by_year_continent</code>.

</li>


```r
library(gapminder)
library(dplyr)
library(ggplot2)

# Summarize the median gdpPercap by year & continent, save as by_year_continent
by_year_continent <- gapminder %>%
  group_by(year, continent) %>%
  summarize(medianGdpPercap = median(gdpPercap))
#> [1m[22m`summarise()` has grouped output by 'year'. You can override using the
#> `.groups` argument.
```

<li>

Use the <code>by_year_continent</code> dataset to create a line plot showing the change in median GDP per capita over time, with color representing continent.
<strong>Be sure</strong> to use <code>expand_limits(y = 0)</code> to include 0 on the y-axis.

</li>


```r
# Create a line plot showing the change in medianGdpPercap by continent over time
ggplot(by_year_continent, aes(x = year, y = medianGdpPercap, color = continent)) +
  geom_line() +
  expand_limits(y = 0)
```

<img src="intror_files/figure-html/unnamed-chunk-35-1.png" width="672" />
:::

<p class>

Excellent work!
Take a look at the plot: did the growth in median GDP per capita differ between continents?

</p>

## Bar plots

### Visualizing median GDP per capita by continent

<div>

<p>

A bar plot is useful for visualizing summary statistics, such as the median GDP in each continent.

</p>

</div>

::: exercise--instructions__content
<li>

Use <code>group_by()</code> and <code>summarize()</code> to find the median GDP per capita <strong>within each continent</strong> in the year 1952, calling the output column <code>medianGdpPercap</code>.
Use the assignment operator <code>\<-</code> to save it to a dataset called <code>by_continent</code>.

</li>


```r
library(gapminder)
library(dplyr)
library(ggplot2)

# Summarize the median gdpPercap by continent in 1952
by_continent <- gapminder %>%
  filter(year == 1952) %>%
  group_by(continent) %>%
  summarize(medianGdpPercap = median(gdpPercap))
```

<li>

Use the <code>by_continent</code> dataset to create a bar plot showing the median GDP per capita in each continent.

</li>


```r
# Create a bar plot showing medianGdp by continent
ggplot(by_continent, aes(x = continent, y = medianGdpPercap)) +
  geom_col()
```

<img src="intror_files/figure-html/unnamed-chunk-37-1.png" width="672" />
:::

<p class>

Excellent!
That's three kinds of plots you're now able to make with ggplot2.

</p>

### Visualizing GDP per capita by country in Oceania

<div>

<p>

You've created a plot where each bar represents one continent, showing the median GDP per capita for each.
But the x-axis of the bar plot doesn't have to be the continent: you can instead create a bar plot where each bar represents a country.

</p>

<p>

In this exercise, you'll create a bar plot comparing the GDP per capita between the two countries in the Oceania continent (Australia and New Zealand).

</p>

</div>

::: exercise--instructions__content
<li>

Filter for observations in the <strong>Oceania</strong> continent in the year 1952.
Save this as <code>oceania_1952</code>.

</li>


```r
library(gapminder)
library(dplyr)
library(ggplot2)

# Filter for observations in the Oceania continent in 1952
oceania_1952 <- gapminder %>%
  filter(continent == "Oceania", year == 1952)
```

<li>

Use the <code>oceania_1952</code> dataset to create a bar plot, with country on the x-axis and <code>gdpPercap</code> on the y-axis.

</li>


```r
# Create a bar plot of gdpPercap by country
ggplot(oceania_1952, aes(x = country, y = gdpPercap)) +
  geom_col()
```

<img src="intror_files/figure-html/unnamed-chunk-39-1.png" width="672" />
:::

<p class>

Good work!
Looks like the GDP per capita of these two countries was similar in 1952.

</p>

## Histograms

### Visualizing population

<div>

<p>

A histogram is useful for examining the distribution of a numeric variable.
In this exercise, you'll create a histogram showing the distribution of country populations (by millions) in the year 1952.

</p>

<p>

Code for generating this dataset, <code>gapminder_1952</code>, is provided.

</p>

</div>

::: exercise--instructions__content
<p>

Use the <code>gapminder_1952</code> dataset to create a histogram of country population (<code>pop_by_mil</code>) in the year 1952.
Inside the histogram geom, set the number of <code>bins</code> to <code>50</code>.

</p>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

gapminder_1952 <- gapminder %>%
  filter(year == 1952) %>%
  mutate(pop_by_mil = pop / 1000000)

# Create a histogram of population (pop_by_mil)
ggplot(gapminder_1952, aes(x = pop_by_mil)) +
  geom_histogram(bins = 50)
```

<img src="intror_files/figure-html/unnamed-chunk-40-1.png" width="672" />

<p class>

That's right!
Notice that most of the distribution is in the smallest (leftmost) bins.
In the next exercise you'll put the x-axis on a log scale.

</p>

### Visualizing population with x-axis on a log scale

<div>

<p>

In the last exercise you created a histogram of populations across countries.
You might have noticed that there were several countries with a much higher population than others, which causes the distribution to be very skewed, with most of the distribution crammed into a small part of the graph.
(Consider that it's hard to tell the median or the minimum population from that histogram).

</p>

<p>

To make the histogram more informative, you can try putting the x-axis on a log scale.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Use the <code>gapminder_1952</code> dataset (code is provided) to create a histogram of country population (<code>pop</code>) in the year 1952, putting the x-axis on a log scale with <code>scale_x\_log10()</code>.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

gapminder_1952 <- gapminder %>%
  filter(year == 1952)

# Create a histogram of population (pop), with x on a log scale
ggplot(gapminder_1952, aes(x = pop)) +
  geom_histogram() +
  scale_x_log10()
#> `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.
```

<img src="intror_files/figure-html/unnamed-chunk-41-1.png" width="672" />

<p class>

Great!
Notice that on a log scale, the distribution of country populations is approximately symmetrical.

</p>

## Boxplots

### Comparing GDP per capita across continents

<div>

<p>

A boxplot is useful for comparing a distribution of values across several groups.
In this exercise, you'll examine the distribution of GDP per capita by continent.
Since GDP per capita varies across several orders of magnitude, you'll need to put the y-axis on a log scale.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Use the <code>gapminder_1952</code> dataset (code is provided) to create a boxplot comparing GDP per capita (<code>gdpPercap</code>) among continents.
Put the y-axis on a log scale with <code>scale_y\_log10()</code>.

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

gapminder_1952 <- gapminder %>%
  filter(year == 1952)

# Create a boxplot comparing gdpPercap among continents
ggplot(gapminder_1952, aes(x = continent, y = gdpPercap)) +
  geom_boxplot() +
  scale_y_log10()
```

<img src="intror_files/figure-html/unnamed-chunk-42-1.png" width="672" />

<p class>

Looks good!
What continents had countries with the highest GDP per capita?

</p>

### Adding a title to your graph

<div>

<p>

There are many other options for customizing a <code>ggplot2</code> graph, which you can learn about in other DataCamp courses.
You can also learn about them from online resources, which is an important skill to develop.

</p>

<p>

As the final exercise in this course, you'll practice looking up <code>ggplot2</code> instructions by completing a task we haven't shown you how to do.

</p>

</div>

::: exercise--instructions__content
<ul>

<li>

Add a title to the graph: <strong>Comparing GDP per capita across continents</strong>.
Use a search engine, such as Google or Bing, to learn how to do so.

</li>

<li>

After this exercise you are almost done with your course.
If you enjoyed the material, feel free to send Dave a thank you via twitter.
He'll appreciate it.
<a href="http://twitter.com/home?status=Thoroughly%20enjoyed%20the%20Introduction%20to%20the%20Tidyverse%20course%20%40DataCamp%20by%20%40drob.%20Great%20instructor!%20https%3A%2F%2Fbit.ly%2F2AmGt3t%0A">Tweet to Dave</a>

</li>

</ul>
:::


```r
library(gapminder)
library(dplyr)
library(ggplot2)

gapminder_1952 <- gapminder %>%
  filter(year == 1952)

# Add a title to this graph: "Comparing GDP per capita across continents"
ggplot(gapminder_1952, aes(x = continent, y = gdpPercap)) +
  geom_boxplot() +
  scale_y_log10() +
  ggtitle("Comparing GDP per capita across continents")
```

<img src="intror_files/figure-html/unnamed-chunk-43-1.png" width="672" />

