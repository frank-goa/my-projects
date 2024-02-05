### Cloudwatch Event rule that triggers a Lambda function which sends a Slack Notification when an EC2 Instance is stopped

![Cloudwatch_lambda_Slack](https://github.com/frank-goa/my-projects/assets/137857643/eefb07f7-6ab8-4d72-8034-21454456087e)

### Step 1:
#### Creating Slack Applcation
- Browse to - https://api.slack.com/apps?new_app=1

<img width="1511" alt="Screenshot 2024-02-04 at 21 45 13" src="https://github.com/frank-goa/my-projects/assets/137857643/714a5499-630e-49a2-a5d4-493b457f6bfc">

- Create an App > from scratch
<img width="1511" alt="Screenshot 2024-02-04 at 21 45 55" src="https://github.com/frank-goa/my-projects/assets/137857643/2218b846-bbfd-4557-ace0-4f2e5c6b3953">
- Provide an App Name and select the Workspace

<img width="1511" alt="Screenshot 2024-02-04 at 21 46 15" src="https://github.com/frank-goa/my-projects/assets/137857643/8700368d-5ffe-4abe-ae1a-3844cdc22fe6">
- Select Incoming Web Hooks

<img width="1511" alt="Screenshot 2024-02-04 at 21 46 37" src="https://github.com/frank-goa/my-projects/assets/137857643/b014299b-9c2b-4cfc-a76b-6070e2abc896">
- Activate incoming WebHooks

<img width="1512" alt="Screenshot 2024-02-04 at 21 46 50" src="https://github.com/frank-goa/my-projects/assets/137857643/49290e5c-1e2a-41b5-849f-b3ae14f8d6b1">
- Add New WebHook to Workspace

<img width="1512" alt="Screenshot 2024-02-04 at 21 47 20" src="https://github.com/frank-goa/my-projects/assets/137857643/7fa40681-8f77-49d9-a629-9d10a49fb0e0">
- Allow Permissions

<img width="1512" alt="Screenshot 2024-02-04 at 21 49 40" src="https://github.com/frank-goa/my-projects/assets/137857643/7e1fe603-7a10-4ffb-aae3-495f315dd497">

- Copy Sample Curl Request and paste it into a Terminal Window
<img width="1512" alt="Screenshot 2024-02-04 at 21 49 40" src="https://github.com/frank-goa/my-projects/assets/137857643/3fa504eb-e523-4734-bc4e-19b57b6826b4">

- Check Slack to 'Hello World' Message

<img width="1512" alt="Screenshot 2024-02-04 at 21 51 07" src="https://github.com/frank-goa/my-projects/assets/137857643/8e0617ae-094a-4b6f-b12e-9ad0560d65ae">

### Step 2:
#### Creating a Lambda function
- provide a name for the function
- select Runtime - Python 3.8
- Select appropriate Role
- Create Function
- 

```bash
import json
import urllib3

def lambda_handler(event, context):
    http = urllib3.PoolManager()
    
    data = {"text": "Alert!!!... EC2 Instance Stopped..."}
    
    req = http.request("POST",
                       "https://hooks.slack.com/services/T06GLPQRBSB/B0XXXXXGZ/LNDvDZcXXXXXXXQG7bvn9xK",
                       body = json.dumps(data),
                       headers = {"Content-Type": "application/jso"})
    
    # TODO implement
    return {
        'statusCode': 200,
        'body': json.dumps('Alert!!!...')
    }

```
- Test the lambda function

```bash
Test Event Name
test

Response
{
  "statusCode": 200,
  "body": "\"Alert!!!...\""
}
```

<img width="1509" alt="Screenshot 2024-02-04 at 23 41 43" src="https://github.com/frank-goa/my-projects/assets/137857643/222c5512-e4c4-4d16-b8ff-e438a84c95fe">

### Step 3:
- Create an EC2 Instance
- note the instance ID
<img width="1511" alt="Screenshot 2024-02-04 at 23 51 07" src="https://github.com/frank-goa/my-projects/assets/137857643/937f0b4f-d1a1-4399-9cbe-caded1d35bbd">

### Step 4:
- Creating CloudWatch Event Rule
<img width="1511" alt="Screenshot 2024-02-04 at 23 51 07" src="https://github.com/frank-goa/my-projects/assets/137857643/d85c88af-a116-4869-b2e1-df147107e437">

<img width="1511" alt="Screenshot 2024-02-04 at 23 51 37" src="https://github.com/frank-goa/my-projects/assets/137857643/67892735-0262-431b-99d7-cf3c413724a5">

<img width="1510" alt="Screenshot 2024-02-04 at 23 53 05" src="https://github.com/frank-goa/my-projects/assets/137857643/2d8e985c-188e-459d-b0b2-a75e63e01313">

<img width="1511" alt="Screenshot 2024-02-04 at 23 53 23" src="https://github.com/frank-goa/my-projects/assets/137857643/9f517a78-2106-46cf-82a5-89c19c569139">

<img width="1511" alt="Screenshot 2024-02-04 at 23 54 01" src="https://github.com/frank-goa/my-projects/assets/137857643/d4f1a4b4-ad77-4ecd-a15c-897f18935160">

### Test:
<img width="1512" alt="Screenshot 2024-02-05 at 00 00 11" src="https://github.com/frank-goa/my-projects/assets/137857643/aba50aa4-fba2-4f78-8181-8b6ff5c8edac">

<img width="1510" alt="Screenshot 2024-02-05 at 00 01 18" src="https://github.com/frank-goa/my-projects/assets/137857643/2e23fb8d-bc50-4a0c-a631-94e9988a0c64">

- addition learning
- https://quick-refs.github.io/aws/slack-notifications-from-aws-cloudwatch-alarms

