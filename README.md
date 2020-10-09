### AWS Lambda cron jobs
Sometimes, you'd need execute a certain lambda function periodically so that it can do the required business logic.
With Serverless application model (SAM) this has been made incredibly easy to configure.

Here is an example:

```yaml

  CronJob:
    Type: AWS::Serverless::Function
    Properties:
      Role: !GetAtt CronJobRole.Arn
      Handler: cleanup-lambda.lambdaHandler
      Layers:
        - !Ref NodeDependenciesLayer
      CodeUri: /code/location
      FunctionName: 
      Runtime: nodejs12.x
      Events:
        CloudWatchEvent:
          Type: Schedule
          Properties:
            Schedule: rate(90 days)

```
