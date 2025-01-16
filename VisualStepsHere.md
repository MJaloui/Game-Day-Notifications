![image](https://github.com/user-attachments/assets/ad398757-06f2-40ec-bb79-084f1c035850)


1. Go to Sportsdata.io and create a free account



2. Click "API Free Trail"
![image](https://github.com/user-attachments/assets/4bf332c5-f303-4ad5-9576-97616c8e4cb3)



3. Click "SportsDataIO API Free Trial"
![image](https://github.com/user-attachments/assets/fe09198d-75db-4638-a77d-78d39a49fcd7)



4. Fill out all of the information asked for the free trial and click "Submit".
![image](https://github.com/user-attachments/assets/92916034-cb25-499a-aa62-8f39a77be52b)
![image](https://github.com/user-attachments/assets/758853c4-0dcd-4699-970e-3fa5e038edeb)



5. You will get an email and at the bottom it says "Launch Developer Portal"
![image](https://github.com/user-attachments/assets/a19fcea7-e8dd-4349-af9e-f2922616cb11)
![image](https://github.com/user-attachments/assets/292a8de8-fbca-4034-b8bb-d0331911f2fb)




6. By default it takes you to the NFL, on the left click on NBA
![image](https://github.com/user-attachments/assets/0cba64fe-e369-4f44-ab87-26a149d726eb)
![image](https://github.com/user-attachments/assets/f24a2a60-bc9d-44ae-905e-1e6c772fd313)



7. Scroll down until you see "Standings", your API Key is under "query String Parameters".

![image](https://github.com/user-attachments/assets/ed0d2d02-a540-4994-aacf-74eb3a611ef4)

![image](https://github.com/user-attachments/assets/72cdcd13-483a-4d79-b5bb-024a019f2312)




8. Make copy of my repository.

Enter cmd:
```bash
git clone https://github.com/MJaloui/game-day-notifications
```



9. Create a directory called "game-day-notifications"





10. To create an SNS Topic, open the AWS Management Console and navigate to the SNS service.

   ![image](https://github.com/user-attachments/assets/5478cef6-35f2-441b-84fd-b69c2404fea9)




11. Click Create Topic and select Standard as the topic type.

![image](https://github.com/user-attachments/assets/6123772d-0a76-4a45-a3d8-b68229b751ec)
![image](https://github.com/user-attachments/assets/ec957b4b-73ee-4b27-aa7f-a01019e3fa1a)





12.Select Standard and Name the topic (e.g., gd_topic) , then click "Create Topic

![image](https://github.com/user-attachments/assets/f1c87d31-75ea-4f40-a13b-0f027887124a)
![image](https://github.com/user-attachments/assets/4730837c-96cb-4760-adf4-5461571d088f)





13. Take note of the ARN, you will need to use it later.

![image](https://github.com/user-attachments/assets/48f597c7-3956-47bc-b41c-706902daf7f9)





14. Scroll down to "Subcriptions" and click "Create subscriptions".

![image](https://github.com/user-attachments/assets/2917541a-c373-4998-b579-75484592518d)
![image](https://github.com/user-attachments/assets/7392588c-5c84-4f59-b116-db65ff3c68f4)




15. After creating the topic, to add subscriptions, scroll down to "Subscriptions" tab and click Create subscription. (if you have other SNS 
   Topics created, click the one you just created) 

 - If you want a Email subscription, Select "Email" for Protocol. 
 - For the "Endpoint", enter a valid email address.

 - If you want an SMS (text messages), select "SMS" for protocol
 - For the "Endpoint", enter a valid phone number in international format (e.g., +1234567890).

![image](https://github.com/user-attachments/assets/bb6017c9-2cf5-4044-a44d-363ecf49fedb)




16. Scroll down and click "Create Subscription" on the bottom right.

![image](https://github.com/user-attachments/assets/de198a32-70b4-4290-82f1-55fa060c96fd)





17. If you added an Email subscription:
    
 - Check the inbox of the provided email address.
   
 - Confirm the subscription by clicking the confirmation link in the email.

![image](https://github.com/user-attachments/assets/5f6fc2a1-674b-4719-aa06-8530e69c8a0e)
![image](https://github.com/user-attachments/assets/e9e1f40f-1926-443f-94be-015f8e4589fe)
![image](https://github.com/user-attachments/assets/81ed5d91-281b-4b73-86e6-2796d3d7799c)




18. For SMS (text messages), the subscription will be immediately active after creation.




19. On the AWS page you have open, click "gd_topic" on the top path to validate your confirmed subcription. 

![image](https://github.com/user-attachments/assets/a243923e-6fb5-4d54-ba30-a7edbe1af365)
![image](https://github.com/user-attachments/assets/b90d8a6c-7118-405a-aa5c-ae418652ce85)




20. Next you will create the SNS Publish Policy. Open the IAM service in the AWS Management Console.
    
![image](https://github.com/user-attachments/assets/19aa4ce6-316b-4c60-828f-fb9a2724e02e)
![image](https://github.com/user-attachments/assets/46dd8490-6681-4382-ae2a-b8da96e8fff5)




21. On the left panel, navigate to Policies, then click "Create Policy" on the top right.

![image](https://github.com/user-attachments/assets/dc6e92b5-58cf-4464-bb9c-5666043050e8)
![image](https://github.com/user-attachments/assets/1e599c91-e66d-433b-956c-9ec2e97f56f5)



22. Select the SNS service uner "Select a serivice".

![image](https://github.com/user-attachments/assets/ec00fce6-2d16-4a2e-9379-7b6d3462946f)



23. Click "JSON" tab and paste the JSON policy from gd_sns_policy.json file (the file is located in my github or your account if it was cloned). After tasks are completed click "Next".

![image](https://github.com/user-attachments/assets/d8e72cf6-5b48-4b4f-b6ea-e3e2a0f9a1a8)
![image](https://github.com/user-attachments/assets/d1e2cc77-1743-4c8a-8a96-be231e27d01f)
![image](https://github.com/user-attachments/assets/b93fbd70-8cd5-4cea-8487-361163243fd8)


24. Enter copied script in policy editor.

  - Replace "Resource" contents in the script with ARN.
    
    - Before: "Resource": "arn:aws:sns:REGION:ACCOUNT_ID:gd_topic"
    - After: "Resource": "Your_gd_topics_ARN_Number"
      
  - Under the  path Amazon SNS > Topics, you will find your ARN.
    
![image](https://github.com/user-attachments/assets/7bdc3b34-1d37-433c-9da1-0ccbb8e7f2df)
![image](https://github.com/user-attachments/assets/ec8d0ef0-261f-4373-8046-8ba07e086293)




25. Click Next: Tags (you can skip adding tags).
    
    - Click Next: Review.

![image](https://github.com/user-attachments/assets/5b9e7047-ed6d-45fa-b370-179aa7cd17d5)



    
26. Enter a name for the policy (e.g., gd_sns_policy).

![image](https://github.com/user-attachments/assets/9893ef25-b96d-4c53-ad07-cda6beea3b34)




27. Review and click Create Policy.

![image](https://github.com/user-attachments/assets/48fe9d54-0859-487a-84ba-9d73dd574152)




28. Next you will create an IAM Role for Lambda. To do this, Open the IAM service in the AWS Management Console.



29. On the left Click "Roles", then click "Create role" on the top right.


![image](https://github.com/user-attachments/assets/05c01bec-8701-4048-93ef-db3c3c6c16a5)


30. Select "AWS Service" for your "Trusted enitity type", and choose "Lambda" for your Use case.

![image](https://github.com/user-attachments/assets/bd0844a1-eeef-487c-a601-63f898e10331)


31. Select the following policies:

  - "gd_sns_policy", which is the SNS Publish Policy created in the previous step.

![image](https://github.com/user-attachments/assets/6f41f5ba-9241-44a1-8e8d-7ef871a27601)


  - "AWSLambdaBasicExecutionRole", which Lambda Basic Execution Role, an AWS managed policy.

![image](https://github.com/user-attachments/assets/249ca4be-4a1d-4b79-ab5b-c745b2c4d09e)


32. Click Next: Tags (you can skip adding tags).
Click Next: Review.

![image](https://github.com/user-attachments/assets/6d63a384-f972-4cc7-b176-1972e926dda4)

33. Enter a name for the role (e.g., gd_lambda_role), add a description if you wish, review everything, and click "Create Role".

![image](https://github.com/user-attachments/assets/23b2ea6d-aac8-45ab-8ece-583e0de21710)
![image](https://github.com/user-attachments/assets/9be51ee1-3648-4979-8231-440d9de041f7)
![image](https://github.com/user-attachments/assets/391f0989-80df-442e-98ec-01873d8d902e)



Copy and save the ARN of the role for use in the Lambda function.



34. Next you will Deploy the Lambda Function, open the AWS Management Console and navigate to the Lambda service.

![image](https://github.com/user-attachments/assets/fadd4a85-dc09-454c-98b1-d66dbd677719)



35. Click Create Function.

![image](https://github.com/user-attachments/assets/1e8a7a62-37d6-47d8-a630-f982cf884394)

36. Select the "Author from scratch", enter a "function name" (e.g., gd_notifications), choose Python 3.x as the runtime, and "Architecture" 
    left at default setting "x86_64".

![image](https://github.com/user-attachments/assets/3a38f566-726e-4c55-bc49-e284945bb580)


37. Under "Execution role" select "Use an existing role". Assign the IAM role created earlier (gd_lambda_role) to the function "Existing 
    role". Then click "Create function".

![image](https://github.com/user-attachments/assets/e14fbeca-61f2-4921-956b-30a4afef2b1b)
![image](https://github.com/user-attachments/assets/5e551674-d5f4-412f-9286-3d12c4648efe)

![image](https://github.com/user-attachments/assets/e31b9636-f76a-4217-b3ac-25993d152109)




38. Scroll down to the function "Code" tab.

![image](https://github.com/user-attachments/assets/ea543a83-2706-43d1-9787-52ba8dfe24b4)


39. copy the contents of the src/gd_notifications.py file from the repository and paste it 
    in the code funtion. 
    
![image](https://github.com/user-attachments/assets/db81d713-60f4-4463-94f9-2297afabe513)
![image](https://github.com/user-attachments/assets/bfa42358-dc41-414c-a9e6-3fe53337d9af)



40. You can adjust the timezone if you needed in this script. To change timezone, figure out what number is needed for the timezone in this 
    script. I researched my timezone and it is "5" for Eastern.

    - Scroll down to "#Adjust for Central Time (UTC-5)"
    - Change everywhere you see "6" to "5". 
    - Change everywhere you see "Central" to "Eastern".
    
![image](https://github.com/user-attachments/assets/982d1304-51ba-4ef8-8fa5-0de5ac877956)
![image](https://github.com/user-attachments/assets/7f2d3e56-9ad6-47cb-a367-0474f17893f3)



41. Click deploy on the left panel.

![image](https://github.com/user-attachments/assets/2f9695e0-9cde-4026-ba13-ceabe4a65031)

42. If it was succesfull, you will see a success banner on the top.

![image](https://github.com/user-attachments/assets/48c14022-6052-41e2-89a5-da7f26179cdb)

43. Next, go to "Configuration" tab, then click "Environment Variables" on the left panel. 

![image](https://github.com/user-attachments/assets/74870b44-55d5-42fa-bd67-440eacfc8736)

44. Click "Add environment variable", then add the "Key" name (API Key) and "Value" (API Key).

![image](https://github.com/user-attachments/assets/4d322e99-3c27-47cc-98ce-23b9237ca88c)
![image](https://github.com/user-attachments/assets/fad314d8-7e1d-4884-b03f-fbcf63d0f1e8)


45. Click "Add environment variable" to add a second variable. Add the "Key" name (SNS Topic) and "Value" (ARN of SNS topic created earlier).  After you enter both Variables click "Save" and "Create function"


![image](https://github.com/user-attachments/assets/c20f692f-39ee-46d9-bfae-4b4020635eea)
![image](https://github.com/user-attachments/assets/ace03121-09f7-48cf-9545-9238f294f985)
![image](https://github.com/user-attachments/assets/721c59f8-ad5e-4eb8-94ab-85dba130cb14)
![image](https://github.com/user-attachments/assets/380e37c6-8eb9-45c3-9ae9-25782bf21cc7)

46.You will now have to Set Up Automation with Eventbridge, navigate to the Eventbridge service in the AWS Management Console.

![image](https://github.com/user-attachments/assets/2d1d935f-aabd-4c8e-a14e-e7ea19fb7079)

47. On the Left panel click to "Rules" , then click "Create Rule".

![image](https://github.com/user-attachments/assets/948f6b29-1ae3-461f-b660-905deb5c2213)
![image](https://github.com/user-attachments/assets/211cd152-37b4-4e20-8ef4-96b5df6cd2ea)

48. Test the system to validate it works, click the "Test" tab.

![image](https://github.com/user-attachments/assets/fb58b3b2-cdd2-40cc-a07d-5ca30da863e0)




49. For the "Event name", name it “test1”, and click save. Leave everything else at the default settings.

![image](https://github.com/user-attachments/assets/705eb746-ee1d-448b-9ae1-b9efdb8e6272)




42. After you click "Save" click "Test" on top right. Wait about 3-6 seconds to validate test was successful.

![image](https://github.com/user-attachments/assets/bea16235-3f2d-413d-a7fb-ca2380bce94f)
![image](https://github.com/user-attachments/assets/2c24622b-b481-4004-a9cd-9acff6f520fa)



43. You will recieve a notification in your email. Open the email to validate you recieved some game statuses.

![image](https://github.com/user-attachments/assets/861293fd-9197-45db-a83a-f397ac6ae655)
![image](https://github.com/user-attachments/assets/5a559a9d-188f-411b-bbd7-ff226cefa250)




44. Go to "Amazon EventBridge" service to set the cron schedule for when you updates (e.g., hourly).

![image](https://github.com/user-attachments/assets/a51142ac-c1c5-423f-b972-904cdf11f97f)
![image](https://github.com/user-attachments/assets/0d554777-45c3-4cf1-b5ce-6711d5d7aec5)


45. Scroll down and click "Create rule"

![image](https://github.com/user-attachments/assets/62cff2a0-9009-4493-a36a-ba9a9f3ee40f)



46. For the "Name" enter "gd_rule", for the "Rule type" select "Schedule", then click "Continue in EventBridge Scheduler".

![image](https://github.com/user-attachments/assets/8eae4217-8c82-4d7d-81ec-ed3b25eb237a)



47. Scroll down to "Schedule pattern", then select "Recurring schedule" and "Cron-based schedule".

![image](https://github.com/user-attachments/assets/a653e3c6-3c9c-4c3c-9be1-56a32420ec76)


48. Enter "Cron expression" for your schedule, you can get help to generate an Cron expression on chatGPT or any website you can research 
    Cron expressions. After expressions are entered, select "Off" for "Flexable time window", then click next.

![image](https://github.com/user-attachments/assets/33accc05-fb4a-40b0-a59f-6a2c88858fe2)
![image](https://github.com/user-attachments/assets/deaada33-05fa-4bca-855e-70411edc4208)




49. Scroll down to "Select target" and select "AWS Lambda".

![image](https://github.com/user-attachments/assets/dd531d75-175f-4982-8b8d-0e80cae51e10)




50. Scroll down to "Invoke" and  select the "Lambda function", "gd_notifications",
![image](https://github.com/user-attachments/assets/34f6bb10-d385-42f8-b2f2-4103e8918154)

51. Validate the  "Schedule state" is enabled, and under "Permissions" the "Execution role" is set to “Create new role for this schedule” (this should be default settings), then click next.

![image](https://github.com/user-attachments/assets/5e1948ea-4705-4ea2-9263-081df5405e07)
![image](https://github.com/user-attachments/assets/90c16b0f-0d64-4df9-9f93-8b1c0af05781)
![image](https://github.com/user-attachments/assets/286b42e0-569b-48a3-8045-4f3c27dbca55)



52. Scroll down and click "create schedule" on the bottom right.

![image](https://github.com/user-attachments/assets/efe0910b-1245-426c-8d9a-ff93298ed737)
![image](https://github.com/user-attachments/assets/72667fce-cc73-4bc7-bf1d-d405f2e2f227)



53. Scroll down to "gd_rule" and validate the "Status" is "Enabled. 

![image](https://github.com/user-attachments/assets/029e1f90-5cb6-44d0-a56a-9ff878e86aa4)


Run the function and check CloudWatch Logs for errors.
Verify that SMS notifications are sent to the subscribed users.

























