# Issue Classification and Visualization for Effective Issue Management

Welcome to the "Issue Classification and Visualization for Effective Issue Management" project! This study delves into the crucial realm of issue management, encompassing not only software development but various domains, including business analysis. One of the main goal of this project is to use a cloud-based platform that provides a collaborative workspace for big data analytics and data engineering for processing and analyzing large datasets using Apache Spark(PySpark). Utilizing data sourced from gharchive.org, the dataset covers two hours on January 1, 2015, and aims to identify, categorize, and visualize different types of issues. Our primary objective is twofold: firstly, employing data analysis techniques to categorize issues into bugs, features, and questions, providing insights into issue distribution and characteristics. Secondly, through data visualization, we aim to present these findings insightfully, revealing potential correlations and facilitating efficient issue prioritization and resolution. The significance of this project lies in its applicability to software development and business analysis, optimizing issue management for smoother project execution and informed decision-making. This README will detail the methods, techniques, and results, offering practical insights to improve issue management in diverse domains.

Instructions:

To replicate the project, follow these steps:

* Clone the GitHub repository.
* Install the required dependencies mentioned in the requirements.txt file.
* Download the dataset from gharchive.org for the specified date and time range by using downloading_data.ipynb.
* Use the provided Python code to preprocess the data and perform issue categorization.
* Utilize the data visualization tools and techniques outlined to present the results.

## Instructions to utilize the files in this repository

Apart from downloading the data and combining it into a single file which was done in Jupyter notebook, all the EDA process was done in Databricks Community Edition. Executing the EDA part in jupyter notebook will work but only after doing some changes in the code and the output can vary a little.

In this repository there are 7 files,

1. README.md
2. requirements.txt
3. DOCUMENTATION.md
4. downloading_data.ipynb
5. combining_data.ipynb
6. EDA_with_databricks_visualization.html
7. spark_EDA.ipynb

## BRIEF EXPLANATION OF EACH FILE

I executed "downloading_data.ipynb" and "combining_data.ipynb" in jupyter notebook. Once the data has been downloaded and combined I uploaded the data into databricks community edition using import option. "spark_EDA.ipynb" was executed in databricks community edition but it can also be executed in jupyter notebook, please read the comments in the ipython notebook to understand how to do it. I exported the spark_EDA as "EDA_with_databricks_visualization.html" from databricks so that users who want to look at the visualizations that were done using databricks tools can download the html file and go through it as they are not visible in any IDE/IDLE's as Databricks is a cloud-based platform that was primarily designed for processing and analyzing large datasets also providing data visualization tools. 

## 1. README.md
You are currently in README.md, this file will have all the information that is required to handle the files present in this repository like what are the different types of files that are available, what are they used for and the importance of those files.

## 2.requirements.txt
If you are using a local machine or virtual environment you can use this to install all the necessary libraries/packages. Follow these steps to create a virtual environment and activate it,
1. Open the cmd and navigate to desired directory.
2. use "python -m venv env" to create a python virtual environment called env in the desired location.
3. Once done you can activate it in cmd using "env\Scripts\activate.bat" and execute it. You will be able to see (env) in cmd now.
4. Now type "pip install -r requirements.txt" to install all the packages mentioned in the requirements.txt at once.
5. You can use directly type jupyter notebook and start working with the code now.

## 3. DOCUMENTATION.md
This file contains the complete documentation of this project (Issue Classification and Visualization for Effective Issue Management). This contains contents like Abstract, Introduction, Feasibility study, Literature survey and so on... .

## 4. downloading_data.ipynb
This is a ipython notebook which is supposed to be used in jupyter notebook to download the data from gharchive.org . You can change the values of the parameters from 0 to 24 to download those particular hours of data based on your requirements.  
The files are first downloaded as zip files which are stored in a folder called archive in the same directory. Those files are later unzipped and stored in a new folder called raw as json files.

## 5. combining_data.ipynb
Using this python notebook we combine all the different hours data which are stored in the raw folder as json files into a single json file called combined_data.json which we are going to use for the EDA process.

## 6. EDA_with_databricks_visualization.html
In databricks, we don't need to create a spark session and also there are various in-built visualization tools that we can use to visualize our data by using pyspark or sql statements. These tools are not available in any other IDE like jupyter notebook, Visual studio, Visual studio code, etc. Hence I exported the file as a html file for anyone that wants look at the available visualizations. Also note that for the visualization to work we would be required to display all the rows present in our spark dataframe even if there are 30,000+ rows(it usually truncates the rows but we would still get around 10,000 rows displayed) and exporting this file as an ipython notebook would be a bad idea as all those 10,000 rows will be directly displayed in the notebook making it unreadble. To look at the contents of this file we would have to first download it and open it in a browser.

## 7. spark_EDA.ipynb
In this file I have created a spark session and loaded the combined_data.json file as a spark dataframe. Once the data has been converted to a spark dataframe I have done the EDA process, the main goal for this particular project is to analyze any data that can we use to get an insight and to extract issues to classify them as follows,  
0 = bugs  
1 = feature/enhancement  
2 = question  

For this I have splitted the original dataframe into multiple dataframes by selecting and converting those columns that can be converted into dataframes(these columns usually have values that are of datatypes struct, list, etc) and analyzed each dataframe until I found the dataframe that has the column name "issue". Then I converted that column into a table and found a column in it called "labels" which had the required data that is "bugs", "features", "enhancements" and "questions" as row values. After filtering/cleaning the values(removing null values) and converting them into their respective tables(bugs table, enhancement table and question table) I went ahead and used matplotlib library to visualize the findings.   
    
Note:  
If you import this file into databricks community edition then you will find some visualizations that were created using databricks in-built tools (in the notebook there will be statements such as display(dataframe.limit(10) and you will be able to see something like "Bar Chart" beside "Table" if exists) in the notebook but since I have used ".limit()" on them the graphs won't be accurate and to make them accurate remove ".limi()" functions (example: remove .limit() in display(dataframe.limit(20)) 

### To execute the spark_EDA.ipynb in Jupyter notebook
The main goal of this project is to use a cloud-based platform that provides a collaborative workspace for big data analytics and data engineering for processing and analyzing large datasets using Apache Spark(PySpark).  
Therefore I have executed the code in Databricks Community Edition, executing this code in any other platform or IDE/IDLE will result in probably the same result but the representation of the dataframe will be different. When executed in Jupyter notebook the dataframes were displayed in an unstructured format almost making it impossible to read or understand what is being displayed. To avoid this change all the statements that have "display(dataframe)" or "display(dataframe.limit(20))" to "dataframe.show()".  
If you decide to execute the code in jupyter notebook follow these steps,

1. Read the comments in the notebook at the beginning. I have written instructions on what to uncomment and what to comment out to read the data from the local machine.
2. Change all the statements that have "display(dataframe)" or "display(dataframe.limit(20))" to "dataframe.show()" so that the dataframes are displayed in a tabular format.
3. Make sure the cells that contain the visualizations are set to "Disable scrolling" or "Expand output"

On following these steps you will be able to execute the code without any issues although there is a possibility of some visualizations to alter because of being executed in different platform.

# --------Thanks for reading!--------  
  
Github link : https://github.com/Jagadeesh-Akkinenii/Issue-Classification-and-Visualization-for-Effective-Issue-Management/edit/main/README.md  
  
For any queries or feedback, please contact akkineni.jagadeesh@gmail.com .
Contributions and suggestions are welcome.
