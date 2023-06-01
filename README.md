# Ex-08-Data-Visualization-

### AIM
To Perform Data Visualization on a complex dataset and save the data to a file. 

### Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

### ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


### CODE
```
Developed By : Silambarasan K
Reg No: 212221230101 
```
```python
# Importing the needed libraries
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

tips_df=pd.read_csv("tips.csv")
tips_df

tips_df.head()
tips_df.isnull().sum()
tips_df.duplicated()
# Get some info on the data
tips_df.info()
# Get some description of the data
tips_df.describe()

# Get value counts for the SEX column
pd.DataFrame(tips_df["sex"].value_counts())

# Get value counts for the SMOKER column
pd.DataFrame(tips_df["smoker"].value_counts())

# Correlation of the data
sns.set()
# Plot
sns.pairplot(tips_df, hue='sex', palette='cool')
# Show
plt.show()
# Further correlation of data
plt.figure(figsize=(8,6))
sns.set_context('paper', font_scale=1.4)

# Plot
tips_corr = tips_df.corr()
# Create the heatmap, add annotations and a color map
sns.heatmap(tips_corr, annot=True, cmap='Reds')
# Show
plt.show()

# Frequency of Tip
plt.style.use("ggplot")
# Plot
sns.histplot(tips_df['tip'], kde=True).set(title = "Frequency of Tip")
# Show
plt.show()

# Frequency of Bill
plt.style.use("ggplot")
# Plot
sns.histplot(tips_df['total_bill'], kde=True).set(title = "Frequency of Bill")
# Show
plt.show()

# Which gender is more smoky?
plt.style.use("fivethirtyeight")

# Plot
sns.countplot(data=tips_df, x="smoker", hue="sex").set(title = "Which gender is more smoky?")
plt.text(0.6+0.2, 70.5, "We observe that mostly \nmales smoke more", horizontalalignment='left', size='medium', color='black', weight='semibold')

# Show
plt.show()

# Which is the most common visit day per gender

# Plot
sns.countplot(data=tips_df, x="day", hue="sex").set(title = "Which is the most common visit day per gender")
plt.text(1.4+0.2, 37.5, "Seems Males visit mostly \non Saturdays & Sundays, \nwhile females mostly on Thursdays", horizontalalignment='left', size='medium', color='black', weight='semibold')

# Show
plt.show()

sns.lmplot(x='total_bill', y='tip', data=tips_df, col='day', hue='sex',height=8, aspect=0.6)
sns.lmplot(x='total_bill', y='tip', data=tips_df, col='time', hue='sex', height=8, aspect=0.6)



# On which day the most tip given, hued by Gender?
plt.style.use("fivethirtyeight")
sns.set_context('poster', font_scale=0.8)

# Plot
plt.title("On which day the most tip given, hued by Gender?")
sns.barplot(data=tips_df, x="day", y="tip", hue="sex")
sns.countplot(data=tips_df, x="day", hue="sex")
plt.text(2.3+0.2, 25.5, "Most of the tip \nwas given on Sat, \nby males", horizontalalignment='left', size='small', color='black', weight='semibold')

# Show
plt.show()

# At which time the most tip given, hued by Gender?

# Plot
plt.title("At which time the most tip given, hued by Gender?")
sns.barplot(data=tips_df, x="day", y="tip", hue="sex")
sns.countplot(data=tips_df, x="time", hue="sex")
plt.text(0.5+0.2, 40.5, "Most of the tip \nwas given at Dinner, \nby males", horizontalalignment='left', size='small', color='black', weight='semibold')

# Show
plt.show()

# countplot showing the count of total_bill 
sns.set(style="ticks", palette="muted")

f, axes = plt.subplots(1, 2, figsize=(12, 4)) # set up 1 by 2 plot and figure size 12 by 4
# create a variable to store the order of days to show on the plots
day_order=["Thur", "Fri", "Sat","Sun"] # the order to be shown on the plot

# plot number of tables per day, added in time too
sns.countplot(x ="day",data =tips_df, hue="time", palette=["teal","yellow"], order=day_order, ax=axes[0])
axes[0].set_title("Count of tables served by Day")

# plot number of  tables per day by size of party
sns.countplot(x =("day"), hue="size",data =tips_df, ax=axes[1], order=day_order)
axes[1].set_title("Tables served by Day and by party size");
# hide the matplotlib axes text

```
### OUTPUT:
![p1](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/8039a9a2-20e9-48a9-a96f-3f5642f4c347)
![p2](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/28b6ce5e-2202-4270-a945-021aebb7ff26)
![p3](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/9adeee3e-5922-43e2-a68e-2b5862ea7d05)
![p4](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/b41103f4-eec5-4418-bbed-c395c6bac31b)
![p5](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/39550125-c3e8-4507-884a-5c23d535fcab)
![p5a](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/1959ee02-ec28-4a76-af5d-f8289b9700e8)
![p6](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/86a35f95-d958-49c5-a24a-cba2c0eede3d)
![p7](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/abba88c3-bb5b-4559-91a3-8aad787f5f49)
![p8](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/1c422fd7-20eb-4fa6-ae2c-a3a9a49fa69f)
![p9](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/9ca52112-d4ea-4837-bef5-a78687241446)
![p10](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/e436456c-e9d7-49ae-b908-44d8fbe07816)
![p11](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/4a0b0f49-f2b6-444b-8457-578ed1fde0fc)
![p12](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/3ddc582d-8a8c-4ca7-acaf-04a28b4c20a0)
![p13](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/fedaa3db-ead5-46c0-8dd7-380f3687c4dd)
![p14](https://github.com/simbu07/Ex-08-Data-Visualization_1/assets/94525786/49241331-f11c-4490-ba6f-f03bf96b93ea)

### RESULT:
 Thus the Data Visualization on a given complex dataset is performed sucessfully...

```
# OUPUT
