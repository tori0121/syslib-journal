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
	+ Field examples: `book_id`, `title`, `language`
+ Authors
	+ Field examples: `author_id`, `first name`, `last name`
+ Publishers
	+ Field examples: `publisher_id`, `name`, `location`
+ Subjects/Genres
	+ Field examples: `subject_id`, `classification`

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
3. Search.php connects to the OPAC database we created (remember the books table in MySQL under the `opacdb`). 
4. From here, it goes through the information stored in our database to return results matching our query. 
5. After we configure our OPAC, we added more information to it. 
To add more records to our books table, we use MySQL and begin with `mysql -u opacuser -p` and then use the `insert` command to add new data for our table. An example would be:
> To add books to our database, we use the following format: (author, title, publisher, copyright). 
>> An example: 
>>`insert into books`
>>`('Kaner, Hannah', 'Godkiller', 'Harper Voyager', '2023')`

To translate this data to our cataloging module, we once again begin with HTML. 
1. We create a HTML page to mimic the structure of our books table that contains a form for inserting our data (index.html).
	+ This involves creating a new directory using `cd /var/www/html` and `sudo mkdir cataloging`
	+ Then, we create and add content to the file using `cd cataloging` and `sudo nano index.html` where we then insert the relevant code.
2. Because the index.html page is only a form, we have to insert script that allows us to communicate and add data. Note: All scripts should match forms! (i.e. only including author, title, publisher, and copyright info).
	+ This requires creating a PHP script (insert.php) that contains the relevant code to add the data from the MySQL database and subsequent books table.
3. From here, we establish security settings. 
	+ First we create our authentication file in Apache2 where our config files are stored. This will establsh a username and password.
	+ In our /etc/apache2 directory: `sudo htpasswd -c /etc/apache2/.htpasswd libcat`
	+ We then configure this file using nano (or any other text editor) and edit the `AllowOverride None` to `AllowOverride All`
	+ From here, we create a file called .htaccess in `cd /var/www/html/cataloging` and configure it so it enables authorization. We then check the configuration using `apachectl configtest` and resetting the system.
4. Ownership settings are the last we do, and we begin by finding the Apache2 web server user on our Linux VM. 
	+ We use `grep "www-data" /etc/passwd` to find the account details, which is `nologin` and prevents the account from logging into a shell.
	+ We can update these settings and change ownership of /var/www/html/ to www-data using `sudo chown :www-data /var/www/html`
	+ To ensure that any new files or directories created within /var/www/html inherit group ownership, we use `sudo chmod -R g+s /var/www/html`
5. Finally, we can catalog -- just remember your username and password!

## Some Final Remarks
This module really highlighted how the OPAC is the user-facing tool for discovering and accessing library materials whereas the relational databases are the backend storage structures that power the OPAC's functionality. 
While I didn't run into any significant errors, some things I noticed and looked further into were:
+ I had duplicate books, so I deleted them using `delete from books where id='7';` which caused my OPAC to generate a list of materials that is no longer sequential! I am not sure how to adjust this, but when looking into it, it seemed that it would be quite a pain to adjust so I left it as is. 
+ I looked up what `bind` meant in the php insert script and found that is binds the parameters as strings, which are the explicit outputs we need in our OPAC. I also enjoyed looking into the error messages and how those work within the script.
