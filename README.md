# Exploratory Data Analysis (EDA) using Pandas

**By**: Marti Heit, Joleena Marshall, Faye Pei, and Nestor Teodoro Chavez.

## Motivation
Exploratory Data Analysis (EDA) is one of the most important steps in solving data science problems, considering it takes up 90% of what data scientists do day-to-day. Without using the appropriate cleaned data, the inferences or predictions that are made can be misleading and unreliable. EDA is the process of exploring and cleaning our data to find trends that we can keep in mind, or resolve any issues that the data may cause so that we can choose the most appropriate model that will provide us with the best results to answer our research questions. With a multitude of different tools we can use to conduct EDA, the best solution is to use a tool that has all the functionality we need with one library. Our goal is to display how `Pandas`, a software library written for Python, is a great choice for data manipulation and analysis. Pandas will help you explore, clean, and process your data so that it is ready for modeling or to make inferences.

## The Description

Here, we will explain the significance of the four steps of EDA using Pandas:<br>
1. [Importing the Data](#import)<br>
2. [Data Exploration](#explore)<br>
3. [Data Preprocessing](#preprocess)
4. [Visualization](#viz)<br>

## Getting Started 

Download the [eda-code.ipynb](https://github.com/neteodorochavez/msds610-eda-pandas/blob/main/EDA-Code.ipynb). Next, download the [data](https://github.com/neteodorochavez/msds610-eda-pandas/tree/main/data). If you'd like to use other datasets, make sure to add them into the data folder. The filetypes of choice have a wide range.

## Installation

```
pip install --upgrade pip
pip install pandas
pip install numpy
pip install matplotlib
```

## Our Process

### Benefits of Pandas Library

Python's Pandas library is a powerful tool for EDA because of its flexibility with data manipulation using its provided functions, as well as its compatibility with other commonly-used Python packages in data science such as scipy, numpy, and matplotlib. Pandas provides organized and easy-to-read [documentation](https://pandas.pydata.org/pandas-docs/stable/reference/index.html) to help teach you how to use its different functions. In pandas, a data table is referred to as `DataFrame`. 

### <a name="import">Importing Data</a> 

To begin EDA, the first step is to acquire the data you need. The internet, and other data sources, consist of data in different formats such as XML, HTML, JSON, and CSV. To help make the data more readable and easier to work with, Pandas provides functions to convert these filetypes into data frames with a simple line of code. This way, we can combine data from different formats into one. With a working data frame, we can see every record without the learning curve of learning how to read different source code. Here are a few examples:

XML file to a readable data frame using `pd.read_xml(<filepath>)`

```xml
<data>
  <student name="John">
    <email>john@mail.com</email>
    <grade>A</grade>
    <age>16</age>
  </student>
  ...
  <student name="Hannah">
    <email>hannah@mail.com</email>
    <grade>A</grade>
    <age>17</age>
  </student>
</data>

```

<p float="left">
  <img width="300" alt="Screen Shot 2021-10-08 at 11 17 55 PM" src="https://user-images.githubusercontent.com/31682057/136646611-7522c99d-1862-4e8b-abda-d17adc36468a.png">
</p>

JSON file to a readable data frame using `pd.read_json(<filepath>)`

```json
[
  {
    "id": "A001",
    "name": "Tom",
    "math": 60,
    "physics": 66,
    "chemistry": 61
  }, 
  {
    "id": "A002",
    "name": "James",
    "math": 89,
    "physics": 76,
    "chemistry": 51
  },
  {
    "id": "A003",
    "name": "Jenny",
    "math": 79, 
    "physics": 76,
    "chemistrY": 51,
    }
]

```

<p float="left" >
  <img width="300" alt="Screen Shot 2021-10-08 at 11 20 57 PM" src="https://user-images.githubusercontent.com/31682057/136646707-85bdd8f3-e009-470c-836c-5774653dec5c.png">
</p>

HTML file to a readable data frame using `pd.read_html(<filepath>)`

```html
<table class="wikitable" style="float:right; font-size:95%; margin:190px">
  <caption>
    "Election results from statewide races"
    <sup id="cite_ref-153" class="reference">
      <a href="#cite_note-153">[153]</a>
    </sup>
  </caption>
  <tbody>
    <tr>
      <th>Year </th>
      <th>Office </th>
      <th>
        <a href="/wiki/Minnesota_Republican_Party" class="mw-redirect" title="Minnesota Republican Party">GOP</a>
      </th>
      ...
    </tr>
  </tbody>
</table>

```


<p float="left">
<img width="300" alt="Screen Shot 2021-10-08 at 11 23 11 PM" src="https://user-images.githubusercontent.com/31682057/136646776-b40ddcf7-5bd5-4622-bbfe-b8b80c33c044.png">
</p>

CSV file to a data frame using `pd.read_csv(<filepath>)` (This is useful when aggregating with data from other filetypes or to use Pandas to preprocess data)

| id      | name      | age |
| :-------|:---------:| ---:|
| 065     | Marti     | 21  |
| 066     | Joleena   | 22  |
| 067     | Nestor    | 23  |
| 068     | Faye      | 24  |
| 069     | Bobby     | 20  |
| 070     | Tom       | 26  |
| 071     | Xue       | 21  |
| 064     | Isabella  | 22  |

<p float="left">
<img width="144" alt="Screen Shot 2021-10-08 at 11 25 29 PM" src="https://user-images.githubusercontent.com/31682057/136646834-1ac6ce1c-9f74-4055-a616-38cb0835b02c.png">
</p>

### <a name="explore">Data Exploration</a> 

Due to the fact that raw data is difficult for humans to read, it is common to obtain a data frame, but not know what it holds. The data may have millions of rows, so it is not plausible to comb through every data frame row by row. Instead, Pandas functions provide the ability to get a high-level view of the data. The most common way of quickly examining data is to look at a small subset of the rows. Shown below, the `df.head(n)` function will display the first `n`, five by default, rows of the data frame.

< p float="left">
<img width="645" alt="df_head" src="https://user-images.githubusercontent.com/59813199/136682027-6aa28b71-65ef-481b-a1a1-3b77d9b80702.png">
</p>

This provides a peek in to the data, but it is important to get some summary information as well. Both `df.describe()` and `df.info()` will return summary tables for the data frame. The describe function provides summary statistics, including mean, standard deviation, median, minimum, and maximum, for numeric columns. The info function, shown below, on the other hand, can be used to determine data types, data frame shape, and nullity issues.   

< p float="left">
<img width="395" alt="df_info" src="https://user-images.githubusercontent.com/59813199/136681907-f481707b-7c01-490a-a53f-3e5dd4e845c4.png">
</p>

If there are discrepancies between columns non-null counts, calling `df.isnull()` on a data frame, or any subset of that data frame, will return a data frame of the same size containing Boolean true or false values describing each entry's nullity.  

### <a name="preprocess">Preprocessing</a>

Preprocessing is the stage in EDA that explores the dataset and ensures its integrity. In other words, it makes sure that the dataset is properly formatted in order to continue with the next step of the process. Oftentimes this stage deals with missing or misleading data, creating better features (columns) than the ones already provided by the original dataset, and explores options for making the process of data retrieval more efficient.  

#### Converting Data Types
The benefit in using Pandas is that it allows one to easily convert data types. This stage is called data manipulation, and its where Pandas really shines. We are able to use functions that are specific to the pandas library to convert from one data type to another without altering the metadata itself. For instance, if a survey was recording birthdays of its users in order to find out, on average, how many users celebrate their birthday during the holiday months. Pandas allows to convert strings in the form of '12-24-2001' into a `datetime` object in order for us to easily extract month, day, or year. Common functionalities such as these are made efficient processes with the help from Pandas. 

<p float="left">
  <img src="figures/df_student_dtypes.png" width="300"/>
  <img src="figures/df_student_dtypes_new.png" width="285"/>
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
  <img src="figures/df_student.png" width="375"/>
  <img src="figures/df_student_append.png" width="425"/>
</p>

#### Removing Data 

The process for removal is similar to that of appending with one small change. Although the methodology and syntax is very similar, when removing data from the DataFrame we want to ensure we are deleting the entire column or the entire row. Importance is weighted heavily on the axis parameter within the function call, `.drop(col, axis = 1)`. This allows you to delete columns in the DataFrame. 

#### Indexing Data

One last important step before you are ready to start the visualization process is with regards to efficiency. In this last step, we are going to organize our data usch that we can uniquely identify certain rows. Oftentimes, DataFrames will be serialized and the row will start at 0 and increase as we add more rows. We can reindex the entire DataFrame to fit with our Research Questions. The purpose of this stage is to consider the data you are going to work with in the near future and how can one set themselves up for success by organizing. As a simpel example, age has been chosen as the index. The rationale is that we not have our rows sorted by an integer value that will allow us to nicely 'slice' up the rows in order to categorize them by age for buidling insights on age groups rather than individuals. 

### Research Questions 

Asking questions throughout the stages outlined above it pivotal. If it hasn't been done yet, now is a great time to start. In this stage of the EDA process, the user is comfortable and confident with the dataset. In other words, they understand what data has been collected, where it came from, and that the data has been parsed in such a way that makes it universal to questions who may or may not have started to ask. 

In order to build models and insights its important to ask thought-provoking questions. This stage follows hand-in-hand with the scientific method. What exactly was the goal of utilizing this dataset? What questions did you initially have and how have they evolved since working with the dataset? One of the most common practices is building evidence for relationships that exist within your dataset.

The questions you pose here are not set in stone but they will be the motivation for the next step, Visualization. Oftentimes, the data will offer information or enlightenment on the topic of your choice and it is up to the user to continue to dig deeper for significant insights. Usually, these insights should be data-driven. When you've gathered your promising evidence, make sure you question its validity and explore your results; perhaps even, modify your initial question. 

### <a name="viz">Visualization</a>

<p float="left">
  <img src="figures/avg_account.jpg" width="270" />

Scatter plot- It is a type of plot which will be in a scatter format. It is mainly between 2 features. Here we will plot previous Age vs Salary and see if there is any linearity. From this scatter plot,we might make a preliminary conclusion  that there is the linear relationship between age and salary.

  <img src="figures/job_freq.jpg" width="262" /> 
  
Bar plot or bar chart- It is a graph that represents the category of data with rectangular bars with lengths and heights that is proportional to the values which they represent. The bar plots can be plotted horizontally or vertically. A bar chart describes the comparisons between the discrete categories. One of the axis of the plot represents the specific categories being compared, while the other axis represents the measured values corresponding to those categories. We plot the frequency of previous jobs for each person, the bar plot could clearly present the data.

Histogram plot- A histogram is a graph showing frequency distributions.
It is a graph showing the number of observations within each given interval.
This type of plots are very popular in statistical analysis. Example: Say you ask for the salary of 8 people, you might end up with a histogram like this:

  <img src="figures/salary_hist.jpg" width="262" />

</p>


### What's Next? 
Reporting on developments of other Python libraries.

Digging deeper into Panda's efficiency with `Big Data`.
