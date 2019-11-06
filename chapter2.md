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

Welcome to your first coding exercise. Below you find the instructions. On the right you find example code. On the lower right you have the R console in where you can try out code. 

Write the solution in the panel to the right, try it out with "Run Code". If you think that you found the solution push "Submit answer".

Before we can start analzying data we have to import it into R. Date may come in many different formats. Here we deal with the most commonly used data format ***.csv** (_stands for comma separated values_). You already know that R comes with different packages that include functions to import data. Here we'll work with one of R's basic functions **read.csv()**. The function is part of the **utils** package which is preloaded.

`@instructions`
<!-- Guidelines for instructions https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
1. Start reading the help file for the `read_csv` function with `?read_csv`. It provides information on how the function works and code examples.
2. Everything in R is an object and you can store anything in an object. Type `data_stored`, then assign something to data `data_stored <- 2` and type `data_stored` again.
3. Now load the dataset with the `read.csv()` function and store it in an object called `data`. Use the example code on the right.
3. Check whether the dataset was really imported by typing `class(data)`.

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- Run ?read.csv.
- Run data <- read.csv("https://assets.datacamp.com/production/repositories/5485/datasets/4581ad84bed2a2226f738097e36ceaf122dd5c30/data.csv").

`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
# 1. ?read.csv

?read.csv

# 2. Assigned something to an object:


# 3. Load the dataset: 
#    Use read.csv("https://assets.datacamp.com/production/repositories/5485/datasets/4581ad84bed2a2226f738097e36ceaf122dd5c30/data.csv").
# 	 and assign it to "data": "data <- read.csv(...)".

# 4. ...

```

`@solution`
```{r}
# 1. ?read.csv

?read.csv

# 2. Assigned something to an object:

# 3. Load the dataset: 
#    read.csv("https://assets.datacamp.com/production/repositories/5485/datasets/4581ad84bed2a2226f738097e36ceaf122dd5c30/data.csv")
# 	 Assign it to "data": "data <- read.csv(...)".

data <- read.csv("https://assets.datacamp.com/production/repositories/5485/datasets/4581ad84bed2a2226f738097e36ceaf122dd5c30/data.csv")

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
data <- read.csv("https://assets.datacamp.com/production/repositories/5485/datasets/4581ad84bed2a2226f738097e36ceaf122dd5c30/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
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
We are also interested in they types of variables that are included in the dataset. There are two ways to do this...

`@instructions`
<!-- Guidelines for instructions https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
1. With `names(data)` we can display the names of all the variables. Try that out.
2. The function `str()` can be used to find out more about the variables. For instance, what kind of data type the variable is. We also can see how observations (rows) and variables we have in our data. Try that out.
3. And we can use the `$` sign to directly access a variable in a dataset. Try out typing `data$name`

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- str(data)
- Scroll up in the output until you reach the first variable.

`@pre_exercise_code`
```{r}
data <- read.csv("https://assets.datacamp.com/production/repositories/5485/datasets/4581ad84bed2a2226f738097e36ceaf122dd5c30/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
```

`@sample_code`
```{r}
# 1. str(data)



# 2. What type of variable is the first variable? And how many observations and variables are in the dataset?
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
We found out that the dataset is on the level of tweets. In other words, the rows in the dataset are single tweets. But we are interested in summarizing this data. For instance, we probably want to calculate which politician tweets the most or which party has the most tweets.

`@instructions`
<!-- Guidelines for instructions https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
1. Load the dplyr package that contains functions we need for many analyses: `library(dplyr)`.
2. Count the number of tweets per party by aggregating the dataset with the following command: `data %>% group_by(party) %>% summarize(number_of_tweets = n())`. Did you expect that?
3. Now, we do the same but order the results according to the number of tweets: `data %>% group_by(party) %>% summarize(number_of_tweets = n()) %>% arrange(desc(number_of_tweets))`.
4. Using the command from above: What do I need to type to find the politician with the most tweets? (Hint: group by name)

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- This is an example hint.
- This is an example hint.

`@pre_exercise_code`
```{r}
data <- read.csv("https://assets.datacamp.com/production/repositories/5485/datasets/4581ad84bed2a2226f738097e36ceaf122dd5c30/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
```

`@sample_code`
```{r}
# 1. library(dplyr)



# 2. data %>% group_by(party) %>% summarize(number_of_tweets = n())



# 3. data %>% group_by(party) %>% summarize(number_of_tweets = n()) %>% arrange(desc(number_of_tweets))



# 4. data %>% group_by(party) %>% summarize(number_of_tweets = n()) %>% arrange(desc(number_of_tweets))
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
As we discussed one characteristics of Big Data is that it is often temporarily very fine-grained. For instance, it's possible that we collect observations every minute. Fortunately, the twitter dataset we have here contains a time stamp for each tweet that we'll quickly explore here.

`@instructions`
<!-- Guidelines for instructions https://instructor-support.datacamp.com/en/articles/2375526-course-coding-exercises. -->
- The time variable in our dataset is called `tweet_created_at`. You can have a a look at the variable by typing `data$tweet_created_at`. It contains both the data and the time of the tweet.
- Try to find out what the oldest and the newest tweet is using the functions `min()` and `max()`. That should also tell you how many days are 
- How many days does the dataset contain?

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- This is an example hint.
- This is an example hint.

`@pre_exercise_code`
```{r}
data <- read.csv("https://assets.datacamp.com/production/repositories/5485/datasets/4581ad84bed2a2226f738097e36ceaf122dd5c30/data.csv", encoding="UTF-8", stringsAsFactors=FALSE)
```

`@sample_code`
```{r}

```

`@solution`
```{r}

```

`@sct`
```{r}
# Examples of good success messages: https://instructor-support.datacamp.com/en/articles/2299773-exercise-success-messages.
```

---

## Analyzing activity

```yaml
type: MultipleChoiceExercise
key: 4d8a8ea9c7
xp: 50
```

<!-- Guidelines for the question: https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises. -->

`@possible_answers`
- [Correct answer 1]
- Wrong answer 2
- Wrong answer 3

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- This is an example hint.
- This is an example hint.

`@pre_exercise_code`
```{r}

```

`@sct`
```{r}
# Check https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises on how to write feedback messages for this exercise.
```

---

## Analyzing influence

```yaml
type: MultipleChoiceExercise
key: 9429d31d39
xp: 50
```

<!-- Guidelines for the question: https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises. -->

`@possible_answers`
- [Correct answer 1]
- Wrong answer 2
- Wrong answer 3

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- This is an example hint.
- This is an example hint.

`@pre_exercise_code`
```{r}

```

`@sct`
```{r}
# Check https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises on how to write feedback messages for this exercise.
```
