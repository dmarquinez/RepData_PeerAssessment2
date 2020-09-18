---
title: "Data analysis"
output: 
  html_document:
    keep_md: true
---



<10 lines

## Data Processing  

### Loading data  

The data was downloaded from the next link :  

* [Storm Data](https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2FStormData.csv.bz2)


```r
if(!file.exists("repdata_data_StormData.csv.bz2")){
  link <- "https://d396qusza40orc.cloudfront.net/repdata%2Fdata%2FStormData.csv.bz2"
  download.file(link,
                destfile = "repdata_data_StormData.csv.bz2")
}
dataRAW <- read.csv("repdata_data_StormData.csv.bz2")
```
Let's take a look at the dimension of the data

```r
dim(dataRAW)
```

```
## [1] 902297     37
```
Wow! Almost a million of observations and 37 variables. Maybe we could remove some that are unnecesary.

There is also some documentation of the database available. Here you will find how some of the variables are constructed/defined.  

* National Weather Service [Storm Data Documentation](https://d396qusza40orc.cloudfront.net/repdata%2Fpeer2_doc%2Fpd01016005curr.pdf)

* National Climatic Data Center Storm Events [FAQ](https://d396qusza40orc.cloudfront.net/repdata%2Fpeer2_doc%2FNCDC%20Storm%20Events-FAQ%20Page.pdf)

### Subsetting data  
As we have seen before, there are a lot of variables so we are going to select only those that are necessary to our research questions:  

1. Across the United States, which types of events (as indicated in the **EVTYPE** variable) are most harmful with respect to population health? 

2. Across the United States, which types of events have the greatest economic consequences?  


```r
dataSub <- dataRAW[c(1,8,23:28,37),]
names(dataSub) 
```

```
##  [1] "STATE__"    "BGN_DATE"   "BGN_TIME"   "TIME_ZONE"  "COUNTY"    
##  [6] "COUNTYNAME" "STATE"      "EVTYPE"     "BGN_RANGE"  "BGN_AZI"   
## [11] "BGN_LOCATI" "END_DATE"   "END_TIME"   "COUNTY_END" "COUNTYENDN"
## [16] "END_RANGE"  "END_AZI"    "END_LOCATI" "LENGTH"     "WIDTH"     
## [21] "F"          "MAG"        "FATALITIES" "INJURIES"   "PROPDMG"   
## [26] "PROPDMGEXP" "CROPDMG"    "CROPDMGEXP" "WFO"        "STATEOFFIC"
## [31] "ZONENAMES"  "LATITUDE"   "LONGITUDE"  "LATITUDE_E" "LONGITUDE_"
## [36] "REMARKS"    "REFNUM"
```
Those are the variables that we need to do our research. In the next chunk we are going to calculate the property and crop total damages.

### Cleaning and tidying data  


```r
character <- c("H","h","K","k","M","m","B","b","+","-","?","0","1","2","3","4","5","6","7","8"," ")
multiple <- c(100,100,1000,1000,1000000,1000000,1000000000,1000000000,1,0,0,10,10,10,10,10,10,10,10,10,0)
exponents <- cbind(character,multiple)
```



```r
#dataSub$PROPERTY <- #multiple[match(dataSub$PROPDMGEXP,character)]
```

## Results    



