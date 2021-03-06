# Project-II-ST558
Project II -ST558

## Brief about the repo
This repo is built for the project II, ST558. This repo is built for direct connection with the R-studio, so that it would be readily available to the auther as 
well as to the users if any. And also to doucument the work securely for future reference. This repo contains the analysis about the **online news popularity**. 

## The list of R-packages used are: 
  + tidyverse 
  + knitr 
  + caret 
  + gbm
  + rattle 
  + rmarkdown 
  + ggplot2.


The analysis is done for each of the week day.
1. Analysis for [Monday is available here](mondayAnalysis.md)
2. Analysis for [Tuesday is available here](tuesdayAnalysis.md)
3. Analysis for [Wednesday is available here](wednesdayAnalysis.md)
4. Analysis for [Thursday is available here](thursdayAnalysis.md)
5. Analysis for [Friday is available here](fridayAnalysis.md)
6. Analysis for [Saturday is available here](saturdayAnalysis.md)
7. Analysis for [Sunday is available here](sundayAnalysis.md)


## Code used for Automation



```{r }
#select the weekdays from the data
weekDays<- c("monday", "tuesday", "wednesday", "thursday", "friday", "saturday", "sunday")

params= lapply(weekDays, FUN = function(x){list(weekday=x)})
params
output_file<- paste0(weekDays, "Analysis.md")
output_file
#put the filenames into the dataframe
reports<- tibble(output_file, params)
reports
```


```{r}
apply(reports, MARGIN = 1, 
      FUN = function(x){
        render(input="path\Project-II.Rmd", output_file = x[[1]], params =  x[[2]])
      })
