![image](https://github.com/user-attachments/assets/ad398757-06f2-40ec-bb79-084f1c035850)



1. Make copy of my repository.
Enter cmd:
```bash
git clone https://github.com/MJaloui/game-day-notifications
```

2. Create a directory called "game-day-notifications"


3. To create an SNS Topic, open the AWS Management Console and navigate to the SNS service.

   ![image](https://github.com/user-attachments/assets/5478cef6-35f2-441b-84fd-b69c2404fea9)

4. Click Create Topic and select Standard as the topic type.

![image](https://github.com/user-attachments/assets/6123772d-0a76-4a45-a3d8-b68229b751ec)
![image](https://github.com/user-attachments/assets/ec957b4b-73ee-4b27-aa7f-a01019e3fa1a)


5.Select Standard and Name the topic (e.g., gd_topic) , then click "Create Topic

![image](https://github.com/user-attachments/assets/f1c87d31-75ea-4f40-a13b-0f027887124a)
![image](https://github.com/user-attachments/assets/4730837c-96cb-4760-adf4-5461571d088f)

7. Take note of the ARN, you will need to use it later.

![image](https://github.com/user-attachments/assets/48f597c7-3956-47bc-b41c-706902daf7f9)

8. Scroll down to "Subcriptions" and click "Create subscriptions".

![image](https://github.com/user-attachments/assets/2917541a-c373-4998-b579-75484592518d)
![image](https://github.com/user-attachments/assets/7392588c-5c84-4f59-b116-db65ff3c68f4)

9. After creating the topic, to add subscriptions, scroll down to "Subscriptions" tab and click Create subscription. (if you have other SNS 
   Topics created, click the one you just created) 

 - If you want a Email subscription, Select "Email" for Protocol. 
 - For the "Endpoint", enter a valid email address.

 - If you want an SMS (text messages), select "SMS" for protocol
 - For the "Endpoint", enter a valid phone number in international format (e.g., +1234567890).

![image](https://github.com/user-attachments/assets/bb6017c9-2cf5-4044-a44d-363ecf49fedb)

10. Scroll down and click "Create Subscription" on the bottom right.

![image](https://github.com/user-attachments/assets/de198a32-70b4-4290-82f1-55fa060c96fd)

11. If you added an Email subscription:
    
 - Check the inbox of the provided email address.
   
 - Confirm the subscription by clicking the confirmation link in the email.

![image](https://github.com/user-attachments/assets/5f6fc2a1-674b-4719-aa06-8530e69c8a0e)
![image](https://github.com/user-attachments/assets/e9e1f40f-1926-443f-94be-015f8e4589fe)
![image](https://github.com/user-attachments/assets/81ed5d91-281b-4b73-86e6-2796d3d7799c)

12. For SMS (text messages), the subscription will be immediately active after creation.

13. On the AWS page you have open, click "gd_topic" on the top path to validate your confirmed subcription. 

![image](https://github.com/user-attachments/assets/a243923e-6fb5-4d54-ba30-a7edbe1af365)
![image](https://github.com/user-attachments/assets/b3c4fc56-49e6-4770-b220-73b57e182eb5)

13. Next you will create the SNS Publish Policy. Open the IAM service in the AWS Management Console.


Navigate to Policies → Create Policy.
Click JSON and paste the JSON policy from gd_sns_policy.json file
Replace REGION and ACCOUNT_ID with your AWS region and account ID.
Click Next: Tags (you can skip adding tags).
Click Next: Review.
Enter a name for the policy (e.g., gd_sns_policy).
Review and click Create Policy.
Create an IAM Role for Lambda
Open the IAM service in the AWS Management Console.
Click Roles → Create Role.
Select AWS Service and choose Lambda.
Attach the following policies:
SNS Publish Policy (gd_sns_policy) (created in the previous step).
Lambda Basic Execution Role (AWSLambdaBasicExecutionRole) (an AWS managed policy).
Click Next: Tags (you can skip adding tags).
Click Next: Review.
Enter a name for the role (e.g., gd_role).
Review and click Create Role.
Copy and save the ARN of the role for use in the Lambda function.
Deploy the Lambda Function
Open the AWS Management Console and navigate to the Lambda service.
Click Create Function.
Select Author from Scratch.
Enter a function name (e.g., gd_notifications).
Choose Python 3.x as the runtime.
Assign the IAM role created earlier (gd_role) to the function.
Under the Function Code section:
Copy the content of the src/gd_notifications.py file from the repository.
Paste it into the inline code editor.
Under the Environment Variables section, add the following:
NBA_API_KEY: your NBA API key.
SNS_TOPIC_ARN: the ARN of the SNS topic created earlier.
Click Create Function.
Set Up Automation with Eventbridge
Navigate to the Eventbridge service in the AWS Management Console.
Go to Rules → Create Rule.
Select Event Source: Schedule.
Set the cron schedule for when you want updates (e.g., hourly).
Under Targets, select the Lambda function (gd_notifications) and save the rule.
Test the System
Open the Lambda function in the AWS Management Console.
Create a test event to simulate execution.
Run the function and check CloudWatch Logs for errors.
Verify that SMS notifications are sent to the subscribed users.

























