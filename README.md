# Exploratory Data Analysis (EDA) using Pandas

**By**: Marti Heit, Joleena Marshall, Faye Pei, and Nestor Teodoro Chavez.

## Our Goal 
The goal of this project is display how `Pandas`, a software library written for Python, is a great choice for data manipulation and analysis. Pandas will help you explore, clean, and process your data. In pandas, a data table is referred to as `DataFrame`. 

## The Description
This projects shows the entire process of EDA. Pandas handles data acquisition really well. Pandas is able to import   `xml`,`json`,`csv`,`xls`,and `html`. 

<< fill in >>

## Getting Started 

Download the [eda-code.ipynb](https://github.com/neteodorochavez/msds610-eda-pandas/blob/main/EDA-Code.ipynb). Next, download the [data](https://github.com/neteodorochavez/msds610-eda-pandas/tree/main/data). If you'd like to use other datasets, make sure to add them into the data folder. The filetypes of choice have a wide range.

## Installation

```
pip install --upgrade pip
pip install pandas
pip install matplotlib
```

## Our Process

### Benefits of Pandas Library (Joleena)

### Importing Data (Joleena)

### Data Exploration (Marti)
#### Manipulating Data Frame

### Preprocessing 

Preprocessing is the stage in EDA that explores the data and ensures its integrity. In other words, it makes sure that the dataset is properly formatted in order to continue with the next step of the process. Oftentimes this stage deals with missing or misleading data, creating better features (columns) than the ones already provided by the original dataset, and explores options for making the process of data retrieval more efficient.  

#### Converting Data Types
The benefit in using Pandas is that it allows one to easily convert data types. This stage is called data manipulation, and its where Pandas really shines. We are able to use functions that are specific to the pandas library to convert from one data type to another without altering the metadata itself. For instance, if a survey was recording birthdays of its users in order to find out, on average, how many users celebrate their birthday during the holiday months. Pandas allows to convert strings in the form of '12-24-2001' into a `datetime` object in order for us to easily extract month, day, or year. Common functionalities such as these are made efficient processes with the help from Pandas. 

<p float="left">
  <img src="figures/df_student_dtypes.png" width="300"/>
  <img src="figures/df_student_dtypes_new.png" width="300"/>
</p>

In the case of missing information, Pandas allows the `.fillna(value)` function that allows us to set all of the `NaN` or missing values to whatever value we desire; typically 0. The importance behind this is seen dramatically when our dataset is minimal. For example, if the dataset we were working with contained 5 observations, getting rid of 1 observation diminishes 20% of the data set. This problem is seen on the same order with large datasets but in order to preserve order with any size of datasets, Pandas lets us do inplace replacement to keep rows that one may otherwise remove entirely. 

#### Appending Data 
We've seen that data conversion is an important part in cleaning up data. Once we've cleaned up our data it might behoove the user to be able to update the existing table or add in more values that aid in the process of building holistic insights.

```
df_student['gender'] = ['F', 'F', 'M', 'F', 'M', 'M', 'F', 'F']
df_student
```
This gives us the opportunity to create any new row and population it with values. In the above example, we have created a new column represented by `gender` on the DataFrame `df_student`. 

<p float="left">
  <img src="figures/df_student.png" width="400"/>
  <img src="figures/df_student_append.png" width="450"/>
</p>

#### Removing Data 

The process for removal is similar to that of appending with one small change. Although the methodology and syntax is very similar, when removing data from the DataFrame we want to ensure we are deleting the entire column or the entire row. Importance is weighted heavily on the axis parameter within the function call, `.drop(col, axis = 1)`. This allows you to delete columns in the DataFrame. 

#### Indexing Data

### Research Questions

### Visualization (Faye)

<p float="left">
  <img src="figures/avg_account.jpg" width="270" />
  <img src="figures/job_freq.jpg" width="262" /> 
  <img src="figures/salary_hist.jpg" width="262" />
</p>


### What's Next? 
