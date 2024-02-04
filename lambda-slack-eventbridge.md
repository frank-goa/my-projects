### Cloudwatch Event rule that triggers a Lambda function which sends a Slack Notification when an EC2 Instance is stopped

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

<img width="1512" alt="Screenshot 2024-02-04 at 21 47 48" src="https://github.com/frank-goa/my-projects/assets/137857643/b1748318-260f-4d63-a231-6568848e532a">
- Copy Sample Curl Request and paste it into a Terminal Window

<img width="1512" alt="Screenshot 2024-02-04 at 21 49 40" src="https://github.com/frank-goa/my-projects/assets/137857643/a7cb9d08-63fc-413a-a2f7-321e9f1f1c7a">
- Check Slack to 'Hello World' Message

<img width="1512" alt="Screenshot 2024-02-04 at 21 51 07" src="https://github.com/frank-goa/my-projects/assets/137857643/8e0617ae-094a-4b6f-b12e-9ad0560d65ae">
