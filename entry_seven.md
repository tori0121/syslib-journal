This week, I worked on bringing my LAMP server together! 

#MySQL: What is it and how it works
MySQL is a relational database management system that helps us store and manage data in a structured way. It organizes data into tables, which are like spreadsheets where rows are individual records, and columns are the attributes of those records.

When using MySQL, we have to make a personal account. Like Linux, the root user is the ‘god’ user and we don’t want to work a lot in the root for this to protect from vulnerabilities. However, we do still want to have control over what we are doing, so we are giving ourselves full access to the functions of our specific user within MySQL using “grant all privileges on opacdb.* to 'opacuser'@'localhost' with grant option;” where “*” equals all tables. Limiting these functions would limit how other users interact with our website. 

#Two ideas to think about:
1. Database: Think of a database as a folder that holds all our data.
2. Tables: Inside that folder, data is organized into tables. A table is like a grid, with rows and columns. Each row represents an individual record, and each column represents a specific piece of information about that record.
Ex: In class, we practiced this by breaking down information about library materials (books). We created columbs for author, title, and copyright values and were able to retrieve the information for those records using MySQL commands. These commands ends with a <b>;</b> which I am still getting used to.

I was able to follow the commands and it was gratifying to see the table change as we manipualted it. Updating the table to reflect the values and make it easier to see them using the "update books" commands with the required values shows how this can really streamline the process of reviewing data and information. 

The most confusing part is connecting MySQL to PHP. Mostly because I didn't get any errors, but I do not see see the data from the opacdb database and books table rendered in on my webpage. I will keep trying and will log any errors I found/any tips here. 
