# *Data Representation Project 2015*
## Prison Committals and Population


**Name:** Pawel Borzym </br>
**College:** Galway-Mayo Institute of Technology </br>
**Course:** Software Development </br>
**Module:** Data Representation and Querying </br>
**Lecturer:** Dr.Ian Mcloughlin </br>

#Project Overview

As part of my Data Representation and Querying Module I was asked to design an **API** for a Dataset but not to actually implement it. This API's main goal is to let the users access information that will be useful to them. It will be easy to use and also be user-friendly. The Dataset was accessed through [Data.Gov.ie] (https://data.gov.ie/data) and I was then sent to the [Irish Prisons website] (http://www.irishprisons.ie).

#The DATASET

The DATASET used is in PDF format, it can be found on the [Irish Prisons Statistics] (http://www.irishprisons.ie/index.php/statistics) web page.</br> 
Data Contains Information about:

  * Prison Commitals
  * Prison Population

Persons committed each year from **2007 to 2014** BY: 
* [Age/Gender] (http://www.irishprisons.ie/images/annualstats/age_gender_2007_2014.pdf) of person commited
* [Address] (http://www.irishprisons.ie/images/annualstats/county_commitals_year_2008_2014.pdf) Given by persons commited by County 
* [Nationality](http://www.irishprisons.ie/images/annualstats/nationality_commitals_year_2008_2014.pdf) of person commited
* [Offence Groups] (http://www.irishprisons.ie/images/annualstats/committal_offence_group_2007_2014.pdf) of sentence commitals by YEAR 
* [Sentence Length] (http://www.irishprisons.ie/images/annualstats/committal_sentence_length_2007_2014.pdf) of commitals by Year.


##METHODS

*Method* | *Account*
---------|----------
GET| Requests data from a specified resource
POST| Submits data to be processed to a specified resource
DELETE| Removes all current representations of the target resource given by a URI
PUT| Creates/ Replaces all current representations of the target resource with the uploaded content.


####**Quick Overview of the Methods named**
#####**GET**
*  Can be bookmarked/cached.
*  Parameters remain in browser history. 
*  Data is visible to everyone in the URL.
*  GET -less secure compared to POST because data sent is part of the URL. 
*  Never send sensitive info such as password.

#####**PUT**
*  Canot be bookmarked and is NOT cached.
*  Parameters are NOT saved in browser history. 
*  Data is NOT displayed in the URL.
*  No data length restriction.
*  POST is a safer than GET because the parameters are not stored in browser history or in web server logs.
*  Never send sensitive info such as password.


##GENERAL - *URL (Uniform Resource Locator*)
* Below we have an example of a URL that user will use to access the main page of the page.</br>
 ```http://www.irishprisons.ie/``` </br>

#### 1. **Number of persons commited to prison by AGE and GENDER 2007-2014**

*Example:* The dataset is divided into TOTAL of 5 columns. Only 2014 will be used for examples. Idea will be same for other years.</br>
* AGE, Female, Male, Total, % </br>

**Age:** Represents data age by intervals. ex. **<17 years old**</br>
**Female:** Represents number of females commited by age.</br>
**Male:**  Represents number of males commited by age.</br>
**Total:**  Represents total number commited by age.</br>
**%:** Represents percentage of commited by age.</br>

**Age/Gender 2014 Commitals:** </br>
![image](http://oi65.tinypic.com/or2eww.jpg)

**URL** that would display *TOTAL* number of commitals for year **2014**:</br>
**URL:** https://irishprisons.ie/commitals/2014*

Example URL for displaying needed information:</br>
**URL**: *https://irishprisons.ie/commitals/agegender/(YEAR)/(GENDER)/(AGE)*  Replace (Year) with seeked value to display data for that given year.

**Method** used : *GET* (used for this information retrieval)

**URL** that would display specific information:</br>
**URL**: *https://irishprisons.ie/commitals/2014/male/18-21* Returns number of commitals for the year 2014 ordered by age 18-21 and gender male.

Data will be retured in **JSON**  format. It is a lightweight data-interchange format. It is easy for humans to read and write.

*id:* Identification number of the table **(2 = Age/Gender table)**</br>
*year:* Year of the Data</br>
*age:* Age of the commited</br>
*gender:* Gender of the commited</br>
*type:* Type of Request Sent</br>
*url:* URL of the Request</br>

*JSON* data that will be returned, example. </br>
```json
[{"id": 2,
"Year": 2014, 
"Age": 18-21, 
"Gender": Male, 
"type" : "GET",
"url" : "https://irishprisons.ie/commitals/2014/male/18-21"}]
```
-------


#### 2. **Number of Place of Origin given by persons commited 2008-2014**

*Example:* The dataset is divided into TOTAL of 8 columns. Only 2014 will be used for examples. Idea will be same for other years.</br>
* County, 2014, 2013, 2012, 2011, 2010, 2009, 2008(TOTAL) </br>

**County:** Represents data by county</br>
**2014...:** Represents total of commited by county in this year.</br>

**County 2014 Commitals:** </br>
![image](http://oi66.tinypic.com/35ludmd.jpg)

**URL** that would display *TOTAL* number of commitals for year **2014**:</br>
**URL:** https://irishprisons.ie/commitals/2014*

Example URL for displaying needed information:</br>
**URL**: *https://irishprisons.ie/commitals/(YEAR)/(COUNTY)* Replace (county) with seeked county name + Replace (Year) with seeked value to display data for that given year.

**Method** used : *GET* (used for this information retrieval)

**URL** that would display specific information:</br>
**URL**: *https://irishprisons.ie/commitals/2014/galway* Returns number of commitals for the year 2014 from Galway

Data will be retured in **JSON**  format. It is a lightweight data-interchange format. It is easy for humans to read and write.

*id:* Identification number of the table **(3 = COUNTY table)**</br>
*year:* Year of the Data</br>
*county:* Place of Origin of commited</br>
*type:* Type of Request Sent</br>
*url:* URL of the Request</br>

*JSON* data that will be returned, example. </br>
```json
[{"id": 2,
"Year": 2014, 
"County": Galway, 
"type" : "GET",
"url" : "https://irishprisons.ie/commitals/2014/galway"}]
```
