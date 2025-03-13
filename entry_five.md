This week, we are learning about LAMP servers and, specifically, we are installing Apache. 
# What is a LAMP Server?
It stands for Linux, Apache, MySQL, and PHP, which are the four key components that make up this server setup. I want to break this down further so that I can keep track of how these parts interconnect. 

1. Linux -> Open source OS that serves as the foundation of the server.
2. Apache -> A very popular web server that supports a wide range of configurations. It also has a strong community support. It is responsible for handling HTTP requests and serving web pages to users. When I type a website address into my browser, Apache handles the request, processes it, and sends back the web page.
3. MySQL -> Allows you to query data using SQL (Structured Query Language), which makes it easy to manage large amounts of structured data.
4. PHP -> Server-side scripting language used to make web pages. It interacts with MySQL to store/retrieve data. 

# Installing & Setting Up Apache:
I installed Apache using w3m. To do this, I installed w3m using the sudo apt install command, which gave me no issues. Before installing apache, I did have to reset my VM because I was getting a 'lock' error that I could not bypass. While I did find some online forums that broke down how to get past this, I was still struggling and so re-established my VM following along with the notes from https://cseanburns.github.io/systems-librarianship/2a-using-gcloud-virtual-machines.html 

It does throw me off a bit that the link to my website is through the VM external link, which I'm posting here as well: http://34.56.87.225/
I think I was expecting it to pop up in the terminal alongside my other files for some reason? Regardless, installing Apache was straightforward and using the html was fun!

# HTML Notes
HTML acts as the skeleton of a webpage, specifying where text, images, links, and other media should be placed on a page. I'm still getting used to links and media specificially with HTML, but the rest is easy to emulate and practice. 
I like how customizable HTML is and can see it being a useful tool for curating an online catalog or other digital  organizational model. 

# How LAMP works:
1. Apache receives the request from the client (browser).
2. Then, Apache checks if the request corresponds to a static file (like an image or a simple HTML file). If it's a static file, it serves it directly.
3. If the request is for a dynamic page (such as a PHP file), Apache passes the request to PHP.
4. PHP processes the request using MySQL. 
5. After processing, PHP sends the final HTML output back to Apache.
6. Apache then sends the HTML content to the client’s browser, where it is displayed to the user.

