# AWS-CloudWatch-Alarm-for-EC2-Memory-Utilization-Monitoring

## Project Title: AWS CloudWatch Alarm for EC2 Memory Utilization Monitoring
# Project Objective
To monitor EC2 instance memory usage using AWS CloudWatch and send proactive notifications (e.g., via SNS) when memory utilization crosses a defined threshold. This helps optimize performance and maintain system reliability.

# Step-by-Step Implementation
# Step 1: Understand the Challenge
Unlike CPU, disk, and network metrics, EC2 memory utilization is not available by default in CloudWatch. It requires custom configuration using the CloudWatch Agent.

# Step 2: Install & Configure the CloudWatch Agent
# 2.1 Install CloudWatch Agent
For Amazon Linux, Ubuntu, etc.:

# sudo yum install amazon-cloudwatch-agent
# or
# sudo apt install amazon-cloudwatch-agent

# 2.2 Create Agent Configuration File
Use the Wizard to generate a config file:

# sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard

The config file is saved as

# /opt/aws/amazon-cloudwatch-agent/bin/config.json

# 2.3 Start the Agent

# sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl \
  -a fetch-config \
  -m ec2 \
  -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json \
  -s

# Step 3: Verify Custom Metrics in CloudWatch
Go to the CloudWatch Console.

Navigate to Metrics > CWAgent > InstanceId.

Confirm you can see mem_used_percent or similar metric.

# Step 4: Create a CloudWatch Alarm
In the CloudWatch Console, go to Alarms > Create Alarm.

Select Metric:

Browse to CWAgent > InstanceId > mem_used_percent.

Choose the memory metric for your EC2 instance.

Set Conditions:

Threshold Type: Static

Condition: Greater than 80 (example threshold)

Period: 5 minutes

Datapoints: e.g., 3 out of 3 (consistency check)

# Create Notification:

Choose or create an SNS topic.

Subscribe an email or Lambda function to receive alerts.

Name and Review:

Give a meaningful name like HighMemoryUsageAlarm.

Review settings and click Create Alarm.


My Work
![image](https://github.com/user-attachments/assets/0ace31f2-3789-443e-b7a6-b5ddd33289ef)
![image](https://github.com/user-attachments/assets/0aa28d7b-be3f-44ef-862a-8f359d1e9c4a)
![image](https://github.com/user-attachments/assets/6665e633-8248-456d-bd2a-a634fba02852)
![image](https://github.com/user-attachments/assets/ed4ccdc6-11dd-4aa9-8e64-3f93b60c8e3f)
![image](https://github.com/user-attachments/assets/31345fca-01c2-4823-be44-6c7edf27b02c)
![image](https://github.com/user-attachments/assets/c63f24a8-6eb8-4cc4-8f4f-7302a937cd82)
![image](https://github.com/user-attachments/assets/0561eff7-85a6-4b50-8e30-92b0d1421e11)
![image](https://github.com/user-attachments/assets/f80be05f-026f-40af-926e-2f1830e96768)
![10](https://github.com/user-attachments/assets/4ba55493-8348-480f-b80c-a5c994a5cf35)
![11](https://github.com/user-attachments/assets/8100d769-5f78-47f8-9de3-08b4efa55055)
![12](https://github.com/user-attachments/assets/d00ceb63-a0c5-4d54-a2b3-95abfe910015)
![13](https://github.com/user-attachments/assets/318aefb3-ddf8-48d3-b81e-71601d8074eb)
![14](https://github.com/user-attachments/assets/9811fa54-43cc-4e13-9072-53d610949211)
![15](https://github.com/user-attachments/assets/9dcbc84e-2972-450e-89f1-7d491dee4000)
![16](https://github.com/user-attachments/assets/e9abc153-9a71-4fee-a409-4ad5bb5d8009)
![19](https://github.com/user-attachments/assets/978d0a5e-1a48-41b3-945a-36220f215711)
![20](https://github.com/user-attachments/assets/c7b7eabe-0818-4199-a648-4f5d5fb07f9d)
![21](https://github.com/user-attachments/assets/05e5a141-a79b-47c0-93f9-954916374a3c)
![22](https://github.com/user-attachments/assets/d77e0edb-4602-4823-bf00-11670abda058)
![24](https://github.com/user-attachments/assets/e7e5b088-be79-440a-9de8-c9bb54f7fc14)
![25](https://github.com/user-attachments/assets/dfc39383-5ade-4058-b5e9-9b44ef5e98ef)
![26](https://github.com/user-attachments/assets/2a209ce4-f293-42f7-ba8a-4b9aa121f7ae)
![27](https://github.com/user-attachments/assets/895d3702-9b71-4a8a-9c1e-3b0a53d479d2)
![28](https://github.com/user-attachments/assets/9687c326-ef1a-48a2-b698-63c239ca7b16)
![29](https://github.com/user-attachments/assets/4478873c-ce23-48e1-bc0c-3a251fd11e49)
![30](https://github.com/user-attachments/assets/2830852a-dbf5-421f-9ed3-b2ce3a1a0b51)
![31](https://github.com/user-attachments/assets/04ae4787-a4a9-453e-9520-17fa3eee5a43)
![32](https://github.com/user-attachments/assets/ef188201-d9e2-4e50-83a1-c4ac8a05b503)
![33](https://github.com/user-attachments/assets/7b7be5ba-d3a7-45ea-a6a4-b3f60861bb17)
![34](https://github.com/user-attachments/assets/68940797-0c90-44f6-86d4-3b22c8cc3cd9)








