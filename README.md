# Docker image of Wordpress (Tag php7.1) with LDAP support
This images stays up to date with the original one but with LDAP support. Enjoy.

Just added this code snippet as suggested by https://github.com/tianon, Wordpress official image mantainer with modification for tag php7.1

````
FROM wordpress:php7.1

RUN set -x \
	&& apt-get update \
	&& apt-get install -y libldap2-dev \
	&& rm -rf /var/lib/apt/lists/* \
	&& docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu/ \
	&& docker-php-ext-install ldap \
	&& apt-get purge -y --auto-remove libldap2-dev
  ````
  
  To build the image just run:
  
  ````
  docker build -t [username]/[imagename] .
  ````

  # Thanx to dalareo for his inspiration.
  