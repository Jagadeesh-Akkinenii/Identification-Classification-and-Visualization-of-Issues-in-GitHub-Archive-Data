# Issue Classification and Visualization for Effective Issue Management

Welcome to the "Issue Classification and Visualization for Effective Issue Management" project! This study delves into the crucial realm of issue management, encompassing not only software development but various domains, including business analysis. Utilizing data sourced from gharchive.org, the dataset covers two hours on January 1, 2015, and aims to identify, categorize, and visualize different types of issues. Our primary objective is twofold: firstly, employing data analysis techniques to categorize issues into bugs, features, and questions, providing insights into issue distribution and characteristics. Secondly, through data visualization, we aim to present these findings insightfully, revealing potential correlations and facilitating efficient issue prioritization and resolution. The significance of this project lies in its applicability to software development and business analysis, optimizing issue management for smoother project execution and informed decision-making. This README will detail the methods, techniques, and results, offering practical insights to improve issue management in diverse domains.

Instructions:

To replicate the project, follow these steps:

* Clone the GitHub repository.
* Install the required dependencies mentioned in the requirements.txt file.
* Download the dataset from gharchive.org for the specified date and time range.
* Use the provided Python code to preprocess the data and perform issue categorization.
* Utilize the data visualization tools and techniques outlined to present the results.

## Instructions to utilize the files in this repository

In this repository there are 

1. README.md
2. DOCUMENTATION.md
3. downloading_data.ipynb
4. combining_data.ipynb
5. EDA_with_databricks_visualization.html
6. spark_EDA.ipynb

## 1. README.md
You are currently in README.md, this file will have all the information that is required to handle the files present in this repository like what are the different types of files that are available, what are they used for and the importance of those files.

## 2. DOCUMENTATION
This file contains the complete documentation of this project (Issue Classification and Visualization for Effective Issue Management). This contains contents like Abstract, Introduction, Feasibility study, Literature survey and so on... .

## 3. downloading_data.ipynb
This is a ipython notebook which is supposed to be used in jupyter notebook to download the data from gharchive.org . You can change the values of the parameters from 0 to 24 to download those particular hours of data based on your requirements.  
The files are first downloaded as zip files which are stored in a folder called archive in the same directory. Those files are later unzipped and stored in a new folder called raw as json files.

## 4. combining_data.ipynb
Using this python notebook we combine all the different hours data which are stored in the raw folder as json files into a single json file called combined_data.json which we are going to use for the EDA process.

## 5. EDA_with_databricks_visualization.html
In databricks, we don't need to create a spark session and also there are various in-built visualization tools that we can use to visualize our data by using pyspark or sql statements. These tools are not available in any other IDE like jupyter notebook, Visual studio, Visual studio code, etc. Hence I exported the file as a html file for anyone that wants look at the available visualizations. Also note that for the visualization to work we would be required to display all the rows present in our spark dataframe even if there are 30,000+ rows(it usually truncates the rows but we would still get around 10,000 rows displayed) and exporting this file as an ipython notebook would be a bad idea as all those 10,000 rows will be directly displayed in the notebook making it unreadble. To look at the contents of this file we would have to first download it and open it in a browser.

## 6. spark_EDA.ipynb
In this file I have created a spark session and loaded the combined_data.json file as a spark dataframe. Once the data has been converted to a spark dataframe I have done the EDA process, the main goal for this particular project is to analyze any data that can we use to get an insight and to extract issues to classify them as follows,  
0 = bugs  
1 = feature/enhancement  
2 = question  

For this I have splitted the original dataframe into multiple dataframes by selecting and converting those columns that can be converted into dataframes(these columns usually have values that are of datatypes struct, list, etc) and analyzed each dataframe until I found the dataframe that has the column name "issue". Then I converted that column into a table and found a column in it called "labels" which had the required data that is "bugs", "features", "enhancements" and "questions" as row values. After filtering/cleaning the values and converting them in their respective tables(bugs table, enhancement table and question table) I went ahead and used matplotlib library to visualize the findings.  

Note:  
If you import this file into databricks community edition then you will find some visualizations that were created using databricks in-built tools (in the notebook there will be statements such as display(dataframe.limit(10) and you will be able to see something like "Visualization 1" beside "Table" if exists) in the notebook but since I have used ".limit()" on them the graphs won't be accurate and to make them accurate remove ".limi()" functions (example: remove .limit() in display(dataframe.limit(20)) 

For any queries or feedback, please contact akkineni.jagadeesh@gmai.com .
Contributions and suggestions are welcome.
