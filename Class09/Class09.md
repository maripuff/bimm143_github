# Class09: Halloween Mini-Project
Marina Puffer(A16341339)

# 1.Importing candy data:

``` r
candy.file <- "candy-data.txt"
candy=read.csv(candy.file, row.names = 1)
head(candy)
```

                 chocolate fruity caramel peanutyalmondy nougat crispedricewafer
    100 Grand            1      0       1              0      0                1
    3 Musketeers         1      0       0              0      1                0
    One dime             0      0       0              0      0                0
    One quarter          0      0       0              0      0                0
    Air Heads            0      1       0              0      0                0
    Almond Joy           1      0       0              1      0                0
                 hard bar pluribus sugarpercent pricepercent winpercent
    100 Grand       0   1        0        0.732        0.860   66.97173
    3 Musketeers    0   1        0        0.604        0.511   67.60294
    One dime        0   0        0        0.011        0.116   32.26109
    One quarter     0   0        0        0.011        0.511   46.11650
    Air Heads       0   0        0        0.906        0.511   52.34146
    Almond Joy      0   1        0        0.465        0.767   50.34755

## Q1. How many different candy types are in this dataset?

``` r
nrow(candy)
```

    [1] 85

85 different types of candy are in the dataset

## Q2. How many fruity candy types are in the dataset?

``` r
sum(candy$fruity)
```

    [1] 38

38 fruity types of candy are in the dataset

# 2. What is your favorite candy?

## Q3. What is your favorite candy in the dataset and what is it’s `winpercent` value?

My favorite candy is Twix:

``` r
candy["Twix",]$winpercent
```

    [1] 81.64291

Win percent of Twix is 81%

## Q4. What is the `winpercent` value for “Kitkat”?

``` r
candy["Kit Kat",]$winpercent
```

    [1] 76.7686

## Q5. What is the winpercent value for “Tootsie Roll Snack Bars”?

``` r
candy["Tootsie Roll Snack Bars",]$winpercent
```

    [1] 49.6535

## Q6. Is there any variable/column that looks to be on a different scale to the majority of the other columns in the dataset?

``` r
library("skimr")
skim(candy)
```

|                                                  |       |
|:-------------------------------------------------|:------|
| Name                                             | candy |
| Number of rows                                   | 85    |
| Number of columns                                | 12    |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |       |
| Column type frequency:                           |       |
| numeric                                          | 12    |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |       |
| Group variables                                  | None  |

Data summary

**Variable type: numeric**

| skim_variable    | n_missing | complete_rate |  mean |    sd |    p0 |   p25 |   p50 |   p75 |  p100 | hist  |
|:-----------------|----------:|--------------:|------:|------:|------:|------:|------:|------:|------:|:------|
| chocolate        |         0 |             1 |  0.44 |  0.50 |  0.00 |  0.00 |  0.00 |  1.00 |  1.00 | ▇▁▁▁▆ |
| fruity           |         0 |             1 |  0.45 |  0.50 |  0.00 |  0.00 |  0.00 |  1.00 |  1.00 | ▇▁▁▁▆ |
| caramel          |         0 |             1 |  0.16 |  0.37 |  0.00 |  0.00 |  0.00 |  0.00 |  1.00 | ▇▁▁▁▂ |
| peanutyalmondy   |         0 |             1 |  0.16 |  0.37 |  0.00 |  0.00 |  0.00 |  0.00 |  1.00 | ▇▁▁▁▂ |
| nougat           |         0 |             1 |  0.08 |  0.28 |  0.00 |  0.00 |  0.00 |  0.00 |  1.00 | ▇▁▁▁▁ |
| crispedricewafer |         0 |             1 |  0.08 |  0.28 |  0.00 |  0.00 |  0.00 |  0.00 |  1.00 | ▇▁▁▁▁ |
| hard             |         0 |             1 |  0.18 |  0.38 |  0.00 |  0.00 |  0.00 |  0.00 |  1.00 | ▇▁▁▁▂ |
| bar              |         0 |             1 |  0.25 |  0.43 |  0.00 |  0.00 |  0.00 |  0.00 |  1.00 | ▇▁▁▁▂ |
| pluribus         |         0 |             1 |  0.52 |  0.50 |  0.00 |  0.00 |  1.00 |  1.00 |  1.00 | ▇▁▁▁▇ |
| sugarpercent     |         0 |             1 |  0.48 |  0.28 |  0.01 |  0.22 |  0.47 |  0.73 |  0.99 | ▇▇▇▇▆ |
| pricepercent     |         0 |             1 |  0.47 |  0.29 |  0.01 |  0.26 |  0.47 |  0.65 |  0.98 | ▇▇▇▇▆ |
| winpercent       |         0 |             1 | 50.32 | 14.71 | 22.45 | 39.14 | 47.83 | 59.86 | 84.18 | ▃▇▆▅▂ |

The winpercent variable looks to be on a different scale than the
others, all of the statistics in that row are much greater than the
rest.

## Q7. What do you think a zero and one represent for the `candy$chocolate` column?

A zero means that that particular candy does not contain chocolate, and
a 1 means that the candy does contain chocolate.

## Q8. Plot a histogram of winpercent values

``` r
hist(candy$winpercent)
```

![](Class09_files/figure-commonmark/unnamed-chunk-8-1.png)

## Q9. Is the distribution of winpercent values symmetrical?

No, it is skewed to the right.

## Q10. Is the center of the distribution above or below 50%?

The center is below 50%

## Q11. On average is chocolate candy higher or lower ranked than fruit candy?

``` r
chocolate.rank <-candy$winpercent[as.logical(candy$chocolate)]
mean(chocolate.rank)
```

    [1] 60.92153

``` r
fruity.rank <- candy$winpercent[as.logical(candy$fruity)]
mean(fruity.rank)
```

    [1] 44.11974

On average, the chocolate candy is higher ranked than fruit candy.

## Q12. Is this difference statistically significant?

``` r
t.test(chocolate.rank, fruity.rank)
```


        Welch Two Sample t-test

    data:  chocolate.rank and fruity.rank
    t = 6.2582, df = 68.882, p-value = 2.871e-08
    alternative hypothesis: true difference in means is not equal to 0
    95 percent confidence interval:
     11.44563 22.15795
    sample estimates:
    mean of x mean of y 
     60.92153  44.11974 

Since the p-value is below 0.05 , the difference between the rankings of
fruity and chocolate candy are statistically significant.

# 3. Overall candy rankings

## Q13. What are the five least liked candy types in this set?

``` r
head(candy[order(candy$winpercent),], n=5)
```

                       chocolate fruity caramel peanutyalmondy nougat
    Nik L Nip                  0      1       0              0      0
    Boston Baked Beans         0      0       0              1      0
    Chiclets                   0      1       0              0      0
    Super Bubble               0      1       0              0      0
    Jawbusters                 0      1       0              0      0
                       crispedricewafer hard bar pluribus sugarpercent pricepercent
    Nik L Nip                         0    0   0        1        0.197        0.976
    Boston Baked Beans                0    0   0        1        0.313        0.511
    Chiclets                          0    0   0        1        0.046        0.325
    Super Bubble                      0    0   0        0        0.162        0.116
    Jawbusters                        0    1   0        1        0.093        0.511
                       winpercent
    Nik L Nip            22.44534
    Boston Baked Beans   23.41782
    Chiclets             24.52499
    Super Bubble         27.30386
    Jawbusters           28.12744

Nik L Nip, Boston Baked Beans, Chiclets, Super Bubble, and Jawbusters
are the least liked candy types.

## Q14. What are the top 5 all time favorite candy types out of this set?

``` r
tail(candy[order(candy$winpercent),], n=5)
```

                              chocolate fruity caramel peanutyalmondy nougat
    Snickers                          1      0       1              1      1
    Kit Kat                           1      0       0              0      0
    Twix                              1      0       1              0      0
    Reese's Miniatures                1      0       0              1      0
    Reese's Peanut Butter cup         1      0       0              1      0
                              crispedricewafer hard bar pluribus sugarpercent
    Snickers                                 0    0   1        0        0.546
    Kit Kat                                  1    0   1        0        0.313
    Twix                                     1    0   1        0        0.546
    Reese's Miniatures                       0    0   0        0        0.034
    Reese's Peanut Butter cup                0    0   0        0        0.720
                              pricepercent winpercent
    Snickers                         0.651   76.67378
    Kit Kat                          0.511   76.76860
    Twix                             0.906   81.64291
    Reese's Miniatures               0.279   81.86626
    Reese's Peanut Butter cup        0.651   84.18029

Snickers, Kit Kat, Twix, Reese’s Minis, and Reese’s Peanut Butter cup
are the most favorite.

## Q15. Make a first barplot of candy ranking based on winpercent values.

``` r
library(ggplot2)
ggplot(candy, aes(winpercent, rownames(candy)))+
  geom_col()
```

![](Class09_files/figure-commonmark/unnamed-chunk-13-1.png)

## Q16. This is quite ugly, use the reorder() function to get the bars sorted by winpercent?

``` r
ggplot(candy, aes(winpercent, reorder(rownames(candy),winpercent)))+
  geom_col()
```

![](Class09_files/figure-commonmark/unnamed-chunk-14-1.png)

``` r
#select column by candy$___, set as.logical then designate color
my_cols=rep("black", nrow(candy))
my_cols[as.logical(candy$chocolate)] = "chocolate"
my_cols[as.logical(candy$bar)] = "brown"
my_cols[as.logical(candy$fruity)] = "pink"
my_cols[as.logical(candy$hard)]="grey"
#ggplot using set colors
ggplot(candy) + 
  aes(winpercent, reorder(rownames(candy),winpercent)) +
  geom_col(fill=my_cols) 
```

![](Class09_files/figure-commonmark/unnamed-chunk-15-1.png)

## Q17. What is the worst ranked chocolate candy?

Sixlets

## Q18. What is the best ranked fruity candy?

Starburst

# 4. Taking a look at pricepoint

## Q19. Which candy type is the highest ranked in terms of winpercent for the least money - i.e. offers the most bang for your buck?

``` r
library(ggrepel)

# plot of price vs winpercent
ggplot(candy) +
  aes(winpercent, pricepercent, label=rownames(candy)) +
  geom_point(col=my_cols) + 
  geom_text_repel(col=my_cols, size=3.3, max.overlaps = 52)
```

![](Class09_files/figure-commonmark/unnamed-chunk-16-1.png)

Reese’s Miniatures are the best bang for your buck.

## Q20. What are the top 5 most expensive candy types in the dataset and of these which is the least popular?

``` r
ord <- order(candy$pricepercent, decreasing = TRUE)
head( candy[ord,c(11,12)], n=5 )
```

                             pricepercent winpercent
    Nik L Nip                       0.976   22.44534
    Nestle Smarties                 0.976   37.88719
    Ring pop                        0.965   35.29076
    Hershey's Krackel               0.918   62.28448
    Hershey's Milk Chocolate        0.918   56.49050

The top 5 most expensive candies are Nik L Nip, Nestle Smartiesm Ring
popm Hershey’s Krackel, and Hershey’s Milk Chocolate. Of these, Nik L
Nip is the least popular.

## Q21. Make a barplot again with geom_col() this time using pricepercent and then improve this step by step, first ordering the x-axis by value and finally making a so called “dot chat” or “lollipop” chart by swapping geom_col() for geom_point() + geom_segment().

``` r
ggplot(candy) +
  aes(pricepercent, reorder(rownames(candy), pricepercent)) +
  geom_segment(aes(yend = reorder(rownames(candy), pricepercent), 
                   xend = 0), col="gray40") +
    geom_point()
```

![](Class09_files/figure-commonmark/unnamed-chunk-18-1.png)

# 5. Exploring the correlation structure

``` r
library(corrplot)
```

    corrplot 0.92 loaded

``` r
cij <- cor(candy)
corrplot(cij)
```

![](Class09_files/figure-commonmark/unnamed-chunk-19-1.png)

## Q22. Examining this plot what two variables are anti-correlated (i.e. have minus values)?

Chocolate and fruity are anti-correlated.

## Q23. Similarly, what two variables are most positively correlated?

Chocolate and winpercent are the most positively correlated.

# 6. PCA

``` r
pca <- prcomp(candy, scale=TRUE)
summary(pca)
```

    Importance of components:
                              PC1    PC2    PC3     PC4    PC5     PC6     PC7
    Standard deviation     2.0788 1.1378 1.1092 1.07533 0.9518 0.81923 0.81530
    Proportion of Variance 0.3601 0.1079 0.1025 0.09636 0.0755 0.05593 0.05539
    Cumulative Proportion  0.3601 0.4680 0.5705 0.66688 0.7424 0.79830 0.85369
                               PC8     PC9    PC10    PC11    PC12
    Standard deviation     0.74530 0.67824 0.62349 0.43974 0.39760
    Proportion of Variance 0.04629 0.03833 0.03239 0.01611 0.01317
    Cumulative Proportion  0.89998 0.93832 0.97071 0.98683 1.00000

``` r
plot(pca$x[,1:2]) #plot of main PCA score of PC1 vs PC2
```

![](Class09_files/figure-commonmark/unnamed-chunk-21-1.png)

``` r
plot(pca$x[,1:2], col=my_cols, pch=16)
```

![](Class09_files/figure-commonmark/unnamed-chunk-22-1.png)

``` r
#add color and change plotting character
```

``` r
# Make a new data-frame with our PCA results and candy data
my_data <- cbind(candy, pca$x[,1:3])
p <- ggplot(my_data) + 
        aes(x=PC1, y=PC2, 
            size=winpercent/100,  
            text=rownames(my_data),
            label=rownames(my_data)) +
        geom_point(col=my_cols)

p
```

![](Class09_files/figure-commonmark/unnamed-chunk-23-1.png)

``` r
library(ggrepel)

p + geom_text_repel(size=3.3, col=my_cols, max.overlaps = 52)  + 
  theme(legend.position = "none") +
  labs(title="Halloween Candy PCA Space",
       subtitle="Colored by type: chocolate bar (dark brown), chocolate other (light brown), fruity (red), other (black)",
       caption="Data from 538")
```

![](Class09_files/figure-commonmark/unnamed-chunk-24-1.png)

``` r
#library(plotly)
```

``` r
#ggplotly(p) 
#plotly code does not render to pdf, only HTML
```

``` r
par(mar=c(8,4,2,2))
barplot(pca$rotation[,1], las=2, ylab="PC1 Contribution")
```

![](Class09_files/figure-commonmark/unnamed-chunk-27-1.png)

## Q24. What original variables are picked up strongly by PC1 in the positive direction? Do these make sense to you?

Fruity, hard, and pluribus are picked up strongly by PC1 in the positive
direction. This makes sense because these characteristics show negative
correlations with the other variables. On the corrplot, fruity is highly
negatively correlated with chocolate and is moderately negatively
correlated with several othr variables, such as bar and price. Pluribus
is highly negatively correlated with bar and is weakly negatively
correlated with most other variables. Hard does not show any negative
correlations of high magnitude, but shows small negative coorelations
with most other categories in the plot. PCA shows which variables have
the highest variance, so this plot shows the variables which have the
most negative correlations by placing them on opposite ends of the
scale.
