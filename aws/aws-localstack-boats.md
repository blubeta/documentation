# Running Helm using Localstack
## Prerequisites
-Install Docker.
-Install Ngrok - I downloaded the main Ngrok program from the website and put it in the ~ directory.
-Have the AWS CLI installed and credentials created, see AWS docs.
-Install localstack with pip install localstack. You might have an issue with your default Python path. If you do, run echo $PATH to see if you have a Python path, and if you do, add it to the bottom of your path file with a text editor.
-Install awslocal by running $ pip install awscli-local. This allows you to run AWS CLI commands without having to set an endpoint URL in every command.
## Start Localstack
1. ```$ LAMBDA_EXECUTOR=docker localstack start --docker```
This starts the local stack service in a Docker container. The environment variable is required to run Lambda functions written in Node.
# Add a test email to an s3 bucket
1.  Get a MIME formatted email and put it into a file named “testemail” (no file extension). I did this by sending an email to a Route 53 domain I set up to receive emails and deposit them in an S3 bucket in SES, then grabbing the email manually from the S3 bucket and renaming it. There are probably other ways to do this.
2. ``` $ awslocal s3 mb s3://emails ```
This is the AWS CLI command to create an S3 bucket. “emails” is the name of the bucket.

3. ```$ awslocal s3 cp testemail s3://emails```
Adds your testemail file to the s3 bucket.

## Start Ngrok to tunnel from the lambda function to localhost.
1. ``` $./ngrok http *PORT FOR API-COMMUNCIATOR*``` 
Creates a tunnel to localhost on that port number so that the Lambda function can tunnel to it. The downloaded Ngrok file needs to be in the directory you run the command from. Note the URL that ngrok gives you.

## Create the lambda function to receive email.
1. Add the Ngrok URL to the lambda function’s post request configuration.

2. Navigate to folder containing the lambda function, then run $ zip index.zip . -r

3. ```$ awslocal lambda create-function --function-name=index --runtime=nodejs6.10 --role=r1 --handler=index.handler --zip-file fileb://index.zip```

Run this in the same directory as your created zip file. This creates the lambda function.

## Start Boats microservices
1. If you haven’t done so already, add your AWS access key and secret key to the api-mail configuration (if you want to actually send email, this requires further setup inside AWS SES), then add a configuration object for api-communicator which looks like this:
```
"api-communicator": {
    "server": {
      "port": 4000
    }
  },
 ```

2. In the folder for configd, run ```$ NODE_ENV=development npm start```

3. In the folder for api-mail, run ```$ npm start```

4. Navigate to the api being used to send the email (currently temporarily temp-api, in the future api-communicator), then start it. Temp-api is started by running ```$ node server.js``` in its root directory.

## Instantiate the Lambda
1. ```$ awslocal lambda invoke --function-name index \ outputfile.txt``` 
This will invoke the lambda function, which takes the email from the S3 bucket, sends it to the API, which parses it then sends it to api-mail, which sends it through SES.
