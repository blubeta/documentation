# Build Steps

## Pre-requisites
1. Working System Ruby Installation

```
git clone https://github.com/aws/aws-codedeploy-agent.git
gem install bundler
cd aws-codedeploy-agent
bundle install
rake clean 
bundle exec rake
```

```
sudo aptitude update
sudo aptitude python-pip
sudo aptitude install ruby 2.0
sudo pip install awscli
cd
aws s3 s3://[bucket-name]/latest/install . --region [region]
chmod +x install
sudo ./install auto
```

[AWS Docs][http://docs.aws.amazon.com/codedeploy/latest/userguide/how-to-run-agent.html#how-to-run-agent-install-ubuntu]

## Notes
deployment-root folder is organized by deployment_group_id/deployment_id
deployment-root/deployment-instructions maintains a list of previous deployments including `last_succesful_install`
to wipe out and start fresh, both of these folders need to be wiped
