# fall2020

Week One:

1)Upload missing person data set to Rstudio as data frame and Github

2) Answer Question
	A) how many missing cases are there by gender by state
		how many gender minor cases by state

	B) Are there any missing data (observations)

	C) Are there any duplicate cases

3) Read through chapter 4 and 5 from R for Data Science

(Optional) Data science pipe line: Data wrangling section

Week 1


#load in the libraries and files
library(tidyr)
library(dplyr)
library(ggplot2)
library(tidyverse)
library(ggExtra)

adultfemale <- read.csv("D:\\rprojects\\fall2020\\fall2020\\adultfemale.csv")
adultmale <- read.csv("D:\\rprojects\\fall2020\\fall2020\\adultmale.csv")
minorsall <- read.csv("D:\\rprojects\\fall2020\\fall2020\\minorsall.csv")

#clean up collum names

adultfemale <- rename(adultfemale, fName = "First.Name", lName = "Last.Name", ethnicity = "Race...Ethnicity", mDate = "Date.Modified", case = "ï..Case.Number", mAge = "Missing.Age")

adultmale <- rename(adultmale, fName = "First.Name", lName = "Last.Name", ethnicity = "Race...Ethnicity", mDate = "Date.Modified", case = "ï..Case.Number", mAge = "Missing.Age")

minorsall <- rename(minorsall, fName = "First.Name", lName = "Last.Name", ethnicity = "Race...Ethnicity", mDate = "Date.Modified", case = "ï..Case.Number", mAge = "Missing.Age")

#A) how many missing cases are there by gender by state
#   how many gender minor cases by state 

af.cntbyst <- adultfemale %>% count(State)
am.cntbyst <- adultmale %>% count(State)
ma.cntbyst <- minorsall %>% count(State, Sex)


#B) Are there any missing data (observations)

sum(is.na(adultfemale))
sum(is.na(adultmale))
sum(is.na(minorsall))

#C) Are there any duplicate cases

anyDuplicated(adultfemale, incomparables = FALSE)
anyDuplicated(adultmale, incomparables = FALSE)
anyDuplicated(minorsall, incomparables = FALSE)