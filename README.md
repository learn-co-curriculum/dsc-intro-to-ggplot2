# Intro to ggplot2

## To Do 

* [ ] Get Tips Data 
* [ ] Create R Script
* [ ] Create Markdown
* [ ] Create Project 
* [ ] Add images from markdown 

## Lesson Goals 

By the end of this lesson, you will be able to:

* [ ] List here  
* [ ] List here  
* [ ] List here  
* [ ] List here  
* [ ] List here  
* [ ] List here  

# ggplot2 

The thing you often hear a lot about with R is how it's great at making graphics. 
This is true.
If you combine the functionality from a library like `ggplot2` with some of the tools we will look at next session, you'll be a plot pro. 

The library that we're going to focus on today is called `ggplot2`.
Continuing on from what we talked about in Lesson 0, the code below will look somewhat a familiar. 

```{r}
library(readr) # for getting data
library(ggplot2) # for plotting data

tips <- read_csv("tips.csv")

# You can change where this is output above in "Settings (by knit) > Chunk Output in Console"
tips

```

Let's make a scatterplot of our total bill by tips with ggplot.

What do we need to tell ggplot if we want to make a plot of this?

Well, the first thing we should tell ggplot is our data.
If we do this we get a nice blank screen, why?
ggplot has no idea what data we want to plot!

```{r}
ggplot(tips)
```

To change this, we need to tell it! 
How?
We use the `aes()` argument which states for aesthetics.

```{r}
ggplot(tips, aes(x = total_bill, y = tip))
```

What do you now see?

```{r}
ggplot(tips, aes(x = total_bill, y = tip)) +
  geom_point()
```

Now what if we want to keep modifying it?
Let's dissect the code below.

```{r}
ggplot(tips, aes(x = total_bill, y = tip, color = time)) +
  geom_point()
```

```{r}
ggplot(tips, aes(x = total_bill, y = tip, shape = smoker)) +
  geom_point()
```

```{r}
ggplot(tips, aes(x = total_bill, y = tip, color = time, shape = smoker)) +
  geom_point()
```

```{r}
ggplot(tips, aes(x = total_bill, y = tip, color = time, shape = smoker)) +
  geom_point() + 
  facet_wrap(~day)
```

Let's dive into the data a bit more and make a barplot comparing how many counts we have of each day!

What is similar about this plot compared to the ones before?
What is different?

```{r}
ggplot(tips, aes(x = day)) +
  geom_bar()
```

```{r}
ggplot(tips, aes(x = day, fill= smoker)) +
  geom_bar()
```

```{r}
ggplot(tips, aes(x = day, fill= smoker)) +
  geom_bar(position = "dodge")
```

```{r}
ggplot(tips, aes(x = day, fill= smoker)) +
  geom_bar(position = "fill")
```

Let's now take a plot from above that we liked and begin to modify it! 

```{r}
ggplot(tips, aes(x = total_bill, y = tip, color = time, shape = smoker)) +
  geom_point() +
  labs(title = "Bill by Tip", x = "Total Bill", y = "Tip in USD") 
```

```{r}
ggplot(tips, aes(x = total_bill, y = tip, color = time, shape = smoker)) +
  geom_point() +
  labs(title = "Bill by Tip", x = "Total Bill", y = "Tip in USD") +
  theme_minimal()
```
