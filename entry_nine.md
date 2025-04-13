# DIY Integrated Library Systems
---
## What is an ILS?
An Integrated Library System or ILS is software used by libraries to manage the day-to-day operations, such as:
+ Cataloging
+ Circulation
+ Acquisitions
+ Patron Managment
This system allows libraries to easily manage their collections through OPACs, ensuring that library users can also search for information and find the resources they need. 
OPACs and cataloging modules are "cornerstone" modules in all ILS. 

## Relational Databases & How They Work
For this course, we used MySQL -- a relational database -- to understand how to store and manipulate data. A relational database stores data in tables, which are related to one another through keys and strings. In the case of a bibliographic table, it would look something like:
+ Books 
	+ Field examples: 'book_id', 'title', 'language'
+ Authors
	+ Field examples: 'author_id', 'first name', 'last name'
+ Publishers
	+ Field examples: 'publisher_id', 'name', 'location'
+ Subjects/Genres
	+ Field examples: 'subject_id', 'classification'

These relationships model bibliographic metadata, allowing allowing this information to be stored, updated, and organized in a structured way. 

In order for our database tables to interact with an OPAC, we have to create an HTML page that allows users to enter queries. 
For our class, we utilized the following to create a search page:
> HTML page (mylibrary.html) -> search button on that form activates search.php -> that establishes a connection to the OPAC we created. 
> The PHP script contains a MySQL query that allows us to search the books table or bibliographic record. 

## Step-by-Step Set Up
Before we can begin creating an ILS, we have to set up and configure our LAMP server. We touched on this a couple weeks ago (refer to [entry eight](https://github.com/tori0121/syslib-journal/blob/main/entry_eight.md) on my GitHub), but this involved creating an 'opacdb' database that contained a 'books' table, which included many of the elements I listed aboved. While we only work with one table for our OPAC, the reality is that an ILS relies on several tables to efficiently store, manage, and retrieve information. 
As already touched on, we begin with an HTML page
1. We create an HTML page that enables queries (mylibrary.html). This includes a submit or search button.
2. The submit button activates a PHP script (search.php).
3. Search.php connects to the OPAC database we created (remember the books table in MySQL under the 'opacdb'). 
4. From here, it goes through the information stored in our database to return results matching our query. 
5. After we configure our OPAC, we added more information to it. 
To add more records to our books table, we use MySQL and begin with 'mysql -u opacuser -p' and then use the 'insert' command to add new data for our table. An example would be:
> To add books to our database, we use the following format: (author, title, publisher, copyright). 
>> An example: 
>>insert into books
>>('Kaner, Hannah', 'Godkiller', 'Harper Voyager', '2023')
