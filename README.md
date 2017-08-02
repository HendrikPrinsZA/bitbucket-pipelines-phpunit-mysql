[Bitbucket Pipelines](https://bitbucket.org/product/features/pipelines) [Docker](https://www.docker.com/) image based on [Debian _Jessie_](https://www.debian.org/releases/jessie/).

*Please note that it does not include the **mysql server**, as you should be using pipeline's mysql service. However, it does include the **mysql client**.*

----------

## Packages installed
 - [Node.js](https://nodejs.org/) `4.x LTS`
 - [Perl](https://www.perl.org/) `5.20`
 - [PHP](http://www.php.net/) `5.6`
 - [PHPUnit](https://phpunit.de/) `5.7`
 - [Python](https://www.python.org/) `2.7`
 - [Ruby](https://www.ruby-lang.org/) `2.1`
 - [Sencha CMD](http://docs.sencha.com/cmd/) `6.5`
 - [Composer](https://getcomposer.org/), [Gulp](http://gulpjs.com/), [Webpack](https://webpack.github.io/), [Mocha](https://mochajs.org/), [Grunt](http://gruntjs.com/), [Codeception](https://codeception.com/), [Yarn](https://yarnpkg.com/) `latest`
 - `apt-transport-https`, `bzip2`, `ca-certificates`, `clean-css-cli`, `curl`, `gettext`, `git`, `imagemagick`, `memcached`, `mysql-client`, `openjdk-7-jre`, `openssh-client`, `perl`, `php-gettext`, `php5-apcu`, `php5-cli`, `php5-curl`, `php5-gd`, `php5-geoip`, `php5-imagick`, `php5-intl`, `php5-json`, `php5-mcrypt`, `php5-memcached`, `php5-mysqlnd`, `php5-sqlite`, `php5-xdebug`, `php5-xhprof`, `php5-xmlrpc`, `python`, `python3`, `rsync`, `ruby`, `software-properties-common`, `subversion`, `unzip`, `uglify-js`, `wget`, `zip`

----------

## Example - Local
```SHELL
docker run -it --volume=/Applications/MAMP/htdocs/project:/project --workdir="/project" --entrypoint=/bin/bash hendrikprinsza/bitbucket-pipelines-phpunit-mysql
```

----------

## Example - [Bitbucket Pipelines](https://bitbucket.org/product/features/pipelines)
```YAML
pipelines:
  default:
    - step:
        image: hendrikprinsza/bitbucket-pipelines-phpunit-mysql
        script:
          - phpunit --version
          - mysql -h127.0.0.1 -uroot -ppassword123 -e "SET GLOBAL sql_mode = 'NO_ENGINE_SUBSTITUTION';"
        services:
          - mysql

definitions:
  services:
    mysql:
      image: mysql:5.6
      environment:
        MYSQL_DATABASE: test_database
        MYSQL_ROOT_PASSWORD: password123
```
