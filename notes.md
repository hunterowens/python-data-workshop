#Python For Data Analysis

## Data Structures
There are two important data structures in Pandas. 
### The Series
The series is a 'one dimesional array like object containing an array of data (of any Numpy data type) and an associated array of data labels, called an index.

```
obj = Series([4,5,6,'a string'])

```
This example is only an array of data. 

```
obj2 = Series([4,5,6,'a string'],index=['a','b','c','d'])

```
This example has a labeled index.

A series can be though of as a fixed length order dict. Frequently, you will want to take some dictionary an put it into a series. You can also use a series in many functions that take dicts. 


```
food_trucks = {'La Adelita': 'Mexican', 'King Schnizel':'German','Bridgeport Pasty':'German'}
food_truck_series = Series(food_trucks)
```
### The Dataframe 
The dataframe is a 2-dimesional array- think of it as a spreadsheet. You can use hierachical ordering to achieve multi-dimesional arrays. (We won't be covering that, though)

```
data = {'building':['Ryerson','Ryerson','Pick', 'Harper'],
              'room':[251,276,532,140],
              'capacity':[153,54,15,96]}
df = DataFrame(data)
```

There are many different indexs you can set on data frames. 

## Loading Data
Pandas makes it super easy to load data. There are build in methods such as `read_csv` & `load`(for pickle files). You can also easily load at dict into a data frame, providing an easy way to interact with JSON REST API's on the Web. How easy? This easy

```
url = 'http://divvybikes.com/stations/json'
resp = requests.get(url)

data = json.loads(resp.text)
stations_metadata = data['stationBeanList']
stations_dataFrame = DataFrame(stations_metadata)
```
Or, in one line
```
r = DataFrame(json.loads((requests.get('http://divvybikes.com/stations/json')).text)['stationBeanList'])
```

Not Covered in the This Workshop: Loading Data from Databases. However, there are several built in methods for creating dataframes from SQL and NoSQL Databases.

## Cleaning Data
1. Get Dataset
2. Clean Dataset
3. Repeat. 

Anyways, one of the first things you need to do when you recieve a Dataset is clean it/validate it. 

Pandas provides a set of built in methods for handling missing and erroronous data. Please consult either the documentation for Python for Data Analysis by Wes Mckinney. 


## Sorting Data
One of the first thinks that you might do is sort the data into several different DataFrames. With the Divvy Dataset, we have station id and records at every minute.  

## Merging Data
Database styles joins are possible with Pandas. You can Join 2 Dataframes, and or a DataFrame+Sequences. There are left, right, and inner joins. Here is a key join of two dataframes. 

```
mergeset = pd.merge(september_dataframe,ldata,left_on='station_id',right_on='id')
```

However, you may also want to concatenate data. For those of you familar with Numpy arrays, Pandas includes the .concat method to allow concatination in the same way. 


## Graphing Data
Pandas integrates well with the standard MatPlotLib graphing 

## Mapping Data
Pandas/Matplot can also map data based on a shapefile. 

