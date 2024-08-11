# demographic_dataset

##### This exercise is inspired by [freeCodeCamp's Demographic Data Analyzer](https://www.freecodecamp.org/learn/data-analysis-with-python/data-analysis-with-python-projects/demographic-data-analyzer). It's only for practice purposes. 

## 📒 Step-by-step description

## I. Import libraries
#### only libraries useful for the notebook will be imported. this is a general rule.

Usage:

🟥numpy is the fundamental library for numerical computations in Python 
<br>
🟨pandas is used for data manipulation and analysis. It's built on NumPy
<br>
🟩matplotlib.pyplot is responsbile for creating a wide range of static, animated, and interactive visualizations. It provides a simple interface for creating plots, histograms, power spectra, bar charts, error bars, scatterplots, etc
    <br>
🟦ipywidgets are interactive HTML widgets 

***

## II. Data collection

1. Load the collected data 

        data = pd.read_csv('adult.data.csv')

2. Provide a quick overview of the dataset

        data.info()  


## III. Pre-exercise 🌟

1. Transform the data into a structured format that can be easily analyzed and manipulated using pandas functions

        df = pd.DataFrame(data) 

2. Calculate the frequency of each unique value in the 'native-country' column of the DataFrame

       df['native-country'].value_counts() 

3. Count the number of unique countries
   
       num_countries = df['native-country'].value_counts().shape[0]

4.  Print the number of countries

        print(f"The number of unique countries: {num_countries}")

***

#### 💡 f -> formatted strings

***


5. Select the first row of the DataFrame df based on its row label (which is 0 in this case)
   
       df.loc[0]

***
   
  ####  💡 .loc -> is used for labe-based selection

***
  
  
## IV. Exercises!
  ### 1. What is the mean age of men?
  
        mean_age_men = round(df[df['gender'] == 'Male']['age'].mean(),1) 

        print(mean_age_men)

***

 🔹     Filter the DataFrame df to include only rows where the 'gender' column has the value 'Male';  
 
     df[df['gender'] == 'Male] 
 
 🔹   Select only the 'age' column from the filtered DataFrame; 
 
     ['age']
 
 🔹   Calculate the mean (average) of the selected 'age' values; 
 
      .mean() 
 
 🔹   Round the calculated average to one decimal place; 
 
     round (..., 1) 
 
 🔹   Assign the calculated average age to the variable mean_age_men.
 
     mean_age_men  
 

***

  ### 2. What is the number of people who are over 30 years old and have a Bachelors? 

          bachelors_degree_over_30 = len(df[(df['age'] > 30) & (df['education'] == 'Bachelors')]) 
  
          print(bachelors_degree_over_30)

 ***

 🔸   Filter the DataFrame df to include only rows where both the 'age' is greater than 30 and the 'education' is Bachelors

 
         len(df[(df['age'] > 30) & (df['education'] == 'Bachelors')])  
         
#### 💡len() -> is used to count the number of rows in the filtered DataFrame, which represents the number of people meeting both criteria.

***
  ### 3. Calculate the percentage of the previous data
         total_people = len(df)

         bachelors_degree_over_30_percentage = round((bachelors_degree_over_30 / total_people) * 100, 1)

         print(bachelors_degree_over_30_percentage)

***

#### 💡 len() is used again.

 Let's decompose 
 
                         round((bachelors_degree_over_30 / total_people) * 100, 1)
                         
 
1. calculate the percentage of individuals with a bachelor's degree who are over 30. <br>
2. to obtain the percentage, the result is multiplied by 100 <br>
3. the percentage is then rounded to one decimal place. That's why, function "round" is used. 

***

### 4. What is the number of people who are over 30 years old and have a Masters?
    masters_degree_over_30 = len(df[(df['age'] > 30) & (df['education'] == 'Masters')])
  
    print(masters_degree_over_30)

***
Replicating the previous steps, this time for Masters.

***

### 5. Calculate the percentage of the previous data

    total_people = len(df)

    masters_degree_over_30_percentage = round((masters_degree_over_30 / total_people) * 100, 1)

    print(masters_degree_over_30_percentage)

***

Idem 4.

***

### 6. Create a pie plot showing the percentage of people with Bachelors or Masters Degree who are >30 years old

    x = [bachelors_degree_over_30, masters_degree_over_30] # 

    y = ['Bachelors', 'Masters'] # the list of labels corresponding to each slice

    plt.pie(x, labels=y, autopct='%1.1f%%')

    plt.title('Percentage of People with Bachelors or Masters Degrees (Over 30)')

    plt.show()

***
x calculates the numerical values for each slice

y creates a list of labels corresponding to each slice

💡 it's not necessary to name the variables 'x', respectively 'y'. any suitable name is preferred.

***

### 7. Which country hast the biggest number of people who make >50k?

    high_income_df = df[df['salary'] == '>50K']

    country_counts = high_income_df['native-country'].value_counts()

    country_with_highest_count = country_counts.index[0]

    print(country_with_highest_count)

🟩🟩🟩🟩🟩🟩🟩🟩🟩🟩🟩🟩🟩🟩🟩

## BONUS: Which is the top function in France? ✍️

    top_IN_occupation = df[(df['native-country'] == 'France') & (df['salary'] == '>50K')]['occupation'].value_counts().index[0]  

    print(top_IN_occupation)

*** 

🔸  Filter the DataFrame to include only rows where the country is 'France' and the salary is greater than 50K;                            

        df[(df['native-country'] == 'France') & (df['salary'] == '>50K')]['occupation'].value_counts().index[0] 
        

🔹  Select the 'occupation' column from the filtered DataFrame;

        ['occupation'] 

🔸  Count the occurrences of each occupation;

        .value_counts() 

🔹  Get the most frequent occupation (the first index of the resulting Series).


        .index[0]  

***
