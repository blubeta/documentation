Prerequisites:
- Created New Server
- Configured Network (security) Policies
- Recieved Permission to Establish New Pipeline


Server Side: Install Software
- AWS CLI (CodeCommit)

- Caddy (Encrypted Webserver + reverse proxy) -> Link full guide on opening ports and config system

- PHP (5 or 7)
- Ruby
- Mysql (and php/ruby mysql client)
- Docker 
- Sidekiq / Redis
- Imagemagick

Install Codedeploy Agent (ubuntu server)
- http://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent-operations-install-ubuntu.html

  Confirmation command should look like this:
  ubuntu@hostname:~$ sudo service codedeploy-agent status
  The AWS CodeDeploy agent is running as PID 1491

- Create Application folder in /var/mount/
- Crease Release (applicationname-release) folder in /var/mount/
- Ensure App user (ubuntu, app, etc) has full ownership of these directories and everything in them


AWS Console Side
Create Application and Deployment Group
- Create Deployment Group -> name (development / staging / production)
- In Place Deployment
- Choose Instance (by hostname or tag,make sure Key Value pair matches to 1 instance)
- Deployment Config - OneAtATime (default)
- Advanced : Rollback if Deployment Fails (production) / Disable Rollbacks (development)
- Service Role: 'arn:aws:iam::430326878821:role/CodeDeployRole'

Link CodePipeLine
- Create Pipeline 
- Name (applicationname + deployment type)
- Github as source
- Choose Branch
- Build - None
- Deployment Provider (as codedeploy, enter previous name / group)
- Role = AWS-CodePipeline-Service
- Confirm

Find EC2 Instance: 
- Select in EC2 List
- Select Actions -> Actions -> Instance Settings -> Attach / Replace IAM Role
- Set CodeDeployRole 

???
Test First Release


