# Conditionals and Control Flow

<p>In this chapter, you'll learn about relational operators for comparing R objects, and logical operators like "and" and "or" for combining TRUE and FALSE values.  Then, you'll use this knowledge to build conditional statements.
  </p>
  
## Relational Operators



### Equality


<div class>
<p>The most basic form of comparison is equality. Let's briefly recap its syntax. The following statements all evaluate to <code>TRUE</code> (feel free to try them out in the console).</p>
<pre><code>3 == (2 + 1)
"intermediate" != "r"
TRUE != FALSE
"Rchitect" != "rchitect"
</code></pre>
<p>Notice from the last expression that R is case sensitive: "R" is not equal to "r". Keep this in mind when solving the exercises in this chapter!</p>
</div>

<li>In the editor on the right, write R code to see if <code>TRUE</code> equals <code>FALSE</code>.</li>

```r
# Comparison of logicals
TRUE == FALSE
#> [1] FALSE
```
<li>Likewise, check if <code>-6 * 14</code> is <em>not</em> equal to <code>17 - 101</code>.</li>

```r
# Comparison of numerics
-6 * 14 != 17 - 101
#> [1] FALSE
```
<li>Next up: comparison of character strings. Ask R whether the strings "useR" and "user" are equal.</li>

```r
# Comparison of character strings
"useR" == "user"
#> [1] FALSE
```
<li>Finally, find out what happens if you compare logicals to numerics: are <code>TRUE</code> and 1 equal?</li>

```r
# Compare a logical with a numeric
TRUE == 1
#> [1] TRUE
```

<p class="">Awesome! Since <code>TRUE</code> coerces to <code>1</code> under the hood, <code>TRUE == 1</code> evaluates to <code>TRUE</code>. Make sure not to mix up <code>==</code> (comparison) and <code>=</code> (assignment), <code>==</code> is what need to check the equality of R objects.
</p>

### Greater and less than


<div class>
<p>Apart from equality operators, Filip also introduced the <em>less than</em> and <em>greater than</em> operators: <code>&lt;</code> and <code>&gt;</code>. You can also add an equal sign to express <em>less than or equal to</em> or <em>greater than or equal to</em>, respectively. Have a look at the following R expressions, that all evaluate to <code>FALSE</code>:</p>
<pre><code>(1 + 2) &gt; 4
"dog" &lt; "Cats"
TRUE &lt;= FALSE
</code></pre>
<p>Remember that for string comparison, R determines the <em>greater than</em> relationship based on alphabetical order. Also, keep in mind that <code>TRUE</code> is treated as <code>1</code> for arithmetic, and <code>FALSE</code> is treated as <code>0</code>. Therefore, <code>FALSE &lt; TRUE</code> is <code>TRUE</code>.</p>
</div>
<div class="exercise--instructions__content">
<p>Write R expressions to check whether:</p>

<li>
<code>-6 * 5 + 2</code> is greater than or equal to <code>-10 + 1</code>.</li>

```r
# Comparison of numerics
-6 * 5 + 2 >= -10 + 1
#> [1] FALSE
```
<li>"raining" is less than or equal to "raining dogs".</li>

```r
# Comparison of character strings
"raining" <= "raining dogs"
#> [1] TRUE
```
<li>TRUE is greater than FALSE.</li>

```r
# Comparison of logicals
TRUE > FALSE
#> [1] TRUE
```

</div>

<p class="">Great job! Make sure to have a look at the console output to see if R returns the results you expected.
</p>

### Compare vectors


<div class>
<p>You are already aware that R is very good with vectors. Without having to change anything about the syntax, R's relational operators also work on vectors.</p>
<p>Let's go back to the example that was started in the video. You want to figure out whether your activity on social media platforms have paid off and decide to look at your results for LinkedIn and Facebook. The sample code in the editor initializes the vectors <code>linkedin</code> and <code>facebook</code>. Each of the vectors contains the number of profile views your LinkedIn and Facebook profiles had over the last seven days.</p>
</div>
<div class="exercise--instructions__content">

```r
# The linkedin and facebook vectors have already been created for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)
facebook <- c(17, 7, 5, 16, 8, 13, 14)

```
<p>Using relational operators, find a logical answer, i.e. <code>TRUE</code> or <code>FALSE</code>, for the following questions:</p>
<ul>
<li>On which days did the number of LinkedIn profile views exceed 15?</li>

```r
# Popular days
linkedin > 15
#> [1]  TRUE FALSE FALSE FALSE FALSE  TRUE FALSE
```
<li>When was your LinkedIn profile viewed only 5 times or fewer?</li>

```r
# Quiet days
linkedin <= 5
#> [1] FALSE FALSE FALSE  TRUE  TRUE FALSE FALSE
```
<li>When was your LinkedIn profile visited more often than your Facebook profile?</li>

```r
# LinkedIn more popular than Facebook
linkedin > facebook
#> [1] FALSE  TRUE  TRUE FALSE FALSE  TRUE FALSE
```
</ul>
</div>

<p class="">Wonderful! Have a look at the console output. Your LinkedIn profile was pretty popular on the sixth day, but less so on the fourth and fifth day.
</p>

### Compare matrices


<div class>
<p>R's ability to deal with different data structures for comparisons does not stop at vectors. Matrices and relational operators also work together seamlessly!</p>
<p>Instead of in vectors (as in the previous exercise), the LinkedIn and Facebook data is now stored in a matrix called <code>views</code>. The first row contains the LinkedIn information; the second row the Facebook information. The original vectors <code>facebook</code> and <code>linkedin</code> are still available as well.</p>
</div>
<div class="exercise--instructions__content">

```r
# The social data has been created for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)
facebook <- c(17, 7, 5, 16, 8, 13, 14)
views <- matrix(c(linkedin, facebook), nrow = 2, byrow = TRUE)
```

<p>Using the relational operators you've learned so far, try to discover the following:</p>

<li>When were the views exactly equal to 13? Use the <code>views</code> matrix to return a logical matrix.</li>

```r
# When does views equal 13?
views == 13
#>       [,1]  [,2]  [,3]  [,4]  [,5]  [,6]  [,7]
#> [1,] FALSE FALSE  TRUE FALSE FALSE FALSE FALSE
#> [2,] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE
```
<li>For which days were the number of views less than or equal to 14? Again, have R return a logical matrix.</li>

```r
# When is views less than or equal to 14?
views <= 14
#>       [,1] [,2] [,3]  [,4] [,5]  [,6] [,7]
#> [1,] FALSE TRUE TRUE  TRUE TRUE FALSE TRUE
#> [2,] FALSE TRUE TRUE FALSE TRUE  TRUE TRUE
```

</div>

<p class="">Nice job! This exercise concludes the part on comparators. Now that you know how to query the relation between R objects, the next step will be to use the results to alter the behavior of your programs. Find out all about that in the next video!
</p>

## Logical Operators



### &amp; and |


<div class>
<p>Before you work your way through the next exercises, have a look at the following R expressions. All of them will evaluate to <code>TRUE</code>:</p>
<pre><code>TRUE &amp; TRUE
FALSE | TRUE
5 &lt;= 5 &amp; 2 &lt; 3
3 &lt; 4 | 7 &lt; 6
</code></pre>
<p>Watch out: <code>3 &lt; x &lt; 7</code> to check if <code>x</code> is between 3 and 7 will not work; you'll need <code>3 &lt; x &amp; x &lt; 7</code> for that.</p>
<p>In this exercise, you'll be working with the <code>last</code> variable. This variable equals the last value of the <code>linkedin</code> vector that you've worked with previously. The <code>linkedin</code> vector represents the number of LinkedIn views your profile had in the last seven days, remember? Both the variables <code>linkedin</code> and <code>last</code> have been pre-defined for you.</p>
</div>
<div class="exercise--instructions__content">

```r
# The linkedin and last variable are already defined for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)
last <- tail(linkedin, 1)
```

<p>Write R expressions to solve the following questions concerning the variable <code>last</code>:</p>

<li>Is <code>last</code> under 5 or above 10?</li>

```r
# Is last under 5 or above 10?
last < 5 | last > 10
#> [1] TRUE
```
<li>Is <code>last</code> between 15 and 20, excluding 15 but including 20?</li>

```r
# Is last between 15 (exclusive) and 20 (inclusive)?
last > 15 & last <= 20
#> [1] FALSE
```

</div>

<p class="">Great! Do the results of the different expressions make sense?
</p>

### &amp; and | (2)


<div class>
<p>Like relational operators, logical operators work perfectly fine with vectors and matrices.</p>
<p>Both the vectors <code>linkedin</code> and <code>facebook</code> are available again. Also a matrix - <code>views</code> - has been defined; its first and second row correspond to the <code>linkedin</code> and <code>facebook</code> vectors, respectively. Ready for some advanced queries to gain more insights into your social outreach?</p>
</div>

<li>When did LinkedIn views exceed 10 <em>and</em> did Facebook views fail to reach 10 for a particular day? Use the <code>linkedin</code> and <code>facebook</code> vectors.</li>

```r
# The social data (linkedin, facebook, views) has been created for you

# linkedin exceeds 10 but facebook below 10
linkedin > 10 & facebook < 10
#> [1] FALSE FALSE  TRUE FALSE FALSE FALSE FALSE
```
<li>When were one or both of your LinkedIn and Facebook profiles visited at least 12 times?</li>

```r
# When were one or both visited at least 12 times?
linkedin >= 12 | facebook >= 12
#> [1]  TRUE FALSE  TRUE  TRUE FALSE  TRUE  TRUE
```
<li>When is the <code>views</code> matrix equal to a number between 11 and 14, excluding 11 and including 14?</li>

```r
# When is views between 11 (exclusive) and 14 (inclusive)?
views > 11 & views <= 14
#>       [,1]  [,2]  [,3]  [,4]  [,5]  [,6] [,7]
#> [1,] FALSE FALSE  TRUE FALSE FALSE FALSE TRUE
#> [2,] FALSE FALSE FALSE FALSE FALSE  TRUE TRUE
```

<p class="">Bravo! You'll have noticed how easy it is to use logical operators to vectors and matrices. What do these results tell us? The third day of the recordings was the only day where your LinkedIn profile was visited more than 10 times, while your Facebook profile wasn't. Can you draw similar conclusions for the other results?
</p>

### Reverse the result: !

<div class=""><p>On top of the <code>&amp;</code> and <code>|</code> operators, you also learned about the <code>!</code> operator, which negates a logical value. To refresh your memory, here are some R expressions that use <code>!</code>. They all evaluate to <code>FALSE</code>:</p>
<pre><code>!TRUE
!(5 &gt; 3)
!!FALSE
</code></pre>
<p>What would the following set of R expressions return?</p>
<pre><code>x &lt;- 5
y &lt;- 7
!(!(x &lt; 4) &amp; !!!(y &gt; 12))
</code></pre></div>

<ul
<li><div class=""><code>TRUE</code></div></li>
<strong><li><div class=""><code>FALSE</code></div></li></strong>
<li><div class="">Running this piece of code would throw an error.</div></li>
</ul>

<p class="dc-completion-pane__message dc-u-maxw-100pc">Great!</p>

### Blend it all together


<div class>
<p>With the things you've learned by now, you're able to solve pretty cool problems.</p>
<p>Instead of recording the number of views for your own LinkedIn profile, suppose you conducted a survey inside the company you're working for. You've asked every employee with a LinkedIn profile how many visits their profile has had over the past seven days. You stored the results in a data frame called <code>li_df</code>. This data frame is available in the workspace; type <code>li_df</code> in the console to check it out.</p>
</div>

<li>Select the entire second column, named <code>day2</code>, from the <code>li_df</code> data frame as a vector and assign it to <code>second</code>.</li>

```r
# li_df is pre-loaded in your workspace
li_df=read.csv("https://docs.google.com/spreadsheets/d/e/2PACX-1vR407nDVsa6m6x-dwvqO2gbJs6Ac_gO1_5A6cQSui9Tz1_2Ev6tQUFhrFrvHdiZBhzv2_EwxZdSyxJh/pub?gid=1139830788&single=true&output=csv")
# Select the second column, named day2, from li_df: second
second <- li_df$day2

```
<li>Use <code>second</code> to create a logical vector, that contains <code>TRUE</code> if the corresponding number of views is strictly greater than 25 or strictly lower than 5 and <code>FALSE</code> otherwise. Store this logical vector as <code>extremes</code>.</li>

```r
# Build a logical vector, TRUE if value in second is extreme: extremes
extremes <- second > 25 | second < 5

```
<li>Use <code>sum()</code> on the <code>extremes</code> vector to calculate the number of <code>TRUE</code>s in <code>extremes</code> (i.e. to calculate the number of employees that are either very popular or very low-profile). Simply print this number to the console.</li>

```r
# Count the number of TRUEs in extremes
sum(extremes)
#> [1] 16
```

<p class="">Great! Head over to the next video and learn how relational and logical operators can be used to alter the flow of your R scripts.
</p>

## Conditional Statements



### The if statement


<div class>
<p>Before diving into some exercises on the <code>if</code> statement, have another look at its syntax:</p>
<pre><code>if (condition) {
  expr
}
</code></pre>
<p>Remember your vectors with social profile views? Let's look at it from another angle. The <code>medium</code> variable gives information about the social website; the <code>num_views</code> variable denotes the actual number of views that particular <code>medium</code> had on the last day of your recordings. Both variables have been pre-defined for you.</p>
</div>

```r
# Variables related to your last day of recordings
medium <- "LinkedIn"
num_views <- 14
```

<li>Examine the <code>if</code> statement that prints out <code>"Showing LinkedIn information"</code> if the <code>medium</code> variable equals <code>"LinkedIn"</code>.</li>

```r
# Examine the if statement for medium
if (medium == "LinkedIn") {
  print("Showing LinkedIn information")
}
#> [1] "Showing LinkedIn information"
```
<li>Code an <code>if</code> statement that prints <code>"You are popular!"</code> to the console if the <code>num_views</code> variable exceeds 15.</li>

```r
# Write the if statement for num_views
if (num_views > 15) {
  print("You are popular!")
}
```

<p class="">Great! Try to see what happens if you change the <code>medium</code> and <code>num_views</code> variables and run your code again. Let's further customize these if statements in the next exercise.
</p>

### Add an else


<div class>
<p>You can only use an <code>else</code> statement in combination with an <code>if</code> statement. The <code>else</code> statement does not require a condition; its corresponding code is simply run if all of the preceding conditions in the control structure are <code>FALSE</code>. Here's a recipe for its usage:</p>
<pre><code>if (condition) {
  expr1
} else {
  expr2
}
</code></pre>
<p><em>It's important that the <code>else</code> keyword comes on the same line as the closing bracket of the <code>if</code> part!</em></p>
<p>Both <code>if</code> statements that you coded in the previous exercises are already available to use. It's now up to you to extend them with the appropriate <code>else</code> statements!</p>
</div>
<div class="exercise--instructions__content">

<p>Add an <code>else</code> statement to both control structures, such that</p>
<li>"Unknown medium" gets printed out to the console when the if-condition on <code>medium</code> does not hold.</li>

```r
# Control structure for medium
if (medium == "LinkedIn") {
  print("Showing LinkedIn information")
} else {
  print("Unknown medium")
}
#> [1] "Showing LinkedIn information"
```
<li>R prints out "Try to be more visible!" when the if-condition on <code>num_views</code> is not met.</li>

```r
# Control structure for num_views
if (num_views > 15) {
  print("You're popular!")
} else {
  print("Try to be more visible!")
}
#> [1] "Try to be more visible!"
```
</div>

<p class="">Great job! You also had Facebook information available, remember? Time to add some more statements to our control structures using <code>else if</code>!
</p>

### Customize further: else if


<div class>
<p>The <code>else if</code> statement allows you to further customize your control structure. You can add as many <code>else if</code> statements as you like. Keep in mind that R ignores the remainder of the control structure once a condition has been found that is <code>TRUE</code> and the corresponding expressions have been executed. Here's an overview of the syntax to freshen your memory:</p>
<pre><code>if (condition1) {
  expr1
} else if (condition2) {
  expr2
} else if (condition3) {
  expr3
} else {
  expr4
}
</code></pre>
<p><em>Again, It's important that the <code>else if</code> keywords comes on the same line as the closing bracket of the previous part of the control construct!</em></p>
</div>
<div class="exercise--instructions__content">

<p>Add code to both control structures such that:</p>

<li>R prints out "Showing Facebook information" if <code>medium</code> is equal to "Facebook". Remember that R is case sensitive!</li>

```r
# Control structure for medium
if (medium == "LinkedIn") {
  print("Showing LinkedIn information")
} else if (medium == "Facebook") {
  # Add code to print correct string when condition is TRUE
  print("Showing Facebook information")
} else {
  print("Unknown medium")
}
#> [1] "Showing LinkedIn information"
```
<li>"Your number of views is average" is printed if <code>num_views</code> is between 15 (inclusive) and 10 (exclusive).
Feel free to change the variables <code>medium</code> and <code>num_views</code> to see how the control structure respond. In both cases, the existing code should be extended in the <code>else if</code> statement. No existing code should be modified.</li>

```r
# Control structure for num_views
if (num_views > 15) {
  print("You're popular!")
} else if (num_views <= 15 & num_views > 10) {
  # Add code to print correct string when condition is TRUE
  print("Your number of views is average")
} else {
  print("Try to be more visible!")
}
#> [1] "Your number of views is average"
```

</div>

<p class="">Awesome! Have another look at the second control structure. Because R abandons the control flow as soon as it finds a condition that is met, you can simplify the condition for the <code>else if</code> part in the second construct to <code>num_views &gt; 10</code>.
</p>

### Else if 2.0


<div class>
<p>You can do anything you want inside if-else constructs. You can even put in another set of conditional statements. Examine the following code chunk:</p>
<pre><code>if (number &lt; 10) {
  if (number &lt; 5) {
    result &lt;- "extra small"
  } else {
    result &lt;- "small"
  }
} else if (number &lt; 100) {
  result &lt;- "medium"
} else {
  result &lt;- "large"
}
print(result)
</code></pre>
<p>Have a look at the following statements:</p>
<ol>
<li>If <code>number</code> is set to 6, "small" gets printed to the console.</li>

<li>If <code>number</code> is set to 100, R prints out "medium".</li>

<li>If <code>number</code> is set to 4, "extra small" gets printed out to the console.</li>

<li>If <code>number</code> is set to 2500, R will generate an error, as <code>result</code> will not be defined.</li>

</ol>
<p>Select the option that lists <u>all</u> the true statements.</p>
</div>

<ul>
<li><div class="dc-input-radio__text">2 and 4</div></li>
<li><div class="dc-input-radio__text">1 and 4</div></li>
<strong><li><div class="dc-input-radio__text">1 and 3</div></li></strong>
<li><div class="dc-input-radio__text">2 and 3</div></li>
</ul>

<p class="">Wonderful! If you got this one right, the next exercise will be a piece of cake.
</p>

### Take control!


<div class>
<p>In this exercise, you will combine everything that you've learned so far: relational operators, logical operators and control constructs. You'll need it all!</p>
<p>We've pre-defined two values for you: <code>li</code> and <code>fb</code>, denoting the number of profile views your LinkedIn and Facebook profile had on the last day of recordings. Go through the instructions to create R code that generates a 'social media score', <code>sms</code>, based on the values of <code>li</code> and <code>fb</code>.</p>
</div>
<div class="exercise--instructions__content">
<p>Finish the control-flow construct with the following behavior:</p>

```r
# Variables related to your last day of recordings
li <- 15
fb <- 9

```

<li>If both <code>li</code> and <code>fb</code> are 15 or higher, set <code>sms</code> equal to double the sum of <code>li</code> and <code>fb</code>.</li>

<li>If both <code>li</code> and <code>fb</code> are strictly below 10, set <code>sms</code> equal to half the sum of <code>li</code> and <code>fb</code>.</li>

<li>In all other cases, set <code>sms</code> equal to <code>li + fb</code>.</li>

```r
# Code the control-flow construct
if (li >= 15 & fb >= 15) {
  sms <- 2 * (li + fb)
} else if (li < 10 & fb < 10) {
  sms <- 0.5 * (li + fb)
} else {
  sms <- li + fb
}

```
<li>Finally, print the resulting <code>sms</code> variable.</li>

```r
# Print the resulting sms to the console
sms
#> [1] 24
```

</div>

<p class="">Bellissimo! Feel free to play around some more with your solution by changing the values of <code>li</code> and <code>fb</code>.
</p>

# Loops

<p>Loops can come in handy on numerous occasions. While loops are like repeated if statements, the for loop is designed to iterate over all elements in a sequence. Learn about them in this chapter.
  </p>
  
## While loop



### Write a while loop


<div class>
<p>Let's get you started with building a <code>while</code> loop from the ground up. Have another look at its recipe:</p>
<pre><code>while (condition) {
  expr
}
</code></pre>
<p>Remember that the <code>condition</code> part of this recipe should become <code>FALSE</code> at some point during the execution. Otherwise, the <code>while</code> loop will go on indefinitely. </p>
<p><em>If your session expires when you run your code, check the body of your <code>while</code> loop carefully.</em></p>
<p>Have a look at the sample code provided; it initializes the <code>speed</code> variables and already provides a <code>while</code> loop template to get you started.</p>
</div>
<div class="exercise--instructions__content">
<p>Code a <code>while</code> loop with the following characteristics:</p>
<ul>
<li>The condition of the <code>while</code> loop should check if <code>speed</code> is higher than 30.</li>

<li>Inside the body of the <code>while</code> loop, print out <code>"Slow down!"</code>.</li>

<li>Inside the body of the <code>while</code> loop, decrease the <code>speed</code> by 7 units and assign this new  value to <code>speed</code> again. This step is crucial; otherwise your <code>while</code> loop will never stop and <em>your session will expire</em>.</li>

</ul>
<p><strong><em>If your session expires when you run your code, check the body of your <code>while</code> loop carefully: it's likely that you made a mistake.</em></strong></p>
</div>

```r
# Initialize the speed variable
speed <- 64

# Code the while loop
while (speed > 30) {
  print("Slow down!")
  speed <- speed - 7
}
#> [1] "Slow down!"
#> [1] "Slow down!"
#> [1] "Slow down!"
#> [1] "Slow down!"
#> [1] "Slow down!"

# Print out the speed variable
speed
#> [1] 29
```

<p class="">Great job! Proceed to the next exercise.
</p>

### Throw in more conditionals


<div class>
<p>In the previous exercise, you simulated the interaction between a driver and a driver's assistant: When the speed was too high, "Slow down!" got printed out to the console, resulting in a decrease of your speed by 7 units. </p>
<p>There are several ways in which you could make your driver's assistant more advanced. For example, the assistant could give you different messages based on your speed or provide you with a current speed at a given moment.</p>
<p>A <code>while</code> loop similar to the one you've coded in the previous exercise is already available for you to use. It prints out your current speed, but there's no code that decreases the <code>speed</code> variable yet, which is pretty dangerous. Can you make the appropriate changes?</p>
</div>
<div class="exercise--instructions__content">
<ul>
<li>If the speed is greater than 48, have R print out "Slow down big time!", and decrease the speed by <code>11</code>.</li>

<li>Otherwise, have R simply print out "Slow down!", and decrease the speed by <code>6</code>.</li>

</ul>
<p>If the session keeps timing out and throwing an error, you are probably stuck in an infinite loop! Check the body of your <code>while</code> loop and make sure you are assigning new values to <code>speed</code>.</p>
</div>

```r
# Extend/adapt the while loop
while (speed > 30) {
  print(paste("Your speed is", speed))
  if (speed > 48) {
    print("Slow down big time!")
    speed <- speed - 11
  } else {
    print("Slow down!")
    speed <- speed - 6
  }
}
```

<p class="">Wonderful! To further improve our driver assistant model, head over to the next exercise!
</p>

### Stop the while loop: break


<div class>
<p>There are some very rare situations in which severe speeding is necessary: what if a hurricane is approaching and you have to get away as quickly as possible? You don't want the driver's assistant sending you speeding notifications in that scenario, right?</p>
<p>This seems like a great opportunity to include the <code>break</code> statement in the <code>while</code> loop you've been working on. Remember that the <code>break</code> statement is a control statement. When R encounters it, the <code>while</code> loop is abandoned completely.</p>
</div>
<div class="exercise--instructions__content"><p>Adapt the <code>while</code> loop such that it is abandoned when the <code>speed</code> of the vehicle is greater than 80. This time, the <code>speed</code> variable has been initialized to 88; keep it that way.</p></div>

```r
# Initialize the speed variable
speed <- 88

while (speed > 30) {
  print(paste("Your speed is", speed))
  
  # Break the while loop when speed exceeds 80
  if (speed > 80) {
    break
  }
  
  if (speed > 48) {
    print("Slow down big time!")
    speed <- speed - 11
  } else {
    print("Slow down!")
    speed <- speed - 6
  }
}
#> [1] "Your speed is 88"
```

<p class="">Wonderful! Now that you've correctly solved this exercise, feel free to play around with different values of <code>speed</code> to see how the <code>while</code> loop handles the different cases.
</p>

### Build a while loop from scratch


<div class><p>The previous exercises guided you through developing a pretty advanced <code>while</code> loop, containing a <code>break</code> statement and different messages and updates as determined by control flow constructs. If you manage to solve this comprehensive exercise using a <code>while</code> loop, you're totally ready for the next topic: the <code>for</code> loop.</p></div>
<div class="exercise--instructions__content">
<p>Finish the <code>while</code> loop so that it:</p>

<li>prints out the triple of <code>i</code>, so <code>3 * i</code>, at each run.</li>

<li>is abandoned with a <code>break</code> if the triple of <code>i</code> is divisible by 8, but still prints out this triple before breaking.</li>

```r
# Initialize i as 1 
i <- 1

# Code the while loop
while (i <= 10) {
  print(3 * i)
  if ( (3 * i) %% 8 == 0) {
    break
  }
  i <- i + 1
}
#> [1] 3
#> [1] 6
#> [1] 9
#> [1] 12
#> [1] 15
#> [1] 18
#> [1] 21
#> [1] 24
```

</div>

<p class="">Great work! Head over to the next video!
</p>

## For loop



### Loop over a vector


<div class>
<p>In the previous video, Filip told you about two different strategies for using the <code>for</code> loop. To refresh your memory, consider the following loops that are equivalent in R:</p>
<pre><code>primes &lt;- c(2, 3, 5, 7, 11, 13)

# loop version 1
for (p in primes) {
  print(p)
}

# loop version 2
for (i in 1:length(primes)) {
  print(primes[i])
}
</code></pre>
<p>Remember our <code>linkedin</code> vector? It's a vector that contains the number of views your LinkedIn profile had in the last seven days. The <code>linkedin</code> vector has been pre-defined so that you can fully focus on the instructions!</p>
</div>
<div class="exercise--instructions__content"><p>Write a <code>for</code> loop that iterates over all the elements of <code>linkedin</code> and prints out every element separately. Do this in two ways: using the <em>loop version 1</em> and the <em>loop version 2</em> in the example code above.</p></div>

```r
# The linkedin vector has already been defined for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)

# Loop version 1
for (li in linkedin) {
  print(li)
}
#> [1] 16
#> [1] 9
#> [1] 13
#> [1] 5
#> [1] 2
#> [1] 17
#> [1] 14

# Loop version 2
for (i in 1:length(linkedin)) {
  print(linkedin[i])
}
#> [1] 16
#> [1] 9
#> [1] 13
#> [1] 5
#> [1] 2
#> [1] 17
#> [1] 14
```

<p class="">Piece of cake! Go to the next exercise.
</p>

### Loop over a list


<div class>
<p>Looping over a list is just as easy and convenient as looping over a vector. There are again two different approaches here:</p>
<pre><code>primes_list &lt;- list(2, 3, 5, 7, 11, 13)

# loop version 1
for (p in primes_list) {
  print(p)
}

# loop version 2
for (i in 1:length(primes_list)) {
  print(primes_list[[i]])
}
</code></pre>
<p>Notice that you need double square brackets - <code>[[ ]]</code> - to select the list elements in loop version 2.</p>
<p>Suppose you have a list of all sorts of information on New York City: its population size, the names of the boroughs, and whether it is the capital of the United States. We've already defined a list <code>nyc</code> containing this information (source: Wikipedia).</p>
</div>

```r
# The nyc list is already specified
nyc <- list(pop = 8405837, 
            boroughs = c("Manhattan", "Bronx", "Brooklyn", "Queens", "Staten Island"), 
            capital = FALSE)
```

<div class="exercise--instructions__content">
<p>As in the previous exercise, loop over the <code>nyc</code> list in two different ways to print its elements:</p>

<li>Loop directly over the <code>nyc</code> list (loop version 1).</li>

```r
# Loop version 1
for (info in nyc) {
  print(info)
}
#> [1] 8405837
#> [1] "Manhattan"     "Bronx"         "Brooklyn"      "Queens"       
#> [5] "Staten Island"
#> [1] FALSE
```
<li>Define a looping index and do subsetting using double brackets (loop version 2).</li>

```r
# Loop version 2
for (i in 1:length(nyc)) {
  print(nyc[[i]])
}
#> [1] 8405837
#> [1] "Manhattan"     "Bronx"         "Brooklyn"      "Queens"       
#> [5] "Staten Island"
#> [1] FALSE
```

</div>

<p class="">Good job! Filip mentioned that <code>for</code> loops can also be used for matrices. Let's put that to a test in the next exercise.
</p>

### Loop over a matrix


<div class>
<p>In your workspace, there's a matrix <code>ttt</code>, that represents the status of a <a href="http://en.wikipedia.org/wiki/Tic-tac-toe">tic-tac-toe</a> game. It contains the values "X", "O" and "NA". Print out <code>ttt</code> to get a closer look. On row 1 and column 1, there's "O", while on row 3 and column 2 there's "NA". </p>

```r
ttt=matrix(c("O",NA,"X",NA,"O","O","X",NA,"X"),3,3)
```

<p>To solve this exercise, you'll need a <code>for</code> loop inside a <code>for</code> loop, often called a nested loop. Doing this in R is a breeze! Simply use the following recipe:</p>
<pre><code>for (var1 in seq1) {
  for (var2 in seq2) {
    expr
  }
}
</code></pre>
</div>
<div class="exercise--instructions__content">
<p>Finish the nested <code>for</code> loops to go over the elements in <code>ttt</code>:</p>
<ul>
<li>The outer loop should loop over the rows, with loop index <code>i</code> (use <code>1:nrow(ttt)</code>).</li>

<li>The inner loop should loop over the columns, with loop index <code>j</code> (use <code>1:ncol(ttt)</code>).</li>

<li>Inside the inner loop, make use of <code>print()</code> and <code>paste()</code> to print out information in the following format: "On row i and column j the board contains x", where <code>x</code> is the value on that position.</li>

</ul>
</div>

```r
# The tic-tac-toe matrix ttt has already been defined for you

# define the double for loop
for (i in 1:nrow(ttt)) {
  for (j in 1:ncol(ttt)) {
    print(paste("On row", i, "and column", j, "the board contains", ttt[i,j]))
  }
}
#> [1] "On row 1 and column 1 the board contains O"
#> [1] "On row 1 and column 2 the board contains NA"
#> [1] "On row 1 and column 3 the board contains X"
#> [1] "On row 2 and column 1 the board contains NA"
#> [1] "On row 2 and column 2 the board contains O"
#> [1] "On row 2 and column 3 the board contains NA"
#> [1] "On row 3 and column 1 the board contains X"
#> [1] "On row 3 and column 2 the board contains O"
#> [1] "On row 3 and column 3 the board contains X"
```

<p class="">Awesome! You're sufficiently comfortable with basic <code>for</code> looping, so it's time to step it up a notch!
</p>

### Mix it up with control flow


<div class><p>Let's return to the <em>LinkedIn</em> profile views data, stored in a vector <code>linkedin</code>. In the first exercise on <code>for</code> loops you already did a simple printout of each element in this vector. A little more in-depth interpretation of this data wouldn't hurt, right? Time to throw in some conditionals! As with the <code>while</code> loop, you can use the <code>if</code> and <code>else</code> statements inside the <code>for</code> loop.</p></div>
<div class="exercise--instructions__content">
<p>Add code to the <code>for</code> loop that loops over the elements of the <code>linkedin</code> vector:</p>

```r
# The linkedin vector has already been defined for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)
```

<li>If the vector element's value exceeds 10, print out "You're popular!".</li>

<li>If the vector element's value does not exceed 10, print out "Be more visible!"</li>

```r
# Code the for loop with conditionals
for (li in linkedin) {
  if (li > 10) {
    print("You're popular!")
  } else {
    print("Be more visible!")
  }
  print(li)
}
#> [1] "You're popular!"
#> [1] 16
#> [1] "Be more visible!"
#> [1] 9
#> [1] "You're popular!"
#> [1] 13
#> [1] "Be more visible!"
#> [1] 5
#> [1] "Be more visible!"
#> [1] 2
#> [1] "You're popular!"
#> [1] 17
#> [1] "You're popular!"
#> [1] 14
```

</div>

<p class="">Outstanding! In the next exercise, you'll customize this <code>for</code> loop even further with <code>break</code> and <code>next</code> statements.
</p>

### Next, you break it


<div class>
<p>A possible solution to the previous exercise has been provided for you. The code loops over the <code>linkedin</code> vector and prints out different messages depending on the values of <code>li</code>. </p>
<p>In this exercise, you will use the <code>break</code> and <code>next</code> statements:</p>
<ul>
<li>The <code>break</code> statement abandons the active loop: the remaining code in the loop is skipped and the loop is not iterated over anymore.</li>

<li>The <code>next</code> statement skips the remainder of the code in the loop, but continues the iteration.</li>

</ul>
</div>
<div class="exercise--instructions__content">
<p>Extend the <code>for</code> loop with two new, separate <code>if</code> tests as follows:</p>

<li>If the vector element's value exceeds 16, print out "This is ridiculous, I'm outta here!" and have R abandon the <code>for</code> loop (<code>break</code>).</li>

<li>If the value is lower than 5, print out "This is too embarrassing!" and fast-forward to the next iteration (<code>next</code>).</li>

```r
# Adapt/extend the for loop
for (li in linkedin) {
  if (li > 10) {
    print("You're popular!")
  } else {
    print("Be more visible!")
  }
  
  # Add if statement with break
  if (li > 16) {
    print("This is ridiculous, I'm outta here!")
    break
  }
  
  # Add if statement with next
  if (li < 5) {
    print("This is too embarrassing!")
    next
  }
  
  print(li)
}
#> [1] "You're popular!"
#> [1] 16
#> [1] "Be more visible!"
#> [1] 9
#> [1] "You're popular!"
#> [1] 13
#> [1] "Be more visible!"
#> [1] 5
#> [1] "Be more visible!"
#> [1] "This is too embarrassing!"
#> [1] "You're popular!"
#> [1] "This is ridiculous, I'm outta here!"
```

</div>

<p class="">Great. <code>for</code>, <code>break</code>, <code>next</code>? We name it, you can do it!
</p>

### Build a for loop from scratch


<div class>
<p>This exercise will not introduce any new concepts on <code>for</code> loops.</p>
<p>We already went ahead and defined a variable <code>rquote</code>. This variable has been split up into a vector that contains separate letters and has been stored in a vector <code>chars</code> with the <a href="http://www.rdocumentation.org/packages/base/functions/strsplit"><code>strsplit()</code></a> function.</p>
<p>Can you write code that counts the number of r's that come before the first u in <code>rquote</code>?</p>
</div>

<li>Initialize the variable <code>rcount</code>, as 0.</li>

```r
# Pre-defined variables
rquote <- "r's internals are irrefutably intriguing"
chars <- strsplit(rquote, split = "")[[1]]

# Initialize rcount
rcount <- 0

```
<li>Finish the <code>for</code> loop:</li>

<li>if <code>char</code> equals <code>"r"</code>, increase the value of <code>rcount</code> by 1.</li>

<li>if <code>char</code> equals <code>"u"</code>, leave the <code>for</code> loop entirely with a <code>break</code>.</li>

```r
# Finish the for loop
for (char in chars) {
  if (char == "r") {
    rcount <- rcount + 1
  }
  if (char == "u") {
    break
  }
}

```
<li>Finally, print out the variable <code>rcount</code> to the console to see if your code is correct.</li>

```r
# Print out rcount
rcount
#> [1] 5
```

<p class="">For-midable! This exercise concludes the chapter on <code>while</code> and <code>for</code> loops.
</p>

# Functions

<p>Functions are an extremely important concept in almost every programming language, and R is no different. Learn what functions are and how to use them—then take charge by writing your own functions.
  </p>
  
## Introduction to Functions



### Function documentation


<div class>
<p>Before even thinking of using an R function, you should clarify which arguments it expects. All the relevant details such as a description, usage, and arguments can be found in the documentation. To consult the documentation on the <a href="http://www.rdocumentation.org/packages/base/functions/sample"><code>sample()</code></a> function, for example, you can use one of following R commands:</p>
<pre><code>help(sample)
?sample
</code></pre>
<p>If you execute these commands, you'll be redirected to www.rdocumentation.org.</p>
<p>A quick hack to see the arguments of the <a href="http://www.rdocumentation.org/packages/base/functions/sample"><code>sample()</code></a> function is the <a href="http://www.rdocumentation.org/packages/base/functions/args"><code>args()</code></a> function. Try it out in the console:</p>
<pre><code>args(sample)
</code></pre>
<p>In the next exercises, you'll be learning how to use the <a href="http://www.rdocumentation.org/packages/base/functions/mean"><code>mean()</code></a> function with increasing complexity. The first thing you'll have to do is get acquainted with the <a href="http://www.rdocumentation.org/packages/base/functions/mean"><code>mean()</code></a> function.</p>
</div>

<li>Consult the documentation on the <a href="http://www.rdocumentation.org/packages/base/functions/mean"><code>mean()</code></a> function: <code>?mean</code> or <code>help(mean)</code>.</li>

```r
# Consult the documentation on the mean() function
?mean
help(mean)

```
<li>Inspect the arguments of the <a href="http://www.rdocumentation.org/packages/base/functions/mean"><code>mean()</code></a> function using the <a href="http://www.rdocumentation.org/packages/base/functions/args"><code>args()</code></a> function.</li>

```r
# Inspect the arguments of the mean() function
args(mean)
#> function (x, ...) 
#> NULL
```

<p class="">Great! That wasn't too hard, was it? Take a look at the documentation and head over to the next exercise.
</p>

### Use a function


<div class>
<p>The documentation on the <a href="http://www.rdocumentation.org/packages/base/functions/mean"><code>mean()</code></a> function gives us quite some information:</p>
<ul>
<li>The <a href="http://www.rdocumentation.org/packages/base/functions/mean"><code>mean()</code></a> function computes the arithmetic mean.</li>

<li>The most general method takes multiple arguments: <code>x</code> and <code>...</code>.</li>

<li>The <code>x</code> argument should be a vector containing numeric, logical or time-related information.</li>

</ul>
<p>Remember that R can match arguments both by position and by name. Can you still remember the difference? You'll find out in this exercise!</p>
<p>Once more, you'll be working with the view counts of your social network profiles for the past 7 days. These are stored in the <code>linkedin</code> and <code>facebook</code> vectors and have already been created for you.</p>
</div>

```r
# The linkedin and facebook vectors have already been created for you
linkedin <- c(16, 9, 13, 5, 2, 17, 14)
facebook <- c(17, 7, 5, 16, 8, 13, 14)
```

<li>Calculate the average number of views for both <code>linkedin</code> and <code>facebook</code> and assign the result to <code>avg_li</code> and <code>avg_fb</code>, respectively. Experiment with different types of argument matching!</li>

```r
# Calculate average number of views
avg_li <- mean(x = linkedin)
avg_fb <- mean(facebook)

```
<li>Print out both <code>avg_li</code> and <code>avg_fb</code>.</li>

```r
# Inspect avg_li and avg_fb
avg_li
#> [1] 10.85714
avg_fb
#> [1] 11.42857
```

<p class="">Nice! I'm sure you've already called more advanced R functions in your history as a programmer. Now you also know what actually happens under the hood ;-)
</p>

### Use a function (2)


<div class>
<p>Check the documentation on the <a href="http://www.rdocumentation.org/packages/base/functions/mean"><code>mean()</code></a> function again:</p>
<pre><code>?mean
</code></pre>
<p>The Usage section of the documentation includes two versions of the <a href="http://www.rdocumentation.org/packages/base/functions/mean"><code>mean()</code></a> function. The first usage,</p>
<pre><code>mean(x, ...)
</code></pre>
<p>is the most general usage of the mean function. The 'Default S3 method', however, is:</p>
<pre><code>mean(x, trim = 0, na.rm = FALSE, ...)
</code></pre>
<p>The <code>...</code> is called the ellipsis. It is a way for R to pass arguments along without the function having to name them explicitly. The ellipsis will be treated in more detail in future courses.</p>
<p>For the remainder of this exercise, just work with the second usage of the mean function. Notice that both <code>trim</code> and <code>na.rm</code> have default values. This makes them <strong>optional arguments</strong>.</p>
</div>

<li>Calculate the mean of the element-wise sum of <code>linkedin</code> and <code>facebook</code> and store the result in a variable <code>avg_sum</code>.</li>

```r
# Calculate the mean of the sum
avg_sum <- mean(linkedin + facebook)

```
<li>Calculate the mean once more, but this time set the <code>trim</code> argument equal to 0.2 and assign the result to <code>avg_sum_trimmed</code>.</li>

```r
# Calculate the trimmed mean of the sum
avg_sum_trimmed <- mean(linkedin + facebook, trim = 0.2)

```
<li>Print out both <code>avg_sum</code> and <code>avg_sum_trimmed</code>; can you spot the difference?</li>

```r
# Inspect both new variables
avg_sum
#> [1] 22.28571
avg_sum_trimmed
#> [1] 22.6
```

<p class="">Nice! When the <code>trim</code> argument is not zero, it chops off a fraction (equal to <code>trim</code>) of the vector you pass as argument <code>x</code>.
</p>

### Use a function (3)


<div class>
<p>In the video, Filip guided you through the example of specifying arguments of the <a href="http://www.rdocumentation.org/packages/stats/functions/sd"><code>sd()</code></a> function. The <a href="http://www.rdocumentation.org/packages/stats/functions/sd"><code>sd()</code></a> function has an optional argument, <code>na.rm</code> that specified whether or not to remove missing values from the input vector before calculating the standard deviation.</p>
<p>If you've had a good look at the documentation, you'll know by now that the <a href="http://www.rdocumentation.org/packages/base/functions/mean"><code>mean()</code></a> function also has this argument, <code>na.rm</code>, and it does the exact same thing. By default, it is set to <code>FALSE</code>, as the Usage of the default S3 method shows:</p>
<pre><code>mean(x, trim = 0, na.rm = FALSE, ...)
</code></pre>
<p>Let's see what happens if your vectors <code>linkedin</code> and <code>facebook</code> contain missing values (<code>NA</code>).</p>
</div>

```r
# The linkedin and facebook vectors have already been created for you
linkedin <- c(16, 9, 13, 5, NA, 17, 14)
facebook <- c(17, NA, 5, 16, 8, 13, 14)
```

<li>Calculate the average number of LinkedIn profile views, without specifying any optional arguments. Simply print the result to the console.</li>

```r
# Basic average of linkedin
mean(linkedin)
#> [1] NA
```
<li>Calculate the average number of LinkedIn profile views, but this time tell R to strip missing values from the input vector.</li>

```r
# Advanced average of linkedin
mean(linkedin, na.rm = TRUE)
#> [1] 12.33333
```

<p class="">Awesome! Up to the next exercise!
</p>

### Functions inside functions


<div class>
<p>You already know that R functions return objects that you can then use somewhere else. This makes it easy to use functions inside functions, as you've seen before:</p>
<pre><code>speed &lt;- 31
print(paste("Your speed is", speed))
</code></pre>
<p>Notice that both the <a href="http://www.rdocumentation.org/packages/base/functions/print"><code>print()</code></a> and <a href="http://www.rdocumentation.org/packages/base/functions/paste"><code>paste()</code></a> functions use the ellipsis - <code>...</code> - as an argument. Can you figure out how they're used?</p>
</div>
<div class="exercise--instructions__content"><p>Use <code>abs()</code> on <code>linkedin - facebook</code> to get the absolute differences between the daily Linkedin and Facebook profile views. Place the call to <code>abs()</code> <em>inside</em> <code>mean()</code> to calculate the Mean Absolute Deviation. In the <code>mean()</code> call, make sure to specify <code>na.rm</code> to treat missing values correctly!</p></div>

```r
# Calculate the mean absolute deviation
mean(abs(linkedin - facebook), na.rm = TRUE)
#> [1] 4.8
```

<p class="">Excellent! Proceed to the next exercise.
</p>

### Required, or optional?


<div class>
<p>By now, you will probably have a good understanding of the difference between required and optional arguments. Let's refresh this difference by having one last look at the <a href="http://www.rdocumentation.org/packages/base/functions/mean"><code>mean()</code></a> function:</p>
<pre><code>mean(x, trim = 0, na.rm = FALSE, ...)
</code></pre>
<p><code>x</code> is required; if you do not specify it, R will throw an error. <code>trim</code> and <code>na.rm</code> are optional arguments: they have a default value which is used if the arguments are not explicitly specified.</p>
<p>Which of the following statements about the <a href="http://www.rdocumentation.org/packages/utils/functions/read.table"><code>read.table()</code></a> function are true?</p>
<ol>
<li>
<code>header</code>, <code>sep</code> and <code>quote</code> are all optional arguments.</li>

<li>
<code>row.names</code> and <code>fileEncoding</code> don't have default values.</li>

<li>
<code>read.table("myfile.txt", "-", TRUE)</code> will throw an error.</li>

<li>
<code>read.table("myfile.txt", sep = "-", header = TRUE)</code> will throw an error.</li>

</ol>
</div>

<ul>
<strong><li><div class="dc-input-radio__text">(1) and (3)</div></li></strong>
<li><div class="dc-input-radio__text">(2) and (4)</div></li>
<li><div class="dc-input-radio__text">(1), (2), and (3)</div></li>
<li><div class="dc-input-radio__text">(1), (2), and (4)</div></li>
</ul>

<p class="">Great! Using functions that are already available in R is pretty straightforward, but how about writing your own functions to supercharge your R programs? The next video will tell you how.
</p>

## Writing Functions



### Write your own function


<div class>
<p>Wow, things are getting serious… you're about to write your own function! Before you have a go at it, have a look at the following function template:</p>
<pre><code>my_fun &lt;- function(arg1, arg2) {
  body
}
</code></pre>
<p>Notice that this recipe uses the assignment operator (<code>&lt;-</code>) just as if you were assigning a vector to a variable for example. This is not a coincidence. Creating a function in R basically is the assignment of a function object to a variable! In the recipe above, you're creating a new R variable <code>my_fun</code>, that becomes available in the workspace as soon as you execute the definition. From then on, you can use the <code>my_fun</code> as a function.</p>
</div>

<li>Create a function <code>pow_two()</code>: it takes one argument and returns that number squared (that number times itself).</li>

```r
# Create a function pow_two()
pow_two <- function(x) {
  x ^ 2
}

```
<li>Call this newly defined function with <code>12</code> as input.</li>

```r
# Use the function
pow_two(12)
#> [1] 144
```
<li>Next, create a function <code>sum_abs()</code>, that takes two arguments and returns the sum of the absolute values of both arguments.</li>

```r
# Create a function sum_abs()
sum_abs <- function(x, y) {
  abs(x) + abs(y)
}

```
<li>Finally, call the function <code>sum_abs()</code> with arguments <code>-2</code> and <code>3</code> afterwards.</li>

```r
# Use the function
sum_abs(-2, 3)
#> [1] 5
```

<p class="">Great! Step it up a notch in the next exercise!
</p>

### Write your own function (2)


<div class>
<p>There are situations in which your function does not require an input. Let's say you want to write a function that gives us the random outcome of throwing a fair die:</p>
<pre><code>throw_die &lt;- function() {
  number &lt;- sample(1:6, size = 1)
  number
}

throw_die()
</code></pre>
<p>Up to you to code a function that doesn't take any arguments!</p>
</div>

<li>Define a function, <code>hello()</code>. It prints out "Hi there!" and returns <code>TRUE</code>. It has no arguments.</li>

```r
# Define the function hello()
hello <- function() {
  print("Hi there!")
  TRUE
}

```
<li>Call the function <code>hello()</code>, without specifying arguments of course.</li>

```r
# Call the function hello()
hello()
#> [1] "Hi there!"
#> [1] TRUE
```

<p class="">Truly impressive! Head over to the next exercise.
</p>

### Write your own function (3)


<div class>
<p>Do you still remember the difference between an argument with and without default values? The usage section in the <code>sd()</code> documentation shows the following information:</p>
<pre><code>sd(x, na.rm = FALSE)
</code></pre>
<p>This tells us that <code>x</code> has to be defined for the <code>sd()</code> function to be called correctly, however, <code>na.rm</code> already has a default value. Not specifying this argument won't cause an error.</p>
<p>You can define default argument values in your own R functions as well. You can use the following recipe to do so:</p>
<pre><code>my_fun &lt;- function(arg1, arg2 = val2) {
  body
}
</code></pre>
<p>The editor on the right already includes an extended version of the <code>pow_two()</code> function from before. Can you finish it?</p>
</div>

<li>Add an optional argument, named <code>print_info</code>, that is <code>TRUE</code> by default.</li>

<li>Wrap an <code>if</code> construct around the <code>print()</code> function: this function should only be executed if <code>print_info</code> is <code>TRUE</code>.</li>

```r
# Finish the pow_two() function
pow_two <- function(x, print_info = TRUE) {
  y <- x ^ 2
  if (print_info) {
    print(paste(x, "to the power two equals", y))
  }
  return(y)
}

```
<li>Feel free to experiment with the <code>pow_two()</code> function you've just coded.</li>

```r
# Some calls of the pow_two() function
pow_two(5)
#> [1] "5 to the power two equals 25"
#> [1] 25
pow_two(5, FALSE)
#> [1] 25
pow_two(5, TRUE)
#> [1] "5 to the power two equals 25"
#> [1] 25
```

<p class="">Wonderful! Have you tried calling this <code>pow_two()</code> function? Try <code>pow_two(5)</code>, <code>pow_two(5, TRUE)</code> and <code>pow_two(5, FALSE)</code>. Which ones give different results?
</p>

### Function scoping


<div class>
<p>An issue that Filip did not discuss in the video is function scoping. It implies that variables that are defined inside a function are not accessible outside that function. Try running the following code and see if you understand the results:</p>
<pre><code>pow_two &lt;- function(x) {
  y &lt;- x ^ 2
  return(y)
}
pow_two(4)
y
x
</code></pre>
<p><code>y</code> was defined inside the <code>pow_two()</code> function and therefore it is not accessible outside of that function. This is also true for the function's arguments of course - <code>x</code> in this case.</p>
<p>Which statement is correct about the following chunk of code? The function <code>two_dice()</code> is already available in the workspace.</p>
<pre><code>two_dice &lt;- function() {
  possibilities &lt;- 1:6
  dice1 &lt;- sample(possibilities, size = 1)
  dice2 &lt;- sample(possibilities, size = 1)
  dice1 + dice2
}
</code></pre>
</div>

<ul>
<li><div class="dc-input-radio__text">Executing <code>two_dice()</code> causes an error.</div></li>
<li><div class="dc-input-radio__text">Executing <code>res &lt;- two_dice()</code> makes the contents of <code>dice1</code> and <code>dice2</code> available outside the function.</div></li>
<strong><li><div class="dc-input-radio__text">Whatever the way of calling the <code>two_dice()</code> function, R won't have access to <code>dice1</code> and <code>dice2</code> outside the function.</div></li></strong>
</ul>

<div class="dc-input-radio__text">Whatever the way of calling the <code>two_dice()</code> function, R won't have access to <code>dice1</code> and <code>dice2</code> outside the function.</div>

### R passes arguments by value


<div class>
<p>The title gives it away already: R passes arguments by value. What does this mean? Simply put, it means that an R function cannot change the variable that you input to that function. Let's look at a simple example (try it in the console):</p>
<pre><code>triple &lt;- function(x) {
  x &lt;- 3*x
  x
}
a &lt;- 5
triple(a)
a
</code></pre>
<p>Inside the <code>triple()</code> function, the argument <code>x</code> gets overwritten with its value times three. Afterwards this new <code>x</code> is returned. If you call this function with a variable <code>a</code> set equal to 5, you obtain 15. But did the value of <code>a</code> change? If R were to pass <code>a</code> to <code>triple()</code> <em>by reference</em>, the override of the <code>x</code> <em>inside</em> the function would ripple through to the variable <code>a</code>, outside the function. However, R passes <em>by value</em>, so the R objects you pass to a function can never change unless you do an explicit assignment. <code>a</code> remains equal to 5, even after calling <code>triple(a)</code>.</p>
<p>Can you tell which one of the following statements is <u>false</u> about the following piece of code?</p>
<pre><code>increment &lt;- function(x, inc = 1) {
  x &lt;- x + inc
  x
}
count &lt;- 5
a &lt;- increment(count, 2)
b &lt;- increment(count)
count &lt;- increment(count, 2)
</code></pre>
</div>

<ul>
<li><div class="dc-input-radio__text"><code>a</code> and <code>b</code> equal 7 and 6 respectively after executing this code block.</div></li>
<li><div class="dc-input-radio__text">After the first call of <code>increment()</code>, where <code>a</code> is defined, <code>a</code> equals 7 and <code>count</code> equals 5.</div></li>
<strong><li><div class="dc-input-radio__text">In the end, <code>count</code> will equal 10.</div></li></strong>
<li><div class="dc-input-radio__text">In the last expression, the value of <code>count</code> was actually changed because of the explicit assignment.</div></li>
</ul>

<p class="">Well done! Given that R passes arguments <i>by value</i> and not <i>by reference</i>, the value of <code>count</code> is not changed after the first two calls of <code>increment()</code>. Only in the final expression, where <code>count</code> is re-assigned explicitly, does the value of <code>count</code> change.
</p>

### R you functional?


<div class>
<p>Now that you've acquired some skills in defining functions with different types of arguments and return values, you should try to create more advanced functions. As you've noticed in the previous exercises, it's perfectly possible to add control-flow constructs, loops and even other functions to your function body.</p>
<p>Remember our social media example? The vectors <code>linkedin</code> and <code>facebook</code> are already defined in the workspace so you can get your hands dirty straight away. As a first step, you will be writing a function that can interpret a single value of this vector. In the next exercise, you will write another function that can handle an entire vector at once.</p>
</div>

```r
linkedin <- c(16, 9, 13, 5, 2, 17, 14)
facebook <- c(17, 7, 5, 16, 8, 13, 14)
```

<li>Finish the function definition for <code>interpret()</code>, that interprets the number of profile views on a single day:</li>

<li>The function takes one argument, <code>num_views</code>.</li>

<li>If <code>num_views</code> is greater than 15, the function prints out "You're popular!" to the console and returns <code>num_views</code>.</li>

<li>Else, the function prints out "Try to be more visible!" and returns 0.</li>

```r
# The linkedin and facebook vectors have already been created for you

# Define the interpret function
interpret <- function(num_views) {
  if (num_views > 15) {
    print("You're popular!")
    return(num_views)
  } else {
    print("Try to be more visible!")
    return(0)
  }
}

```
<li>Finally, call the <code>interpret()</code> function twice: on the first value of the <code>linkedin</code> vector and on the second element of the <code>facebook</code> vector.</li>

```r
# Call the interpret function twice
interpret(linkedin[1])
#> [1] "You're popular!"
#> [1] 16
interpret(facebook[2])
#> [1] "Try to be more visible!"
#> [1] 0
```

<p class="">Funkadelic! The annoying thing here is that <code>interpret()</code> only takes one argument. Proceed to the next exercise to implement something more useful.
</p>

### R you functional? (2)


<div class><p>A possible implementation of the <code>interpret()</code> function has been provided for you. In this exercise you'll be writing another function that will use the <code>interpret()</code> function to interpret <em>all</em> the data from your daily profile views inside a vector. Furthermore, your function will return the sum of views on popular days, if asked for. A <code>for</code> loop is ideal for iterating over all the vector elements. The ability to return the sum of views on popular days is something you can code through a function argument with a default value.</p></div>
<div class="exercise--instructions__content">
<p>Finish the template for the <code>interpret_all()</code> function:</p>

<li>Make <code>return_sum</code> an optional argument, that is <code>TRUE</code> by default.</li>

<li>Inside the <code>for</code> loop, iterate over all <code>views</code>: on every iteration, add the result of <code>interpret(v)</code> to <code>count</code>. Remember that <code>interpret(v)</code> returns <code>v</code> for popular days, and <code>0</code> otherwise. At the same time, <code>interpret(v)</code> will also do some printouts.</li>

<li>Finish the <code>if</code> construct:</li>

<li>If <code>return_sum</code> is <code>TRUE</code>, return <code>count</code>.</li>

<li>Else, return <code>NULL</code>.</li>

```r
# Define the interpret_all() function
# views: vector with data to interpret
# return_sum: return total number of views on popular days?
interpret_all <- function(views, return_sum = TRUE) {
  count <- 0

  for (v in views) {
    count <- count + interpret(v)
  }

  if (return_sum) {
    return(count)
  } else {
    return(NULL)
  }
}

```

<p>Call this newly defined function on both <code>linkedin</code> and <code>facebook</code>.</p>

```r
# Call the interpret_all() function on both linkedin and facebook
interpret_all(linkedin)
#> [1] "You're popular!"
#> [1] "Try to be more visible!"
#> [1] "Try to be more visible!"
#> [1] "Try to be more visible!"
#> [1] "Try to be more visible!"
#> [1] "You're popular!"
#> [1] "Try to be more visible!"
#> [1] 33
interpret_all(facebook)
#> [1] "You're popular!"
#> [1] "Try to be more visible!"
#> [1] "Try to be more visible!"
#> [1] "You're popular!"
#> [1] "Try to be more visible!"
#> [1] "Try to be more visible!"
#> [1] "Try to be more visible!"
#> [1] 33
```

</div>

<p class="">Perfect! Have a look at the results; it appears that the sum of views on popular days are the same for Facebook and LinkedIn, what a coincidence! Your different social profiles must be fairly balanced ;-) Head over to the next video!
</p>

## R Packages



### Load an R Package


<div class>
<p>There are basically two extremely important functions when it comes down to R packages:</p>
<ul>
<li>
<a href="http://www.rdocumentation.org/packages/utils/functions/install.packages"><code>install.packages()</code></a>, which as you can expect, installs a given package.</li>

<li>
<a href="http://www.rdocumentation.org/packages/base/functions/library"><code>library()</code></a> which loads packages, i.e. attaches them to the search list on your R workspace.</li>

</ul>
<p>To install packages, you need administrator privileges. This means that <a href="http://www.rdocumentation.org/packages/utils/functions/install.packages"><code>install.packages()</code></a> will thus not work in the DataCamp interface. However, almost all CRAN packages are installed on our servers. You can load them with <a href="http://www.rdocumentation.org/packages/base/functions/library"><code>library()</code></a>.</p>
<p>In this exercise, you'll be learning how to load the <code>ggplot2</code> package, a powerful package for data visualization. You'll use it to create a plot of two variables of the <code>mtcars</code> data frame. The data has already been prepared for you in the workspace.</p>
<p>Before starting, execute the following commands in the console:</p>
<ul>
<li>
<code>search()</code>, to look at the currently attached packages and</li>

<li>
<code>qplot(mtcars$wt, mtcars$hp)</code>, to build a plot of two variables of the <code>mtcars</code> data frame.</li>

</ul>
<p>An error should occur, because you haven't loaded the <code>ggplot2</code> package yet!</p>
</div>

<li>To fix the error you saw in the console, <strong>load</strong> the <a href="http://www.rdocumentation.org/packages/ggplot2"><code>ggplot2</code></a> package. Make sure you are <em>loading</em> (and not <em>installing</em>) the package!</li>

```r
# Load the ggplot2 package
library("ggplot2")

```
<li>Now, retry calling the <a href="http://www.rdocumentation.org/packages/ggplot2/functions/qplot"><code>qplot()</code></a> function with the same arguments.</li>

```r
# Retry the qplot() function
qplot(mtcars$wt, mtcars$hp)

```

<img src="workflow-basics_files/figure-html/unnamed-chunk-116-1.png" width="672" />
<li>Finally, check out the currently attached packages again.</li>

```r
# Check out the currently attached packages again
search()
#>  [1] ".GlobalEnv"        "package:ggplot2"   "package:stats"    
#>  [4] "package:graphics"  "package:grDevices" "package:utils"    
#>  [7] "package:datasets"  "package:methods"   "Autoloads"        
#> [10] "package:base"
```

<p class="">Awesome! Notice how <code>search()</code> and <code>library()</code> are closely interconnected functions. Head over to the next exercise.
</p>

### Different ways to load a package


<div class>
<p>The <a href="http://www.rdocumentation.org/packages/base/functions/library"><code>library()</code></a> and <a href="http://www.rdocumentation.org/packages/base/functions/library"><code>require()</code></a> functions are not very picky when it comes down to argument types: both <code>library(rjson)</code> and <code>library("rjson")</code> work perfectly fine for loading a package.</p>
<p>Have a look at some more code chunks that (attempt to) load one or more packages:</p>
<pre><code># Chunk 1
library(data.table)
require(rjson)

# Chunk 2
library("data.table")
require(rjson)

# Chunk 3
library(data.table)
require(rjson, character.only = TRUE)

# Chunk 4
library(c("data.table", "rjson"))
</code></pre>
<p>Select the option that lists <u>all</u> of the chunks that do not generate an error. The console is yours to experiment in.</p>
</div>

<ul>
<li><div class="dc-input-radio__text">Only (1)</div></li>
<strong><li><div class="dc-input-radio__text">(1) and (2)</div></li></strong>
<li><div class="dc-input-radio__text">(1), (2) and (3)</div></li>
<li><div class="dc-input-radio__text">All of them are valid</div></li>
</ul>

<p class="">Great! Indeed, only chunk 1 and chunk 2 are correct. Can you figure out why the last two aren't valid? This exercise concludes the chapter on functions. Well done!
</p>

# The apply family

<p>Whenever you're using a for loop, you may want to revise your code to see whether you can use the lapply function instead. Learn all about this intuitive way of applying a function over a list or a vector, and how to use its variants, sapply and vapply.
  </p>
  
## lapply



### Use lapply with a built-in R function


<div class>
<p>Before you go about solving the exercises below, have a look at the documentation of the <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> function. The Usage section shows the following expression:</p>
<pre><code>lapply(X, FUN, ...)
</code></pre>
<p>To put it generally, <code>lapply</code> takes a vector or list <code>X</code>, and applies the function <code>FUN</code> to each of its members. If <code>FUN</code> requires additional arguments, you pass them after you've specified <code>X</code> and <code>FUN</code> (<code>...</code>). The output of <code>lapply()</code> is a list, the same length as <code>X</code>, where each element is the result of applying <code>FUN</code> on the corresponding element of <code>X</code>.</p>
<p>Now that you are truly brushing up on your data science skills, let's revisit some of the most relevant figures in data science history. We've compiled a vector of famous mathematicians/statisticians and the year they were born. Up to you to extract some information!</p>
</div>

<li>Have a look at the <a href="http://www.rdocumentation.org/packages/base/functions/strsplit"><code>strsplit()</code></a> calls, that splits the strings in <code>pioneers</code> on the <code>:</code> sign. The result, <code>split_math</code> is a list of 4 character vectors: the first vector element represents the name, the second element the birth year.</li>

```r
# The vector pioneers has already been created for you
pioneers <- c("GAUSS:1777", "BAYES:1702", "PASCAL:1623", "PEARSON:1857")

# Split names from birth year
split_math <- strsplit(pioneers, split = ":")

```
<li>Use <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> to convert the character vectors in <code>split_math</code> to lowercase letters: apply <a href="http://www.rdocumentation.org/packages/base/functions/chartr"><code>tolower()</code></a> on each of the elements in <code>split_math</code>. Assign the result, which is a list, to a new variable <code>split_low</code>.</li>

```r
# Convert to lowercase strings: split_low
split_low <- lapply(split_math, tolower)

```
<li>Finally, inspect the contents of <code>split_low</code> with <a href="http://www.rdocumentation.org/packages/utils/functions/str"><code>str()</code></a>.</li>

```r
# Take a look at the structure of split_low
str(split_low)
#> List of 4
#>  $ : chr [1:2] "gauss" "1777"
#>  $ : chr [1:2] "bayes" "1702"
#>  $ : chr [1:2] "pascal" "1623"
#>  $ : chr [1:2] "pearson" "1857"
```

<p class="">Great! Head over to the next exercise.
</p>

### Use lapply with your own function


<div class>
<p>As Filip explained in the instructional video, you can use <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> on your own functions as well. You just need to code a new function and make sure it is available in the workspace. After that, you can use the function inside <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> just as you did with base R functions.</p>
<p>In the previous exercise you already used <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> once to convert the information about your favorite pioneering statisticians to a list of vectors composed of two character strings. Let's write some code to select the names and the birth years separately.</p>
<p>The sample code already includes code that defined <code>select_first()</code>, that takes a vector as input and returns the first element of this vector.</p>
</div>

<li>Apply <code>select_first()</code> over the elements of <code>split_low</code> with <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> and assign the result to a new variable <code>names</code>.</li>

```r
# Code from previous exercise:
pioneers <- c("GAUSS:1777", "BAYES:1702", "PASCAL:1623", "PEARSON:1857")
split <- strsplit(pioneers, split = ":")
split_low <- lapply(split, tolower)

# Write function select_first()
select_first <- function(x) {
  x[1]
}

# Apply select_first() over split_low: names
names <- lapply(split_low, select_first)

```
<li>Next, write a function <code>select_second()</code> that does the exact same thing for the second element of an inputted vector.</li>

```r
# Write function select_second()
select_second <- function(x) {
  x[2]
}

```
<li>Finally, apply the <code>select_second()</code> function over <code>split_low</code> and assign the output to the variable <code>years</code>.</li>

```r
# Apply select_second() over split_low: years
years <- lapply(split_low, select_second)
```

<p class="">Nice one! Head over to the next exercise to learn about anonymous functions.
</p>

### lapply and anonymous functions


<div class>
<p>Writing your own functions and then using them inside <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> is quite an accomplishment! But defining functions to use them only once is kind of overkill, isn't it? That's why you can use so-called <strong>anonymous functions</strong> in R.</p>
<p>Previously, you learned that functions in R are objects in their own right. This means that they aren't automatically bound to a name. When you create a function, you can use the assignment operator to give the function a name. It's perfectly possible, however, to not give the function a name. This is called an anonymous function:</p>
<pre><code># Named function
triple &lt;- function(x) { 3 * x }

# Anonymous function with same implementation
function(x) { 3 * x }

# Use anonymous function inside lapply()
lapply(list(1,2,3), function(x) { 3 * x })
</code></pre>
<p><code>split_low</code> is defined for you.</p>
</div>

<li>Transform the first call of <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> such that it uses an anonymous function that does the same thing.</li>

```r
# split_low has been created for you
split_low
#> [[1]]
#> [1] "gauss" "1777" 
#> 
#> [[2]]
#> [1] "bayes" "1702" 
#> 
#> [[3]]
#> [1] "pascal" "1623"  
#> 
#> [[4]]
#> [1] "pearson" "1857"
```
<li>In a similar fashion, convert the second call of <code>lapply</code> to use an anonymous version of the <code>select_second()</code> function.</li>

<li>Remove both the definitions of <code>select_first()</code> and <code>select_second()</code>, as they are no longer useful.</li>

```r
# Transform: use anonymous function inside lapply
names <- lapply(split_low, function(x) { x[1] })




# Transform: use anonymous function inside lapply
years <- lapply(split_low, function(x) { x[2] })
```

<p class="">Great! Now, there's another way to solve the issue of using the <code>select_*()</code> functions only once: you can make a more generic function that can be used in more places. Find out more about this in the next exercise.
</p>

### Use lapply with additional arguments


<div class>
<p>In the video, the <code>triple()</code> function was transformed to the <code>multiply()</code> function to allow for a more generic approach. <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> provides a way to handle functions that require more than one argument, such as the <code>multiply()</code> function:</p>
<pre><code>multiply &lt;- function(x, factor) {
  x * factor
}
lapply(list(1,2,3), multiply, factor = 3)
</code></pre>
<p>On the right we've included a generic version of the select functions that you've coded earlier: <code>select_el()</code>. It takes a vector as its first argument, and an index as its second argument. It returns the vector's element at the specified index.</p>
</div>
<div class="exercise--instructions__content"><p>Use <code>lapply()</code> twice to call <code>select_el()</code> over all elements in <code>split_low</code>: once with the <code>index</code> equal to 1 and a second time with the index equal to 2. Assign the result to <code>names</code> and <code>years</code>, respectively.</p></div>

```r
# Definition of split_low
pioneers <- c("GAUSS:1777", "BAYES:1702", "PASCAL:1623", "PEARSON:1857")
split <- strsplit(pioneers, split = ":")
split_low <- lapply(split, tolower)

# Generic select function
select_el <- function(x, index) {
  x[index]
}

# Use lapply() twice on split_low: names and years
names <- lapply(split_low, select_el, index = 1)
years <- lapply(split_low, select_el, index = 2)
```

<p class="">Awesome! Your lapply skills are growing by the minute!
</p>

### Apply functions that return NULL


<div class>
<p>In all of the previous exercises, it was assumed that the functions that were applied over vectors and lists actually returned a meaningful result. For example, the <a href="http://www.rdocumentation.org/packages/base/functions/chartr"><code>tolower()</code></a> function simply returns the strings with the characters in lowercase. This won't always be the case. Suppose you want to display the structure of every element of a list. You could use the <a href="http://www.rdocumentation.org/packages/utils/functions/str"><code>str()</code></a> function for this, which returns <code>NULL</code>:</p>
<pre><code>lapply(list(1, "a", TRUE), str)
</code></pre>
<p>This call actually returns a list, the same size as the input list, containing all <code>NULL</code> values. On the other hand calling</p>
<pre><code>str(TRUE)
</code></pre>
<p>on its own prints only the structure of the logical to the console, not <code>NULL</code>. That's because <a href="http://www.rdocumentation.org/packages/utils/functions/str"><code>str()</code></a> uses <a href="http://www.rdocumentation.org/packages/base/functions/invisible"><code>invisible()</code></a> behind the scenes, which returns an <em>invisible copy</em> of the return value, <code>NULL</code> in this case. This prevents it from being printed when the result of <a href="http://www.rdocumentation.org/packages/utils/functions/str"><code>str()</code></a> is not assigned.</p>
<p>What will the following code chunk return (<code>split_low</code> is already available in the workspace)? Try to reason about the result before simply executing it in the console!</p>
<pre><code>lapply(split_low, function(x) {
  if (nchar(x[1]) &gt; 5) {
    return(NULL)
  } else {
    return(x[2])
  }
})
</code></pre>
</div>

<ul>
<li><div class="dc-input-radio__text"><code>list(NULL, NULL, "1623", "1857")</code></div></li>
<li><div class="dc-input-radio__text"><code>list("gauss", "bayes", NULL, NULL)</code></div></li>
<strong><li><div class="dc-input-radio__text"><code>list("1777", "1702", NULL, NULL)</code></div></li></strong>
<li><div class="dc-input-radio__text"><code>list("1777", "1702")</code></div></li>
</ul>

<p class="">Wonderful! Feel free to experiment some more with your code in the console. Did you notice that <code>lapply()</code> <i>always</i> returns a list, no matter the input? This can be kind of annoying. In the next video tutorial you'll learn about <code>sapply()</code> to solve this.
</p>

## sapply



### How to use sapply


<div class>
<p>You can use <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> similar to how you used <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a>. The first argument of <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> is the list or vector <code>X</code> over which you want to apply a function, <code>FUN</code>. Potential additional arguments to this function are specified afterwards (<code>...</code>):</p>
<pre><code>sapply(X, FUN, ...)
</code></pre>
<p>In the next couple of exercises, you'll be working with the variable <code>temp</code>, that contains temperature measurements for 7 days. <code>temp</code> is a list of length 7, where each element is a vector of length 5, representing 5 measurements on a given day. This variable has already been defined in the workspace: type <code>str(temp)</code> to see its structure.</p>
</div>

<li>Use <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> to calculate the minimum (built-in function <a href="http://www.rdocumentation.org/packages/base/functions/Extremes"><code>min()</code></a>) of the temperature measurements for every day.</li>

```r
# temp has already been defined in the workspace
temp=list(c(3,7,9,6,-1),
c(6,9,12,13,5),
c(4,8,3,-1,-3),
c(1,4,7,2,-2),
c(5,7,9,4,2),
c(-3,5,8,9,4),
c(3,6,9,4,1))
# Use lapply() to find each day's minimum temperature
lapply(temp, min)
#> [[1]]
#> [1] -1
#> 
#> [[2]]
#> [1] 5
#> 
#> [[3]]
#> [1] -3
#> 
#> [[4]]
#> [1] -2
#> 
#> [[5]]
#> [1] 2
#> 
#> [[6]]
#> [1] -3
#> 
#> [[7]]
#> [1] 1
```
<li>Do the same thing but this time with <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a>. See how the output differs.</li>

```r
# Use sapply() to find each day's minimum temperature
sapply(temp, min)
#> [1] -1  5 -3 -2  2 -3  1
```
<li>Use <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> to compute the the maximum (<a href="http://www.rdocumentation.org/packages/base/functions/Extremes"><code>max()</code></a>) temperature for each day.</li>

```r
# Use lapply() to find each day's maximum temperature
lapply(temp, max)
#> [[1]]
#> [1] 9
#> 
#> [[2]]
#> [1] 13
#> 
#> [[3]]
#> [1] 8
#> 
#> [[4]]
#> [1] 7
#> 
#> [[5]]
#> [1] 9
#> 
#> [[6]]
#> [1] 9
#> 
#> [[7]]
#> [1] 9
```
<li>Again, use <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> to solve the same question and see how <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> and <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> differ.</li>

```r
# Use sapply() to find each day's maximum temperature
sapply(temp, max)
#> [1]  9 13  8  7  9  9  9
```

<p class="">Nice! Can you tell the difference between the output of <code>lapply()</code> and <code>sapply()</code>? The former returns a list, while the latter returns a vector that is a simplified version of this list. Notice that this time, unlike in the cities example of the instructional video, the vector is not named.
</p>

### sapply with your own function


<div class>
<p>Like <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a>, <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> allows you to use self-defined functions and apply them over a vector or a list:</p>
<pre><code>sapply(X, FUN, ...)
</code></pre>
<p>Here, <code>FUN</code> can be one of R's built-in functions, but it can also be a function you wrote. This self-written function can be defined before hand, or can be inserted directly as an anonymous function.</p>
</div>

<li>Finish the definition of <code>extremes_avg()</code>: it takes a vector of temperatures and calculates the average of the minimum and maximum temperatures of the vector.</li>

```r
# temp is already defined in the workspace

# Finish function definition of extremes_avg
extremes_avg <- function(x) {
  ( min(x) + max(x) ) / 2
}

```
<li>Next, use this function inside <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> to apply it over the vectors inside <code>temp</code>.</li>

```r
# Apply extremes_avg() over temp using sapply()
sapply(temp, extremes_avg)
#> [1] 4.0 9.0 2.5 2.5 5.5 3.0 5.0
```
<li>Use the same function over <code>temp</code> with <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> and see how the outputs differ.</li>

```r
# Apply extremes_avg() over temp using lapply()
lapply(temp, extremes_avg)
#> [[1]]
#> [1] 4
#> 
#> [[2]]
#> [1] 9
#> 
#> [[3]]
#> [1] 2.5
#> 
#> [[4]]
#> [1] 2.5
#> 
#> [[5]]
#> [1] 5.5
#> 
#> [[6]]
#> [1] 3
#> 
#> [[7]]
#> [1] 5
```

<p class="">Great job! Of course, you could have solved this exercise using an anonymous function, but this would require you to use the code inside the definition of <code>extremes_avg()</code> twice. Duplicating code should be avoided as much as possible!
</p>

### sapply with function returning vector


<div class><p>In the previous exercises, you've seen how <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> simplifies the list that <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> would return by turning it into a vector. But what if the function you're applying over a list or a vector returns a vector of length greater than 1? If you don't remember from the video, don't waste more time in the valley of ignorance and head over to the instructions!</p></div>

<li>Finish the definition of the <code>extremes()</code> function. It takes a vector of numerical values and returns a vector containing the minimum and maximum values of a given vector, with the names "min" and "max", respectively.</li>

```r
# temp is already available in the workspace

# Create a function that returns min and max of a vector: extremes
extremes <- function(x) {
  c(min = min(x), max = max(x))
}

```
<li>Apply this function over the vector <code>temp</code> using <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a>.</li>

```r
# Apply extremes() over temp with sapply()
sapply(temp, extremes)
#>     [,1] [,2] [,3] [,4] [,5] [,6] [,7]
#> min   -1    5   -3   -2    2   -3    1
#> max    9   13    8    7    9    9    9
```
<li>Finally, apply this function over the vector <code>temp</code> using <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> as well.</li>

```r
# Apply extremes() over temp with lapply()
lapply(temp, extremes)
#> [[1]]
#> min max 
#>  -1   9 
#> 
#> [[2]]
#> min max 
#>   5  13 
#> 
#> [[3]]
#> min max 
#>  -3   8 
#> 
#> [[4]]
#> min max 
#>  -2   7 
#> 
#> [[5]]
#> min max 
#>   2   9 
#> 
#> [[6]]
#> min max 
#>  -3   9 
#> 
#> [[7]]
#> min max 
#>   1   9
```

<p class="">Wonderful! Have a final look at the console and see how <code>sapply()</code> did a great job at simplifying the rather uninformative 'list of vectors' that <code>lapply()</code> returns. It actually returned a nicely formatted matrix!
</p>

### sapply can't simplify, now what?


<div class>
<p>It seems like we've hit the jackpot with <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a>. On all of the examples so far, <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> was able to nicely simplify the rather bulky output of <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a>. But, as with life, there are things you can't simplify. How does <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> react?</p>
<p>We already created a function, <code>below_zero()</code>, that takes a vector of numerical values and returns a vector that only contains the values that are strictly below zero.</p>
</div>

<li>Apply <code>below_zero()</code> over <code>temp</code> using <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> and store the result in <code>freezing_s</code>.</li>

```r
# temp is already prepared for you in the workspace

# Definition of below_zero()
below_zero <- function(x) {
  return(x[x < 0])
}

# Apply below_zero over temp using sapply(): freezing_s
freezing_s <- sapply(temp, below_zero)

```
<li>Apply <code>below_zero()</code> over <code>temp</code> using <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a>. Save the resulting list in a variable <code>freezing_l</code>.</li>

```r
# Apply below_zero over temp using lapply(): freezing_l
freezing_l <- lapply(temp, below_zero)

```
<li>Compare <code>freezing_s</code> to <code>freezing_l</code> using the <a href="http://www.rdocumentation.org/packages/base/functions/identical"><code>identical()</code></a> function.</li>

```r
# Are freezing_s and freezing_l identical?
identical(freezing_s, freezing_l)
#> [1] TRUE
```

<p class="">Nice one! Given that the length of the output of <code>below_zero()</code> changes for different input vectors, <code>sapply()</code> is not able to nicely convert the output of <code>lapply()</code> to a nicely formatted matrix. Instead, the output values of <code>sapply()</code> and <code>lapply()</code> are exactly the same, as shown by the <code>TRUE</code> output of <code>identical()</code>.
</p>

### sapply with functions that return NULL


<div class>
<p>You already have some apply tricks under your sleeve, but you're surely hungry for some more, aren't you? In this exercise, you'll see how <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> reacts when it is used to apply a function that returns <code>NULL</code> over a vector or a list. </p>
<p>A function <code>print_info()</code>, that takes a vector and prints the average of this vector, has already been created for you. It uses the <a href="http://www.rdocumentation.org/packages/base/functions/cat"><code>cat()</code></a> function.</p>
</div>

<li>Apply <code>print_info()</code> over the contents of <code>temp</code> with <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a>.</li>

```r
# temp is already available in the workspace

# Definition of print_info()
print_info <- function(x) {
  cat("The average temperature is", mean(x), "\n")
}

# Apply print_info() over temp using sapply()
sapply(temp, print_info)
#> The average temperature is 4.8 
#> The average temperature is 9 
#> The average temperature is 2.2 
#> The average temperature is 2.4 
#> The average temperature is 5.4 
#> The average temperature is 4.6 
#> The average temperature is 4.6
#> [[1]]
#> NULL
#> 
#> [[2]]
#> NULL
#> 
#> [[3]]
#> NULL
#> 
#> [[4]]
#> NULL
#> 
#> [[5]]
#> NULL
#> 
#> [[6]]
#> NULL
#> 
#> [[7]]
#> NULL
```
<li>Repeat this process with <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a>. Do you notice the difference?</li>

```r
# Apply print_info() over temp using lapply()
lapply(temp, print_info)
#> The average temperature is 4.8 
#> The average temperature is 9 
#> The average temperature is 2.2 
#> The average temperature is 2.4 
#> The average temperature is 5.4 
#> The average temperature is 4.6 
#> The average temperature is 4.6
#> [[1]]
#> NULL
#> 
#> [[2]]
#> NULL
#> 
#> [[3]]
#> NULL
#> 
#> [[4]]
#> NULL
#> 
#> [[5]]
#> NULL
#> 
#> [[6]]
#> NULL
#> 
#> [[7]]
#> NULL
```

<p class="">Great! Notice here that, quite surprisingly, <code>sapply()</code> does not simplify the list of <code>NULL's</code>. That's because the 'vector-version' of a list of <code>NULL</code>'s would simply be a <code>NULL</code>, which is no longer a vector with the same length as the input. Proceed to the next exercise.
</p>

### Reverse engineering sapply


<div class>
<pre><code>sapply(list(runif (10), runif (10)), 
       function(x) c(min = min(x), mean = mean(x), max = max(x)))
</code></pre>
<p>Without going straight to the console to run the code, try to reason through which of the following statements are correct and why.</p>
<p>(1) <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> can't simplify the result that <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>lapply()</code></a> would return, and thus returns a list of vectors.<br>
(2) This code generates a matrix with 3 rows and 2 columns.<br>
(3) The function that is used inside <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> is anonymous.<br>
(4) The resulting data structure does not contain any names.  </p>
<p>Select the option that lists <u>all</u> correct statements.</p>
</div>

<ul>
<li><div class="dc-input-radio__text">(1) and (3)</div></li>
<strong><li><div class="dc-input-radio__text">(2) and (3)</div></li></strong>
<li><div class="dc-input-radio__text">(1) and (4)</div></li>
<li><div class="dc-input-radio__text">(2), (3) and (4)</div></li>
</ul>

<p class="">Great! This concludes the exercise set on <code>sapply()</code>. Head over to another video to learn all about <code>vapply()</code>!
</p>

## vapply



### Use vapply


<div class>
<p>Before you get your hands dirty with the third and last apply function that you'll learn about in this intermediate R course, let's take a look at its syntax. The function is called <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>vapply()</code></a>, and it has the following syntax:</p>
<pre><code>vapply(X, FUN, FUN.VALUE, ..., USE.NAMES = TRUE)
</code></pre>
<p>Over the elements inside <code>X</code>, the function <code>FUN</code> is applied. The <code>FUN.VALUE</code> argument expects a template for the return argument of this function <code>FUN</code>. <code>USE.NAMES</code> is <code>TRUE</code> by default; in this case <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>vapply()</code></a> tries to generate a named array, if possible.</p>
<p>For the next set of exercises, you'll be working on the <code>temp</code> list again, that contains 7 numerical vectors of length 5. We also coded a function <code>basics()</code> that takes a vector, and returns a named vector of length 3, containing the minimum, mean and maximum value of the vector respectively.</p>
</div>

<li>Apply the function <code>basics()</code> over the list of temperatures, <code>temp</code>, using <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>vapply()</code></a>. This time, you can use <code>numeric(3)</code> to specify the <code>FUN.VALUE</code> argument.</li>

```r
# temp is already available in the workspace

# Definition of basics()
basics <- function(x) {
  c(min = min(x), mean = mean(x), max = max(x))
}

# Apply basics() over temp using vapply()
vapply(temp, basics, numeric(3))
#>      [,1] [,2] [,3] [,4] [,5] [,6] [,7]
#> min  -1.0    5 -3.0 -2.0  2.0 -3.0  1.0
#> mean  4.8    9  2.2  2.4  5.4  4.6  4.6
#> max   9.0   13  8.0  7.0  9.0  9.0  9.0
```

<p class="">Perfect! Notice how, just as with <code>sapply()</code>, <code>vapply()</code> neatly transfers the names that you specify in the <code>basics()</code> function to the row names of the matrix that it returns.
</p>

### Use vapply (2)


<div class>
<p>So far you've seen that <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>vapply()</code></a> mimics the behavior of <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> if everything goes according to plan. But what if it doesn't? </p>
<p>In the video, Filip showed you that there are cases where the structure of the output of the function you want to apply, <code>FUN</code>, does not correspond to the template you specify in <code>FUN.VALUE</code>. In that case, <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>vapply()</code></a> will throw an error that informs you about the misalignment between expected and actual output.</p>
</div>

<li>Inspect the pre-loaded code and try to run it. If you haven't changed anything, an error should pop up. That's because <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>vapply()</code></a> still expects <code>basics()</code> to return a vector of length 3. The error message gives you an indication of what's wrong.</li>

```r
# temp is already available in the workspace

# Definition of the basics() function
basics <- function(x) {
  c(min = min(x), mean = mean(x), median = median(x), max = max(x))
}

# Fix the error:
#vapply(temp, basics, numeric(3))
```
<li>Try to fix the error by editing the <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>vapply()</code></a> command.</li>

```r
# temp is already available in the workspace

# Definition of the basics() function
basics <- function(x) {
  c(min = min(x), mean = mean(x), median = median(x), max = max(x))
}

# Fix the error:
vapply(temp, basics, numeric(4))
#>        [,1] [,2] [,3] [,4] [,5] [,6] [,7]
#> min    -1.0    5 -3.0 -2.0  2.0 -3.0  1.0
#> mean    4.8    9  2.2  2.4  5.4  4.6  4.6
#> median  6.0    9  3.0  2.0  5.0  5.0  4.0
#> max     9.0   13  8.0  7.0  9.0  9.0  9.0
```

<p class="">Great job! Head over to the next exercise.
</p>

### From sapply to vapply


<div class><p>As highlighted before, <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>vapply()</code></a> can be considered a more robust version of <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a>, because you explicitly restrict the output of the function you want to apply. Converting your <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> expressions in your own R scripts to <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>vapply()</code></a> expressions is therefore a good practice (and also a breeze!).</p></div>
<div class="exercise--instructions__content"><p>Convert all the <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>sapply()</code></a> expressions on the right to their <a href="http://www.rdocumentation.org/packages/base/functions/lapply"><code>vapply()</code></a> counterparts. Their results should be exactly the same; you're only adding robustness. You'll need the templates <code>numeric(1)</code> and <code>logical(1)</code>.</p></div>

```r
# temp is already defined in the workspace

# Convert to vapply() expression
vapply(temp, max, numeric(1))
#> [1]  9 13  8  7  9  9  9

# Convert to vapply() expression
vapply(temp, function(x, y) { mean(x) > y }, logical(1), y = 5)
#> [1] FALSE  TRUE FALSE FALSE  TRUE FALSE FALSE
```

<p class="">Great! You've got no more excuses to use <code>sapply()</code> in the future!
</p>

# Utilities

<p>Mastering R programming is not only about understanding its programming concepts. Having a solid understanding of a wide range of R functions is also important. This chapter introduces you to many useful functions for data structure manipulation, regular expressions, and working with times and dates.
  </p>
  
## Useful Functions



### Mathematical utilities


<div class>
<p>Have another look at some useful math functions that R features:</p>
<ul>
<li>
<a href="http://www.rdocumentation.org/packages/base/functions/MathFun"><code>abs()</code></a>: Calculate the absolute value.</li>

<li>
<a href="http://www.rdocumentation.org/packages/base/functions/sum"><code>sum()</code></a>: Calculate the sum of all the values in a data structure.</li>

<li>
<a href="http://www.rdocumentation.org/packages/base/functions/mean"><code>mean()</code></a>: Calculate the arithmetic mean.</li>

<li>
<a href="http://www.rdocumentation.org/packages/base/functions/round"><code>round()</code></a>: Round the values to 0 decimal places by default. Try out <code>?round</code> in the console for variations of <a href="http://www.rdocumentation.org/packages/base/functions/round"><code>round()</code></a> and ways to change the number of digits to round to.</li>

</ul>
<p>As a data scientist in training, you've estimated a regression model on the sales data for the past six months. After evaluating your model, you see that the training error of your model is quite regular, showing both positive and negative values. A vector <code>errors</code> containing the error values has been pre-defined for you.</p>
</div>
<div class="exercise--instructions__content"><p>Calculate the sum of the absolute rounded values of the training errors. You can work in parts, or with a single one-liner. There's no need to store the result in a variable, just have R print it.</p></div>

```r
# The errors vector has already been defined for you
errors <- c(1.9, -2.6, 4.0, -9.5, -3.4, 7.3)

# Sum of absolute rounded values of errors
sum(abs(round(errors)))
#> [1] 29
```

<p class="">Great! Head over to the next exercise.
</p>

### Find the error


<div class>
<p>We went ahead and pre-loaded some code for you, but there's still an error. Can you trace it and fix it?</p>
<p>In times of despair, help with functions such as <a href="http://www.rdocumentation.org/packages/base/functions/sum"><code>sum()</code></a> and <a href="http://www.rdocumentation.org/packages/base/functions/rev"><code>rev()</code></a> are a single command away; simply execute the code <code>?sum</code> and <code>?rev</code>.</p>
</div>
<div class="exercise--instructions__content"><p>Fix the error by <em>including</em> code on the last line. Remember: you want to call <a href="http://www.rdocumentation.org/packages/base/functions/mean"><code>mean()</code></a> only once!</p></div>

```r
# Don't edit these two lines
vec1 <- c(1.5, 2.5, 8.4, 3.7, 6.3)
vec2 <- rev(vec1)

# Fix the error
#mean(abs(vec1), abs(vec2))
mean(c(abs(vec1), abs(vec2)))
#> [1] 4.48
```

<p class="">Nice work! If you check out the documentation of <code>mean()</code>, you'll see that only the first argument, <code>x</code>, should be a vector. If you also specify a second argument, R will match the arguments by position and expect a specification of the <code>trim</code> argument. Therefore, merging the two vectors is a must!
</p>

### Data Utilities


<div class>
<p>R features a bunch of functions to juggle around with data structures::</p>
<ul>
<li>
<a href="http://www.rdocumentation.org/packages/base/functions/seq"><code>seq()</code></a>: Generate sequences, by specifying the <code>from</code>, <code>to</code>, and <code>by</code> arguments.</li>

<li>
<a href="http://www.rdocumentation.org/packages/base/functions/rep"><code>rep()</code></a>: Replicate elements of vectors and lists.</li>

<li>
<a href="http://www.rdocumentation.org/packages/base/functions/sort"><code>sort()</code></a>: Sort a vector in ascending order. Works on numerics, but also on character strings and logicals.</li>

<li>
<a href="http://www.rdocumentation.org/packages/base/functions/rev"><code>rev()</code></a>: Reverse the elements in a data structures for which reversal is defined.</li>

<li>
<a href="http://www.rdocumentation.org/packages/utils/functions/str"><code>str()</code></a>: Display the structure of any R object.</li>

<li>
<a href="http://www.rdocumentation.org/packages/base/functions/append"><code>append()</code></a>: Merge vectors or lists.</li>

<li>
<code>is.*()</code>: Check for the class of an R object.</li>

<li>
<code>as.*()</code>: Convert an R object from one class to another.</li>

<li>
<a href="http://www.rdocumentation.org/packages/base/functions/unlist"><code>unlist()</code></a>: Flatten (possibly embedded) lists to produce a vector.</li>

</ul>
<p>Remember the social media profile views data? Your LinkedIn and Facebook view counts for the last seven days have been pre-defined as lists.</p>
</div>

<li>Convert both <code>linkedin</code> and <code>facebook</code> lists to a vector, and store them as <code>li_vec</code> and <code>fb_vec</code> respectively.</li>

```r
# The linkedin and facebook lists have already been created for you
linkedin <- list(16, 9, 13, 5, 2, 17, 14)
facebook <- list(17, 7, 5, 16, 8, 13, 14)

# Convert linkedin and facebook to a vector: li_vec and fb_vec
li_vec <- unlist(linkedin)
fb_vec <- unlist(facebook)

```
<li>Next, append <code>fb_vec</code> to the <code>li_vec</code> (Facebook data comes last). Save the result as <code>social_vec</code>.</li>

```r
# Append fb_vec to li_vec: social_vec
social_vec <- append(li_vec, fb_vec)

```
<li>Finally, sort <code>social_vec</code> <em>from high to low</em>. Print the resulting vector.</li>

```r
# Sort social_vec
sort(social_vec, decreasing = TRUE)
#>  [1] 17 17 16 16 14 14 13 13  9  8  7  5  5  2
```

<p class="">Wonderful! These instructions required you to solve this challenge in a step-by-step approach. If you're comfortable with the functions, you can combine some of these steps into powerful one-liners.
</p>

### Find the error (2)


<div class><p>Just as before, let's switch roles. It's up to you to see what unforgivable mistakes we've made. Go fix them!</p></div>
<div class="exercise--instructions__content"><p>Correct the expression. Make sure that your fix still uses the functions <a href="http://www.rdocumentation.org/packages/base/functions/rep"><code>rep()</code></a> and <a href="http://www.rdocumentation.org/packages/base/functions/seq"><code>seq()</code></a>.</p></div>

```r
# Fix me
#seq(rep(1, 7, by = 2), times = 7)
rep(seq(1, 7, by = 2), times = 7)
#>  [1] 1 3 5 7 1 3 5 7 1 3 5 7 1 3 5 7 1 3 5 7 1 3 5 7 1 3 5 7
```

<p class="">Wonderful! Debugging code is also a big part of the daily routine of a data scientist, and you seem to be great at it!
</p>

### Beat Gauss using R


<div class><p>There is a popular story about young Gauss. As a pupil, he had a lazy teacher who wanted to keep the classroom busy by having them add up the numbers 1 to 100. Gauss came up with an answer almost instantaneously, 5050. On the spot, he had developed a formula for calculating the sum of an arithmetic series. There are more general formulas for calculating the sum of an arithmetic series with different starting values and increments. Instead of deriving such a formula, why not use R to calculate the sum of a sequence?</p></div>

<li>Using the function <a href="http://www.rdocumentation.org/packages/base/functions/seq"><code>seq()</code></a>, create a sequence that ranges from 1 to 500 in increments of 3. Assign the resulting vector to a variable <code>seq1</code>.</li>

```r
# Create first sequence: seq1
seq1 <- seq(1, 500, by = 3)

```
<li>Again with the function <a href="http://www.rdocumentation.org/packages/base/functions/seq"><code>seq()</code></a>, create a sequence that ranges from 1200 to 900 in increments of -7. Assign it to a variable <code>seq2</code>.</li>

```r
# Create second sequence: seq2
seq2 <- seq(1200, 900, by = -7)

```
<li>Calculate the total sum of the sequences, either by using the <a href="http://www.rdocumentation.org/packages/base/functions/sum"><code>sum()</code></a> function twice and adding the two results, or by first concatenating the sequences and then using the <a href="http://www.rdocumentation.org/packages/base/functions/sum"><code>sum()</code></a> function once. Print the result to the console.</li>

```r
# Calculate total sum of the sequences
sum(seq1) + sum(seq2)
#> [1] 87029
```

<p class="">Nice! Head over to the next video and learn more about regular expressions!
</p>

## Regular Expressions



### grepl &amp; grep


<div class>
<p>In their most basic form, regular expressions can be used to see whether a pattern exists inside a character string or a vector of character strings. For this purpose, you can use:</p>
<ul>
<li>
<a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>grepl()</code></a>, which returns <code>TRUE</code> when a pattern is found in the corresponding character string.</li>

<li>
<a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>grep()</code></a>, which returns a vector of indices of the character strings that contains the pattern.</li>

</ul>
<p>Both functions need a <code>pattern</code> and an <code>x</code> argument, where <code>pattern</code> is the regular expression you want to match for, and the <code>x</code> argument is the character vector from which matches should be sought.</p>
<p>In this and the following exercises, you'll be querying and manipulating a character vector of email addresses! The vector <code>emails</code> has been pre-defined so you can begin with the instructions straight away!</p>
</div>

<li>Use <a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>grepl()</code></a> to generate a vector of logicals that indicates whether these email addressess contain <code>"edu"</code>. Print the result to the output.</li>

```r
# The emails vector has already been defined for you
emails <- c("john.doe@ivyleague.edu", "education@world.gov", "dalai.lama@peace.org",
            "invalid.edu", "quant@bigdatacollege.edu", "cookie.monster@sesame.tv")

# Use grepl() to match for "edu"
grepl("edu", emails)
#> [1]  TRUE  TRUE FALSE  TRUE  TRUE FALSE
```
<li>Do the same thing with <a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>grep()</code></a>, but this time save the resulting indexes in a variable <code>hits</code>.</li>

```r
# Use grep() to match for "edu", save result to hits
hits <- grep("edu", emails)

```
<li>Use the variable <code>hits</code> to select from the <code>emails</code> vector only the emails that contain <code>"edu"</code>.</li>

```r
# Subset emails using hits
emails[hits]
#> [1] "john.doe@ivyleague.edu"   "education@world.gov"     
#> [3] "invalid.edu"              "quant@bigdatacollege.edu"
```

<p class="">Bellissimo! You can probably guess what we're trying to achieve here: select all the emails that end with “.edu”. However, the strings <code>education@world.gov</code> and <code>invalid.edu</code> were also matched. Let's see in the next exercise what you can do to improve our pattern and remove these false positives.
</p>

### grepl &amp; grep (2)


<div class>
<p>You can use the caret, <code>^</code>, and the dollar sign, <code>$</code> to match the content located in the start and end of a string, respectively. This could take us one step closer to a correct pattern for matching only the ".edu" email addresses from our list of emails. But there's more that can be added to make the pattern more robust:</p>
<ul>
<li>
<code>@</code>, because a valid email must contain an at-sign.</li>

<li>
<code>.*</code>, which matches any character (.) zero or more times (*). Both the dot and the asterisk are metacharacters. You can use them to match any character between the at-sign and the ".edu" portion of an email address.</li>

<li>
<code>\\.edu$</code>, to match the ".edu" part of the email at the end of the string. The <code>\\</code> part <em>escapes</em> the dot: it tells R that you want to use the <code>.</code> as an actual character.</li>

</ul>
</div>

<li>Use <a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>grepl()</code></a> with the more advanced regular expression to return a logical vector. Simply print the result.</li>

```r
# The emails vector has already been defined for you
emails <- c("john.doe@ivyleague.edu", "education@world.gov", "dalai.lama@peace.org",
            "invalid.edu", "quant@bigdatacollege.edu", "cookie.monster@sesame.tv")

# Use grepl() to match for .edu addresses more robustly
grepl("@.*\\.edu$", emails)
#> [1]  TRUE FALSE FALSE FALSE  TRUE FALSE
```
<li>Do a similar thing with <a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>grep()</code></a> to create a vector of indices. Store the result in the variable <code>hits</code>.</li>

```r
# Use grep() to match for .edu addresses more robustly, save result to hits
hits <- grep("@.*\\.edu$", emails)

```
<li>Use <code>emails[hits]</code> again to subset the <code>emails</code> vector.</li>

```r
# Subset emails using hits
emails[hits]
#> [1] "john.doe@ivyleague.edu"   "quant@bigdatacollege.edu"
```

<p class="">Great! A careful construction of our regular expression leads to more meaningful matches. However, even our robust email selector will often match some incorrect email addresses (for instance kiara@@fakemail.edu). Let's not worry about this too much and continue with <code>sub()</code> and <code>gsub()</code> to actually edit the email addresses!
</p>

### sub &amp; gsub


<div class>
<p>While <a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>grep()</code></a> and <a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>grepl()</code></a> were used to simply check whether a regular expression could be matched with a character vector, <a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>sub()</code></a> and <a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>gsub()</code></a> take it one step further: you can specify a <code>replacement</code> argument. If inside the character vector <code>x</code>, the regular expression <code>pattern</code> is found, the matching element(s) will be replaced with <code>replacement</code>.<a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>sub()</code></a> only replaces the first match, whereas <a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>gsub()</code></a> replaces all matches.</p>
<p>Suppose that <code>emails</code> vector you've been working with is an excerpt of DataCamp's email database. Why not offer the owners of the .edu email addresses a new email address on the datacamp.edu domain? This could be quite a powerful marketing stunt: Online education is taking over traditional learning institutions! Convert your email and be a part of the new generation!</p>
</div>
<div class="exercise--instructions__content"><p>With the advanced regular expression <code>"@.*\\.edu$"</code>, use <code>sub()</code> to replace the match with <code>"@datacamp.edu"</code>. Since there will only be one match per character string, <code>gsub()</code> is not necessary here. Inspect the resulting output.</p></div>

```r
# Use sub() to convert the email domains to datacamp.edu
sub("@.*\\.edu$", "@datacamp.edu", emails)
#> [1] "john.doe@datacamp.edu"    "education@world.gov"     
#> [3] "dalai.lama@peace.org"     "invalid.edu"             
#> [5] "quant@datacamp.edu"       "cookie.monster@sesame.tv"
```

<p class="">Awesome! Notice how only the valid .edu addresses are changed while the other emails remain unchanged. To get a taste of other things you can accomplish with regex, head over to the next exercise.
</p>

### sub &amp; gsub (2)


<div class>
<p>Regular expressions are a typical concept that you'll learn by doing and by seeing other examples. Before you rack your brains over the regular expression in this exercise, have a look at the new things that will be used:</p>
<ul>
<li>
<code>.*</code>: A usual suspect! It can be read as "any character that is matched zero or more times".</li>

<li>
<code>\\s</code>: Match a space. The "s" is normally a character, escaping it (<code>\\</code>) makes it a metacharacter.</li>

<li>
<code>[0-9]+</code>: Match the numbers 0 to 9, at least once (+).</li>

<li>
<code>([0-9]+)</code>: The parentheses are used to make parts of the matching string available to define the replacement. The <code>\\1</code> in the <code>replacement</code> argument of <a href="http://www.rdocumentation.org/packages/base/functions/grep"><code>sub()</code></a> gets set to the string that is captured by the regular expression <code>[0-9]+</code>.</li>

</ul>
<pre><code>awards &lt;- c("Won 1 Oscar.",
  "Won 1 Oscar. Another 9 wins &amp; 24 nominations.",
  "1 win and 2 nominations.",
  "2 wins &amp; 3 nominations.",
  "Nominated for 2 Golden Globes. 1 more win &amp; 2 nominations.",
  "4 wins &amp; 1 nomination.")

sub(".*\\s([0-9]+)\\snomination.*$", "\\1", awards)
</code></pre>
<p>What does this code chunk return? <code>awards</code> is already defined in the workspace so you can start playing in the console straight away.</p>
</div>

<ul>
<li><div class="dc-input-radio__text">A vector of integers containing: 1, 24, 2, 3, 2, 1.</div></li>
<li><div class="dc-input-radio__text">The vector <code>awards</code> gets returned as there isn't a single element in <code>awards</code> that matches the regular expression.</div></li>
<li><div class="dc-input-radio__text">A vector of character strings containing "1", "24", "2", "3", "2", "1".</div></li>
<strong><li><div class="dc-input-radio__text">A vector of character strings containing "Won 1 Oscar.", "24", "2", "3", "2", "1".</div></li></strong>
</ul>

<p class="">Great! Can you explain why all of this happened? The <code>([0-9]+)</code> selects the entire number that comes before the word “nomination” in the string, and the entire match gets replaced by this number because of the <code>\\1</code> that reference to the content inside the parentheses. The next video will get you up to speed with times and dates in R!
</p>

## Times &amp; Dates



### Right here, right now


<div class>
<p>In R, dates are represented by <code>Date</code> objects, while times are represented by <code>POSIXct</code> objects. Under the hood, however, these dates and times are simple numerical values. <code>Date</code> objects store the number of days since the 1st of January in 1970. <code>POSIXct</code> objects on the other hand, store the number of seconds since the 1st of January in 1970.</p>
<p>The 1st of January in 1970 is the common origin for representing times and dates in a wide range of programming languages. There is no particular reason for this; it is a simple convention. Of course, it's also possible to create dates and times before 1970; the corresponding numerical values are simply negative in this case.</p>
</div>

<li>Ask R for the current date, and store the result in a variable <code>today</code>.</li>

```r
# Get the current date: today
today <- Sys.Date()

```
<li>To see what <code>today</code> looks like under the hood, call <a href="http://www.rdocumentation.org/packages/base/functions/class"><code>unclass()</code></a> on it.</li>

```r
# See what today looks like under the hood
unclass(today)
#> [1] 19055
```
<li>Ask R for the current time, and store the result in a variable, <code>now</code>.</li>

```r
# Get the current time: now
now <- Sys.time()

```
<li>To see the numerical value that corresponds to <code>now</code>, call <a href="http://www.rdocumentation.org/packages/base/functions/class"><code>unclass()</code></a> on it.</li>

```r
# See what now looks like under the hood
unclass(now)
#> [1] 1646398911
```

<p class="">Great! Using R to get the current date and time is nice, but you should also know how to create dates and times from character strings. Find out how in the next exercises!
</p>

### Create and format dates


<div class>
<p>To create a <code>Date</code> object from a simple character string in R, you can use the <a href="http://www.rdocumentation.org/packages/base/functions/as.Date"><code>as.Date()</code></a> function. The character string has to obey a format that can be defined using a set of symbols (the examples correspond to 13 January, 1982):</p>
<ul>
<li>
<code>%Y</code>: 4-digit year (1982)</li>

<li>
<code>%y</code>: 2-digit year (82)</li>

<li>
<code>%m</code>: 2-digit month (01)</li>

<li>
<code>%d</code>: 2-digit day of the month (13)</li>

<li>
<code>%A</code>: weekday (Wednesday)</li>

<li>
<code>%a</code>: abbreviated weekday (Wed)</li>

<li>
<code>%B</code>: month (January)</li>

<li>
<code>%b</code>: abbreviated month (Jan)</li>

</ul>
<p>The following R commands will all create the same <code>Date</code> object for the 13th day in January of 1982:</p>
<pre><code>as.Date("1982-01-13")
as.Date("Jan-13-82", format = "%b-%d-%y")
as.Date("13 January, 1982", format = "%d %B, %Y")
</code></pre>
<p>Notice that the first line here did not need a format argument, because by default R matches your character string to the formats <code>"%Y-%m-%d"</code> or <code>"%Y/%m/%d"</code>.</p>
<p>In addition to creating dates, you can also convert dates to character strings that use a different date notation. For this, you use the <a href="http://www.rdocumentation.org/packages/base/functions/format"><code>format()</code></a> function. Try the following lines of code:</p>
<pre><code>today &lt;- Sys.Date()
format(Sys.Date(), format = "%d %B, %Y")
format(Sys.Date(), format = "Today is a %A!")
</code></pre>
</div>

<li>Three character strings representing dates have been created for you. Convert them to dates using <a href="http://www.rdocumentation.org/packages/base/functions/as.Date"><code>as.Date()</code></a>, and assign them to <code>date1</code>, <code>date2</code>, and <code>date3</code> respectively. The code for <code>date1</code> is already included.</li>

```r
# Definition of character strings representing dates
str1 <- "May 23, '96"
str2 <- "2012-03-15"
str3 <- "30/January/2006"

# Convert the strings to dates: date1, date2, date3
date1 <- as.Date(str1, format = "%b %d, '%y")
date2 <- as.Date(str2)
date3 <- as.Date(str3, format = "%d/%B/%Y")

```
<li>Extract useful information from the dates as character strings using <a href="http://www.rdocumentation.org/packages/base/functions/format"><code>format()</code></a>. From the first date, select the weekday. From the second date, select the day of the month. From the third date, you should select the abbreviated month and the 4-digit year, separated by a space.</li>

```r
# Convert dates to formatted strings
format(date1, "%A")
#> [1] "Thursday"
format(date2, "%d")
#> [1] "15"
format(date3, "%b %Y")
#> [1] "Jan 2006"
```

<p class="">You're a date magician! You can use <code>POSIXct</code> objects, i.e. Time objects in R, in a similar fashion. Give it a try in the next exercise.
</p>

### Create and format times


<div class>
<p>Similar to working with dates, you can use <a href="http://www.rdocumentation.org/packages/base/functions/as.POSIXlt"><code>as.POSIXct()</code></a> to convert from a character string to a <code>POSIXct</code> object, and <a href="http://www.rdocumentation.org/packages/base/functions/format"><code>format()</code></a> to convert from a <code>POSIXct</code> object to a character string. Again, you have a wide variety of symbols:</p>
<ul>
<li>
<code>%H</code>: hours as a decimal number (00-23)</li>

<li>
<code>%I</code>: hours as a decimal number (01-12)</li>

<li>
<code>%M</code>: minutes as a decimal number</li>

<li>
<code>%S</code>: seconds as a decimal number</li>

<li>
<code>%T</code>: shorthand notation for the typical format <code>%H:%M:%S</code>
</li>

<li>
<code>%p</code>: AM/PM indicator</li>

</ul>
<p>For a full list of conversion symbols, consult the <code>strptime</code> documentation in the console:</p>
<pre><code>?strptime
</code></pre>
<p>Again,<a href="http://www.rdocumentation.org/packages/base/functions/as.POSIXlt"><code>as.POSIXct()</code></a> uses a default format to match character strings. In this case, it's <code>%Y-%m-%d %H:%M:%S</code>. In this exercise, abstraction is made of different time zones.</p>
</div>

<li>Convert two strings that represent timestamps, <code>str1</code> and <code>str2</code>, to <code>POSIXct</code> objects called <code>time1</code> and <code>time2</code>.</li>

```r
# Definition of character strings representing times
str1 <- "May 23, '96 hours:23 minutes:01 seconds:45"
str2 <- "2012-3-12 14:23:08"

```
<li>Using <a href="http://www.rdocumentation.org/packages/base/functions/format"><code>format()</code></a>, create a string from <code>time1</code> containing only the minutes.</li>

```r
# Convert the strings to POSIXct objects: time1, time2
time1 <- as.POSIXct(str1, format = "%B %d, '%y hours:%H minutes:%M seconds:%S")
time2 <- as.POSIXct(str2)

```
<li>From <code>time2</code>, extract the hours and minutes as "hours:minutes AM/PM". Refer to the assignment text above to find the correct conversion symbols!</li>

```r
# Convert times to formatted strings
format(time1, "%M")
#> [1] "01"
format(time2, "%I:%M %p")
#> [1] "02:23 PM"
```

<p class="">Great!
</p>

### Calculations with Dates


<div class>
<p>Both <code>Date</code> and <code>POSIXct</code> R objects are represented by simple numerical values under the hood. This makes calculation with time and date objects very straightforward: R performs the calculations using the underlying numerical values, and then converts the result back to human-readable time information again.</p>
<p>You can increment and decrement <code>Date</code> objects, or do actual calculations with them:</p>
<pre><code>today &lt;- Sys.Date()
today + 1
today - 1

as.Date("2015-03-12") - as.Date("2015-02-27")
</code></pre>
<p>To control your eating habits, you decided to write down the dates of the last five days that you ate pizza. In the workspace, these dates are defined as five <code>Date</code> objects, <code>day1</code> to <code>day5</code>. A vector <code>pizza</code> containing these 5 <code>Date</code> objects has been pre-defined for you.</p>
</div>

<li>Calculate the number of days that passed between the last and the first day you ate pizza. Print the result.</li>

```r
# day1, day2, day3, day4 and day5 are already available in the workspace
day1=as.Date("2022-02-11")
day2=as.Date("2022-02-13")
day3=as.Date("2022-02-18")
day4=as.Date("2022-02-24")
day5=as.Date("2022-03-01")

# Difference between last and first pizza day
day5 - day1
#> Time difference of 18 days
```
<li>Use the function <a href="http://www.rdocumentation.org/packages/base/functions/diff"><code>diff()</code></a> on <code>pizza</code> to calculate the differences between consecutive pizza days. Store the result in a new variable <code>day_diff</code>.</li>

```r
# Create vector pizza
pizza <- c(day1, day2, day3, day4, day5)

# Create differences between consecutive pizza days: day_diff
day_diff <- diff(pizza)

```
<li>Calculate the average period between two consecutive pizza days. Print the result.</li>

```r
# Average period between two consecutive pizza days
mean(day_diff)
#> Time difference of 4.5 days
```

<p class="">Great! Head over to the next exercise.
</p>

### Calculations with Times


<div class>
<p>Calculations using <code>POSIXct</code> objects are completely analogous to those using <code>Date</code> objects. Try to experiment with this code to increase or decrease <code>POSIXct</code> objects:</p>
<pre><code>now &lt;- Sys.time()
now + 3600          # add an hour
now - 3600 * 24     # subtract a day
</code></pre>
<p>Adding or subtracting time objects is also straightforward:</p>
<pre><code>birth &lt;- as.POSIXct("1879-03-14 14:37:23")
death &lt;- as.POSIXct("1955-04-18 03:47:12")
einstein &lt;- death - birth
einstein
</code></pre>
<p>You're developing a website that requires users to log in and out. You want to know what is the total and average amount of time a particular user spends on your website. This user has logged in 5 times and logged out 5 times as well. These times are gathered in the vectors <code>login</code> and <code>logout</code>, which are already defined in the workspace.</p>
</div>

<li>Calculate the difference between the two vectors <code>logout</code> and <code>login</code>, i.e. the time the user was online in each independent session. Store the result in a variable <code>time_online</code>.</li>

```r
# login and logout are already defined in the workspace
login <- c(as.POSIXct("2017-03-16 10:18:04 UTC"), 
            as.POSIXct("2017-03-21 09:14:18 UTC"),
            as.POSIXct("2017-03-21 12:21:51 UTC"), 
            as.POSIXct("2017-03-21 12:37:24 UTC"),
            as.POSIXct("2017-03-23 21:37:55 UTC"))

logout <- c(as.POSIXct("2017-03-16 10:56:29 UTC"),
            as.POSIXct("2017-03-21 09:14:52 UTC"),
            as.POSIXct("2017-03-21 12:35:48 UTC"), 
            as.POSIXct("2017-03-21 13:17:22 UTC"),
            as.POSIXct("2017-03-23 22:08:47 UTC"))

# Calculate the difference between login and logout: time_online
time_online <- logout - login

```
<li>Inspect the variable <code>time_online</code> by printing it.</li>

```r
# Inspect the variable time_online
time_online
#> Time differences in secs
#> [1] 2305   34  837 2398 1852
```
<li>Calculate the total time that the user was online. Print the result.</li>

```r
# Calculate the total time online
sum(time_online)
#> Time difference of 7426 secs
```
<li>Calculate the average time the user was online. Print the result.</li>

```r
# Calculate the average time online
mean(time_online)
#> Time difference of 1485.2 secs
```

<p class="">Great! Time to tackle the final exercise of this course!
</p>

### Time is of the essence


<div class>
<p>The dates when a season begins and ends can vary depending on who you ask. People in Australia will tell you that spring starts on September 1st. The Irish people in the Northern hemisphere will swear that spring starts on February 1st, with the celebration of St. Brigid's Day. Then there's also the difference between astronomical and meteorological seasons: while astronomers are used to equinoxes and solstices, meteorologists divide the year into 4 fixed seasons that are each three months long. (source: www.timeanddate.com)</p>
<p>A vector <code>astro</code>, which contains character strings representing the dates on which the 4 astronomical seasons start, has been defined on your workspace. Similarly, a vector <code>meteo</code> has already been created for you, with the meteorological beginnings of a season.</p>
</div>

<li>Use <code>as.Date()</code> to convert the <code>astro</code> vector to a vector containing <code>Date</code> objects. You will need the <code>%d</code>, <code>%b</code> and <code>%Y</code> symbols to specify the <code>format</code>. Store the resulting vector as <code>astro_dates</code>.</li>

```r
astro <- c("20-Mar-2015", "25-Jun-2015", "23-Sep-2015", "22-Dec-2015")
names(astro) <- c("spring", "summer","fall","winter") 
astro
#>        spring        summer          fall        winter 
#> "20-Mar-2015" "25-Jun-2015" "23-Sep-2015" "22-Dec-2015"

# Convert astro to vector of Date objects: astro_dates
astro_dates <- as.Date(astro, format = "%d-%b-%Y")

```
<li>Use <code>as.Date()</code> to convert the <code>meteo</code> vector to a vector with <code>Date</code> objects. This time, you will need the <code>%B</code>, <code>%d</code> and <code>%y</code> symbols for the <code>format</code> argument. Store the resulting vector as <code>meteo_dates</code>.</li>

```r
meteo <- c("March 1, 15", "June 1, 15", "September 1, 15", "December 1, 15")
names(meteo) <- c("spring", "summer", "fall", "winter")
meteo
#>            spring            summer              fall            winter 
#>     "March 1, 15"      "June 1, 15" "September 1, 15"  "December 1, 15"

# Convert meteo to vector of Date objects: meteo_dates
meteo_dates <- as.Date(meteo, format = "%B %d, %y")

```
<li>With a combination of <code>max()</code>, <code>abs()</code> and <code>-</code>, calculate the maximum absolute difference between the astronomical and the meteorological beginnings of a season, i.e. <code>astro_dates</code> and <code>meteo_dates</code>. Simply print this maximum difference to the console output.</li>

```r
# Calculate the maximum absolute difference between astro_dates and meteo_dates
max(abs(meteo_dates - astro_dates))
#> Time difference of 24 days
```

<p class="">Impressive! Great job on finishing this course!
</p>
