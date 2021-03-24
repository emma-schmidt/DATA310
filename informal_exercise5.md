### Download DHS data 

Country selected: Kenya

### Import the households dataset for your selected country and create a data frame with a variable that describes each of the following: household ID, unit, weights, location, size, gender, age, education, and wealth. Pivot the persons columns within your households data to a long format in order to produce a similarly specified dataset that describes all persons residing within all households.

Code used:
``` households <- read_dta("KEHR72DT/KEHR72FL.DTA")


hhid <- households$hhid #check length(unique(hhid))
unit <- households$hv004
weights <- households$hv005 / 1000000
location <- as_factor(households$shcounty)
size <- households$hv009
sex <- households[ ,312:334]
age <- households[ ,335:357]
edu <- households[ ,358:380]
wealth <- households$hv270


hhs <- cbind.data.frame(hhid, unit, weights, location, size, sex, age, edu, wealth)


gender <- hhs %>%
  pivot_longer(cols = starts_with("hv104"),
               names_to = "pid",
               values_to = "gender",
               values_drop_na = TRUE)

age <- hhs %>%
  pivot_longer(cols = starts_with("hv105"),
               names_to = "pid",
               values_to = "age",
               values_drop_na = TRUE)

edu <- hhs %>%
  pivot_longer(cols = starts_with("hv106"),
               names_to = "pid",
               values_to = "edu",
               values_drop_na = TRUE)



gender <- select(gender, -starts_with("hv"))
age <- select(age, -starts_with("hv"))
edu <- select(edu, -starts_with("hv"))

gender$id <- paste(gender$hhid, substr(gender$pid, 7,8), sep = '')
age$id <- paste(age$hhid, substr(age$pid, 7,8), sep = '')
edu$id <- paste(edu$hhid, substr(edu$pid, 7,8), sep = '')
pns <- merge(gender, age, by = 'id')
pns <- merge(pns, edu, by = 'id')
```

### Using this data frame describing all persons standardize, normalize and percentize your variables and visualize each post transformed dataset as a heatmap that illustrates the heterogeneity of the combination of patterns.

#### Raw heatmap:

![image](https://user-images.githubusercontent.com/78189165/112363670-26506a80-8cac-11eb-8c10-5d2e0f0433f5.png)

#### Scaled heatmap:

![image](https://user-images.githubusercontent.com/78189165/112363766-3cf6c180-8cac-11eb-951c-da95e77a2511.png)

#### Normalized heatmap:

![image](https://user-images.githubusercontent.com/78189165/112363856-539d1880-8cac-11eb-9e4c-d04da5abef4d.png)

#### Percentized heatmap:

![image](https://user-images.githubusercontent.com/78189165/112363893-61eb3480-8cac-11eb-840b-46510a5939e0.png)
