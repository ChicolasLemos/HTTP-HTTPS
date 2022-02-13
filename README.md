# HTTP-HTTPS

HTTP-HTTPS (Apache2)
```
apt install apache2
a2enmod ssl
a2ensite default-ssl.conf
systemctl restart apache2
nano /etc/apache2/sites-available/default-ssl.conf
 - change the html to htmls
 - change the crt and key
cd /var/www/
cp -r html/ htmls
cd html (this one is the insecure/80)
nano index.html (this index is the site, you can create your site from here. but remember this is the insecure)
cd htmls (this is the secure/443)
nano index.html (if you want to do your own site. this is the secure)
systemctl restart apache2
```
HTTP-HTTPS (Ngnix)
```
apt install nginx
apt install ssl-cert
cd /etc/nginx/snippets/
cp snakeoil.conf yourdomain.conf
nano yourdomain.conf
 - change the crt and key
cd ../sites-available/
cp default secure (this name is for the secure page, but you call it whatever you want)
nano secure
 - delete the first lines with the :80
 - uncomment the lines with the :443
 - uncomment the snippets/snakeoil.conf;
 - change the snakeoil.conf to yourdomain.conf
 - change root to htmls
cd /var/www
cp -r html/ htmls
cd html/
nano index (this index is the site, you can create your site from here. but remember this is the insecure)
cd htmls/
nano index (if you want to do your own site. this is the secure)
cd /etc/nginx/sites-enable
ln -s /etc/nginx/sites-available/secure secure
systemctl restart nginx
systemctl status nginx (to see if is working)
```
