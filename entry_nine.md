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

