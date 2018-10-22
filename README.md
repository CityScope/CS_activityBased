# Activity scheduler and mode choice model
The nhtsSimple.py script uses data from the National House Travel Survey to calibrate a simple activity-based mobility model. 

## Inputs


##### NHTS data
The main source of data for this analysis is the National Household Travel Survey. 

###### Blocks data

The design team collaborates with the technical team on the design of the city blocks used in the model simulation via a spreadsheet ([link](https://docs.google.com/spreadsheets/d/1aKRPp83EWWdBri6MwjuGcZVSki2xQuxd_OjMAdrrpS4)).

That spreadsheet is downloaded and saved to `blocks.csv`. The data defines one city block per row and specifies the number of people of each occupation type, the residential capacity and the capacity of the third places. The occupation types are:

| Code 	| Description											|
|-------|-------------------------------------------------------|
| 1		| Sales or service										| 
| 2		| Clerical or administrative 							|
| 3		| Manufacturing, construction, maintenance, or farming	| 
| 4		| Professional, managerial, or technical 				|
| 5		| Student 												|

maxDepth: the maximum depth of the decision tree which will be used to predict mode choice for each choice. This also corresponds to the number of if-else statements required to make the mode choice prediction.

## Outputs

simPop.csv is a dataframe containing the synthetic population corresponding to each defined block. This includes personal characteristics of the population as well as a mobility motif for each person.

treeModeSimple.pdf is a visualisation of the calibrated decision tree for predicting mobility mode choice. The four possible options are as follows:

| 0       | 1       | 2       | 3       |
|---------|---------|---------|---------|
| driving | cycling | walking | transit |

An example tree is shown below.

![viz](./example_tree.png)


modeChoice.py contains python code for the series of if -else statements corresponding to the calibrated decision tree. This script is created by running the nhtsSimple.py script. 


## Running

###### Download the NHTS Data

This data is large and excluded from the repository via an entry in the `.gitignore`.

- Create a folder to hold the data `./nhts/`
- Download the NHTS 2017 v1.1 csv files from https://nhts.ornl.gov/ and save `./nhts/trippub.csv` and `./nhts/perpub.csv`


###### Download the Blocks Data

Download the blocks data from the [spreadsheet](https://docs.google.com/spreadsheets/d/1aKRPp83EWWdBri6MwjuGcZVSki2xQuxd_OjMAdrrpS4) to `blocks.csv`.

###### Recompute

`python nhtsSimple.py`
