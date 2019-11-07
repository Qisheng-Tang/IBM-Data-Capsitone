# Support restaurant decision in North York, Toronto
## Introduction
There is a person who wants to open a restaurant in North York, Toronto. University of Missouri- Columbia locates here. This project tries to give an analysis of where it suits for a restaurant to open in North York. Helping people make a decison about whether a place suits for restaurant.

if a restaurant builds nearing the commercial area. It would be more possible to success in competing with other restaurant. Building restaurant together is a good choice for people to start up a restaurant.


## Data Prepare

For this project, we need prepare several data.

* geo-location information: Gaining specific borough and the neighborhoods in that borough. We specifically and technically mean the latitude and longitude numbers of that borough. Assuming that it is "North York" in Toronto. Data for borough in Toronto with post code has been provided in https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M

* For each postal code geo location, we can find it is in this .csv file https://cocl.us/Geospatial_data.

* Using Foursqaure API to gain venues in each neighborhoods in North York. To view more information with Foursqaure API, view this website https://developer.foursquare.com/docs/api

* We will need data about different venues in different neighbourhoods of that specific borough. In order to gain that, we will use 'Foursqaure' locational information. by location information for each venue we mean basic and advanced information about the venue. For this project, we need something which is advanced information such as category of that venue and whether this venue is popular.

##Step to achieve

### Data Wrangling and Group

We will use Postal Code of different regions in North York to find the list of postal code and information about neighborhoods in North York. Then process the table group with geo location of each neighbourhood into dataframes.
![Import Data](https://github.com/Qisheng-Tang/IBM-Data-Capsitone/blob/master/Import%20Data.png)


### Connecting to Foursqaure and Retrieving Location data

After finding the list of neighbourhoods, then we can connect to Foursqaure API to gather information about each venue and every neighbourhood. For each neighbourhoods, We can choose radius to 2000 meters far from the center of the neighbourhoods. 2000 meters can help us collect enough information about venues.

In this step, we will need define a function to retrive data and normalize the data.
![](https://github.com/Qisheng-Tang/IBM-Data-Capsitone/blob/master/截屏2019-11-07下午4.38.51.png)

### Processing Retrived Data and Creating Dataframe for All the Venues inside North York

When the data is completely collected, we will try to collect some deep level information on that raw data to find our desirable. The feature we will use is the category of venues. We will use one-hot encoded so that different kind of venues will have different feature columns. Add two columns, one is 'Total Restaurant' which calculates total restaurant in a neighbourhood. Another is 'Food Supply' column. We assumed that can reflects the cost of food supply for a Restaurant (The higher 'Food Supply', the cheaper for a restaurant gets food)

Achieving this uses code below

![](https://github.com/Qisheng-Tang/IBM-Data-Capsitone/blob/master/截屏2019-11-07下午4.43.54.png)

### Applying K-MEANS Algorithm

Then we cluster neighborhoods through K-MEANS Algorithm. We can try to make 5 clusters as I think it is enough. Then we will add a column about cluster results.

First, we need select some feature which are relevant about restaurant and food Supply

![](https://github.com/Qisheng-Tang/IBM-Data-Capsitone/blob/master/Select%20Feature%20.png)


Then implementing K-MEANS algorthim

![](https://github.com/Qisheng-Tang/IBM-Data-Capsitone/blob/master/截屏2019-11-07下午4.46.57.png)
### Decision Making and Results

Then we can focus on the center of clusters and compare them for their 'Total Restaurant' and 'Food Supply'. The highest center reflects the neighbourhood which is most suiable for openning a restaurant.

First, we calculate which cluster contains highest score, Then we find which neighbourhood is best

The result is ![](https://github.com/Qisheng-Tang/IBM-Data-Capsitone/blob/master/Recomment%20the%20best.png)
