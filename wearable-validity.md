---
title: "WEARABLE DEVICE VALIDITY ACROSS AGE, SEX AND BMI GROUPS"
author: "Sumayyah Musa"
date: "3/12/2021"
output: 
    html_document:
       keep_md: true
---



## Read in and glimpse the data


```r
data <- read.csv("wearable_review_data_validity_edited.csv")
```

## Data Cleaning 
### Subsetting the data to select Step count


```r
#data <- subset(val_data, Measured != "EE" & Measured != "HR")

glimpse(data)
```

```
## Rows: 1,672
## Columns: 107
## $ X1                          <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13,…
## $ Author                      <chr> "Dooley", "Dooley", "Dooley", "Boudreaux",…
## $ Year                        <int> 2017, 2017, 2017, 2018, 2018, 2018, 2017, …
## $ Substudy                    <chr> "-", "-", "-", "-", "-", "-", "-", "-", "-…
## $ Setting                     <chr> "Controlled", "Controlled", "Controlled", …
## $ Measured                    <chr> "HR", "HR", "HR", "HR", "HR", "HR", "SC", …
## $ Measure_Unit                <chr> "bpm", "bpm", "bpm", "bpm", "bpm", "bpm", …
## $ Brand                       <chr> "Apple", "Apple", "Apple", "Apple", "Apple…
## $ Device                      <chr> "Watch", "Watch", "Watch", "Watch Series 2…
## $ device_name                 <chr> "Apple Watch", "Apple Watch", "Apple Watch…
## $ device_year                 <int> 2015, 2015, 2015, 2016, 2016, 2016, 2015, …
## $ Wear_Location               <chr> "Wrist", "Wrist", "Wrist", "Wrist", "Wrist…
## $ Wear_Info                   <chr> "wrist, random", "wrist, random", "wrist, …
## $ Type                        <chr> "full-text", "full-text", "full-text", "fu…
## $ Good.                       <chr> "y", "y", "y", "y", "y", "y", "y", "y", "y…
## $ Criterion_Measure           <chr> "Heart rate sensor chest strap (Polar T31)…
## $ Criterion_Type              <chr> "chest strap", "chest strap", "chest strap…
## $ Wear_Info_crit              <chr> "chest", "chest", "chest", "upper torso", …
## $ Wear_Location_crit          <chr> "Torso", "Torso", "Torso", "Torso", "Torso…
## $ population_n                <chr> "62", "62", "62", "50", "50", "50", "31", …
## $ population_m                <chr> "26", "26", "26", "22", "22", "22", "16", …
## $ population_f                <chr> "36", "36", "36", "28", "28", "28", "15", …
## $ population                  <chr> "healthy adults", "healthy adults", "healt…
## $ age_code                    <chr> "A", "A", "A", "A", "A", "A", "A", "A", "A…
## $ health_code                 <chr> "H", "H", "H", "H", "H", "H", "H", "H", "H…
## $ age                         <chr> "22.55", "22.55", "22.55", "22.71", "22.71…
## $ age_SD                      <dbl> 4.34, 4.34, 4.34, 2.99, 2.99, 2.99, 12.00,…
## $ weight                      <chr> "72.02", "72.02", "72.02", "67.79", "67.79…
## $ weight_SD                   <dbl> 18.99, 18.99, 18.99, 14.01, 14.01, 14.01, …
## $ height                      <chr> "170", "170", "170", "162.71", "162.71", "…
## $ height_SD                   <dbl> 11.00, 11.00, 11.00, 5.79, 5.79, 5.79, NA,…
## $ BMI                         <chr> "24.6", "24.6", "24.6", "25.83", "25.83", …
## $ BMI_SD                      <dbl> 4.77, 4.77, 4.77, 4.83, 4.83, 4.83, 2.40, …
## $ location                    <chr> "TX, USA", "TX, USA", "TX, USA", "LA, USA"…
## $ activity_type               <chr> "Rest: Seated", "Rest: Seated", "Rest: Sea…
## $ test_type                   <chr> "Rest", "Rest", "Rest", "Rest", "Rest", "A…
## $ activity_type_code          <chr> "Se", "Se", "Se", "Se", "Se", "Mi", "At", …
## $ body_Motion                 <chr> NA, NA, NA, NA, NA, "Mi", "Nr", "Nr", "Nr"…
## $ pace_code                   <chr> NA, NA, NA, NA, NA, NA, "Nm", "Sl", "Sl", …
## $ pace_value                  <chr> NA, NA, NA, NA, NA, NA, "1.33", "0.89", "0…
## $ incline_code                <chr> "N", "N", "N", "N", "N", "N", "N", "N", "N…
## $ incline_pct                 <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ activity_details            <chr> "sedentary, seated baseline assessment, 10…
## $ bout_rest                   <chr> "yes", "yes", "no", NA, NA, NA, NA, NA, NA…
## $ epoch                       <chr> "unknown", "unknown", "unknown", "average …
## $ actual_n_analyzed           <int> 62, 62, 62, 50, 50, 50, 31, 31, 31, 31, 31…
## $ trend                       <chr> "good validity", "good validity", "underes…
## $ CC_type                     <chr> NA, NA, NA, "ICC", "ICC", "ICC", "ICC", "I…
## $ CC                          <dbl> NA, NA, NA, 0.990, 0.820, 0.900, 0.520, 0.…
## $ CC_bins                     <chr> NA, NA, NA, "VS", "VS", "VS", "MOD", "MOD"…
## $ CC_all                      <chr> NA, NA, NA, "0.99", "0.82", "0.9", "0.52",…
## $ CC_CI_pct                   <int> NA, NA, NA, NA, NA, NA, 95, 95, 95, 95, 95…
## $ CC_CI_upper                 <chr> NA, NA, NA, NA, NA, NA, "0.74", "0.77", "0…
## $ CC_CI_lower                 <chr> NA, NA, NA, NA, NA, NA, "0.21", "0.27", "0…
## $ CC_pvalue                   <chr> NA, NA, NA, NA, NA, NA, "< .01", "< .01", …
## $ CC_significance             <chr> NA, NA, NA, NA, NA, NA, "sig", "sig", "sig…
## $ ES_type                     <chr> "Cohen's d", "Cohen's d", "Cohen's d", NA,…
## $ ES                          <dbl> 0.04, 0.01, -0.03, NA, NA, NA, NA, NA, NA,…
## $ ES_CI_upper                 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ ES_CI_lower                 <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ BA_LoA_upper                <chr> NA, NA, NA, NA, NA, NA, "159", "111", "124…
## $ BA_LoA_lower                <chr> NA, NA, NA, NA, NA, NA, "-101", "-74", "-9…
## $ BA_LoA_width                <dbl> NA, NA, NA, NA, NA, NA, 260.0, 185.0, 222.…
## $ devicemean                  <dbl> 72.84, 73.07, 84.02, NA, NA, NA, NA, NA, N…
## $ devicemean_SD               <dbl> 12.08, 11.45, 15.27, NA, NA, NA, NA, NA, N…
## $ critmean                    <dbl> 72.32, 72.99, 84.47, NA, NA, NA, 1108.00, …
## $ critmean_SD                 <dbl> 12.21, 11.30, 15.16, NA, NA, NA, 46.00, 46…
## $ device_v_crit               <chr> "over", "over", "under", "equal", "equal",…
## $ meandiff                    <chr> NA, NA, NA, "0.04", "0.02", "1.28", "29", …
## $ meandiff_SD                 <dbl> NA, NA, NA, 1.71, 1.71, 8.55, 12.00, 9.00,…
## $ meandiff_CI_upper           <dbl> NA, NA, NA, -3.31, -3.33, -15.46, NA, NA, …
## $ meandiff_CI_lower           <dbl> NA, NA, NA, 3.39, 3.37, 18.03, NA, NA, NA,…
## $ MPE                         <dbl> 0.007190265, 0.001096041, -0.005327335, NA…
## $ MPE_bin                     <chr> "± 3%", "± 3%", "± 3%", NA, NA, NA, "± 3%"…
## $ MPE_SD                      <chr> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MPE_significance_test       <chr> "0.78", "0.76", "< .001", NA, NA, NA, NA, …
## $ MPE_significance_num        <chr> "ns", "ns", "sig", NA, NA, NA, NA, NA, NA,…
## $ MAD                         <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MAD_SD                      <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MAD_CI_upper                <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MAD_CI_lower                <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MAPE                        <dbl> 0.0276, 0.0163, 0.0114, 0.0121, 0.0144, 0.…
## $ MAPE_bin                    <chr> "less 3%", "less 3%", "less 3%", "less 3%"…
## $ MAPE_SD                     <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MAPE_CI_upper               <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ MAPE_CI_lower               <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ RMSE                        <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
## $ equivalencetesting          <chr> NA, NA, NA, NA, NA, NA, "-2.20\nWilcoxon s…
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
data$X1 <- as.character(data$X1)
data$population_f <- as.numeric(data$population_f)
```

```
## Warning: NAs introduced by coercion
```

```r
data$population_m <- as.numeric(data$population_m)
```

```
## Warning: NAs introduced by coercion
```

```r
data$BMI <- as.numeric(data$BMI)
```

```
## Warning: NAs introduced by coercion
```

```r
data$age <- as.numeric(data$age)
```

```
## Warning: NAs introduced by coercion
```

## Data Cleaning by Variable

### MPE (Outcome Variable)


```r
#convert to percentage
data$MPE <- (data$MPE)*100
summary(data$MPE)
```

```
##     Min.  1st Qu.   Median     Mean  3rd Qu.     Max.     NA's 
## -100.000  -10.582   -1.450   -4.315    1.396  530.000      294
```


```r
#removing missing values and renaming our final data as df 
df <- drop_na(data, MPE)
```


```r
round(stat.desc(df$MPE),2)
```

```
##      nbr.val     nbr.null       nbr.na          min          max        range 
##      1378.00        56.00         0.00      -100.00       530.00       630.00 
##          sum       median         mean      SE.mean CI.mean.0.95          var 
##     -5946.51        -1.45        -4.32         0.89         1.75      1100.74 
##      std.dev     coef.var 
##        33.18        -7.69
```


```r
mpe_hist <- ggplot(df, aes(MPE)) + 
                  geom_histogram(bins = 25) +
                  theme_classic()
                  #facet_wrap(~ age_category)
plot(mpe_hist)
```

![](wearable-validity_files/figure-html/unnamed-chunk-7-1.png)<!-- -->


```r
mpe_box <- ggplot(df, aes(MPE)) + 
                geom_boxplot() +
                coord_flip() +
                theme_classic()
                #facet_wrap(~ age_cat)
plot(mpe_box)
```

![](wearable-validity_files/figure-html/unnamed-chunk-8-1.png)<!-- -->



```r
#creating a dataframe containing the extreme outliers
df_out <- df %>%
  identify_outliers("MPE") %>%
        filter(is.extreme == TRUE)
```



```r
#merging the outlier dataframe with our original data
total <- merge(df,df_out, all.x = TRUE)
table(total$is.extreme)
```

```
## 
## TRUE 
##  161
```


```r
#renaming those not extreme as FALSE instead of NA
total$is.extreme[is.na(total$is.extreme)] <- FALSE
table(total$is.extreme)
```

```
## 
## FALSE  TRUE 
##  1217   161
```


```r
#subsetting the non-outliers in the data
df_val <- subset(total, is.extreme != TRUE)
```


```r
summary(df_val$MPE)
```

```
##     Min.  1st Qu.   Median     Mean  3rd Qu.     Max. 
## -45.2700  -7.9365  -1.2500  -3.9293   0.8421  37.0000
```


```r
mpe_hist_clean <- ggplot(df_val, aes(MPE)) + 
                  geom_histogram(bins = 30) +
                  theme_classic()
                  #facet_wrap(~ age_cat)
plot(mpe_hist_clean)
```

![](wearable-validity_files/figure-html/unnamed-chunk-14-1.png)<!-- -->

The distribution looks better now that the outliers have been removed


```r
mpe_box_clean <- ggplot(df_val, aes(MPE)) + 
                  geom_boxplot() +
                  coord_flip() +
                  theme_classic()
                  #facet_wrap(~ age_cat)
plot(mpe_box_clean)
```

![](wearable-validity_files/figure-html/unnamed-chunk-15-1.png)<!-- -->

### AGE


```r
round(stat.desc(df_val$age), digits = 1)
```

```
##      nbr.val     nbr.null       nbr.na          min          max        range 
##        933.0          0.0        284.0          3.7         87.0         83.3 
##          sum       median         mean      SE.mean CI.mean.0.95          var 
##      31707.1         27.5         34.0          0.5          1.1        275.5 
##      std.dev     coef.var 
##         16.6          0.5
```

```r
df_val$age_code <- factor(df_val$age_code, c("C","A","OA"), labels = c("Children","Adults","Older Adults"))
```


```r
addmargins(table(df_val$age_code)) #frequency table of age, including the total
```

```
## 
##     Children       Adults Older Adults          Sum 
##           25         1019          173         1217
```

```r
round(prop.table(table(df_val$age_code))*100, digits = 0) #percentage proportion of each category
```

```
## 
##     Children       Adults Older Adults 
##            2           84           14
```

```r
sum(is.na(df_val$age_code))
```

```
## [1] 0
```

### GENDER


```r
df_val <- df_val %>%
        mutate(sex = case_when(
                population_m > population_f ~ "Male",
                population_m < population_f ~ "Female"
        ))
```


```r
df_val$sex <- as.factor(df_val$sex)
addmargins(table(df_val$sex))
```

```
## 
## Female   Male    Sum 
##    413    470    883
```

```r
round(prop.table(table(df_val$sex))*100, digits = 0)
```

```
## 
## Female   Male 
##     47     53
```

```r
sum(is.na(df_val$sex))
```

```
## [1] 334
```

```r
df_val_sex <- drop_na(df_val, sex)
```

### BMI


```r
round(stat.desc(df_val$BMI), digits = 1)
```

```
##      nbr.val     nbr.null       nbr.na          min          max        range 
##        742.0          0.0        475.0         20.5         30.8         10.3 
##          sum       median         mean      SE.mean CI.mean.0.95          var 
##      18136.4         24.6         24.4          0.1          0.1          3.3 
##      std.dev     coef.var 
##          1.8          0.1
```

```r
df_val <- df_val %>%
        mutate(bmi_cat = case_when(
                BMI >= 18.5 & BMI <= 24.9 ~ "Healthy weight",
                BMI > 24.9 & BMI <= 29.9 ~ "Overweight",
                BMI > 29.9 ~ "Obese"
        ))
```


```r
addmargins(table(df_val$bmi_cat))
```

```
## 
## Healthy weight          Obese     Overweight            Sum 
##            453              2            287            742
```

```r
round(prop.table(table(df_val$bmi_cat))*100, digits = 0) #percentage
```

```
## 
## Healthy weight          Obese     Overweight 
##             61              0             39
```

```r
sum(is.na(df_val$bmi_cat))
```

```
## [1] 475
```

```r
df_val_bmi <- drop_na(df_val, bmi_cat)

#df <- filter(df, bmi_cat != "Obese")
```

There are not enough data for obese individuals.


```r
#relevel factors
df_val$age_code <- fct_relevel(df_val$age_code, c("Children","Adults","Older Adults"))
df_val$sex <- fct_relevel(df_val$sex, c("Female","Male"))
df_val$bmi_cat <- fct_relevel(df_val$bmi_cat, c("Healthy weight","Overweight","Obese"))
```

## MPE for Step count, heart rate & energy expenditure across different groups


```r
#AGE GROUP
df_val %>%
    group_by(age_code,Measured) %>%
    get_summary_stats(MPE, type = "mean_sd") %>%
    arrange(Measured)
```

```
## # A tibble: 7 x 6
##   Measured age_code     variable     n   mean    sd
##   <chr>    <fct>        <chr>    <dbl>  <dbl> <dbl>
## 1 EE       Adults       MPE        256 -6.95  18.8 
## 2 HR       Children     MPE          2  1.5    1.98
## 3 HR       Adults       MPE        144 -1.26   6.37
## 4 HR       Older Adults MPE         32  0.964  2.54
## 5 SC       Children     MPE         23  1.47  10.7 
## 6 SC       Adults       MPE        619 -2.74  10.4 
## 7 SC       Older Adults MPE        141 -8.47  14.4
```


```r
#SEX GROUP
df_val_sex %>%
    group_by(sex, Measured) %>%
    get_summary_stats(MPE, type = "mean_sd") %>%
    arrange(Measured)
```

```
## # A tibble: 6 x 6
##   Measured sex    variable     n   mean    sd
##   <chr>    <fct>  <chr>    <dbl>  <dbl> <dbl>
## 1 EE       Female MPE         74 -6.57  16.7 
## 2 EE       Male   MPE        107 -9.42  20.2 
## 3 HR       Female MPE         73 -0.103  7.11
## 4 HR       Male   MPE         84 -0.463  4.63
## 5 SC       Female MPE        266 -4.93  13.5 
## 6 SC       Male   MPE        279 -3.01  10.9
```


```r
#BMI GROUP
df_val_bmi %>%
    group_by(bmi_cat, Measured) %>%
    get_summary_stats(MPE, type = "mean_sd") %>%
    arrange(Measured)
```

```
## # A tibble: 7 x 6
##   Measured bmi_cat        variable     n    mean    sd
##   <chr>    <chr>          <chr>    <dbl>   <dbl> <dbl>
## 1 EE       Healthy weight MPE        106 -10.4   17.2 
## 2 EE       Overweight     MPE         52  -1.08  20.2 
## 3 HR       Healthy weight MPE         81  -2.18   7.45
## 4 HR       Overweight     MPE         28   0.997  4.93
## 5 SC       Healthy weight MPE        266  -0.027  8.86
## 6 SC       Obese          MPE          2 -13.6   21.8 
## 7 SC       Overweight     MPE        207  -5.51  12.6
```

### DEVICES


```r
#Age group, device & wear location
df_val %>%
    group_by(age_code, device_name, Wear_Location, Measured) %>%
    get_summary_stats(MPE, type = "mean_sd") %>%
    arrange(device_name) 
```

```
## # A tibble: 122 x 8
##    Measured device_name     Wear_Location age_code  variable     n    mean    sd
##    <chr>    <chr>           <chr>         <fct>     <chr>    <dbl>   <dbl> <dbl>
##  1 EE       Apple Watch     Wrist         Adults    MPE         21  -3.11  19.0 
##  2 HR       Apple Watch     Wrist         Adults    MPE         49   0.326  3.68
##  3 SC       Apple Watch     Wrist         Adults    MPE         18  -0.752  3.17
##  4 SC       Apple Watch     Wrist         Older Ad… MPE          1   1.59  NA   
##  5 EE       Apple Watch Se… Wrist         Adults    MPE          1  23.0   NA   
##  6 SC       Fitbit          Wrist         Adults    MPE          1  20.6   NA   
##  7 SC       Fitbit          Waist/Hip     Older Ad… MPE          2   6.5    9.19
##  8 EE       Fitbit Blaze    Wrist         Adults    MPE          2 -22.0   24.7 
##  9 EE       Fitbit Charge   Wrist         Adults    MPE          9   2.10  17.9 
## 10 SC       Fitbit Charge   Wrist         Adults    MPE         12   0.218 14.3 
## # … with 112 more rows
```


```r
#sex group, device & wear location
df_val_sex %>%
    group_by(sex, device_name, Wear_Location, Measured) %>%
    get_summary_stats(MPE, type = "mean_sd") %>%
    arrange(device_name)
```

```
## # A tibble: 103 x 8
##    Measured device_name         Wear_Location sex   variable     n    mean    sd
##    <chr>    <chr>               <chr>         <fct> <chr>    <dbl>   <dbl> <dbl>
##  1 EE       Apple Watch         Wrist         Fema… MPE          4   3.07  18.8 
##  2 HR       Apple Watch         Wrist         Fema… MPE          8  -0.662  2.79
##  3 SC       Apple Watch         Wrist         Fema… MPE          3  -1.61   2.79
##  4 EE       Apple Watch         Wrist         Male  MPE          9   5.20  13.9 
##  5 HR       Apple Watch         Wrist         Male  MPE         35   1.23   3.66
##  6 SC       Apple Watch         Wrist         Male  MPE         12   0.995  1.98
##  7 EE       Apple Watch Series… Wrist         Male  MPE          1  23.0   NA   
##  8 SC       Fitbit              Waist/Hip     Fema… MPE          2   6.5    9.19
##  9 SC       Fitbit              Wrist         Fema… MPE          1  20.6   NA   
## 10 EE       Fitbit Blaze        Wrist         Fema… MPE          2 -22.0   24.7 
## # … with 93 more rows
```


```r
#bmi group, device & wear location
df_val_bmi %>%
    group_by(bmi_cat, device_name, Wear_Location, Measured) %>%
    get_summary_stats(MPE, type = "mean_sd") %>%
    arrange(device_name)
```

```
## # A tibble: 95 x 8
##    Measured device_name     Wear_Location bmi_cat   variable     n    mean    sd
##    <chr>    <chr>           <chr>         <chr>     <chr>    <dbl>   <dbl> <dbl>
##  1 EE       Apple Watch     Wrist         Healthy … MPE         14  -6.40  16.3 
##  2 HR       Apple Watch     Wrist         Healthy … MPE         11  -2.65   2.36
##  3 SC       Apple Watch     Wrist         Healthy … MPE          9   0.748  2.25
##  4 EE       Apple Watch     Wrist         Overweig… MPE          6  11.0   13.5 
##  5 HR       Apple Watch     Wrist         Overweig… MPE         15   3.80   4.30
##  6 SC       Apple Watch     Wrist         Overweig… MPE          8  -0.799  2.69
##  7 EE       Apple Watch Se… Wrist         Healthy … MPE          1  23.0   NA   
##  8 EE       Fitbit Blaze    Wrist         Overweig… MPE          2 -22.0   24.7 
##  9 SC       Fitbit Charge   Wrist         Healthy … MPE          3  -7.13  25.7 
## 10 EE       Fitbit Charge   Wrist         Overweig… MPE          4  -6.50  19.2 
## # … with 85 more rows
```


```r
#df_new <- filter(df, Setting != "Free-Living", device_name == "Fitbit One" | device_name == "Fitbit Flex" | device_name == "Fitbit Zip" | device_name == "Fitbit Charge HR" | device_name == "Garmin Vivofit" | device_name == "Withings Pulse O2" | device_name == "Apple Watch")
```


## PLOTS

### Validity of Step count by Age in Controlled setting

* Dashed grey lines indicate ± 3% measurement error


```r
#options(repr.plot.width = 25, repr.plot.height = 8)
df_age_plot <- ggplot(df_val, aes(x = Brand, y = MPE, colour = Measured)) +
                    geom_boxplot(na.rm = TRUE) +
                    geom_beeswarm(dodge.width = 0.2, cex = 0.2, alpha = 0.08, groupOnX = TRUE, na.rm = TRUE) +   
                    geom_hline(yintercept = 0) +  
                    geom_hline(yintercept = 3, size = 0.5, colour = "grey", linetype = "dashed") + 
                    geom_hline(yintercept = -3, size = 0.5, colour = "grey", linetype = "dashed") +   
                    scale_y_continuous(limits=c(-10, 10)) +
                    ylab("Step MPE (%)") +
                    scale_colour_brewer(palette="Dark2") +
                    theme_bw() +
                    theme(axis.text.x = element_text(colour = "grey20", size = 10, angle = 90, hjust = 0.5, 
                                                     vjust = 0.5),
                        axis.text.y = element_text(colour = "grey20", size = 10),
                        strip.text = element_text(face = "italic"),
                        text = element_text(size = 12)) +
                    facet_wrap(~ age_code)
plot(df_age_plot)
```

```
## Warning: Removed 6 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 301 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 60 rows containing missing values (position_beeswarm).
```

![](wearable-validity_files/figure-html/unnamed-chunk-30-1.png)<!-- -->
### Validity of step count by gender in controlled setting


```r
df_sex_plot <- ggplot(df_val_sex, aes(x = Brand, y = MPE, colour = Measured)) +
                    geom_boxplot(na.rm = TRUE) +
                    geom_beeswarm(dodge.width = 0.2, cex = 0.2, alpha = 0.08, groupOnX = TRUE, na.rm = TRUE) +   
                    geom_hline(yintercept = 0) +  
                    geom_hline(yintercept = 3, size = 0.5, colour = "grey", linetype = "dashed") + 
                    geom_hline(yintercept = -3, size = 0.5, colour = "grey", linetype = "dashed") +   
                    scale_y_continuous(limits=c(-10, 10)) +
                    ylab("Step MPE (%)") +
                    scale_colour_brewer(palette="Dark2") +
                    theme_bw() +
                    theme(axis.text.x = element_text(colour = "grey20", size = 10, angle = 90, hjust = 0.5, 
                                                     vjust = 0.5),
                        axis.text.y = element_text(colour = "grey20", size = 10),
                        strip.text = element_text(face = "italic"),
                        text = element_text(size = 12)) +
                    facet_wrap(~ sex)
plot(df_sex_plot)
```

```
## Warning: Removed 140 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 141 rows containing missing values (position_beeswarm).
```

![](wearable-validity_files/figure-html/unnamed-chunk-31-1.png)<!-- -->

### Validity of step count by BMI in controlled setting


```r
df_bmi_plot <- ggplot(df_val_bmi, aes(x = Brand, y = MPE, colour = Measured)) +
                    geom_boxplot(na.rm = TRUE) +
                    geom_beeswarm(dodge.width = 0.2, cex = 0.2, alpha = 0.08, groupOnX = TRUE, na.rm = TRUE) +   
                    geom_hline(yintercept = 0) +  
                    geom_hline(yintercept = 3, size = 0.5, colour = "grey", linetype = "dashed") + 
                    geom_hline(yintercept = -3, size = 0.5, colour = "grey", linetype = "dashed") +   
                    scale_y_continuous(limits=c(-10, 10)) +
                    ylab("Step MPE (%)") +
                    scale_colour_brewer(palette="Dark2") +
                    theme_bw() +
                    theme(axis.text.x = element_text(colour = "grey20", size = 10, angle = 90, hjust = 0.5, 
                                                     vjust = 0.5),
                        axis.text.y = element_text(colour = "grey20", size = 10),
                        strip.text = element_text(face = "italic"),
                        text = element_text(size = 12)) +
                    facet_wrap(~ bmi_cat)
plot(df_bmi_plot)
```

```
## Warning: Removed 119 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 1 rows containing missing values (position_beeswarm).
```

```
## Warning: Removed 95 rows containing missing values (position_beeswarm).
```

![](wearable-validity_files/figure-html/unnamed-chunk-32-1.png)<!-- -->


```r
#figure1 <- plot_grid(df_new_age_plot, df_new_sex_plot, df_new_bmi_plot, labels = c('A','B','C'), label_size = 12)
```


```r
#ggsave("figure1.pdf", plot = figure1, width = 20, height = 16)
```


## Regression Analysis


```r
reg1 <- lm(MPE ~ Wear_Location, df_val)
reg2 <- lm(MPE ~ age_code + Wear_Location, df_val)
reg3 <- lm(MPE ~ sex + Wear_Location, df_val)
reg4 <- lm(MPE ~ bmi_cat + Wear_Location, df_val)
```


```r
summary(reg1)
```

```
## 
## Call:
## lm(formula = MPE ~ Wear_Location, data = df_val)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -41.702  -4.442   2.398   5.137  41.078 
## 
## Coefficients:
##                        Estimate Std. Error t value Pr(>|t|)   
## (Intercept)             -5.0709     1.7696  -2.866  0.00423 **
## Wear_LocationThigh     -25.7467    13.0037  -1.980  0.04794 * 
## Wear_LocationTorso      -0.8532     2.2760  -0.375  0.70782   
## Wear_LocationUpper Arm   2.9871     5.5491   0.538  0.59047   
## Wear_LocationWaist/Hip   0.3267     1.9172   0.170  0.86473   
## Wear_LocationWrist       1.7726     1.8294   0.969  0.33277   
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 12.88 on 1211 degrees of freedom
## Multiple R-squared:  0.008115,	Adjusted R-squared:  0.00402 
## F-statistic: 1.982 on 5 and 1211 DF,  p-value: 0.07873
```


```r
summary(reg2) #age
```

```
## 
## Call:
## lm(formula = MPE ~ age_code + Wear_Location, data = df_val)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -42.110  -4.537   2.293   5.593  44.128 
## 
## Coefficients:
##                        Estimate Std. Error t value Pr(>|t|)   
## (Intercept)              1.6351     3.1605   0.517  0.60499   
## age_codeAdults          -5.8382     2.6225  -2.226  0.02619 * 
## age_codeOlder Adults    -8.9044     2.7789  -3.204  0.00139 **
## Wear_LocationThigh     -23.5484    12.9623  -1.817  0.06951 . 
## Wear_LocationTorso      -1.5245     2.2729  -0.671  0.50252   
## Wear_LocationUpper Arm   2.1193     5.5300   0.383  0.70161   
## Wear_LocationWaist/Hip  -0.5247     1.9213  -0.273  0.78482   
## Wear_LocationWrist       1.3127     1.8261   0.719  0.47237   
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 12.82 on 1209 degrees of freedom
## Multiple R-squared:  0.01945,	Adjusted R-squared:  0.01378 
## F-statistic: 3.427 on 7 and 1209 DF,  p-value: 0.001235
```


```r
summary(reg3) #sex 
```

```
## 
## Call:
## lm(formula = MPE ~ sex + Wear_Location, data = df_val)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -41.387  -5.205   2.580   6.106  40.820 
## 
## Coefficients:
##                         Estimate Std. Error t value Pr(>|t|)  
## (Intercept)             -5.02129    1.97302  -2.545   0.0111 *
## sexMale                  0.08128    0.91538   0.089   0.9293  
## Wear_LocationThigh     -25.79632   13.43637  -1.920   0.0552 .
## Wear_LocationTorso      -1.97532    2.59642  -0.761   0.4470  
## Wear_LocationWaist/Hip   0.45338    2.07461   0.219   0.8271  
## Wear_LocationWrist       1.32671    1.93614   0.685   0.4934  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 13.29 on 877 degrees of freedom
##   (334 observations deleted due to missingness)
## Multiple R-squared:  0.008783,	Adjusted R-squared:  0.003132 
## F-statistic: 1.554 on 5 and 877 DF,  p-value: 0.1706
```


```r
summary(reg4) #bmi
```

```
## 
## Call:
## lm(formula = MPE ~ bmi_cat + Wear_Location, data = df_val)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -42.046  -4.054   2.248   5.004  41.260 
## 
## Coefficients:
##                        Estimate Std. Error t value Pr(>|t|)
## (Intercept)              0.6823     3.6772   0.186    0.853
## bmi_catOverweight       -1.1538     0.9857  -1.171    0.242
## bmi_catObese           -12.7407     9.2478  -1.378    0.169
## Wear_LocationTorso      -4.7236     3.9498  -1.196    0.232
## Wear_LocationUpper Arm  -1.6123     6.3663  -0.253    0.800
## Wear_LocationWaist/Hip  -4.4547     3.7409  -1.191    0.234
## Wear_LocationWrist      -3.1196     3.6792  -0.848    0.397
## 
## Residual standard error: 12.8 on 735 degrees of freedom
##   (475 observations deleted due to missingness)
## Multiple R-squared:  0.00819,	Adjusted R-squared:  9.329e-05 
## F-statistic: 1.012 on 6 and 735 DF,  p-value: 0.4164
```










