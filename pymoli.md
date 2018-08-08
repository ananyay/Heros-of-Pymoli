# Heros-of-Pymoli

```python
# Importing Dependencies 
import pandas as pd 
import numpy as np
```


```python
#  Create a path to the csv file
pymoli = "resources/purchase_data.csv"

# Read the path using pandas into a DataFrame
pymoli_df = pd.read_csv(pymoli,encoding='utf-8')

#head displays the top rows 
pymoli_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase ID</th>
      <th>SN</th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Lisim78</td>
      <td>20</td>
      <td>Male</td>
      <td>108</td>
      <td>Extraction, Quickblade Of Trembling Hands</td>
      <td>3.53</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Lisovynya38</td>
      <td>40</td>
      <td>Male</td>
      <td>143</td>
      <td>Frenzied Scimitar</td>
      <td>1.56</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Ithergue48</td>
      <td>24</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>4.88</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Chamassasya86</td>
      <td>24</td>
      <td>Male</td>
      <td>100</td>
      <td>Blindscythe</td>
      <td>3.27</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Iskosia90</td>
      <td>23</td>
      <td>Male</td>
      <td>131</td>
      <td>Fury</td>
      <td>1.44</td>
    </tr>
  </tbody>
</table>
</div>




```python
# calculate total players count ,by extracting the unique player list by using .unique() and counting them by using len()
Total_players = len(pymoli_df["SN"].unique())
Total_players
```




    576




```python
# create a data frame with total_players count 
player_count = pd.DataFrame({"Total players":Total_players},index = [0])
player_count

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total players</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>576</td>
    </tr>
  </tbody>
</table>
</div>




```python
                                # Purchasing Analysis (Total) #
# calculate the count of unique items 
unique_items_count = len(pymoli_df["Item ID"].unique())
# calculate the average price of the purchase 
average_price = pymoli_df["Price"].mean()
# caluclate the total number of purchases made 
number_purchases = pymoli_df["Purchase ID"].count()
# calculate the total revenue
total_revenue = pymoli_df["Price"].sum()

```


```python
# create a summary data frame with the above results and do a clean formatting  
Purchasing_Analysis = pd.DataFrame({"Number of unique items":unique_items_count,"Average Price":average_price,
                                    "Number od Purchases":number_purchases,"Total Revenue":total_revenue}, index=[0])
Purchasing_Analysis["Average Price"] = Purchasing_Analysis["Average Price"].map("${:.2f}".format)
Purchasing_Analysis["Total Revenue"] = Purchasing_Analysis["Total Revenue"].map("${:,.2f}".format)
Purchasing_Analysis

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Number of unique items</th>
      <th>Average Price</th>
      <th>Number od Purchases</th>
      <th>Total Revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>183</td>
      <td>$3.05</td>
      <td>780</td>
      <td>$2,379.77</td>
    </tr>
  </tbody>
</table>
</div>




```python
                      # Gender Demographs #
#displayed table again for my reference
pymoli_df.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase ID</th>
      <th>SN</th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Lisim78</td>
      <td>20</td>
      <td>Male</td>
      <td>108</td>
      <td>Extraction, Quickblade Of Trembling Hands</td>
      <td>3.53</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Lisovynya38</td>
      <td>40</td>
      <td>Male</td>
      <td>143</td>
      <td>Frenzied Scimitar</td>
      <td>1.56</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Ithergue48</td>
      <td>24</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>4.88</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Chamassasya86</td>
      <td>24</td>
      <td>Male</td>
      <td>100</td>
      <td>Blindscythe</td>
      <td>3.27</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Iskosia90</td>
      <td>23</td>
      <td>Male</td>
      <td>131</td>
      <td>Fury</td>
      <td>1.44</td>
    </tr>
  </tbody>
</table>
</div>




```python
                             # Gender Demographics #
# Calcualting 
# Count of Male Players
# Count of Female Players
# Count of Other / Non-Disclosed

total_count = pymoli_df["Gender"].value_counts()
total_count

```




    Male                     652
    Female                   113
    Other / Non-Disclosed     15
    Name: Gender, dtype: int64




```python
# Calculating                   
# Percentage of Male Players
# Percentage of Female Players
# Percentage and Count of Other / Non-Disclosed

Percent_of_players = (pymoli_df["Gender"].value_counts()/Total_players)*100
Percent_of_players
```




    Male                     113.194444
    Female                    19.618056
    Other / Non-Disclosed      2.604167
    Name: Gender, dtype: float64




```python
# Gender Demographics summary DataFrame to hold the total count and percentage results 

summary_table = pd.DataFrame({"Percentage of players":Percent_of_players,"Total Count":total_count})
summary_table["Percentage of players"] = summary_table["Percentage of players"] .map("{:.2f}".format)

summary_table
             

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Percentage of players</th>
      <th>Total Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Male</th>
      <td>113.19</td>
      <td>652</td>
    </tr>
    <tr>
      <th>Female</th>
      <td>19.62</td>
      <td>113</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>2.60</td>
      <td>15</td>
    </tr>
  </tbody>
</table>
</div>




```python
                                   # Purchasing Analysis(Gender)
# Do a groupby on gender and calculations to obtain purchase count, avg. purchase price, avg. purchase total per person 
gender_grouped = pymoli_df.groupby("Gender")
purchase_count = gender_grouped["Age"].count()
avg_purchase = gender_grouped["Price"].mean()
total_purchase_value = gender_grouped["Price"].sum()
avg_purchase_person =(gender_grouped["Price"].sum()/gender_grouped["Age"].count())

# create a summary DataFrame to hold the above results 
summary_df = pd.DataFrame({"Purchase count":purchase_count,"Average Purchase Price":avg_purchase,
                           "Total Purchase value":total_purchase_value,"Average Purchase Total per person":avg_purchase_person})
# do a clean formatting 
summary_df["Average Purchase Price"] = summary_df["Average Purchase Price"].map("${:.2f}".format)
summary_df["Total Purchase value"]  = summary_df["Total Purchase value"].map("${:,.2f}".format)
summary_df["Average Purchase Total per person"] = summary_df["Average Purchase Total per person"].map("${:.2f}".format)
summary_df.head()


```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase value</th>
      <th>Average Purchase Total per person</th>
    </tr>
    <tr>
      <th>Gender</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Female</th>
      <td>113</td>
      <td>$3.20</td>
      <td>$361.94</td>
      <td>$3.20</td>
    </tr>
    <tr>
      <th>Male</th>
      <td>652</td>
      <td>$3.02</td>
      <td>$1,967.64</td>
      <td>$3.02</td>
    </tr>
    <tr>
      <th>Other / Non-Disclosed</th>
      <td>15</td>
      <td>$3.35</td>
      <td>$50.19</td>
      <td>$3.35</td>
    </tr>
  </tbody>
</table>
</div>




```python
                                # Age Demographics
# Establish bins for ages and create labels 
age_bins = [0, 9.90, 14.90, 19.90, 24.90, 29.90, 34.90, 39.90, 99999]
group_names = ["<10", "10-14", "15-19", "20-24", "25-29", "30-34", "35-39", "40+"]

# slice the data using pd.cut and  Categorize the existing players based on age_bins  
pymoli_df["Age Group"] = pd.cut(pymoli_df["Age"],age_bins, labels=group_names)
pymoli_df

# do a groupby on Age Group 
pymoli_age_grouped = pymoli_df.groupby("Age Group")
#calculate total count and percenatge of players by age category
total_count = pymoli_age_grouped["SN"].count()
Percent_of_players = (total_count/Total_players)*100
# create a DataFrame to hold the above results 
age_demographics = pd.DataFrame({"Percentage of players":Percent_of_players,"Total count":total_count})
# change the index to none and do clean formatting 
age_demographics.index.name = None
age_demographics["Percentage of players"] = age_demographics["Percentage of players"].map("{:.2f}".format)
age_demographics
# Displaying Age Demographics table #
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Percentage of players</th>
      <th>Total count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;10</th>
      <td>3.99</td>
      <td>23</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>4.86</td>
      <td>28</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>23.61</td>
      <td>136</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>63.37</td>
      <td>365</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>17.53</td>
      <td>101</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>12.67</td>
      <td>73</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>7.12</td>
      <td>41</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>2.26</td>
      <td>13</td>
    </tr>
  </tbody>
</table>
</div>




```python
                       # Purchasing Analysis(Age)

# do calculations to obtain purchase count, avg. purchase price, total purchase value , average purchase per person
purchase_count = pymoli_age_grouped["Age"].count()
avg_purchase = pymoli_age_grouped["Price"].mean()
total_purchase_value = pymoli_age_grouped["Price"].sum()
avg_purchase_person =(pymoli_age_grouped["Price"].sum()/pymoli_age_grouped["Age"].count())

# create a DataFrame to hold the above results 
Purchase_analysis_age = pd.DataFrame({"Purchase count":purchase_count,"Average Purchase Price":avg_purchase,
                           "Total Purchase value":total_purchase_value,"Average Purchase Total per person":avg_purchase_person})
# do a clean formatting 
Purchase_analysis_age["Average Purchase Price"] = Purchase_analysis_age["Average Purchase Price"].map("${:.2f}".format)
Purchase_analysis_age["Total Purchase value"]  = Purchase_analysis_age["Total Purchase value"].map("${:,.2f}".format)
Purchase_analysis_age["Average Purchase Total per person"] = Purchase_analysis_age["Average Purchase Total per person"].map("${:.2f}".format)

Purchase_analysis_age

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase value</th>
      <th>Average Purchase Total per person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&lt;10</th>
      <td>23</td>
      <td>$3.35</td>
      <td>$77.13</td>
      <td>$3.35</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>28</td>
      <td>$2.96</td>
      <td>$82.78</td>
      <td>$2.96</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>136</td>
      <td>$3.04</td>
      <td>$412.89</td>
      <td>$3.04</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>365</td>
      <td>$3.05</td>
      <td>$1,114.06</td>
      <td>$3.05</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>101</td>
      <td>$2.90</td>
      <td>$293.00</td>
      <td>$2.90</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>73</td>
      <td>$2.93</td>
      <td>$214.00</td>
      <td>$2.93</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>41</td>
      <td>$3.60</td>
      <td>$147.67</td>
      <td>$3.60</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>13</td>
      <td>$2.94</td>
      <td>$38.24</td>
      <td>$2.94</td>
    </tr>
  </tbody>
</table>
</div>




```python
                                       # Top Spenders 
# do a groupby on (SN-Screen Name) and assign it to a variable 
pymoli_SN_grouped = pymoli_df.groupby("SN")

# do calculations to obtain purchase count, avg. purchase price, total purchase value 
purchase_count = pymoli_SN_grouped["Age"].count()
avg_purchase = pymoli_SN_grouped["Price"].mean()
total_purchase_value = pymoli_SN_grouped["Price"].sum()

# create a DataFrame to hold the results 
Top_spenders = pd.DataFrame({"Purchase count":purchase_count,"Average Purchase Price":avg_purchase,
                           "Total Purchase value":total_purchase_value})

# Sort the total purchase value column in descending order 
Top_spenders = Top_spenders.sort_values("Total Purchase value", ascending = False)

# do a clean formatting 
Top_spenders["Average Purchase Price"] = Top_spenders["Average Purchase Price"].map("${:.2f}".format)
Top_spenders["Total Purchase value"]  = Top_spenders["Total Purchase value"].map("${:,.2f}".format)

# display the above results(Top Spenders sumamry table )
Top_spenders.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Purchase count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase value</th>
    </tr>
    <tr>
      <th>SN</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Lisosia93</th>
      <td>5</td>
      <td>$3.79</td>
      <td>$18.96</td>
    </tr>
    <tr>
      <th>Idastidru52</th>
      <td>4</td>
      <td>$3.86</td>
      <td>$15.45</td>
    </tr>
    <tr>
      <th>Chamjask73</th>
      <td>3</td>
      <td>$4.61</td>
      <td>$13.83</td>
    </tr>
    <tr>
      <th>Iral74</th>
      <td>4</td>
      <td>$3.40</td>
      <td>$13.62</td>
    </tr>
    <tr>
      <th>Iskadarya95</th>
      <td>3</td>
      <td>$4.37</td>
      <td>$13.10</td>
    </tr>
  </tbody>
</table>
</div>




```python
                                    #Most Popular Items
# Retrieve the Item ID, Item Name, and Item Price columns (using .loc)  
popular_df = pymoli_df.loc[:,["Item ID","Item Name","Price"]]

# Group by Item ID and Item Name. 
popular_grouped = pymoli_df.groupby(["Item ID","Item Name"])

# Perform calculations to obtain purchase count, item price, and total purchase value
purchase_count = popular_grouped["Age"].count()
avg_purchase = popular_grouped["Price"].mean()
total_purchase_value = popular_grouped["Price"].sum()

# create a DataFrame to hold the results 
most_popular_items = pd.DataFrame({"Purchase count":purchase_count,"Average Purchase Price":avg_purchase,
                                   "Total Purchase value":total_purchase_value})

# Sort the purchase count  column in descending order 
most_popular_items = most_popular_items.sort_values("Purchase count", ascending = False)

# do a clean formatting 
most_popular_items["Total Purchase value"]  = most_popular_items["Total Purchase value"].map("${:,.2f}".format)
most_popular_items["Average Purchase Price"] = most_popular_items["Average Purchase Price"].map("${:.2f}".format)


# display the Most Popular Items summary table 
most_popular_items.head()




```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Purchase count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase value</th>
    </tr>
    <tr>
      <th>Item ID</th>
      <th>Item Name</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>178</th>
      <th>Oathbreaker, Last Hope of the Breaking Storm</th>
      <td>12</td>
      <td>$4.23</td>
      <td>$50.76</td>
    </tr>
    <tr>
      <th>145</th>
      <th>Fiery Glass Crusader</th>
      <td>9</td>
      <td>$4.58</td>
      <td>$41.22</td>
    </tr>
    <tr>
      <th>108</th>
      <th>Extraction, Quickblade Of Trembling Hands</th>
      <td>9</td>
      <td>$3.53</td>
      <td>$31.77</td>
    </tr>
    <tr>
      <th>82</th>
      <th>Nirvana</th>
      <td>9</td>
      <td>$4.90</td>
      <td>$44.10</td>
    </tr>
    <tr>
      <th>19</th>
      <th>Pursuit, Cudgel of Necromancy</th>
      <td>8</td>
      <td>$1.02</td>
      <td>$8.16</td>
    </tr>
  </tbody>
</table>
</div>




```python
                                  # Most Profitable Items
# Group by Item ID and Item Name. 
popular_grouped = pymoli_df.groupby(["Item ID","Item Name"])

# Perform calculations to obtain purchase count, item price, and total purchase value
purchase_count = popular_grouped["Age"].count()
avg_purchase = popular_grouped["Price"].mean()
total_purchase_value = popular_grouped["Price"].sum()

# create a DataFrame to hold the results 
most_popular_items = pd.DataFrame({"Purchase count":purchase_count,"Average Purchase Price":avg_purchase,
                                   "Total Purchase value":total_purchase_value})


# Sort the  total purchase value column in descending order 
most_popular_items = most_popular_items.sort_values("Total Purchase value", ascending = False)
most_popular_items["Total Purchase value"]  = most_popular_items["Total Purchase value"].map("${:,.2f}".format)
most_popular_items["Average Purchase Price"] = most_popular_items["Average Purchase Price"].map("${:.2f}".format)

# display the Most Profitable Items summary table 
most_popular_items.head()



```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Purchase count</th>
      <th>Average Purchase Price</th>
      <th>Total Purchase value</th>
    </tr>
    <tr>
      <th>Item ID</th>
      <th>Item Name</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>178</th>
      <th>Oathbreaker, Last Hope of the Breaking Storm</th>
      <td>12</td>
      <td>$4.23</td>
      <td>$50.76</td>
    </tr>
    <tr>
      <th>82</th>
      <th>Nirvana</th>
      <td>9</td>
      <td>$4.90</td>
      <td>$44.10</td>
    </tr>
    <tr>
      <th>145</th>
      <th>Fiery Glass Crusader</th>
      <td>9</td>
      <td>$4.58</td>
      <td>$41.22</td>
    </tr>
    <tr>
      <th>92</th>
      <th>Final Critic</th>
      <td>8</td>
      <td>$4.88</td>
      <td>$39.04</td>
    </tr>
    <tr>
      <th>103</th>
      <th>Singed Scalpel</th>
      <td>8</td>
      <td>$4.35</td>
      <td>$34.80</td>
    </tr>
  </tbody>
</table>
</div>


