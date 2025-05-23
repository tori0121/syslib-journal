# WordPress & Making a Website!

This week was incredibly fun and getting to make a website like this really highlighted the time and effort it takes to make a good-looking and user-friendly webpage that is informational -- which are key for libraries. I didn't encounter significant errors, but I will go over the process below and what I noticed. 

## Libraries & WordPress Overview
Libraries use WordPress in a variety of ways to enhance their digital presence and connect with their communities. Many libraries build their official websites on WordPress because it's flexible, cost-effective, and easy to update without requiring advanced technical skills. They use it to share news, promote events, provide access to digital resources, host blogs or reading recommendations, and manage online catalogs through integration with library systems. WordPress also supports plugins that allow libraries to offer features like contact forms, event calendars, booking systems, and accessibility tools, making it a powerful platform for both public-facing content and internal communication. While wordPress has many benefits, it is also prone to attack because it is so widely used. Because of this, Wordpress has a dedicated security team that constantly works to identify and resolve security issues. 

## Installing WordPress
We did not use the `apt` command this week to install WordPress because it can actually complicate the process. Rather, we downloaded and extracted WordPress and then create the database and user, similarly to when we created our OPAC. This allows us to better protect our server's security. 
1. First, we ensure the system is up-to-date using `php --version` and `mysql --version`
	+ The WordPress installation requires PHP version 7.4 and up, and MySQL version 8.0 and up. 
	+ We can easily check our system meets the requirements using `cat /etc/issue.net`
2. We install additional PHP modules so WordPress can fully operate using `sudo apt install php-curl php-xml php-imagick php-mbstring php-zip php-intl`
	+ We have to restart Apache and MySQL afterwards
3. We go into the /var/www/html directory and use `sudo wget https://wordpress.org/latest.zip` to download the latest version of WordPress and unzip using `sudo unzip latest.zip`
	+ To get the link for this, we go to WordPress' websdite and hover over the download and copy the link that way. 
	+ To install the unzip utility, we use `sudo apt install unzip`
4. We then create a database and user from the root Linux user and then log in as the MySQL root user. Again, this protects our server. 
	+ In MySQL root, `create user 'wordpress'@'localhost' identified by 'password here';`
	+ Then, we create a wordpress database and grant all privileges. 
5. Similarly to our ILS, we then have to edit the configuration files. In our wordpress directory (`cd /var/www/html/wordpress`) we copy and rename the wp-config-sample.php file to wp-config.php and edit the database name, user name, and password. We then add `define('FS_METHOD','direct');` to the end of our wp-config.php file.
6. After that, we change file ownership so that WordPress will write files in the base directory using `sudo chown -R www-data:www-data /var/www/html/wordpress`
7. Finally, we go to our browser and, using the VM external link, finalize the installation process for WordPress. 

## Making a Website
When making the website, I wasn't sure what kind of library I was going to make or how to even begin the editing process. I ultimately thought about words associated with books and landed on Fable, which instilled a cozy, community-led vibe — and so here we are! After deciding on a name, I went into the template options for appearance and found a cozy bookish theme that matched my idea for this library. Playing around with the settings was super fun, and I changed the color scheme to be simple but warm. 

From here, I added some useful plug-ins such as a form maker and an event calendar. Both of these helped me bring my library to life. However, I did struggle with getting my event calendar to include the banner for my homepage, and am still a bit stuck there, but it's a process. I also struggled a bit to connect the events calendar to my libray site, but was able to go over some of the videos and instructions provided by the plug-in creator, which was helpful. I also included a vision, mission, and values statement and filled up my events calendar with book clubs, community nights, and storytimes. I have some popular books listed on the homepage, but for an actual libary, would like to include information about new arrivals or trending reads. WordPress is super flexible and easy to make into your own. For libraries, having a free resource like this can really connect you to a larger group of people and can make managing events or updates easy. It also integrates well with catalog systems and digital resources! 
