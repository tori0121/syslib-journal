#Omeka
I was *super* nervous about this week because this was the first week we didn't have explicit step-by-step instructions. However, this week was truly a lesson in trusting myself, trusting what I have learned through this course, and reviewing my notes alongside the textbook. So while it was definitely nerve-wracking to go at it independently, I felt accomplished and confident moreso than I have at any other point throughout the semester. In the end, I trusted myself and the process and it went great!

##Omeka Installation
Before installing Omeka, I did ensure that my system was up-to-date using the `sudo apt update` command and `sudo apt -y upgrade` and then cleaned everything up. From here, I reviewed the Omeka overview provided in the textbook and then went back through the ILS notes for the processes that I knew would be similar. After that, I got into it:
1. I installed the prerequisites for Omeka using `sudo apt install imagemagick` and `sudo a2enmod rewrite` and then restarted Apache using `sudo systemctl restart apache2`
2. From here, I created a new user and database in MySQL for Omeka
	- I used `sudo su` and then `mysql -u root` before creating a new user and database
	- After that, I used `create user 'omeka'@'localhost' identified by 'XXXXXX';` and then `create database omeka;` 
	- I also granted all privileges using `grant all privileges on omeka.* to 'omeka'@'localhost';` 
	- Once finished, I checked my work by checking the MySQL databases.
3. Once I ensured the user and databse were added, I exited MySQL and went into '/var/www/html' using the `cd` command. Once there, I used `sudo wget https://github.com/omeka/Omeka/releases/download/v3.1.2/omeka-3.1.2.zip`
	- Once Omeka Classic was  downloaded, I extracted the zip file using `sudo unzip omeka-3.1.2.zip`
4. I renamed the extracted directory 'Omeka' using `sudo mv omeka-3.1.2 omeka` and checked to see if this worked using `ls` to see my directories. 
5. I went into the extracted Omeka directory using `cd omeka` and then the `ls` command again to find the 'db.ini' file.
	- After finding the file, I added my database credentials using `sudo nano db.ini` and changing the XXXX values to reflect my databse name, user, and identifier. 
6. After adjusting the file, I used `sudo chown -R www-data:www-data /var/www/html/omeka` and `sudo chown :www-data /var/www/html/omeka` to make sure the user and owner are owned by www-data. 
7. Finally, I restarted Apache2 and MySQL and checked to ensure they were active.

##Setting Up Omeka
After successfully installing Omeka, I went back to my web browser and completed the setup via the web form, which was straight forward. I was then able to go in and adjust appearance settings, create collections, items, and make the site into my own. The first thing I did was make the appearance match my WordPress site. For this, I didn't download a new theme, but edited the colors and display of the Omeka site. I did this by grabbing the hex codes and implementing them in the same fields, such as background, links, text. I also made a special header for my library using Canva and then inserting through the appearance editing options. From here, I started making some items and created two new collections that I could see being important for a community-led library: Aroma Archives for cooking and Loop Library for crochet patterns (this could be expanded to include other yarn crafts, but I didn't go that into it). After getting my items and collections established, I created a couple 'featured' items and then was able to link my Omeka site to my WordPress site by creating a link to my digital library at the top. While I did not have any crazy errors, I really took this lesson slow and really focused on what I was doing and am quite proud of the result!
