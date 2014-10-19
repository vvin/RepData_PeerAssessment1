# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data


```r
activity <- read.csv("activity.csv")
```

## What is mean total number of steps taken per day?


Make a histogram of the total number of steps taken each day

```r
stepsums <- tapply(activity$steps, activity$date, sum, na.rm = TRUE)
hist(stepsums, breaks=20)
```

![](./PA1_template_files/figure-html/unnamed-chunk-2-1.png) 

Calculate and report the mean and median total number of steps taken per day

```r
mean(stepsums)
```

```
## [1] 9354.23
```

```r
median(stepsums)
```

```
## [1] 10395
```


## What is the average daily activity pattern?
Make a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)

```r
averaged_intervals <- tapply(activity$steps, activity$interval, mean, na.rm=TRUE)
plot(averaged_intervals, type="l", xlab="Interval ID", ylab="Average steps")
```

![](./PA1_template_files/figure-html/unnamed-chunk-4-1.png) 

Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?

```r
names(which.max(averaged_intervals))
```

```
## [1] "835"
```
## Imputing missing values
Calculate and report the total number of missing values in the dataset (i.e. the total number of rows with NAs)

```r
sum(is.na(activity$steps))
```

```
## [1] 2304
```


## Are there differences in activity patterns between weekdays and weekends?
