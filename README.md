
# 🌦️ AWS Weather Report Application

A **serverless Weather Report Application** built using **AWS services** that provides real-time weather information for any city. The application fetches live data from the **OpenWeather API**, stores it in **Amazon DynamoDB**, and serves users through a scalable, cloud-native architecture.

🔗 **Live Demo:**
👉 [https://staging.d3ss57sm9nebgk.amplifyapp.com](https://staging.d3ss57sm9nebgk.amplifyapp.com)

---

## 📌 Project Overview

This application allows users to enter a city name and instantly view:

* 🌡️ Current temperature
* 🌤️ Weather description
* ⏱️ Timestamp of the request

All weather requests are securely stored in a DynamoDB table for persistence and future analysis.

The project follows a **Serverless Architecture**, ensuring:

* High scalability
* Low operational cost
* Minimal maintenance

---

## 🛠️ Technical Requirements

* AWS Account
* OpenWeather API Key
* JavaScript / Node.js
* AWS Amplify CLI
* AWS Lambda & API Gateway
* Amazon DynamoDB
* IAM Roles & Policies
* Development Environment (VS Code)

---

## 🧩 Architecture Pattern

* **Serverless Architecture**
* **RESTful API Design**

---

## 🏗️ Architecture Flow

1. **Frontend (AWS Amplify)**
   User enters a city name via a web interface.

2. **API Gateway**
   Receives HTTP requests and forwards them to Lambda.

3. **AWS Lambda**
   Fetches live weather data from OpenWeather API.

4. **Amazon DynamoDB**
   Stores weather details (city, temperature, description, timestamp).

5. **CloudWatch Logs**
   Monitors execution, logs errors, and tracks API usage.

---

## ☁️ AWS Services Used

| Service             | Purpose                       |
| ------------------- | ----------------------------- |
| **AWS Lambda**      | Backend logic execution       |
| **API Gateway**     | REST API exposure             |
| **AWS Amplify**     | Frontend hosting & deployment |
| **Amazon DynamoDB** | NoSQL data storage            |
| **CloudWatch Logs** | Monitoring & debugging        |
| **IAM**             | Secure permissions management |

---

## 🚀 Live Application

You can test the application here:
👉 [https://staging.d3ss57sm9nebgk.amplifyapp.com](https://staging.d3ss57sm9nebgk.amplifyapp.com)

---

## 🧪 Features

* Real-time weather data retrieval
* Serverless backend
* Persistent data storage
* Scalable and cost-efficient architecture
* Secure AWS service communication
* CORS-enabled frontend-backend integration

---

## 🧑‍💻 Backend Code (AWS Lambda – Node.js)

```javascript
import httpsModule from 'https';
import { DynamoDBClient, PutItemCommand } from '@aws-sdk/client-dynamodb';

const dynamoDB = new DynamoDBClient({ region: 'us-east-1' });

export const handler = async (event) => {
    const city = event.queryStringParameters?.city || 'New York';
    const apiKey = 'YOUR_API_KEY';
    const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;

    try {
        const weatherData = await fetchWeatherData(url);
        await saveToDynamoDB(city, weatherData);

        return {
            statusCode: 200,
            body: JSON.stringify({
                message: 'Weather data fetched and saved successfully',
                data: weatherData,
            }),
        };
    } catch (error) {
        return {
            statusCode: 500,
            body: JSON.stringify({ message: 'Error fetching weather data' }),
        };
    }
};
```

---

## 🔮 Future Enhancements

* Improved error handling and user feedback
* Additional weather parameters (humidity, wind speed)
* Scheduled weather updates using AWS EventBridge
* Mobile-friendly UI or mobile app version

---

## 📄 Summary

This **AWS Weather Report Application** demonstrates a complete **end-to-end serverless solution**, integrating frontend hosting, API management, backend processing, and database storage. The architecture is scalable, efficient, and production-ready, making it an excellent real-world cloud project for learning and showcasing AWS skills.

---

### 👨‍💻 Author

**Vamsi Krishna Mohan Kommaraju**
B.Tech IT | VIT Vellore

Connect me on LinkedIn: https://www.linkedin.com/in/vamsikommaraju/

---


