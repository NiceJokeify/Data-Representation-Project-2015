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
* Below is an example of a URL that user will use to access the main page of the page.</br>
 ```http://irishprisons.ie/``` </br>





