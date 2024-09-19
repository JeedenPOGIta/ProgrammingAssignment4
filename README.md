# PROGRAMMING ASSIGNMENT NO. 4 <br>

<div align="justify">

Welcome! This programming assignment focuses on the use of Data Wrangling and Data Visualization in Python. <br>

### [OBJECTIVES]

1. To identify the codes and functions needed in cleaning and visualizing data <br>
2. To be able to apply and use the different codes and functions in creating a Python program that will
be used in data wrangling and data visualization <br><br>

## [PROBLEM 1] 

Before we proceed, it is essential that we first import the PANDAS functions to our Python code: <br>

<br>

```
#import pandas into the code
import pandas as pd
```

<br>

For this programming assignment, we used a .csv file named "board2.csv" containing sample data of board exam takers. If you want to recreate the problems below, feel free to use your own .csv files.

To access the file within the code, we first need to import the file in the code and save it as a data frame. I achieved this by using the following syntax:

<br>

```
#import the data frame from the file
df1 = pd.read_csv("board2.csv")
```

<br>

SAMPLE DATA FRAME:

|    | Name   | Gender   | Track            | Hometown   |   Math |   Electronics |   GEAS |   Communication |
|---:|:-------|:---------|:-----------------|:-----------|-------:|--------------:|-------:|----------------:|
|  0 | S1     | Male     | Instrumentation  | Luzon      |     58 |            89 |     75 |              78 |
|  1 | S2     | Female   | Communication    | Mindanao   |     52 |            75 |     90 |              52 |
|  2 | S3     | Female   | Instrumentation  | Mindanao   |     83 |            74 |     77 |              57 |
|  3 | S4     | Male     | Instrumentation  | Visayas    |     65 |            58 |     91 |              68 |
|  4 | S5     | Male     | Communication    | Luzon      |     59 |            86 |     43 |              88 |
|  5 | S6     | Female   | Microelectronics | Visayas    |     88 |            45 |     86 |              83 |
|  6 | S7     | Female   | Instrumentation  | Luzon      |     66 |            60 |     60 |              48 |
|  7 | S8     | Male     | Instrumentation  | Luzon      |     49 |            81 |     64 |              53 |
|  8 | S9     | Male     | Instrumentation  | Luzon      |     50 |            36 |     63 |              42 |
|  9 | S10    | Male     | Microelectronics | Mindanao   |     80 |            84 |     61 |              44 |
| 10 | S11    | Female   | Communication    | Visayas    |     48 |            56 |     48 |              67 |
| 11 | S12    | Male     | Communication    | Visayas    |     89 |            67 |     84 |              64 |
| 12 | S13    | Female   | Microelectronics | Luzon      |     88 |            35 |     83 |              43 |
| 13 | S14    | Female   | Microelectronics | Luzon      |     83 |            77 |     89 |              73 |
| 14 | S15    | Female   | Microelectronics | Mindanao   |     69 |            41 |     40 |              86 |
| 15 | S16    | Female   | Communication    | Luzon      |     71 |            70 |     87 |              81 |
| 16 | S17    | Female   | Microelectronics | Mindanao   |     81 |            79 |     77 |              45 |
| 17 | S18    | Male     | Communication    | Visayas    |     81 |            40 |     81 |              52 |
| 18 | S19    | Male     | Microelectronics | Luzon      |     79 |            63 |     79 |              71 |
| 19 | S20    | Female   | Communication    | Mindanao   |     59 |            60 |     62 |              85 |
| 20 | S21    | Female   | Microelectronics | Visayas    |     83 |            51 |     68 |              72 |
| 21 | S22    | Female   | Communication    | Visayas    |     64 |            39 |     89 |              58 |
| 22 | S23    | Male     | Instrumentation  | Luzon      |     84 |            70 |     74 |              47 |
| 23 | S24    | Female   | Microelectronics | Visayas    |     85 |            45 |     60 |              41 |
| 24 | S25    | Male     | Communication    | Luzon      |     74 |            91 |     94 |              42 |
| 25 | S26    | Female   | Instrumentation  | Visayas    |     71 |            47 |     83 |              62 |
| 26 | S27    | Male     | Microelectronics | Visayas    |     70 |            47 |     40 |              86 |
| 27 | S28    | Male     | Communication    | Visayas    |     85 |            53 |     80 |              53 |
| 28 | S29    | Male     | Instrumentation  | Mindanao   |     73 |            48 |     71 |              62 |
| 29 | S30    | Male     | Instrumentation  | Luzon      |     78 |            81 |     57 |              56 |

<br>

a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as
Instrumentation and hometown Luzon  <br>

For this problem, I was tasked to display the Name, GEAS scores, and Electronics scores of the students from the instrumentation track, which 
is from Luzon and has a score of greater than 70 in Electronics. At first, I was a bit lost on how to tackle the problem, 
but then I remembered how PANDAS could help me with arranging and nit-picking certain data from a given data frame. With 
that, I used the following syntax:

```
#stores multiple indexes in a single variable and specify certain conditions on what data to get
Instru = (df1['Hometown']=='Luzon') & (df1['Track']=='Instrumentation') & (df1['Electronics']>70)

#displays the data frame with specific columns only
df1.loc[Instru, ['Name','GEAS','Electronics']]
```
<br>

SAMPLE OUTPUT:

|    | Name   |   GEAS |   Electronics |
|---:|:-------|-------:|--------------:|
|  0 | S1     |     75 |            89 |
|  7 | S8     |     64 |            81 |
| 29 | S30    |     57 |            81 |

<br>

b.  Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is
constant as Mindanao and gender Female <br>

In this next problem, I was tasked to display the Name, Track, Electronics score, and Averages greater than or equal to 55
of those who are female and from Mindanao. There are a lot of things I prepared first before proceeding to display the table. 
First, I made sure to get the average score of each student by using the mean() function. <br>

```
# get the average score of everyone
df1['Average'] = df1[['Math','Electronics','GEAS','Communication']].mean(axis=1)
```
<br>

Next, I set up the conditions for the data to be displayed. 

```
# store multiple indexes with conditions
Mindy = (df1['Hometown']=='Mindanao') & (df1['Gender']=='Female') & (df1['Average']>=55)
```

<br>

And finally, I displayed the table with the required columns. However, the indexes were a mess -- that's why
I put the reset_index function to fix the issue.

```
# displays the data frame with specific columns only
table = df1.loc[Mindy, ['Name','Track','Electronics','Average']].reset_index(drop=1) #resets the indexes back to 0

#Outputs the table
table
```

<br>

SAMPLE OUTPUT:
|    | Name   | Track            |   Electronics |   Average |
|---:|:-------|:-----------------|--------------:|----------:|
|  0 | S2     | Communication    |            75 |     67.25 |
|  1 | S3     | Instrumentation  |            74 |     72.75 |
|  2 | S15    | Microelectronics |            41 |     59    |
|  3 | S17    | Microelectronics |            79 |     70.5  |
|  4 | S20    | Communication    |            60 |     66.5  |

<br>

With that, I was able to nit-pick and display specific data asked of me from a large-scale data frame!  <br>

### [VERSION(s)]
This section of the ReadME file contains the versions of the code. This may be updated if a more efficient way of coding 
is found. <br>

Version 1.0 - use of Pandas and simple data wrangling <br><br>

## [PROBLEM 2]

For the next problem, I was tasked to create a visualization that shows how the different features such as tracking, hometown, 
and gender affect the average scores. I decided to opt for simple bar graphs that effectively show the relationship between 
two variables. 

But before graphing, matplotlib or seaborn must be imported. In this case I used matplotlib.

<br>

```
#import matplotlib 
import matplotlib.pyplot as plt
```

Then, I used the bar() function to display the different graphs. Using the following syntaxes:

<br>

```
# assigns as size of 12in x 5in canvas
plt.figure(figsize=(12,5)) 

#Displays Track Vs Average graph
plt.bar(df1['Track'], df1['Average'])
```

SAMPLE OUTPUT: <br>
![Image_Alt](https://github.com/JeedenPOGIta/Screenshots/blob/14a7210f2060a8c0794475ef548b110b90713f4b/graph1.png)

<br>

```
#Displays Gender Vs Average graph
plt.bar(df1['Gender'], df1['Average'])
```

<br>

SAMPLE OUTPUT: <br>
![Image_Alt](https://github.com/JeedenPOGIta/Screenshots/blob/14a7210f2060a8c0794475ef548b110b90713f4b/graph2.png)
```
#Displays Gender Vs Average graph
plt.bar(df1['Hometown'], df1['Average'])
```

SAMPLE OUTPUT: <br>
![Image_Alt](https://github.com/JeedenPOGIta/Screenshots/blob/14a7210f2060a8c0794475ef548b110b90713f4b/graph3.png)


### [TAKEAWAYS]

For my takeaways from these problems, I was reminded of how perseverance can lead us to results. It took me quite
a while to figure out what line of code I should write to accomplish the problem at hand. There were some moments
that I felt frustrated, but that did not stop me from searching for possible solutions from both my past works and
the internet. In the end, nothing will change if nothing will change. <br>

### [VERSION(s)]
This section of the ReadME file contains the versions of the code. This may update if a more efficient way of coding <br>
is found. <br>

Version 1.0 - Use of matplotlib to dsplay relationships between variables <br>
            
## [END OF REPOSITORY]

And that is a wrap! This is the end of my repository on our programming assignment 34. Please let me 
know if you have any feedback, tips, tricks, or suggestions for improving my coding efficiency! 
Thank you once again! <br>

## [ACKNOWLEDGEMENT] 
I would like to acknowledge Ms. Ma. Madecheen Pangaliman and Mr. Nikko John Lobos for providing knowledge about Python data wrangling
and data visualization and for providing the practice problems presented in the repository. Thank you to both of you!

</div>
