# bitbucket-pipelines-phpunit-mysql

[Bitbucket Pipelines](https://bitbucket.org/product/features/pipelines) [Docker](https://www.docker.com/) image based on [Debian _Jessie_](https://www.debian.org/releases/jessie/) with [PHP](http://php.net/)/[MySQL](https://www.mysql.com)/[PHPUnit](https://phpunit.de/) (and more !)


# bitbucket-pipelines-phpunit-mysql
Bitbucket Pipelines image based on Debian/Jessie with PHPUnit/MySQL/Sencha CMD/Node/Composer/...

Docker image at [hendrikprinsza/bitbucket-pipelines-phpunit-mysql](https://hub.docker.com/r/hendrikprinsza/bitbucket-pipelines-phpunit-mysql/) (no `CMD` as it is overriden by *Pipelines*)

```CMD
docker run -it --volume=/Applications/MAMP/htdocs/project:/project --workdir="/project" --memory=4g --memory-swap=4g --entrypoint=/bin/bash hendrikprinsza/bitbucket-pipelines-phpunit-mysql
```

# Packages installed
 - `php5-apcu`, `php5-cli`, `php5-curl`, `php5-gd`, `php5-geoip`, `php-gettext`, `php5-imagick`, `php5-intl`, `php5-json`, `php5-mcrypt`, `php5-memcached`, `php5-mysqlnd`, `php5-sqlite`, `php5-xdebug`, `php5-xhprof`, `php5-xmlrpc`, `memcached`, `imagemagick`, `openssh-client`, `curl`, `gettext`, `zip`, `bzip2`, `git`, `subversion`
 - [Perl](https://www.perl.org/) 5.20
 - [Python](https://www.python.org/) 2.7 & 3.4
 - [MySQL](https://www.mysql.com/) 5.5 (user `root:root`)
 - [PHP](http://www.php.net/) 5.6
 - [Ruby](https://www.ruby-lang.org/) 2.1
 - [Node.js](https://nodejs.org/) 4.x LTS
 - [PHPUnit](https://phpunit.de/) 5.7
 - Latest [Composer](https://getcomposer.org/), [Gulp](http://gulpjs.com/), [Webpack](https://webpack.github.io/), [Mocha](https://mochajs.org/), [Grunt](http://gruntjs.com/), [Codeception](https://codeception.com/), [Yarn](https://yarnpkg.com/)

 # Sample `bitbucket-pipelines.yml`
 ```YAML
 image: hendrikprinsza/bitbucket-pipelines-phpunit-mysql
 pipelines:
   default:
     - step:
         script:
           - service mysql start
           - mysql -h localhost --user=root --password=root -e "CREATE DATABASE test;"
           - composer config -g github-oauth.github.com XXXXXXXX
           - composer install --no-interaction --no-progress --prefer-dist
           - npm install --no-spin
           - gulp
 ```
