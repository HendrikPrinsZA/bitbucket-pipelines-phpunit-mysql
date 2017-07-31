# bitbucket-pipelines-phpunit-mysql
Bitbucket Pipelines image based on Debian/Jessie with PHPUnit/MySQL/Sencha CMD/Node/Composer/...

# Build image
docker build -t bitbucket-pipelines-phpunit-mysql .

# Run & enter terminal
docker run -it --volume=/Applications/MAMP/htdocs/clevva:/clevva --workdir="/clevva" --memory=4g --memory-swap=4g --entrypoint=/bin/bash bitbucket-pipelines-phpunit-mysql

docker run -it --volume=/Applications/MAMP/htdocs/clevva:/clevva --workdir="/clevva" --memory=4g --memory-swap=4g --entrypoint=/bin/bash clevva-test-1


# Other images
docker run -it --entrypoint=/bin/bash kaivolland/jdk-node7-sencha6
