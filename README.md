# NBA Game Day Notifications / Sports Alerts System
![image](https://github.com/user-attachments/assets/c61dd22f-7bfe-4b7e-8208-bb224459bd6f)





## **Project Highlights**
🏀 This project sends live NBA game score updates to subscriped users via text messages or emails.

🏀 It leverages **Amazon SNS**, **AWS Lambda and Python**, **Amazon EventBridge** and **NBA APIs** to provide sports fans with up-to-date game information. 

🏀 This project demonstrates how to utilize cloud computing to set up a quick and efficient way to send notifications.

---

## **Capabilities**
🔧 Fetches live NBA game scores using an external API.

🔧 Sends formatted score updates to subscribers via SMS/Email using Amazon SNS.

🔧 Scheduled automation for regular updates using Amazon EventBridge.

🔧 Designed with security in mind, following the principle of least privilege for IAM roles.

## **Prerequisites**
- Free account with subscription and API Key at [sportsdata.io](https://sportsdata.io/)
- Personal AWS account with basic understanding of AWS and Python

---

## **Technical Architecture**
<img src="https://github.com/user-attachments/assets/5e19635e-0685-4c07-9601-330f7d1231f9" width="50%" />


---


## **Technologies**
- **Linux**
- **Virtual Box**
- **Ubuntu**
- **Visual Studio Code**
- **Cloud Provider**: AWS
- **Core Services**: SNS, Lambda, EventBridge
- **External API**: NBA Game API (SportsData.io)
- **Programming Language**: Python 3.x
- **IAM Security**:
  - Least privilege policies for Lambda, SNS, and EventBridge.

---


## **Setup Instructions**

### **Clone the Repository**
```bash
git clone https://github.com/MJaloui/game-day-notifications
cd game-day-notifications
```

1. Create an SNS Topic**


2. Add Subscriptions to the SNS Topic**


### **Create the SNS Publish Policy**


### **Create an IAM Role for Lambda**


### **Deploy the Lambda Function**



### **Set Up Automation with Eventbridge**



### **Test the System**


---

### **Key Takeaways**
✔️ Designing a notification system with AWS SNS and Lambda.

✔️ Securing AWS services with least privilege IAM policies.

✔️ Automating workflows using EventBridge.

✔️ Integrating external APIs into cloud-based workflows.


### **Opportunities for Growth**
🌱 Add NFL score alerts for extended functionality.

🌱 Store user preferences (teams, game types) in DynamoDB for personalized alerts.

🌱 Implement a web UI
