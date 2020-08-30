# docker-wp-lemp-ssl

Docker build for creating a local WordPress website running on a LEMP stack with SSL from Lets Encrypt. Includes a PHPMyAdmin container so you have a GUI for the database. The nginx.conf includes a variety of directives to enhance the security of the WordPress website.

### Getting Started
``` docker-compose up -d ```

### Access Site
``` https://localhost ```
(or at the custom URL that you create using the instructions in the comments near the https-portal container :wink:)

### Access PHPMyAdmin
``` http://localhost:8081 ```

### Preset PHPMyAdmin creds
<p><b>User:</b> root</p>
<p><b>Pass:</b> wordpressrootpw</p>

### Edit the nginx.conf file to whitelist your IP and block others
The IP address you are looking to whitelist comes from the <i>https-portal</i> container.

Find the container's ID by running: ``` docker ps ``` to see the list of running containers.

Then run this, replacing CONTAINER_ID with the ID: ``` docker inspect CONTAINER_ID | grep "IPAddress" ```

Uncomment lines 76-79 in nginx.conf and replace XXX.XX.X.X with the container IP address.

Run ``` docker-compose up ``` to commit the changes.
