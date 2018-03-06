> Requires python v 2.6.7+ or Python 3.3+

`python --version`

# Install Ruby 2.0 for system
`sudo aptitude install ruby2.0`

# Installing via pip

`sudo aptitude install python-pip`
`sudo pip install awscli`

# Install via CLI

```
curl "https://s3.amazonaws.com/aws-cli/awscli-bundle.zip" -o "awscli-bundle.zip"
unzip awscli-bundle.zip
sudo ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
```

# AWS ECS ( deploying )

* eval $(aws ecr --profile blubeta get-login --region us-east-1 | sed 's|https://||')
* docker build -t [name] [path] (i.e. docker build tech-crawl .)
* docker tag [name]:[tag:latest] [ECS URL]:[tag:latest]
* docker push [ECS URL]:[tag:latest]


# Docker
