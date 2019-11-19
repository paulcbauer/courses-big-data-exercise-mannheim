---
title: 'Analyzing some Twitter data'
description: 'Some code examples to learn how to approach a Twitter dataset.'
---

## Importing data

```yaml
type: NormalExercise
key: 2c742278c4
xp: 100
```

Welcome to your first coding exercise. Below you find the instructions. On the right you find example code. On the lower right you have the R console in which you can try out code. We'll analyze Twitter data of members of the German Bundestag (a time period of 7 days).

Write the solution in the panel to the right, try it out with "Run Code". If you think that you found the solution push "Submit answer".

Before we can start analzying data we have to import it into R. Data may come in many different formats. Here we deal with the most commonly used data format ***.csv** (_stands for comma separated values_). You already know that R comes with different packages that include functions to import data. Here we'll work with one of R's basic functions **read.csv()**. The function is part of the **utils** package which is preloaded.

`@instructions`
<!-- Guidelines for instructions https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
1. Start reading the help file for the `read_csv` function with `?read_csv`. It provides information on how the function works and code examples.
2. Everything in R is an object and you can store anything in an object. Type `data_stored`, then assign something to data `data_stored <- 2` and type `data_stored` again.
3. Now load the dataset with the `read.csv()` function and store it in an object called `data`. Use the example code on the right.
3. Check whether the dataset was really imported by typing `class(data)`.

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- Run ?read.csv.
- Run data <- read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv").

`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
# 1.

?read.csv


# 2. Assign something to an object and print the object

data_stored <- 2
data_stored


# 3. 

read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv") # Load the dataset

data <- read.csv(...) # assign it to an object in which you store the data


# 4.

class(...)

```

`@solution`
```{r}
# 1. ?read.csv

?read.csv

# 2. Assigned something to an object:

# 3. Load the dataset: 
#    read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv")
# 	 Assign it to "data": "data <- read.csv(...)".

data <- read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv")

# 4. ...

class(data)
```

`@sct`
```{r}
# Examples of good success messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.
```

---

## Rows and columns

```yaml
type: NormalExercise
key: 8cc1005e51
xp: 100
```

<!-- Guidelines for contexts: https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
We'll start by exploring the dataset a little. First, we are interested in the dimensions of the dataset, i.e., how many rows and columns it has.

`@instructions`
<!-- Guidelines for instructions https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
1. Please check how many rows and columns the dataset has with the functions `nrow()` and `ncol()`.
2. You can use the `head()` function to see the first rows of a dataset. Do that. Maybe you can already make a guess what observations we have in this dataset here.

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- nrow(data)
- ncol(data)
- head(data)

`@pre_exercise_code`
```{r}
data <- read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
library(lubridate)
data$tweet_created_at <- ymd_hms(data$tweet_created_at)
```

`@sample_code`
```{r}
# 1. The data has been loaded already. Use the functions nrow() and ncol() on the dataset.



# 2. Apply the head() function to "data". 



```

`@solution`
```{r}
# 1. The data has been loaded already. Use the functions nrow() and ncol() on the dataset.

nrow(data)
ncol(data)

# 2. Apply the head() function to "data". 

head(data)
```

`@sct`
```{r}
# Examples of good success messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.
```

---

## Types of variables

```yaml
type: NormalExercise
key: 0b7bfbcdf9
xp: 100
```

<!-- Guidelines for contexts: https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
We are also interested in they types of variables that are included in the dataset. There are several ways to check out those variables...

`@instructions`
<!-- Guidelines for instructions https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
1. With `names(data)` we can display the names of all the variables. Try that out.
2. The function `str()` can be used to find out more about the variables. For instance, what kind of data type the variable is. We also can see how observations (rows) and variables we have in our data. Try that out.
3. And we can use the `$` sign to directly access a variable in a dataset. Try out typing `data$nameofvariable` for different variables.
4. What observations do we find in the rows of the dataset (no code necessary here!).

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- str(data)
- Scroll up in the output until you reach the first variable.

`@pre_exercise_code`
```{r}
data <- read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
library(lubridate)
data$tweet_created_at <- ymd_hms(data$tweet_created_at)
```

`@sample_code`
```{r}
# 1. Type in names(data)



# 2. str(data)



# 3. and 4. What type of variable is the first variable? And how many observations and variables are in the dataset? Try data$nameofvariable.



```

`@solution`
```{r}

```

`@sct`
```{r}
# Examples of good success messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.
```

---

## Aggregating data

```yaml
type: NormalExercise
key: 241d66ee73
xp: 100
```

<!-- Guidelines for contexts: https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
We found out that the observations (= rows) in the dataset are tweets. In other words, the rows are single tweets. However, there may be several tweets by the same politician or party in the dataset. And that is what interests us. For instance, we probably want to calculate which politician tweets the most or which party has the most tweets. 

For that we have to aggregate the data. This is done int two steps. First, we group the data (`group_by()`). Second, we summarize the data along these groups (`summarize()`).

`@instructions`
<!-- Guidelines for instructions https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
1. Load the dplyr package that contains functions we need for many analyses: `library(dplyr)`.
2. Count the number of tweets per party by aggregating the dataset with the following command: `data %>% group_by(party) %>% summarize(number_of_tweets = n())`. Did you expect that?
3. We can use the same command and add `arrange()` to order according to a variable. For instance, order according to the number of tweets.
4. Using the command from above: What do I need to type to find the politician with the most tweets? (Hint: `group_by(name)`).

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- This is an example hint.
- This is an example hint.

`@pre_exercise_code`
```{r}
data <- read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
library(lubridate)
data$tweet_created_at <- ymd_hms(data$tweet_created_at)
```

`@sample_code`
```{r}
# 1. library(dplyr)



# 2. data %>% group_by(party) %>% summarize(number_of_tweets = n())



# 3. data %>% group_by(party) %>% summarize(number_of_tweets = n()) %>% arrange(desc(number_of_tweets))



# 4. data %>% group_by(...) %>% summarize(number_of_tweets = n()) %>% arrange(desc(number_of_tweets))
```

`@solution`
```{r}

```

`@sct`
```{r}
# Examples of good success messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.
```

---

## Time

```yaml
type: NormalExercise
key: a682f87d24
xp: 100
```

<!-- Guidelines for contexts: https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
One characteristics of Big Data is that it is often temporarily very fine-grained. For instance, it's possible that we collect observations every minute. Fortunately, the twitter dataset we have here contains a time stamp for each tweet that we'll quickly explore here (some of the functions used here are in the `lubridate` package which is preloaded.

`@instructions`
<!-- Guidelines for instructions https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
- The time variable in our dataset is called `tweet_created_at`. You can have a a look at the variable by typing `data$tweet_created_at`. It contains both the date and the time when the tweet was published.
- Try to find out what the oldest and the newest tweet is using the functions `min()` and `max()`. That should also tell you how many days are 
- Can you find out how many days the dataset covers?

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- This is an example hint.
- This is an example hint.

`@pre_exercise_code`
```{r}
data <- read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
library(lubridate)
data$tweet_created_at <- ymd_hms(data$tweet_created_at)
```

`@sample_code`
```{r}
# 1. Type data$tweet_created_at



# 2. min(data$tweet_created_at)



# 3. Try looking at the ouput of day(data$tweet_created_at) or table(date(data$tweet_created_at))!



```

`@solution`
```{r}

```

`@sct`
```{r}
# Examples of good success messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.
```

---

## Analyzing activity: Number of tweets

```yaml
type: MultipleChoiceExercise
key: 4d8a8ea9c7
xp: 50
```

<!-- Guidelines for the question: https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises. -->
Finally, we are interested in who the most active politician is. Who tweets the most? 

Try the code on the right and give the answer on the left. Take the functions we used before:

`data %>% group_by(name) %>% summarize(number_of_tweets = n()) %>% ...`

You might need to add the `arrange(desc(...))` function to find that out.

`@possible_answers`
- Saskia Esken
- [Johannes Kahrs]
- Oliver Luksic

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- No hints for you.. try again! :-)

`@pre_exercise_code`
```{r}
data <- read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
library(lubridate)
library(dplyr)
data$tweet_created_at <- ymd_hms(data$tweet_created_at)
```

`@sct`
```{r}
# Check https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises on how to write feedback messages for this exercise.

# Example solution: second instruction correct out of three options.

# Corresponding SCT:
msg1 <- "Not good, try again!"
msg2 <- "Nice one!"
msg3 <- "Not quite, give it another shot."
ex() %>% check_mc(2, feedback_msgs = c(msg1, msg2, msg3))
```

---

## Analyzing influence: Number of retweets

```yaml
type: MultipleChoiceExercise
key: 9429d31d39
xp: 50
```

<!-- Guidelines for the question: https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises. -->
One measure of influence is the number of retweets someone gets. The variable `retweet_count` contains the number of retweets per tweet. Now we are interested in how many retweets each politician got and we'll use the function `sum()` for that. You just need to insert the right variable.

`data %>% group_by(name) %>% summarize(sum_of_tweets = sum(...)) %>% arrange(desc(sum_of_tweets))`

Who is the candidate with the most retweets in the time period we study? (Which parties are those people from?)

`@possible_answers`
- Manuela Rottmann
- Martin Renner
- [Petr Bystron]

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- No hints for you.. try again! :-)

`@pre_exercise_code`
```{r}
data <- read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
library(lubridate)
library(dplyr)
data$tweet_created_at <- ymd_hms(data$tweet_created_at)
```

`@sct`
```{r}
# Check https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises on how to write feedback messages for this exercise.

# Example solution: second instruction correct out of three options.

# Corresponding SCT:
msg1 <- "Not good, try again!"
msg2 <- "Not quite, give it another shot."
msg3 <- "Nice one!"
ex() %>% check_mc(3, feedback_msgs = c(msg1, msg2, msg3))
```

---

## Analyzing activity across time

```yaml
type: NormalExercise
key: 137b39b8f5
xp: 100
```

<!-- Guidelines for contexts: https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
You already know that we have a time variables in the dataset. There is also a time variable that contains the date called `tweet_created_at_date`. If we want to know how much politicans have tweeted across time we can use this variable to group the data.

`@instructions`
<!-- Guidelines for instructions https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
1. Use `table(data$tweet_created_at_date)` to find out how man observations there are per date.
2. Then aggregate the dataset and count the observations but now grouping according to the date.
3. Now aggregate the dataset according to two variables (`tweet_created_at_date`, `party`), to find how the members of which party tweeted the most across the days.
4. Since not all the data is shown in the console try out the `filter` function to only show subsets of the data.

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- No hints for you.. try again! :-)

`@pre_exercise_code`
```{r}
data <- read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
library(lubridate)
library(dplyr)
library(ggplot2)
data$tweet_created_at <- ymd_hms(data$tweet_created_at)
```

`@sample_code`
```{r}
# 1. 

table(data$tweet_created_at_date)

# 2. 

data %>% group_by(...) %>% summarize(number_of_tweets = n())

# 3. 

data %>% group_by(party, tweet_created_at_date) %>% summarize(...)

# 4. 

data %>% group_by(party, tweet_created_at_date) %>% summarize(number_of_tweets = n()) %>% filter(party == "CDU_CSU")

```

`@solution`
```{r}

```

`@sct`
```{r}
# Examples of good success messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.
```

---

## Visualizing activity over time

```yaml
type: NormalExercise
key: af3f24a4a6
xp: 100
```

<!-- Guidelines for contexts: https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->

`@instructions`
<!-- Guidelines for instructions https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
- Let's try to draw a quick line plot showing the number of tweets for different parties across time. For that we have to store the aggregate data in a new object (let's call it `data_plot`) and use the ggplot function. Use the sample code on the right.
- Which statistic would make more sense than the absolute number of tweets per party (of its party members) across time? No code needed here.

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- No hints for you.. try again! :-)

`@pre_exercise_code`
```{r}
data <- read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
library(lubridate)
library(dplyr)
library(ggplot2)
data$tweet_created_at <- ymd_hms(data$tweet_created_at)
```

`@sample_code`
```{r}
# Store the data in a new object: 

data_plot <- data %>% group_by(party, tweet_created_at_date) %>% summarize(number_of_tweets = n()) %>% ungroup()

# Then use the ggplot command: 

ggplot(data_plot, aes(x = tweet_created_at_date, y = number_of_tweets, group = ..., color = ...)) + geom_line()
```

`@solution`
```{r}

```

`@sct`
```{r}
# Examples of good success messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.
```

---

## Analyzing content

```yaml
type: NormalExercise
key: 76c1b28918
xp: 100
```

<!-- Guidelines for contexts: https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
We discussed short examples to measure twitter activity and influence. Naturally, the most interesting thing about tweets is their content. The simplest thing we can do is frequency analysis (calculating the frequency of certain words). Below we count the frequency of the word `Klima` across tweets, trying to see whether it is more frequent in some parties than in others.

`@instructions`
<!-- Guidelines for instructions https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
1. First we need to create a variable that tells us whether `Klima` appeared in a tweet or not. We can do this with the `str_detect` function from the `stringr` package (preloaded). And we use `data$variable <- ` to create a new variable in the dataset. Try it on the right.
2. Check out this variable with `data$klimawandel`. It has the values TRUE/FALSE depending on whether the word was in the tweet or not.
3. Now we can count how frequent the term is among the tweets of different parties again by aggregating the data on to the party level. Among which party's tweets is the Word Klima most common?
4. Try this with another word namely "Trump". Use the sample code on the right for this.

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- No hints for you.. try again! :-)

`@pre_exercise_code`
```{r}
data <- read.csv("https://assets.datacamp.com/production/repositories/5540/datasets/3d4964c14700ec724d0dd96d3fc526d95db224e9/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
library(lubridate)
library(dplyr)
library(stringr)
data$tweet_created_at <- ymd_hms(data$tweet_created_at)
```

`@sample_code`
```{r}
# 1.

data$Klima <- str_detect(data$text, "Klima")

# 2. Type data$...



# 3. Type:

data %>% group_by(party) %>% summarize(number_of_tweets = n(), number_of_Klima = sum(Klima), frequency_of_Klima = number_of_Klima/number_of_tweets)

# 4. Insert "Trump".

data$... <- str_detect(data$text, "...")
data %>% group_by(party) %>% summarize(number_of_tweets = n(), number_of_... = sum(...), frequency_of_... = number_of_.../number_of_tweets)


```

`@solution`
```{r}
data$Klima <- str_detect(data$text, "Klima")

# 2. Type data$...

data$Klima

# 3. Type:

data %>% group_by(party) %>% summarize(number_of_tweets = n(), number_of_Klima = sum(Klima), frequency_of_Klima = number_of_Klima/number_of_tweets)

# 4. Insert "Trump".

data$Trump <- str_detect(data$text, "Trump")
data %>% group_by(party) %>% summarize(number_of_tweets = n(), number_of_Trump = sum(Trump), frequency_of_Trump = number_of_Trump/number_of_tweets)
```

`@sct`
```{r}
# Examples of good success messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.
```
