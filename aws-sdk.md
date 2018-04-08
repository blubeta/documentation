# Installing 
> Requires python v 2.6.7+ or Python 3.3+

`python --version`

## Install Ruby 2.0 for system
`sudo aptitude install ruby2.0`

## Installing via Python 3.3+ & AWS CLI (recommended)

```python
brew install python || brew upgrade python
cd ~/ (or whatever directory you'd like to download the script to)
curl -O https://bootstrap.pypa.io/get-pip.py
python3 get-pip.py --user
pip3 install --upgrade pip3
pip3 install awscli --upgrade --user
```

## To Move aws bin to your path
* [AWSCLI Install OS X Path](https://docs.aws.amazon.com/cli/latest/userguide/cli-install-macos.html#awscli-install-osx-path)

## Install via CLI

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
