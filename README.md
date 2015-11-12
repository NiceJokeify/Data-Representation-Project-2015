# *Data Representation Project 2015*
## Prison Committals and Population


**Name:** Pawel Borzym </br>
**College:** Galway-Mayo Institute of Technology </br>
**Course:** Software Development </br>
**Module:** Data Representation and Querying </br>
**Lecturer:** Dr.Ian Mcloughlin </br>

#Project Overview

As part of my Data Representation and Querying Module I was asked to design an **API** for a Dataset but not to actually implement it. This API's main goal is to let the users access information that will be useful to them. It will be easy to use and also be user-friendly. The Dataset was accessed through [Data.Gov.ie] (https://data.gov.ie/data) and I was then sent to the [Irish Prisons website] (http://www.irishprisons.ie). 

In the first part (GET method) I will be focusing on User side of the application. 
In the second part I will present the POST, DELETE and PUT methods, this part will apply to the Admin side or the developer side. Why would the second part not apply to standard users? Simply because we cannot have anyone just adding/ editing information in the dataset. This DataSet must remain credible source of information.

#The DATASET

The DATASET used is in PDF format, it can be found on the [Irish Prisons Statistics] (http://www.irishprisons.ie/index.php/statistics) web page.</br> 
Data Contains Information about:

  * Prison Commitals
  * Prison Population

Persons committed each year from **2007 to 2014** BY: 
* [Age/Gender] (http://www.irishprisons.ie/images/annualstats/age_gender_2007_2014.pdf) of person commited
* [Address] (http://www.irishprisons.ie/images/annualstats/county_commitals_year_2008_2014.pdf) Given by persons commited by County 
* [Nationality](http://www.irishprisons.ie/images/annualstats/nationality_commitals_year_2008_2014.pdf) of person commited



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


##*GET*
------
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
"Gender": "Male", 
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
[{"id": 3,
"Year": 2014, 
"County": "Galway", 
"type" : "GET",
"url" : "https://irishprisons.ie/commitals/2014/galway"}]
```
-------


#### 3. **Number of persons commited by NATIONALITY 2008-2014**

*Example:* The dataset is divided into TOTAL of 8 columns and 10 rows. Only 2014 will be used for examples. Idea will be same for other years.</br>
* Nationality Group , 2014, 2013, 2012, 2011, 2010, 2009, 2008(TOTAL) </br>
* Nationality Group , Irish, UK, Other European, African, Asian, Australian, South American, North American, Not Recorded, TOTAL </br>

**Nationality Group:** Represents data by county</br>
**2014...:** Represents total of commited by county in this year.</br>

**Nationality 2014 Commitals:** </br>
![image](http://oi63.tinypic.com/2rdhgnp.jpg)

**URL** that would display *TOTAL* number of NATIONALITY commitals for year **2014**:</br>
**URL:** https://irishprisons.ie/commitals/nationality/total*

Example URL for displaying needed information:</br>
**URL**: *https://irishprisons.ie/commitals/(YEAR)/(NATIONALITY)* Replace (nationality) with seeked nationality + Replace (Year) with seeked value to display data for that given year.

**Method** used : *GET* (used for this information retrieval)

**URL** that would display specific information:</br>
**URL**: *https://irishprisons.ie/commitals/2014/African* Returns number of commitals for the year 2014 from Galway

Data will be retured in **JSON**  format. It is a lightweight data-interchange format. It is easy for humans to read and write.

*id:* Identification number of the table **(4 = Nationality table)**</br>
*year:* Year of the Data</br>
*nationality:* Nationality of commited</br>
*type:* Type of Request Sent</br>
*url:* URL of the Request</br>

*JSON* data that will be returned, example. </br>
```json
[{"id": 4,
"Year": 2014, 
"Nationality": "African", 
"type" : "GET",
"url" : "https://irishprisons.ie/commitals/2014/african"}]
```

##*POST*
------
#### 1. **ADDING persons commited to prison by AGE and GENDER 2007-2014**
If for example, new year starts or administrators will want to include data from previous years (<2007) that can be done using the **POST** method. </br>

I will show below an example of **URL** that could be responsible for this.

**NOTE:** URL's with ID are only available to system administrators or people that have previously logged in to their accounts providing that their accounts are with special rights. 
Ordinary User will not be able to do anything without obtaining privilege option.

**URL:** ```http://irishprisons.ie/commitals/2/addyear```  *2 = ID of the table, this will direct the admin to this specific table*

First **request will be sent** to add a year column to the table.
```
POST /addyear/newyear_table HTTP/1.1
User-Agent: Chrome/47.0.2526.58 (compatible; Windows; Mac; Linux; MSIE5.01; Windows NT)
Host: www.irishprisons.ie
Content-Type: text/html; charset=utf-8
Accept-Language: en-us
year="2014"&Male=" "&Female=" "&Total=" "
Connection: Keep-Alive
```

After we would **receive** this kind of response: 

```
HTTP/1.1 200 OK
Date: 17:16:00 11 November 9 2015
Server: Apache/2.2.14 (Win32)
Last-Modified: 13:56:53 Wednesday November 11 2015 GMT
ETag: "63fh8765-p-3652fe00"
Content-Type: text/html
Connection: Closed

<html>
<body>
<h1>Column added successfully</h1>
</body>
</html>
```


**Note: the task will be similar for adding information to the other tables as well, writing them up makes me feel like I'm mostly wasting readers time and just making the project longer and more complicated in genera. I want to keep things clear and easy to follow, Thank You**




##*PUT*
------
#### 2. **UPDATING data about persons commited to prison by NATIONALITY 2007-2014**
Let's say now the developer wants to send some info about updating the table at the root of the server, hw can do this through the PUT method. Best idea is to use PUT when you can update a resource completely through a specific resource. You would do this only if you know the specific location of this. Below I will show example of specific item in the URL...</br>
```http://irishprisons.ie/commitals/3/updateyear``` *3 = ID of the NATIONALITY dataset.* 


I will show below an example of **URL** that could be responsible for this.

**URL:** ```http://irishprisons.ie/commitals/3/updateyear```  *3 = ID of the table, this will direct the admin to this specific table*

First **request will be sent** to update a year column to the table.
```
PUT /year.htm HTTP/1.1
User-Agent:Chrome/47.0.2526.58 (compatible; Windows; Mac; Linux; MSIE5.01; Windows NT)
Host: www.irishprisons.ie
Accept-Language: en-us
updateyear="2014"&Nationality Group=" "&Irish=" "&UK=" "&Other European=" "&African=" "&Asian=" "&Australian=" "&South American=" "&North American=" "&Not Recorded=" "&TOTAL=" "
Connection: Keep-Alive
Content-type: text/html

```

After we would **receive** this kind of response: 

```
HTTP/1.1 201 Created
Date: Thursday, 12 November 2015 02:31:00 GMT
Server: Apache/2.2.14 (Win32)
Content-type: text/html
Content-length: 30
Connection: Closed


<html>
<body>
<h1>The file was updated.</h1>
</body>
</html>

```


**Note: the task will be similar for updating information to the other tables and years in the tables as well. I want to keep things clear and easy to follow. Project will be updated in the future as we go along.**


##*DELETE*
------

#### 3. **DELETING data about persons commited to prison by NATIONALITY 2007-2014 from the DATASET**

Information can be added, information can be updated/modified then we also need the possibility of deleting information from the DATASET for a number of resons. Instead of constantly modifying the dataset and there is always a possibility to make stuff messy, it could be easier and more efficient to make new table. Whatever is it thar administrator prefers. Possibility of deleting must be there. For that we will use the **DELETE**  method. 

Let's remind ourselves what **DELETE** method does.

>**DELETE** method is used for deleting certain information from the dataset</br>

Below is an example of a URL to delete the whole table from the dataset.</br>

**URL:** ```http://irishprisons.ie/removetable/(id)``` *Substituting (id) with table ID will result in deletion of the whole table from the dataset* </br>

Example to delete year from the dataset would be this.</br>
**URL:** *```http://irishprisons.ie/removetable/(id)/(year)```*  *Substituting (id) and (year) with specific information will result in deletion of the specified column YEAR*</br>

Example of actual URL that would be user to remove table column year 2014 from table of ID 3.</br>
**URL** *```http://irishprisons.ie/removetable/3/2014```*

*Request* example in http: (for deleting year in the nationality table)

DELETE /removetable/3/2014 HTTP/1.1
User-Agent: Chrome/47.0.2526.58 (compatible; Windows; Mac; Linux; MSIE5.01; Windows NT)
Host: localhost
Content-Type: text/html; charset=utf-8
Accept-Language: en-us
Connection: keep-alive
A responce example in http:

HTTP/1.1 200 OK
Date: 17:55:00 Thursday November 12 2015
Server: Apache Server
Connection: Closed
Content-Type: text/html
uri: "http://irishprisons.ie/removetable/3/2014"

<html>
<body>
<h1>Year column deleted.</h1>
</body>
</html>


