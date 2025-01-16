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
![image](https://github.com/user-attachments/assets/b90d8a6c-7118-405a-aa5c-ae418652ce85)




14. Next you will create the SNS Publish Policy. Open the IAM service in the AWS Management Console.
    
![image](https://github.com/user-attachments/assets/19aa4ce6-316b-4c60-828f-fb9a2724e02e)
![image](https://github.com/user-attachments/assets/46dd8490-6681-4382-ae2a-b8da96e8fff5)




15. On the left panel, navigate to Policies, then click "Create Policy" on the top right.

![image](https://github.com/user-attachments/assets/dc6e92b5-58cf-4464-bb9c-5666043050e8)
![image](https://github.com/user-attachments/assets/1e599c91-e66d-433b-956c-9ec2e97f56f5)



16. Select the SNS service uner "Select a serivice".

![image](https://github.com/user-attachments/assets/ec00fce6-2d16-4a2e-9379-7b6d3462946f)



17. Click "JSON" tab and paste the JSON policy from gd_sns_policy.json file (the file is located in my github or your account if it was cloned). After tasks are completed click "Next".

![image](https://github.com/user-attachments/assets/d8e72cf6-5b48-4b4f-b6ea-e3e2a0f9a1a8)
![image](https://github.com/user-attachments/assets/d1e2cc77-1743-4c8a-8a96-be231e27d01f)
![image](https://github.com/user-attachments/assets/b93fbd70-8cd5-4cea-8487-361163243fd8)


18. Enter copied script in policy editor.

  - Replace "Resource" contents in the script with ARN.
    
    - Before: "Resource": "arn:aws:sns:REGION:ACCOUNT_ID:gd_topic"
    - After: "Resource": "Your_gd_topics_ARN_Number"
      
  - Under the  path Amazon SNS > Topics, you will find your ARN.
    
![image](https://github.com/user-attachments/assets/7bdc3b34-1d37-433c-9da1-0ccbb8e7f2df)
![image](https://github.com/user-attachments/assets/ec8d0ef0-261f-4373-8046-8ba07e086293)




19. Click Next: Tags (you can skip adding tags).
    
    - Click Next: Review.

![image](https://github.com/user-attachments/assets/5b9e7047-ed6d-45fa-b370-179aa7cd17d5)



    
20. Enter a name for the policy (e.g., gd_sns_policy).

![image](https://github.com/user-attachments/assets/9893ef25-b96d-4c53-ad07-cda6beea3b34)




21. Review and click Create Policy.

![image](https://github.com/user-attachments/assets/48fe9d54-0859-487a-84ba-9d73dd574152)




22. Next you will create an IAM Role for Lambda. To do this, Open the IAM service in the AWS Management Console.



23. On the left Click "Roles", then click "Create role" on the top right.


![image](https://github.com/user-attachments/assets/05c01bec-8701-4048-93ef-db3c3c6c16a5)


24. Select "AWS Service" for your "Trusted enitity type", and choose "Lambda" for your Use case.

![image](https://github.com/user-attachments/assets/bd0844a1-eeef-487c-a601-63f898e10331)


Select the following policies:

  - "gd_sns_policy", which is the SNS Publish Policy created in the previous step.

![image](https://github.com/user-attachments/assets/6f41f5ba-9241-44a1-8e8d-7ef871a27601)


  - "AWSLambdaBasicExecutionRole", which Lambda Basic Execution Role, an AWS managed policy.

![image](https://github.com/user-attachments/assets/249ca4be-4a1d-4b79-ab5b-c745b2c4d09e)


Click Next: Tags (you can skip adding tags).
Click Next: Review.

![image](https://github.com/user-attachments/assets/6d63a384-f972-4cc7-b176-1972e926dda4)

Enter a name for the role (e.g., gd_lambda_role), add a description if you wish, review everything, and click "Create Role".

![image](https://github.com/user-attachments/assets/23b2ea6d-aac8-45ab-8ece-583e0de21710)
![image](https://github.com/user-attachments/assets/9be51ee1-3648-4979-8231-440d9de041f7)
![image](https://github.com/user-attachments/assets/391f0989-80df-442e-98ec-01873d8d902e)



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

























