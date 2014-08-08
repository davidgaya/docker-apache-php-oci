tutum-docker-apache-php + Oracle OCI8 drivers
=============================================

Docker image based on tutum/apache-php with Oracle InstantClient OCI8
driver

License
-------

You must accept the OTN Development and Distribution License Agreement
for Instant Client to download this software.
<http://www.oracle.com/technetwork/licenses/instant-client-lic-152016.html>

Usage
-----

(See `tutum/apache-php` for more information.)

Start your image binding the external ports 80 in all interfaces to your
container:

docker run -d -p 80:80 davidgaya/apache-php-oci

Test your deployment:

curl http://localhost/

Loading your custom PHP application
-----------------------------------

In order to replace the "phpinfo" application that comes bundled
with this docker image,
create a new `Dockerfile` in an empty folder with the following
contents:

FROM davidgaya/apache-php-oci:latest
RUN rm -fr    /app && git clone https://github.com/username/customapp.git /app

replacing `https://github.com/username/customapp.git` with your
application's GIT repository.
After that, build the new `Dockerfile`:

docker build -t username/my-php-app .

And test it:

docker run -d -p 80:80 username/my-php-app

Test your deployment:

curl http://localhost/

That'Thats it!
