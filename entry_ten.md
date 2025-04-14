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
Using WordPress is fun and exciting, although some parts took some getting used to. Navigating WordPress is fairly straight forward
