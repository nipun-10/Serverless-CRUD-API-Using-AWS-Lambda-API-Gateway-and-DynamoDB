📌 <h2><b>SERVERLESS CRUD API USING AWS LAMBDA, API GATEWAY & DYNAMODB</b></h2>


This project demonstrates a fully serverless backend built using **AWS Lambda**, **API Gateway**, and **DynamoDB**. The solution follows event-driven design, is infinitely scalable, and requires zero server management. It provides CRUD functionality through RESTful endpoints to create, retrieve, update, and delete users.

---

⭐ **Project Summary (Using STAR Method)**

**S – Situation**

I wanted to gain hands-on experience with serverless architecture and build a backend service that required **no server provisioning**, could **scale automatically**, and operated on a **pay-per-use** model.

 **T – Task**

My goal was to design and deploy a complete **CRUD API** using fully managed AWS components. The system needed secure access controls, clean routing, logging, and error handling.

 **A – Action**

* Designed CRUD logic in **AWS Lambda (Python)**
* Created REST endpoints using **API Gateway HTTP APIs**
* Used **DynamoDB** as a NoSQL database for user data
* Configured **IAM Roles** to securely allow Lambda → DynamoDB access
* Enabled **CloudWatch Logs** for debugging and monitoring
* Added validation and structured responses
* Tested all endpoints using **Postman** and **cURL**
* Implemented error handling & logging across functions

 **R – Result**

The outcome was a **100% serverless, auto-scaling, cost-efficient backend API**.
It enhanced my understanding of:

* Serverless compute
* AWS event-driven design
* DynamoDB NoSQL modeling
* API Gateway integrations
* Security & observability best practices

---

# ## 🏗️ **Architecture Overview**


![Architecture Diagram](https://raw.githubusercontent.com/nipun-10/Serverless-CRUD-API-Using-AWS-Lambda-API-Gateway-and-DynamoDB/main/Architecture_Diagram.png)


---

# ## 🛠️ **Tech Stack**

| Component                  | Purpose                         |
| -------------------------- | ------------------------------- |
| **AWS Lambda**             | Compute backend running Python  |
| **API Gateway (HTTP API)** | RESTful routing                 |
| **DynamoDB**               | NoSQL database for user records |
| **IAM**                    | Secure permissions              |
| **CloudWatch**             | Logs & monitoring               |

---

🚀 **Setup Guide – Step-by-Step**

---

 ✅ **Step 1: Create a DynamoDB Table**

1. Open the AWS Console
2. Navigate to **DynamoDB → Tables → Create Table**
3. Enter table details:

   * **Table Name:** `Users`
   * **Primary Key:** `userId` (String)
4. Click **Create Table**

![DynamoDB Creation](https://raw.githubusercontent.com/nipun-10/Serverless-CRUD-API-Using-AWS-Lambda-API-Gateway-and-DynamoDB/main/DynamoDB_creation.png)
---

✅ **Step 2: Create a Python Lambda Function**

1. Open **AWS Lambda**
2. Click **Create Function → Author from Scratch**
3. **Function name:** `UserCrudAPI`
4. **Runtime:** Python 3.x
5. Click **Create Function**

![Lambda Function](https://raw.githubusercontent.com/nipun-10/Serverless-CRUD-API-Using-AWS-Lambda-API-Gateway-and-DynamoDB/main/Lambda_function.png)
### **Add DynamoDB Permissions**

1. Open **Configuration → Permissions**
2. Click the IAM role name
3. Add this inline policy that allow
        "dynamodb:PutItem",
        "dynamodb:GetItem",
        "dynamodb:Scan",
        "dynamodb:UpdateItem",
        "dynamodb:DeleteItem"

---

✅ **Step 3: Add Lambda Code (CRUD Operations)**

Add the Python code inside the Lambda function That perform CURD Operations:

![User CRUD API](https://raw.githubusercontent.com/nipun-10/Serverless-CRUD-API-Using-AWS-Lambda-API-Gateway-and-DynamoDB/main/User_CURD_API.png)

---

✅ **Step 4: Create API Gateway**

1. Open **API Gateway**
2. Select **Create API → HTTP API → Build**
3. API Name → `UserAPI`
4. Add the following routes:

| Method | Path  |
| ------ | ----- |
| POST   | /user |
| GET    | /user |
| PUT    | /user |
| DELETE | /user |

5. Attach integration:
   **Lambda → UserCrudAPI**
![Edit Item](https://raw.githubusercontent.com/nipun-10/Serverless-CRUD-API-Using-AWS-Lambda-API-Gateway-and-DynamoDB/main/Edit_item.png)

---

✅ **Step 5: Deploy the API**

1. Open **Deployments**
2. Click **Create Deployment**
3. Stage name → `prod`
4. Click **Deploy**
5. Copy your **Invoke URL**

Example:

```
https://xyz123.execute-api.us-east-1.amazonaws.com
```

---

🧪 **Testing the API Using cURL**

---

✅ Windows CMD (uses ^ for multiline commands)

### **1. Create User (POST)**

```cmd
curl -X POST ^
https://your-api.execute-api.amazonaws.com/user ^
-H "Content-Type: application/json" ^
-d "{ \"userId\": \"123\", \"name\": \"John Doe\", \"email\": \"john.doe@example.com\" }"
```

### **2. Get User (GET)**

```cmd
curl -X GET "https://your-api.execute-api.amazonaws.com/user?userId=123"
```

### **3. Update User (PUT)**

```cmd
curl -X PUT ^
https://your-api.execute-api.amazonaws.com/user ^
-H "Content-Type: application/json" ^
-d "{ \"userId\": \"123\", \"name\": \"John Doe Updated\", \"email\": \"john.updated@example.com\" }"
```

### **4. Delete User (DELETE)**

```cmd
curl -X DELETE "https://your-api.execute-api.amazonaws.com/user?userId=123"
```

---

# ## ✅ Linux / macOS

### **1. Create User (POST)**

```bash
curl -X POST \
https://your-api.execute-api.amazonaws.com/user \
-H "Content-Type: application/json" \
-d '{ "userId": "123", "name": "John Doe", "email": "john.doe@example.com" }'
```

### **2. Get User**

```bash
curl -X GET 'https://your-api.execute-api.amazonaws.com/user?userId=123'
```

### **3. Update User**

```bash
curl -X PUT \
https://your-api.execute-api.amazonaws.com/user \
-H "Content-Type: application/json" \
-d '{ "userId": "123", "name": "John Doe Updated", "email": "john.updated@example.com" }'
```

### **4. Delete User**

```bash
curl -X DELETE 'https://your-api.execute-api.amazonaws.com/user?userId=123'
```

---

📌 Key Learning Outcomes

* Building event-driven serverless systems
* Designing REST APIs with API Gateway
* CRUD implementation using Lambda & Python
* DynamoDB NoSQL table design
* IAM security for least-privilege access
* Logging & monitoring with CloudWatch
* Testing APIs using Postman & cURL

---

📚 Future Enhancements

* Add Authentication using Cognito
* Add custom domain + HTTPS via Route 53 & ACM
* Add schema validation using API Gateway models
* Add CI/CD using GitHub Actions or AWS CodePipeline
* Implement Unit Tests using pytest

---

🤝 Get In Touch
I am open to discussing cloud architecture, DevOps practices, and potential opportunities.

Email: nipuntyagi983@gmail.com
LinkedIn: https://www.linkedin.com/in/nipun-bhardwaj-6312a9265
GitHub: https://github.com/nipun-10
