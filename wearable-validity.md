---
title: "FINAL ASSIGNMENT"
author: "Sumayyah Musa"
date: "3/12/2021"
output: 
    html_document:
       keep_md: true
---



## Read in and glimpse the data


```r
val_data <- read.csv("wearable_review_data_validity_edited.csv")
```

## Data Cleaning 
### Subsetting the data to select the variables we are interested in


```r
new_data <- subset(val_data, Measured != "EE" & Measured != "HR")

glimpse(new_data)
```

```
## Rows: 1,067
## Columns: 107
## $ X1                          <int> 7, 8, 9, 10, 11, 12, 16, 17, 18, 19, 20, 2…
## $ Author                      <chr> "Fokkema", "Fokkema", "Fokkema", "Fokkema"…
## $ Year                        <int> 2017, 2017, 2017, 2017, 2017, 2017, 2017, …
## $ Substudy                    <chr> "-", "-", "-", "-", "-", "-", "-", "-", "-…
## $ Setting                     <chr> "Controlled", "Controlled", "Controlled", …
## $ Measured                    <chr> "SC", "SC", "SC", "SC", "SC", "SC", "SC", …
## $ Measure_Unit                <chr> "steps/10 min", "steps/10 min", "steps/10 …
## $ Brand                       <chr> "Apple", "Apple", "Apple", "Apple", "Apple…
## $ Device                      <chr> "Watch", "Watch", "Watch", "Watch", "Watch…
## $ device_name                 <chr> "Apple Watch", "Apple Watch", "Apple Watch…
## $ device_year                 <int> 2015, 2015, 2015, 2015, 2015, 2015, 2015, …
## $ Wear_Location               <chr> "Wrist", "Wrist", "Wrist", "Wrist", "Wrist…
## $ Wear_Info                   <chr> "wrist, left", "wrist, left", "wrist, left…
## $ Type                        <chr> "full-text", "full-text", "full-text", "fu…
## $ Good.                       <chr> "y", "y", "y", "y", "y", "y", "y", "y", "y…
## $ Criterion_Measure           <chr> "Manual count", "Manual count", "Manual co…
## $ Criterion_Type              <chr> "manual count", "manual count", "manual co…
## $ Wear_Info_crit              <chr> NA, NA, NA, NA, NA, NA, NA, NA, "thigh, ri…
## $ Wear_Location_crit          <chr> NA, NA, NA, NA, NA, NA, NA, NA, "Thigh", "…
## $ population_n                <chr> "31", "31", "31", "31", "31", "31", "31", …
## $ population_m                <chr> "16", "16", "16", "16", "16", "16", "16", …
## $ population_f                <chr> "15", "15", "15", "15", "15", "15", "15", …
## $ population                  <chr> "healthy adults", "healthy adults", "healt…
## $ age_code                    <chr> "A", "A", "A", "A", "A", "A", "A", "A", "O…
## $ health_code                 <chr> "H", "H", "H", "H", "H", "H", "H", "H", "N…
## $ age                         <chr> "32", "32", "32", "32", "32", "32", "32", …
## $ age_SD                      <dbl> 12.0, 12.0, 12.0, 12.0, 12.0, 12.0, 12.0, …
## $ weight                      <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, "7…
## $ weight_SD                   <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, 3,…
## $ height                      <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, "1…
## $ height_SD                   <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, 1.…
## $ BMI                         <chr> "22.6", "22.6", "22.6", "22.6", "22.6", "2…
## $ BMI_SD                      <dbl> 2.40, 2.40, 2.40, 2.40, 2.40, 2.40, 2.40, …
## $ location                    <chr> "Netherlands", "Netherlands", "Netherlands…
## $ activity_type               <chr> "Walk: Treadmill", "Walk: Treadmill", "Wal…
## $ test_type                   <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ activity_type_code          <chr> "At", "At", "At", "At", "At", "At", "At", …
## $ body_Motion                 <chr> "Nr", "Nr", "Nr", "Nr", "Nr", "Nr", "Nr", …
## $ pace_code                   <chr> "Nm", "Sl", "Sl", "Nm", "Nm", "Nm", "Nm", …
## $ pace_value                  <chr> "1.33", "0.89", "0.89", "1.78", "1.78", "1…
## $ incline_code                <chr> "N", "N", "N", "N", "N", "N", "N", "N", "N…
## $ incline_pct                 <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ activity_details            <chr> "walk, 4.8 km/h, 10 min, Session 2", "walk…
## $ bout_rest                   <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, "y…
## $ epoch                       <chr> "unknown", "unknown", "unknown", "unknown"…
## $ actual_n_analyzed           <int> 31, 31, 31, 31, 31, 31, 31, 31, 33, 33, 32…
## $ trend                       <chr> "good validity", "good validity", "good va…
## $ CC_type                     <chr> "ICC", "ICC", "ICC", "ICC", "ICC", "ICC", …
## $ CC                          <dbl> 0.520, 0.570, 0.730, 0.910, 0.860, 0.930, …
## $ CC_bins                     <chr> "MOD", "MOD", "ST", "VS", "VS", "VS", "WK"…
## $ CC_all                      <chr> "0.52", "0.57", "0.73", "0.91", "0.86", "0…
## $ CC_CI_pct                   <int> 95, 95, 95, 95, 95, 95, 95, 95, 95, 95, NA…
## $ CC_CI_upper                 <chr> "0.74", "0.77", "0.86", "0.95", "0.93", "0…
## $ CC_CI_lower                 <chr> "0.21", "0.27", "0.52", "0.82", "0.72", "0…
## $ CC_pvalue                   <chr> "< .01", "< .01", "< .01", "< .01", "< .01…
## $ CC_significance             <chr> "sig", "sig", "sig", "sig", "sig", "sig", …
## $ ES_type                     <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ ES                          <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ ES_CI_upper                 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ ES_CI_lower                 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ BA_LoA_upper                <chr> "159", "111", "124", "56", "67", "35", "16…
## $ BA_LoA_lower                <chr> "-101", "-74", "-98", "-45", "-65", "-36",…
## $ BA_LoA_width                <dbl> 260.0, 185.0, 222.0, 101.0, 132.0, 71.0, 2…
## $ devicemean                  <dbl> NA, NA, NA, NA, NA, NA, NA, NA, 219.0, 677…
## $ devicemean_SD               <dbl> NA, NA, NA, NA, NA, NA, NA, NA, 20.3, 66.7…
## $ critmean                    <dbl> 1108.0, 953.0, 940.0, 1259.0, 1251.0, 1117…
## $ critmean_SD                 <dbl> 46.0, 46.0, 61.0, 53.0, 54.0, 44.0, 44.0, …
## $ device_v_crit               <chr> "over", "over", "over", "over", "over", "e…
## $ meandiff                    <chr> "29", "18", "13", "6", "1", "0", "22", "19…
## $ meandiff_SD                 <dbl> 12.0, 9.0, 10.0, 5.0, 6.0, 3.0, 13.0, 13.0…
## $ meandiff_CI_upper           <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ meandiff_CI_lower           <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MPE                         <dbl> 0.026173285, 0.018887723, 0.013829787, 0.0…
## $ MPE_bin                     <chr> "± 3%", "± 3%", "± 3%", "± 3%", "± 3%", "±…
## $ MPE_SD                      <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MPE_significance_test       <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MPE_significance_num        <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, "n…
## $ MAD                         <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MAD_SD                      <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MAD_CI_upper                <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MAD_CI_lower                <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MAPE                        <dbl> 0.0260, 0.0190, 0.0140, 0.0050, 0.0010, 0.…
## $ MAPE_bin                    <chr> "less 3%", "less 3%", "less 3%", "less 3%"…
## $ MAPE_SD                     <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, 0.…
## $ MAPE_CI_upper               <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MAPE_CI_lower               <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ RMSE                        <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ equivalencetesting          <chr> "-2.20\nWilcoxon signed-rank test in case …
## $ accuracypct                 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ accuracypct_CI_upper        <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ accuracypct_CI_lower        <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ TEEstandardized             <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ TEEstandardized_CI_upper    <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ TEEstandardized_CI_lower    <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ deviceSE                    <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ deviceCofV                  <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ critCofV                    <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ n_5pctofcrit                <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ n_10pctofcrit               <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ n_15pctofcrit               <lgl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ n_20pctofcrit               <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ n_25pctofcrit               <int> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ systematicbias_slope        <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ systematicbias_intercept    <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ systematicbias_probability  <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ systematicbias_significance <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ Other                       <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
```

```r
attach(new_data) #attach the data so that the variables can be referred by their column names
```

```
## The following object is masked from package:tidyr:
## 
##     population
```


```r
X1 <- as.character(X1)
population_f <- as.numeric(population_f)
```

```
## Warning: NAs introduced by coercion
```

```r
population_m <- as.numeric(population_m)
```

```
## Warning: NAs introduced by coercion
```

```r
BMI <- as.numeric(BMI)
```

```
## Warning: NAs introduced by coercion
```

## Data Cleaning by Variable

### AGE

#### Converting age to categorical variable


```r
new_data <- new_data %>%
        mutate(age_cat = case_when(
                age_code == "C" ~ "Children",
                age_code == "A" ~ "Adults",
                age_code == "OA" ~ "Older Adults"
        ))
attach(new_data)
```

```
## The following objects are masked _by_ .GlobalEnv:
## 
##     BMI, population_f, population_m, X1
```

```
## The following objects are masked from new_data (pos = 3):
## 
##     accuracypct, accuracypct_CI_lower, accuracypct_CI_upper,
##     activity_details, activity_type, activity_type_code,
##     actual_n_analyzed, age, age_code, age_SD, Author, BA_LoA_lower,
##     BA_LoA_upper, BA_LoA_width, BMI, BMI_SD, body_Motion, bout_rest,
##     Brand, CC, CC_all, CC_bins, CC_CI_lower, CC_CI_pct, CC_CI_upper,
##     CC_pvalue, CC_significance, CC_type, critCofV, Criterion_Measure,
##     Criterion_Type, critmean, critmean_SD, Device, device_name,
##     device_v_crit, device_year, deviceCofV, devicemean, devicemean_SD,
##     deviceSE, epoch, equivalencetesting, ES, ES_CI_lower, ES_CI_upper,
##     ES_type, Good., health_code, height, height_SD, incline_code,
##     incline_pct, location, MAD, MAD_CI_lower, MAD_CI_upper, MAD_SD,
##     MAPE, MAPE_bin, MAPE_CI_lower, MAPE_CI_upper, MAPE_SD, meandiff,
##     meandiff_CI_lower, meandiff_CI_upper, meandiff_SD, Measure_Unit,
##     Measured, MPE, MPE_bin, MPE_SD, MPE_significance_num,
##     MPE_significance_test, n_10pctofcrit, n_15pctofcrit, n_20pctofcrit,
##     n_25pctofcrit, n_5pctofcrit, Other, pace_code, pace_value,
##     population, population_f, population_m, population_n, RMSE,
##     Setting, Substudy, systematicbias_intercept,
##     systematicbias_probability, systematicbias_significance,
##     systematicbias_slope, TEEstandardized, TEEstandardized_CI_lower,
##     TEEstandardized_CI_upper, test_type, trend, Type, Wear_Info,
##     Wear_Info_crit, Wear_Location, Wear_Location_crit, weight,
##     weight_SD, X1, Year
```

```
## The following object is masked from package:tidyr:
## 
##     population
```


```r
age_cat <- as.factor(age_cat)
addmargins(table(age_cat)) #frequency table of age, including the total
```

```
## age_cat
##       Adults     Children Older Adults          Sum 
##          847           26          194         1067
```

```r
round(prop.table(table(age_cat))*100, digits = 0) #percentage proportion of each category
```

```
## age_cat
##       Adults     Children Older Adults 
##           79            2           18
```

```r
sum(is.na(age_cat))
```

```
## [1] 0
```

### GENDER


```r
#studies that had equal number of male and female participants were recoded as neutral.
new_data <- new_data %>%
        mutate(gender = case_when(
                population_m > population_f ~ "Male",
                population_m < population_f ~ "Female",
                population_m == population_f ~ "Neutral"
        ))
attach(new_data)
```

```
## The following objects are masked _by_ .GlobalEnv:
## 
##     age_cat, BMI, population_f, population_m, X1
```

```
## The following objects are masked from new_data (pos = 3):
## 
##     accuracypct, accuracypct_CI_lower, accuracypct_CI_upper,
##     activity_details, activity_type, activity_type_code,
##     actual_n_analyzed, age, age_cat, age_code, age_SD, Author,
##     BA_LoA_lower, BA_LoA_upper, BA_LoA_width, BMI, BMI_SD, body_Motion,
##     bout_rest, Brand, CC, CC_all, CC_bins, CC_CI_lower, CC_CI_pct,
##     CC_CI_upper, CC_pvalue, CC_significance, CC_type, critCofV,
##     Criterion_Measure, Criterion_Type, critmean, critmean_SD, Device,
##     device_name, device_v_crit, device_year, deviceCofV, devicemean,
##     devicemean_SD, deviceSE, epoch, equivalencetesting, ES,
##     ES_CI_lower, ES_CI_upper, ES_type, Good., health_code, height,
##     height_SD, incline_code, incline_pct, location, MAD, MAD_CI_lower,
##     MAD_CI_upper, MAD_SD, MAPE, MAPE_bin, MAPE_CI_lower, MAPE_CI_upper,
##     MAPE_SD, meandiff, meandiff_CI_lower, meandiff_CI_upper,
##     meandiff_SD, Measure_Unit, Measured, MPE, MPE_bin, MPE_SD,
##     MPE_significance_num, MPE_significance_test, n_10pctofcrit,
##     n_15pctofcrit, n_20pctofcrit, n_25pctofcrit, n_5pctofcrit, Other,
##     pace_code, pace_value, population, population_f, population_m,
##     population_n, RMSE, Setting, Substudy, systematicbias_intercept,
##     systematicbias_probability, systematicbias_significance,
##     systematicbias_slope, TEEstandardized, TEEstandardized_CI_lower,
##     TEEstandardized_CI_upper, test_type, trend, Type, Wear_Info,
##     Wear_Info_crit, Wear_Location, Wear_Location_crit, weight,
##     weight_SD, X1, Year
```

```
## The following objects are masked from new_data (pos = 4):
## 
##     accuracypct, accuracypct_CI_lower, accuracypct_CI_upper,
##     activity_details, activity_type, activity_type_code,
##     actual_n_analyzed, age, age_code, age_SD, Author, BA_LoA_lower,
##     BA_LoA_upper, BA_LoA_width, BMI, BMI_SD, body_Motion, bout_rest,
##     Brand, CC, CC_all, CC_bins, CC_CI_lower, CC_CI_pct, CC_CI_upper,
##     CC_pvalue, CC_significance, CC_type, critCofV, Criterion_Measure,
##     Criterion_Type, critmean, critmean_SD, Device, device_name,
##     device_v_crit, device_year, deviceCofV, devicemean, devicemean_SD,
##     deviceSE, epoch, equivalencetesting, ES, ES_CI_lower, ES_CI_upper,
##     ES_type, Good., health_code, height, height_SD, incline_code,
##     incline_pct, location, MAD, MAD_CI_lower, MAD_CI_upper, MAD_SD,
##     MAPE, MAPE_bin, MAPE_CI_lower, MAPE_CI_upper, MAPE_SD, meandiff,
##     meandiff_CI_lower, meandiff_CI_upper, meandiff_SD, Measure_Unit,
##     Measured, MPE, MPE_bin, MPE_SD, MPE_significance_num,
##     MPE_significance_test, n_10pctofcrit, n_15pctofcrit, n_20pctofcrit,
##     n_25pctofcrit, n_5pctofcrit, Other, pace_code, pace_value,
##     population, population_f, population_m, population_n, RMSE,
##     Setting, Substudy, systematicbias_intercept,
##     systematicbias_probability, systematicbias_significance,
##     systematicbias_slope, TEEstandardized, TEEstandardized_CI_lower,
##     TEEstandardized_CI_upper, test_type, trend, Type, Wear_Info,
##     Wear_Info_crit, Wear_Location, Wear_Location_crit, weight,
##     weight_SD, X1, Year
```

```
## The following object is masked from package:tidyr:
## 
##     population
```


```r
gender <- as.factor(gender)
addmargins(table(gender))
```

```
## gender
##  Female    Male Neutral     Sum 
##     315     482     257    1054
```

```r
round(prop.table(table(gender))*100, digits = 0)
```

```
## gender
##  Female    Male Neutral 
##      30      46      24
```

```r
sum(is.na(new_data$gender))
```

```
## [1] 13
```

```r
new_data <- drop_na(new_data, gender)
```

### BMI


```r
summary(BMI)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
##   20.90   23.20   24.20   24.49   26.00   30.80     522
```

```r
new_data <- new_data %>%
        mutate(bmi_cat = case_when(
                BMI > 18.5 & BMI < 24.9 ~ "Normal weight",
                BMI > 24.9 & BMI < 29.9 ~ "Overweight",
                BMI > 29.9 ~ "Obese"
        ))
```


```r
new_data$bmi_cat <- as.factor(new_data$bmi_cat)
addmargins(table(new_data$bmi_cat))
```

```
## 
## Normal weight         Obese    Overweight           Sum 
##           316           166           220           702
```

```r
round(prop.table(table(new_data$bmi_cat))*100, digits = 0) #percentage
```

```
## 
## Normal weight         Obese    Overweight 
##            45            24            31
```

```r
sum(is.na(new_data$bmi_cat))
```

```
## [1] 352
```

### Wear Location


```r
new_data$Wear_Location <- as.factor(new_data$Wear_Location)
addmargins(table(new_data$Wear_Location))
```

```
## 
##       LAF     Thigh     Torso Upper Arm Waist/Hip     Wrist       Sum 
##        67         1        93         6       308       579      1054
```

```r
round(prop.table(table(new_data$Wear_Location))*100, digits = 0) #percentage
```

```
## 
##       LAF     Thigh     Torso Upper Arm Waist/Hip     Wrist 
##         6         0         9         1        29        55
```

```r
sum(is.na(new_data$Wear_Location))
```

```
## [1] 0
```

### MPE


```r
summary(new_data$MPE)
```

```
##     Min.  1st Qu.   Median     Mean  3rd Qu.     Max.     NA's 
## -1.00000 -0.09711 -0.01440 -0.06913  0.00246  5.30000      187
```

We can remove the missing values


```r
#rename our final data as df 
df <- drop_na(new_data, MPE)
```


```r
summary(df$MPE)
```

```
##      Min.   1st Qu.    Median      Mean   3rd Qu.      Max. 
## -1.000000 -0.097111 -0.014400 -0.069128  0.002463  5.300000
```

```r
round(stat.desc(df$MPE),3)
```

```
##      nbr.val     nbr.null       nbr.na          min          max        range 
##      867.000       46.000        0.000       -1.000        5.300        6.300 
##          sum       median         mean      SE.mean CI.mean.0.95          var 
##      -59.934       -0.014       -0.069        0.012        0.023        0.117 
##      std.dev     coef.var 
##        0.341       -4.939
```

Grand mean and median of the MPE are -0.069% and -0.014% respectively, which means that generally the devices were relatively accurate in measuring step count.


```r
mpe_hist <- ggplot(df, aes(MPE)) + 
                  geom_histogram(bins = 25) +
                  theme_classic()
                  #facet_wrap(~ age_category)
plot(mpe_hist)
```

![](Part-1_files/figure-html/unnamed-chunk-14-1.png)<!-- -->

The histogram above indicates the presence of potential outliers. The distribution is positively skewed and leptokurtic (the values are closely spread and concentrated around the 0% mark).


```r
mpe_box <- ggplot(df, aes(MPE)) + 
                geom_boxplot() +
                coord_flip() +
                theme_classic()
                #facet_wrap(~ age_cat)
plot(mpe_box)
```

![](Part-1_files/figure-html/unnamed-chunk-15-1.png)<!-- -->

This is also evident by the box plot. Let's examine the extreme outliers by using the identify_outlier function.


```r
#A dataframe containing the extreme outliers
df_out <- df %>%
  identify_outliers("MPE") %>%
        filter(is.extreme == TRUE)
```

Most of the 110 extreme outliers had the activity type of ADL or walking (overground, treadmill). We will merge the outlier dataframe with our original data


```r
total <- merge(df,df_out, all.x = TRUE)
table(total$is.extreme)
```

```
## 
## TRUE 
##  110
```


```r
#renaming those no extreme as FALSE instead of NA
total$is.extreme[is.na(total$is.extreme)] <- FALSE
table(total$is.extreme)
```

```
## 
## FALSE  TRUE 
##   757   110
```


```r
#subsetting the non-outliers in the data
df_val <- subset(total, is.extreme != TRUE)
```


```r
summary(df_val$MPE)
```

```
##      Min.   1st Qu.    Median      Mean   3rd Qu.      Max. 
## -0.394600 -0.058500 -0.009009 -0.032625  0.002595  0.294000
```

```r
table(df_val$MPE_bin)
```

```
## 
##     ± 10%      ± 3% less -10%  less -3%  more 10%   more 3% 
##        29       364        11       256        21        76
```

```r
round(prop.table(table(df_val$MPE_bin))*100, digits = 0) #percentage
```

```
## 
##     ± 10%      ± 3% less -10%  less -3%  more 10%   more 3% 
##         4        48         1        34         3        10
```

### Brand


```r
df_val$Brand <- as.factor(df_val$Brand)
addmargins(table(df_val$Brand))
```

```
## 
##    Apple   Fitbit   Garmin      Mio   Misfit    Polar  Samsung Withings 
##       19      499      118        5       21       27       14       49 
##   Xiaomi      Sum 
##        5      757
```

```r
round(prop.table(table(df_val$Brand))*100, digits = 0) #percentage
```

```
## 
##    Apple   Fitbit   Garmin      Mio   Misfit    Polar  Samsung Withings 
##        3       66       16        1        3        4        2        6 
##   Xiaomi 
##        1
```

```r
sum(is.na(df_val$Brand))
```

```
## [1] 0
```


```r
df_val <- subset(df_val, Brand != "Mio" & Brand != "Xiaomi")
```


```r
mpe_hist_clean <- ggplot(df_val, aes(MPE)) + 
                  geom_histogram(bins = 30) +
                  theme_classic()
                  #facet_wrap(~ age_cat)
plot(mpe_hist_clean)
```

![](Part-1_files/figure-html/unnamed-chunk-23-1.png)<!-- -->

The distribution looks better now that the outliers have been removed


```r
mpe_box_clean <- ggplot(df_val, aes(MPE)) + 
                  geom_boxplot() +
                  coord_flip() +
                  theme_classic()
                  #facet_wrap(~ age_cat)
plot(mpe_box_clean)
```

![](Part-1_files/figure-html/unnamed-chunk-24-1.png)<!-- -->

The boxplot is also much better, there is no evidence of extreme outliers.


```r
table(df_val$Setting)
```

```
## 
##  Controlled Free-Living 
##         687          60
```

```r
round(prop.table(table(df_val$Setting))*100, digits = 0) #percentage
```

```
## 
##  Controlled Free-Living 
##          92           8
```

```r
mpe_box_set <- ggplot(df_val, aes(MPE, fill = Setting)) + 
                geom_boxplot() +
                coord_flip() +
                #facet_wrap(~ age_cat) +
                theme_classic()
plot(mpe_box_set)
```

![](Part-1_files/figure-html/unnamed-chunk-25-1.png)<!-- -->


```r
mpe_box_brand <- ggplot(df_val, aes(MPE, fill = Brand)) + 
                geom_boxplot() +
                coord_flip() +
                #facet_wrap(~ age_cat) +
                theme_classic()
plot(mpe_box_brand)
```

![](Part-1_files/figure-html/unnamed-chunk-26-1.png)<!-- -->


```r
table(df_val$Setting)
```

```
## 
##  Controlled Free-Living 
##         687          60
```

```r
df_val %>%
        group_by(Brand, Setting
                 ) %>%
        summarize(count = n())
```

```
## `summarise()` has grouped output by 'Brand'. You can override using the `.groups` argument.
```

```
## # A tibble: 13 x 3
## # Groups:   Brand [7]
##    Brand    Setting     count
##    <fct>    <chr>       <int>
##  1 Apple    Controlled     18
##  2 Apple    Free-Living     1
##  3 Fitbit   Controlled    459
##  4 Fitbit   Free-Living    40
##  5 Garmin   Controlled    113
##  6 Garmin   Free-Living     5
##  7 Misfit   Controlled     13
##  8 Misfit   Free-Living     8
##  9 Polar    Controlled     24
## 10 Polar    Free-Living     3
## 11 Samsung  Controlled     14
## 12 Withings Controlled     46
## 13 Withings Free-Living     3
```

The above shows that only Fitbit has enough studies in free living conditions to examine for validity, while all brands except from Mio and Xiaomi have enough studies in controlled setting.

## Filtering data for plotting
### Summary statistics by the groups


```r
#By age
df_val %>%
        group_by(age_cat, Setting
                 ) %>%
        get_summary_stats(MPE, type = "mean_sd")
```

```
## # A tibble: 6 x 6
##   Setting     age_cat      variable     n   mean    sd
##   <chr>       <chr>        <chr>    <dbl>  <dbl> <dbl>
## 1 Controlled  Adults       MPE        551 -0.028 0.09 
## 2 Free-Living Adults       MPE         41  0.02  0.154
## 3 Controlled  Children     MPE         14 -0.041 0.056
## 4 Free-Living Children     MPE          9  0.102 0.111
## 5 Controlled  Older Adults MPE        122 -0.078 0.108
## 6 Free-Living Older Adults MPE         10 -0.017 0.169
```


```r
#By gender
df_val %>%
        group_by(gender, Setting) %>%
        get_summary_stats(MPE, type = "mean_sd")
```

```
## # A tibble: 6 x 6
##   Setting     gender  variable     n   mean    sd
##   <chr>       <chr>   <chr>    <dbl>  <dbl> <dbl>
## 1 Controlled  Female  MPE        156 -0.025 0.08 
## 2 Free-Living Female  MPE         32  0.026 0.142
## 3 Controlled  Male    MPE        316 -0.047 0.108
## 4 Free-Living Male    MPE         23 -0.011 0.162
## 5 Controlled  Neutral MPE        215 -0.033 0.083
## 6 Free-Living Neutral MPE          5  0.193 0.045
```


```r
#by BMI
df_val %>%
        group_by(bmi_cat, Setting) %>%
        get_summary_stats(MPE, type = "mean_sd")
```

```
## # A tibble: 8 x 6
##   Setting     bmi_cat       variable     n   mean    sd
##   <chr>       <fct>         <chr>    <dbl>  <dbl> <dbl>
## 1 Controlled  Normal weight MPE        201 -0.002 0.084
## 2 Free-Living Normal weight MPE         14  0.101 0.103
## 3 Controlled  Obese         MPE        130 -0.028 0.054
## 4 Free-Living Obese         MPE         14 -0.033 0.139
## 5 Controlled  Overweight    MPE        144 -0.059 0.09 
## 6 Free-Living Overweight    MPE         16  0.009 0.146
## 7 Controlled  <NA>          MPE        212 -0.061 0.115
## 8 Free-Living <NA>          MPE         16  0.03  0.188
```


```r
#by wear location
df_val %>%
        group_by(Wear_Location, Setting) %>%
        get_summary_stats(MPE, type = "mean_sd")
```

```
## # A tibble: 10 x 6
##    Setting     Wear_Location variable     n   mean     sd
##    <chr>       <fct>         <chr>    <dbl>  <dbl>  <dbl>
##  1 Controlled  LAF           MPE         50 -0.044  0.11 
##  2 Free-Living LAF           MPE          1  0.038 NA    
##  3 Controlled  Thigh         MPE          1 -0.308 NA    
##  4 Controlled  Torso         MPE         64 -0.036  0.108
##  5 Free-Living Torso         MPE          1  0.111 NA    
##  6 Controlled  Upper Arm     MPE          6 -0.021  0.02 
##  7 Controlled  Waist/Hip     MPE        207 -0.035  0.092
##  8 Free-Living Waist/Hip     MPE         26  0.032  0.108
##  9 Controlled  Wrist         MPE        359 -0.037  0.092
## 10 Free-Living Wrist         MPE         32  0.018  0.186
```


```r
#relevel factors
df_val$age_cat <- fct_relevel(df_val$age_cat, c("Children","Adults","Older Adults"))
df_val$gender <- fct_relevel(df_val$gender, c("Female","Male","Neutral"))
df_val$bmi_cat <- fct_relevel(df_val$bmi_cat, c("Normal weight","Overweight","Obese"))
df_val$Wear_Location <- fct_relevel(df_val$Wear_Location, c("Wrist","Waist/Hip","Torso","LAF","Upper Arm", "Thigh"))
```

# Filter MPE by setting and removing those with less than 10 comparisons


```r
df_val_control <- filter(df_val, Setting == "Controlled", Wear_Location != "Thigh", Wear_Location != "Upper Arm")
df_val_free <- filter(df_val, Setting == "Free-Living", age_cat != "Children", gender != "Neutral", Wear_Location != "LAF", Wear_Location != "Torso")
```

## Controlled setting
### Validity of Step count in controlled setting - Overall


```r
addmargins(table(df_val_control$MPE_bin))
```

```
## 
##     ± 3% less -3%  more 3%      Sum 
##      355      249       76      680
```

```r
round(prop.table(table(df_val_control$MPE_bin))*100, digits = 0) #percentage
```

```
## 
##     ± 3% less -3%  more 3% 
##       52       37       11
```

```r
summary(df_val_control$MPE)
```

```
##       Min.    1st Qu.     Median       Mean    3rd Qu.       Max. 
## -0.3946000 -0.0586250 -0.0110000 -0.0369691  0.0008064  0.2940000
```

The overall tendency was to underestimate step count in control setting (mean = -0.04%, median = -0.01%)

## Free living setting
### Validity of Step count in free living setting - Overall


```r
addmargins(table(df_val_free$MPE_bin))
```

```
## 
##     ± 10% less -10%  more 10%       Sum 
##        24        10        13        47
```

```r
round(prop.table(table(df_val_free$MPE_bin))*100, digits = 0) #percentage
```

```
## 
##     ± 10% less -10%  more 10% 
##        51        21        28
```

```r
summary(df_val_free$MPE)
```

```
##       Min.    1st Qu.     Median       Mean    3rd Qu.       Max. 
## -0.3375604 -0.0832073  0.0223357  0.0009686  0.1028896  0.2835438
```

The overall tendency was to accurately estimate step count in free living setting (mean = 0.0009%, median = 0.02%)

## Controlled Setting
### Validity of Step count by Age in Controlled setting
* Dashed grey lines indicate ± 3% measurement error


```r
#options(repr.plot.width = 25, repr.plot.height = 8)
df_val_agecontrol_plot <- ggplot(df_val_control, aes(x = Brand, y = MPE, colour = Brand)) +
                    geom_boxplot() +
                    geom_beeswarm(dodge.width = 0.2, cex = 0.2, alpha = 0.08) +   
                    geom_hline(yintercept = 0) +  
                    geom_hline(yintercept = 0.03, size = 0.5, colour = "grey", linetype = "dashed") + 
                    geom_hline(yintercept = -0.03, size = 0.5, colour = "grey", linetype = "dashed") +   
                    scale_y_continuous(limits=c(-0.1, 0.1), #labels = percent
                                       ) +
                    ylab("Step MPE (%)") +
                    scale_colour_brewer(palette="Dark2") +
                    theme_bw() +
                    theme(axis.text.x = element_text(colour = "grey20", size = 10, angle = 90, hjust = 0.5, 
                                                     vjust = 0.5),
                        axis.text.y = element_text(colour = "grey20", size = 10),
                        strip.text = element_text(face = "italic"),
                        text = element_text(size = 12)) +
                    facet_wrap(~ age_cat)
plot(df_val_agecontrol_plot)
```

```
## Warning: Removed 141 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 1 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 96 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 44 rows containing missing values (position_beeswarm).
```

![](Part-1_files/figure-html/unnamed-chunk-36-1.png)<!-- -->
### Validity of step count by gender in controlled setting


```r
df_val_sexcontrol_plot <- ggplot(df_val_control, aes(x = Brand, y = MPE, colour = Brand)) +
                    geom_boxplot() +
                    geom_beeswarm(dodge.width = 0.2, cex = 0.2, alpha = 0.08) +   
                    geom_hline(yintercept = 0) +  
                    geom_hline(yintercept = 0.03, size = 0.5, colour = "grey", linetype = "dashed") + 
                    geom_hline(yintercept = -0.03, size = 0.5, colour = "grey", linetype = "dashed") +   
                    scale_y_continuous(limits=c(-0.1, 0.1), #labels = percent
                                       ) +
                    ylab("Step MPE (%)") +
                    scale_colour_brewer(palette="Dark2") +
                    theme_bw() +
                    theme(axis.text.x = element_text(colour = "grey20", size = 10, angle = 90, hjust = 0.5, 
                                                     vjust = 0.5),
                        axis.text.y = element_text(colour = "grey20", size = 10),
                        strip.text = element_text(face = "italic"),
                        text = element_text(size = 12)) +
                    facet_wrap(~ gender)
plot(df_val_sexcontrol_plot)
```

```
## Warning: Removed 141 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 27 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 85 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 29 rows containing missing values (position_beeswarm).
```

![](Part-1_files/figure-html/unnamed-chunk-37-1.png)<!-- -->

### Validity of step count by BMI in controlled setting


```r
df_val_bmicontrol_plot <- ggplot(df_val_control, aes(x = Brand, y = MPE, colour = Brand)) +
                    geom_boxplot() +
                    geom_beeswarm(dodge.width = 0.2, cex = 0.2, alpha = 0.08) +   
                    geom_hline(yintercept = 0) +  
                    geom_hline(yintercept = 0.03, size = 0.5, colour = "grey", linetype = "dashed") + 
                    geom_hline(yintercept = -0.03, size = 0.5, colour = "grey", linetype = "dashed") +   
                    scale_y_continuous(limits=c(-0.1, 0.1), #labels = percent
                                       ) +
                    ylab("Step MPE (%)") +
                    scale_colour_brewer(palette="Dark2") +
                    theme_bw() +
                    theme(axis.text.x = element_text(colour = "grey20", size = 10, angle = 90, hjust = 0.5, 
                                                     vjust = 0.5),
                        axis.text.y = element_text(colour = "grey20", size = 10),
                        strip.text = element_text(face = "italic"),
                        text = element_text(size = 12)) +
                    facet_wrap(~ bmi_cat)
plot(df_val_bmicontrol_plot)
```

```
## Warning: Removed 141 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 27 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 36 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 12 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 66 rows containing missing values (position_beeswarm).
```

![](Part-1_files/figure-html/unnamed-chunk-38-1.png)<!-- -->

### Validity of step count by Wear location in controlled setting


```r
df_val_wlcontrol_plot <- ggplot(df_val_control, aes(x = Brand, y = MPE, colour = Brand)) +
                    geom_boxplot() +
                    geom_beeswarm(dodge.width = 0.2, cex = 0.2, alpha = 0.08) +   
                    geom_hline(yintercept = 0) +  
                    geom_hline(yintercept = 0.03, size = 0.5, colour = "grey", linetype = "dashed") + 
                    geom_hline(yintercept = -0.03, size = 0.5, colour = "grey", linetype = "dashed") +   
                    scale_y_continuous(limits=c(-0.1, 0.1), #labels = percent
                                       ) +
                    ylab("Step MPE (%)") +
                    scale_colour_brewer(palette="Dark2") +
                    theme_bw() +
                    theme(axis.text.x = element_text(colour = "grey20", size = 10, angle = 90, hjust = 0.5, 
                                                     vjust = 0.5),
                        axis.text.y = element_text(colour = "grey20", size = 10),
                        strip.text = element_text(face = "italic"),
                        text = element_text(size = 12)) +
                    facet_wrap(~ Wear_Location)
plot(df_val_wlcontrol_plot)
```

```
## Warning: Removed 141 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 81 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 33 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 13 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 14 rows containing missing values (position_beeswarm).
```

![](Part-1_files/figure-html/unnamed-chunk-39-1.png)<!-- -->


```r
figure2 <- plot_grid(df_val_agecontrol_plot, df_val_sexcontrol_plot, df_val_bmicontrol_plot, df_val_wlcontrol_plot,
                     labels = c('A','B','C','D'), label_size = 12)
```

```
## Warning: Removed 141 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 1 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 96 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 44 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 141 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 27 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 85 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 29 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 141 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 27 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 36 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 12 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 66 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 141 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 81 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 33 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 13 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 14 rows containing missing values (position_beeswarm).
```

```r
plot(figure2)
```

![](Part-1_files/figure-html/unnamed-chunk-40-1.png)<!-- -->


```r
ggsave("figure2.pdf", plot = figure2, width = 18, height = 16)
```

## Free living Setting
### Validity of Step count by Age in free living setting
* Dashed grey lines indicate ± 10% measurement error


```r
df_val_agefree_plot <- ggplot(df_val_free, aes(x = Brand, y = MPE, colour = Brand)) +
                    geom_boxplot() +
                    geom_beeswarm(dodge.width = 0.2, cex = 0.2, alpha = 0.08) +   
                    geom_hline(yintercept = 0) +  
                    geom_hline(yintercept = 0.1, size = 0.5, colour = "grey", linetype = "dashed") + 
                    geom_hline(yintercept = -0.1, size = 0.5, colour = "grey", linetype = "dashed") +   
                    scale_y_continuous(limits=c(-0.2, 0.2), #labels = percent
                                       ) +
                    ylab("Step MPE (%)") +
                    scale_colour_brewer(palette="Dark2") +
                    theme_bw() +
                    theme(axis.text.x = element_text(colour = "grey20", size = 10, angle = 90, hjust = 0.5, 
                                                     vjust = 0.5),
                        axis.text.y = element_text(colour = "grey20", size = 10),
                        strip.text = element_text(face = "italic"),
                        text = element_text(size = 12)) +
                    facet_wrap(~ age_cat)
plot(df_val_agefree_plot)
```

```
## Warning: Removed 11 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 8 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 3 rows containing missing values (position_beeswarm).
```

![](Part-1_files/figure-html/unnamed-chunk-42-1.png)<!-- -->

### Validity of step count by gender in free living setting


```r
df_val_sexfree_plot <- ggplot(df_val_free, aes(x = Brand, y = MPE, colour = Brand)) +
                    geom_boxplot() +
                    geom_beeswarm(dodge.width = 0.2, cex = 0.2, alpha = 0.08) +   
                    geom_hline(yintercept = 0) +  
                    geom_hline(yintercept = 0.1, size = 0.5, colour = "grey", linetype = "dashed") + 
                    geom_hline(yintercept = -0.1, size = 0.5, colour = "grey", linetype = "dashed") +   
                    scale_y_continuous(limits=c(-0.2, 0.2), #labels = percent
                                       ) +
                    ylab("Step MPE (%)") +
                    scale_colour_brewer(palette="Dark2") +
                    theme_bw() +
                    theme(axis.text.x = element_text(colour = "grey20", size = 10, angle = 90, hjust = 0.5, 
                                                     vjust = 0.5),
                        axis.text.y = element_text(colour = "grey20", size = 10),
                        strip.text = element_text(face = "italic"),
                        text = element_text(size = 12)) +
                    facet_wrap(~ gender)
plot(df_val_sexfree_plot)
```

```
## Warning: Removed 11 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 5 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 6 rows containing missing values (position_beeswarm).
```

![](Part-1_files/figure-html/unnamed-chunk-43-1.png)<!-- -->

### Validity of step count by BMI in free living setting


```r
df_val_bmifree_plot <- ggplot(df_val_free, aes(x = Brand, y = MPE, colour = Brand)) +
                    geom_boxplot() +
                    geom_beeswarm(dodge.width = 0.2, cex = 0.2, alpha = 0.08) +   
                    geom_hline(yintercept = 0) +  
                    geom_hline(yintercept = 0.1, size = 0.5, colour = "grey", linetype = "dashed") + 
                    geom_hline(yintercept = -0.1, size = 0.5, colour = "grey", linetype = "dashed") +   
                    scale_y_continuous(limits=c(-0.2, 0.2), #labels = percent
                                       ) +
                    ylab("Step MPE (%)") +
                    scale_colour_brewer(palette="Dark2") +
                    theme_bw() +
                    theme(axis.text.x = element_text(colour = "grey20", size = 10, angle = 90, hjust = 0.5, 
                                                     vjust = 0.5),
                        axis.text.y = element_text(colour = "grey20", size = 10),
                        strip.text = element_text(face = "italic"),
                        text = element_text(size = 12)) +
                    facet_wrap(~ bmi_cat)
plot(df_val_bmifree_plot)
```

```
## Warning: Removed 11 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 1 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 3 rows containing missing values (position_beeswarm).

## Warning: Removed 3 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 4 rows containing missing values (position_beeswarm).
```

![](Part-1_files/figure-html/unnamed-chunk-44-1.png)<!-- -->

### Validity of step count by Wear location in fee living setting


```r
df_val_wlfree_plot <- ggplot(df_val_free, aes(x = Brand, y = MPE, colour = Brand)) +
                    geom_boxplot() +
                    geom_beeswarm(dodge.width = 0.2, cex = 0.2, alpha = 0.08) +   
                    geom_hline(yintercept = 0) +  
                    geom_hline(yintercept = 0.1, size = 0.5, colour = "grey", linetype = "dashed") + 
                    geom_hline(yintercept = -0.1, size = 0.5, colour = "grey", linetype = "dashed") +   
                    scale_y_continuous(limits=c(-0.2, 0.2), #labels = percent
                                       ) +
                    ylab("Step MPE (%)") +
                    scale_colour_brewer(palette="Dark2") +
                    theme_bw() +
                    theme(axis.text.x = element_text(colour = "grey20", size = 10, angle = 90, hjust = 0.5, 
                                                     vjust = 0.5),
                        axis.text.y = element_text(colour = "grey20", size = 10),
                        strip.text = element_text(face = "italic"),
                        text = element_text(size = 12)) +
                    facet_wrap(~ Wear_Location)
plot(df_val_wlfree_plot)
```

```
## Warning: Removed 11 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 10 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 1 rows containing missing values (position_beeswarm).
```

![](Part-1_files/figure-html/unnamed-chunk-45-1.png)<!-- -->


```r
figure3 <- plot_grid(df_val_agefree_plot, df_val_sexfree_plot, df_val_bmifree_plot, df_val_wlfree_plot, labels = c('A','B','C','D'), label_size = 12)
```

```
## Warning: Removed 11 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 8 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 3 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 11 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 5 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 6 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 11 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 1 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 3 rows containing missing values (position_beeswarm).

## Warning: Removed 3 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 4 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 11 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 10 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 1 rows containing missing values (position_beeswarm).
```

```r
plot(figure3)
```

![](Part-1_files/figure-html/unnamed-chunk-46-1.png)<!-- -->


```r
ggsave("figure3.pdf", plot = figure3, width = 18, height = 16)
```

## Comparing Means between population groups
### Computing Kruskal Wallis Test

We want to know if there is any significant differences between the Step MPE of the different population groups by brands regardless of settings.

#Filtering data by brand for comparison


```r
df_val_apple <- filter(df_val, Brand == "Apple")
df_val_fitbit <- filter(df_val, Brand == "Fitbit")
df_val_garmin <- filter(df_val, Brand == "Garmin")
df_val_misfit <- filter(df_val, Brand == "Misfit")
df_val_polar <- filter(df_val, Brand == "Polar")
df_val_samsung <- filter(df_val, Brand == "Samsung")
df_val_withings <- filter(df_val, Brand == "Withings")
```

### Age

Polar devices was commented out because it only had observations for adults


```r
kruskal.test(MPE ~ age_cat, data = df_val_apple)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by age_cat
## Kruskal-Wallis chi-squared = 0.53333, df = 1, p-value = 0.4652
```

```r
kruskal.test(MPE ~ age_cat, data = df_val_fitbit)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by age_cat
## Kruskal-Wallis chi-squared = 27.797, df = 2, p-value = 9.205e-07
```

```r
kruskal.test(MPE ~ age_cat, data = df_val_garmin)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by age_cat
## Kruskal-Wallis chi-squared = 6.4332, df = 2, p-value = 0.04009
```

```r
kruskal.test(MPE ~ age_cat, data = df_val_misfit)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by age_cat
## Kruskal-Wallis chi-squared = 0.032086, df = 1, p-value = 0.8578
```

```r
#kruskal.test(MPE ~ age_cat, data = df_val_polar)
kruskal.test(MPE ~ age_cat, data = df_val_samsung)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by age_cat
## Kruskal-Wallis chi-squared = 0.13846, df = 1, p-value = 0.7098
```

```r
kruskal.test(MPE ~ age_cat, data = df_val_withings)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by age_cat
## Kruskal-Wallis chi-squared = 2.9009, df = 1, p-value = 0.08853
```

```r
#table(df_val_polar$age_cat)
```

As only the p-values of Fitbit and Garmin devices were less than the significance level 0.05, we can conclude that there are significant differences in the validity of these devices between age groups.

From the output of the Kruskal-Wallis test, we know that there is a significant difference between the age groups in Fitbit and Garmin, but we don’t know which pairs of groups are different. We will do a pairwise comparisons to determine the groups that are different, using Dunn's test, a non-parametric pairwise comparison test.


```r
# Pairwise comparisons
pwc_age_fitbit <- df_val_fitbit %>% 
  dunn_test(MPE ~ age_cat, p.adjust.method = "bonferroni") 
pwc_age_fitbit
```

```
## # A tibble: 3 x 9
##   .y.   group1   group2       n1    n2 statistic         p    p.adj p.adj.signif
## * <chr> <chr>    <chr>     <int> <int>     <dbl>     <dbl>    <dbl> <chr>       
## 1 MPE   Children Adults       21   386     -1.12   2.61e-1  7.83e-1 ns          
## 2 MPE   Children Older Ad…    21    92     -3.45   5.68e-4  1.71e-3 **          
## 3 MPE   Adults   Older Ad…   386    92     -5.01   5.35e-7  1.60e-6 ****
```

```r
pwc_age_garmin <- df_val_garmin %>% 
  dunn_test(MPE ~ age_cat, p.adjust.method = "bonferroni") 
pwc_age_garmin
```

```
## # A tibble: 3 x 9
##   .y.   group1   group2          n1    n2 statistic      p p.adj p.adj.signif
## * <chr> <chr>    <chr>        <int> <int>     <dbl>  <dbl> <dbl> <chr>       
## 1 MPE   Children Adults           2    90     1.62  0.105  0.315 ns          
## 2 MPE   Children Older Adults     2    26     0.954 0.340  1     ns          
## 3 MPE   Adults   Older Adults    90    26    -2.06  0.0394 0.118 ns
```


```r
# Visualization: box plots with significance
pwc_age_fitbit <- pwc_age_fitbit %>% add_xy_position(x = "age_cat")
age_sig <- ggboxplot(df_val_fitbit, x = "age_cat", y = "MPE") +
  stat_pvalue_manual(pwc_age_fitbit, hide.ns = TRUE) +
  labs(caption = get_pwc_label(pwc_age_fitbit))
plot(age_sig)
```

![](Part-1_files/figure-html/unnamed-chunk-51-1.png)<!-- -->

Pairwise Dunn's test between groups showed that only the differences between children and older adults (Dunn’s test, p = 1.71e-03), and between adults and older adults (Dunn's test, p = 1.60e-06) were significant for Fitbit devices. It also showed no significant differences in the Garmin devices, a rather surprising find.

### Gender


```r
kruskal.test(MPE ~ gender, data = df_val_apple)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by gender
## Kruskal-Wallis chi-squared = 9.9338, df = 2, p-value = 0.006965
```

```r
kruskal.test(MPE ~ gender, data = df_val_fitbit)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by gender
## Kruskal-Wallis chi-squared = 3.5704, df = 2, p-value = 0.1678
```

```r
kruskal.test(MPE ~ gender, data = df_val_garmin)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by gender
## Kruskal-Wallis chi-squared = 4.1189, df = 2, p-value = 0.1275
```

```r
kruskal.test(MPE ~ gender, data = df_val_misfit)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by gender
## Kruskal-Wallis chi-squared = 0.010101, df = 1, p-value = 0.9199
```

```r
kruskal.test(MPE ~ gender, data = df_val_polar)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by gender
## Kruskal-Wallis chi-squared = 1.6512, df = 2, p-value = 0.438
```

```r
kruskal.test(MPE ~ gender, data = df_val_samsung)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by gender
## Kruskal-Wallis chi-squared = 6.9886, df = 2, p-value = 0.03037
```

```r
kruskal.test(MPE ~ gender, data = df_val_withings)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by gender
## Kruskal-Wallis chi-squared = 17.037, df = 2, p-value = 0.0001997
```

The p-values of Apple, Samsung and Withings devices were lesser than the significance level 0.05, we can conclude that there are significant differences in the validity of these devices between the gender groups.


```r
# Pairwise comparisons
pwc_sex_apple <- df_val_apple %>% 
  dunn_test(MPE ~ gender, p.adjust.method = "bonferroni") 
pwc_sex_apple
```

```
## # A tibble: 3 x 9
##   .y.   group1 group2     n1    n2 statistic       p   p.adj p.adj.signif
## * <chr> <chr>  <chr>   <int> <int>     <dbl>   <dbl>   <dbl> <chr>       
## 1 MPE   Female Male        1    14     1.45  0.148   0.444   ns          
## 2 MPE   Female Neutral     1     4    -0.159 0.874   1       ns          
## 3 MPE   Male   Neutral    14     4    -2.96  0.00312 0.00937 **
```

```r
pwc_sex_samsung <- df_val_samsung %>% 
  dunn_test(MPE ~ gender, p.adjust.method = "bonferroni") 
pwc_sex_samsung
```

```
## # A tibble: 3 x 9
##   .y.   group1 group2     n1    n2 statistic      p  p.adj p.adj.signif
## * <chr> <chr>  <chr>   <int> <int>     <dbl>  <dbl>  <dbl> <chr>       
## 1 MPE   Female Male        5     8     2.26  0.0236 0.0707 ns          
## 2 MPE   Female Neutral     5     1    -0.567 0.570  1      ns          
## 3 MPE   Male   Neutral     8     1    -1.80  0.0714 0.214  ns
```

```r
pwc_sex_withings <- df_val_withings %>% 
  dunn_test(MPE ~ gender, p.adjust.method = "bonferroni") 
pwc_sex_withings
```

```
## # A tibble: 3 x 9
##   .y.   group1 group2     n1    n2 statistic         p    p.adj p.adj.signif
## * <chr> <chr>  <chr>   <int> <int>     <dbl>     <dbl>    <dbl> <chr>       
## 1 MPE   Female Male       22    15     -4.12 0.0000377 0.000113 ***         
## 2 MPE   Female Neutral    22    12     -1.78 0.0758    0.227    ns          
## 3 MPE   Male   Neutral    15    12      1.92 0.0552    0.166    ns
```


```r
# Visualization: box plots with significance
pwc_sex_apple <- pwc_sex_apple %>% add_xy_position(x = "gender")
sex_sig_apple <- ggboxplot(df_val_apple, x = "gender", y = "MPE") +
  stat_pvalue_manual(pwc_sex_apple, hide.ns = TRUE) +
  labs(caption = get_pwc_label(pwc_sex_apple))
plot(sex_sig_apple)
```

![](Part-1_files/figure-html/unnamed-chunk-54-1.png)<!-- -->

```r
pwc_sex_withings <- pwc_sex_withings %>% add_xy_position(x = "gender")
sex_sig_withings <- ggboxplot(df_val_withings, x = "gender", y = "MPE") +
  stat_pvalue_manual(pwc_sex_withings, hide.ns = TRUE) +
  labs(caption = get_pwc_label(pwc_sex_withings))
plot(sex_sig_withings)
```

![](Part-1_files/figure-html/unnamed-chunk-54-2.png)<!-- -->

Pairwise Dunn's test between sex groups showed that only the differences between male and neutral (Dunn’s test, p = 0.0094) for apple devices, and between females and males (Dunn's test, p = 0.0001) were significant for Withings devices. It also showed no significant differences in the Samsung devices.

### BMI


```r
kruskal.test(MPE ~ bmi_cat, data = df_val_apple)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by bmi_cat
## Kruskal-Wallis chi-squared = 0.75, df = 1, p-value = 0.3865
```

```r
kruskal.test(MPE ~ bmi_cat, data = df_val_fitbit)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by bmi_cat
## Kruskal-Wallis chi-squared = 15.883, df = 2, p-value = 0.0003557
```

```r
kruskal.test(MPE ~ bmi_cat, data = df_val_garmin)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by bmi_cat
## Kruskal-Wallis chi-squared = 12.92, df = 2, p-value = 0.001565
```

```r
kruskal.test(MPE ~ bmi_cat, data = df_val_misfit)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by bmi_cat
## Kruskal-Wallis chi-squared = 7.6825, df = 2, p-value = 0.02147
```

```r
kruskal.test(MPE ~ bmi_cat, data = df_val_polar)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by bmi_cat
## Kruskal-Wallis chi-squared = 14.098, df = 2, p-value = 0.0008683
```

```r
kruskal.test(MPE ~ bmi_cat, data = df_val_samsung)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by bmi_cat
## Kruskal-Wallis chi-squared = 0.97403, df = 1, p-value = 0.3237
```

```r
kruskal.test(MPE ~ bmi_cat, data = df_val_withings)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by bmi_cat
## Kruskal-Wallis chi-squared = 1.3404, df = 2, p-value = 0.5116
```

The p-values of Fitbit, Garmin, Misfit and Polar were less than the significance level 0.05, we can conclude that there are significant differences in the validity of these devices between the bmi groups.

From the output of the Kruskal-Wallis test, we know that there is a significant difference between the BMI groups, but we don’t know which pairs of groups are different.


```r
# Pairwise comparisons
pwc_bmi_fitbit <- df_val_fitbit %>% 
  dunn_test(MPE ~ bmi_cat, p.adjust.method = "bonferroni") 
pwc_bmi_fitbit
```

```
## # A tibble: 3 x 9
##   .y.   group1     group2       n1    n2 statistic        p   p.adj p.adj.signif
## * <chr> <chr>      <chr>     <int> <int>     <dbl>    <dbl>   <dbl> <chr>       
## 1 MPE   Normal we… Overweig…   130   122     -3.90  9.80e-5 2.94e-4 ***         
## 2 MPE   Normal we… Obese       130    85     -2.46  1.39e-2 4.16e-2 *           
## 3 MPE   Overweight Obese       122    85      1.05  2.96e-1 8.87e-1 ns
```

```r
pwc_bmi_garmin <- df_val_garmin %>% 
  dunn_test(MPE ~ bmi_cat, p.adjust.method = "bonferroni") 
pwc_bmi_garmin
```

```
## # A tibble: 3 x 9
##   .y.   group1      group2       n1    n2 statistic       p   p.adj p.adj.signif
## * <chr> <chr>       <chr>     <int> <int>     <dbl>   <dbl>   <dbl> <chr>       
## 1 MPE   Normal wei… Overweig…    38    14    -3.03  2.43e-3 0.00728 **          
## 2 MPE   Normal wei… Obese        38    34     0.722 4.70e-1 1       ns          
## 3 MPE   Overweight  Obese        14    34     3.52  4.28e-4 0.00128 **
```

```r
pwc_bmi_misfit <- df_val_misfit %>% 
  dunn_test(MPE ~ bmi_cat, p.adjust.method = "bonferroni") 
pwc_bmi_misfit
```

```
## # A tibble: 3 x 9
##   .y.   group1       group2       n1    n2 statistic       p  p.adj p.adj.signif
## * <chr> <chr>        <chr>     <int> <int>     <dbl>   <dbl>  <dbl> <chr>       
## 1 MPE   Normal weig… Overweig…     7     7    -2.70  0.00695 0.0209 *           
## 2 MPE   Normal weig… Obese         7     3    -1.63  0.104   0.312  ns          
## 3 MPE   Overweight   Obese         7     3     0.465 0.642   1      ns
```

```r
pwc_bmi_polar <- df_val_polar %>% 
  dunn_test(MPE ~ bmi_cat, p.adjust.method = "bonferroni") 
pwc_bmi_polar
```

```
## # A tibble: 3 x 9
##   .y.   group1      group2       n1    n2 statistic       p   p.adj p.adj.signif
## * <chr> <chr>       <chr>     <int> <int>     <dbl>   <dbl>   <dbl> <chr>       
## 1 MPE   Normal wei… Overweig…    13     3    -2.54  1.10e-2 0.0331  *           
## 2 MPE   Normal wei… Obese        13    11    -3.39  7.06e-4 0.00212 **          
## 3 MPE   Overweight  Obese         3    11     0.369 7.12e-1 1       ns
```


```r
# Visualization: box plots with significance
pwc_bmi_fitbit <- pwc_bmi_fitbit %>% add_xy_position(x = "bmi_cat")
bmi_sig_fitbit <- ggboxplot(df_val_fitbit, x = "bmi_cat", y = "MPE") +
  stat_pvalue_manual(pwc_bmi_fitbit, hide.ns = TRUE) +
  labs(caption = get_pwc_label(pwc_bmi_fitbit))
plot(bmi_sig_fitbit)
```

![](Part-1_files/figure-html/unnamed-chunk-57-1.png)<!-- -->

```r
pwc_bmi_garmin <- pwc_bmi_garmin %>% add_xy_position(x = "bmi_cat")
bmi_sig_garmin <- ggboxplot(df_val_garmin, x = "bmi_cat", y = "MPE") +
  stat_pvalue_manual(pwc_bmi_garmin, hide.ns = TRUE) +
  labs(caption = get_pwc_label(pwc_bmi_garmin))
plot(bmi_sig_garmin)
```

![](Part-1_files/figure-html/unnamed-chunk-57-2.png)<!-- -->

```r
pwc_bmi_misfit <- pwc_bmi_misfit %>% add_xy_position(x = "bmi_cat")
bmi_sig_misfit <- ggboxplot(df_val_misfit, x = "bmi_cat", y = "MPE") +
  stat_pvalue_manual(pwc_bmi_misfit, hide.ns = TRUE) +
  labs(caption = get_pwc_label(pwc_bmi_misfit))
plot(bmi_sig_misfit)
```

![](Part-1_files/figure-html/unnamed-chunk-57-3.png)<!-- -->

```r
pwc_bmi_polar <- pwc_bmi_polar %>% add_xy_position(x = "bmi_cat")
bmi_sig_polar <- ggboxplot(df_val_polar, x = "bmi_cat", y = "MPE") +
  stat_pvalue_manual(pwc_bmi_polar, hide.ns = TRUE) +
  labs(caption = get_pwc_label(pwc_bmi_polar))
plot(bmi_sig_polar)
```

![](Part-1_files/figure-html/unnamed-chunk-57-4.png)<!-- -->

### Wear Location


```r
#kruskal.test(MPE ~ Wear_Location, data = df_val_apple)
kruskal.test(MPE ~ Wear_Location, data = df_val_fitbit)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by Wear_Location
## Kruskal-Wallis chi-squared = 10.167, df = 5, p-value = 0.07063
```

```r
#kruskal.test(MPE ~ Wear_Location, data = df_val_garmin)
kruskal.test(MPE ~ Wear_Location, data = df_val_misfit)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by Wear_Location
## Kruskal-Wallis chi-squared = 8.1568, df = 2, p-value = 0.01693
```

```r
#kruskal.test(MPE ~ Wear_Location, data = df_val_polar)
#kruskal.test(MPE ~ Wear_Location, data = df_val_samsung)
kruskal.test(MPE ~ Wear_Location, data = df_val_withings)
```

```
## 
## 	Kruskal-Wallis rank sum test
## 
## data:  MPE by Wear_Location
## Kruskal-Wallis chi-squared = 14.326, df = 2, p-value = 0.0007748
```

Only Fitbit, Misfit and Withings had more than 1 wear locations in the data. The p-values of Misfit and Withings were less than the significance level 0.05, we can conclude that there are significant differences in the validity of these devices between the wear location groups.

From the output of the Kruskal-Wallis test, we know that there is a significant difference between the Wear location groups, but we don’t know which pairs of groups are different.


```r
# Pairwise comparisons
pwc_wl_misfit <- df_val_misfit %>% 
  dunn_test(MPE ~ Wear_Location, p.adjust.method = "bonferroni") 
pwc_wl_misfit
```

```
## # A tibble: 3 x 9
##   .y.   group1    group2       n1    n2 statistic      p  p.adj p.adj.signif
## * <chr> <chr>     <chr>     <int> <int>     <dbl>  <dbl>  <dbl> <chr>       
## 1 MPE   Wrist     Waist/Hip     7    12     2.31  0.0208 0.0624 ns          
## 2 MPE   Wrist     Torso         7     2    -0.689 0.491  1      ns          
## 3 MPE   Waist/Hip Torso        12     2    -2.16  0.0305 0.0916 ns
```

```r
pwc_wl_withings <- df_val_withings %>% 
  dunn_test(MPE ~ Wear_Location, p.adjust.method = "bonferroni") 
pwc_wl_withings
```

```
## # A tibble: 3 x 9
##   .y.   group1    group2       n1    n2 statistic        p   p.adj p.adj.signif
## * <chr> <chr>     <chr>     <int> <int>     <dbl>    <dbl>   <dbl> <chr>       
## 1 MPE   Wrist     Waist/Hip    17    30     3.53  0.000421 0.00126 **          
## 2 MPE   Wrist     Torso        17     2    -0.413 0.679    1       ns          
## 3 MPE   Waist/Hip Torso        30     2    -1.89  0.0589   0.177   ns
```

Only Withings showed a significant difference between waist/hip and wrist wear locations.


```r
# Visualization: box plots with significance
pwc_wl_withings <- pwc_wl_withings %>% add_xy_position(x = "Wear_Location")
wl_sig <- ggboxplot(df_val_withings, x = "Wear_Location", y = "MPE") +
  stat_pvalue_manual(pwc_wl_withings, hide.ns = TRUE) +
  labs(caption = get_pwc_label(pwc_wl_withings))
plot(wl_sig)
```

![](Part-1_files/figure-html/unnamed-chunk-60-1.png)<!-- -->



```r
gender_plot <- plot_grid(sex_sig_apple,sex_sig_withings, labels = c('Apple','Withings'), label_size = 8)
bmi_plot <- plot_grid(bmi_sig_fitbit,bmi_sig_garmin,bmi_sig_misfit,bmi_sig_polar, labels = c('Fitbit','Garmin','Misfit','Polar'), label_size = 8)

figure4 <- plot_grid(age_sig,gender_plot,bmi_plot,wl_sig, labels = c('A','B','C','D'), label_size = 12)

plot(gender_plot)
```

![](Part-1_files/figure-html/unnamed-chunk-61-1.png)<!-- -->

```r
plot(bmi_plot)
```

![](Part-1_files/figure-html/unnamed-chunk-61-2.png)<!-- -->

```r
plot(figure4)
```

![](Part-1_files/figure-html/unnamed-chunk-61-3.png)<!-- -->


```r
ggsave("figure4.pdf", plot = figure4, width = 21, height = 14)
```













