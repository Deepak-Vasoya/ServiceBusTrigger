# 🚀 Azure Service Bus Trigger Function

![.NET 6](https://img.shields.io/badge/.NET-6.0-blue?style=flat-square&logo=dotnet) 
![Azure Service Bus](https://img.shields.io/badge/Azure-Service_Bus-blue?style=flat-square&logo=microsoft-azure) 
![Azure Functions](https://img.shields.io/badge/Azure-Functions-yellow?style=flat-square&logo=microsoft-azure)

This project demonstrates how to use **Azure Functions** with a **Service Bus Trigger** to process messages asynchronously from an Azure Service Bus queue.

---

## ✨ Features

- 🚦 **Azure Service Bus Trigger**: Automatically processes messages from a queue.
- 📡 **Event-Driven Architecture**: Respond to messages asynchronously.
- ☁️ **Seamless Integration**: Built to work within the Azure cloud ecosystem.
- 🔧 **Cloud-First Design**: Scalable and resilient for high message throughput.

---

## 🏗️ Architecture

+--------------------+         +-------------------+
| Azure Service Bus  | ----->  | Service Bus Trigger |
+--------------------+         +-------------------+
Azure Service Bus: Stores messages in the queue.
Service Bus Trigger: Processes messages and performs actions upon receipt.

## 🛠️ Prerequisites

.NET 6 SDK

Azure Service Bus connection string (Learn more)

Azure Functions Core Tools (Install Guide)


## 📦 Getting Started

Configure Azure Service Bus
Open the local.settings.json file.
Add your Azure Service Bus connection string:


    
    "IsEncrypted": false,
    
    "Values": {
    
        "AzureWebJobsStorage": "UseDevelopmentStorage=true",
        
        "FUNCTIONS_WORKER_RUNTIME": "dotnet",
        
        "ServiceBusConnectionString": "<your-connection-string>",
        
        "QueueName": "<your queue name>"
        
    }  

## 🚀 Running the Project
Start the Azure Functions project locally:

The function will automatically listen for messages on the configured Service Bus queue.

To test, send a message to the Azure Service Bus queue using:

A Web API project (like your Service Bus Demo Web API)
Any Service Bus client SDK (e.g., Azure SDK for .NET)

## 📖 Logs and Monitoring

All logs, including processed messages, can be viewed in the console or the Azure Portal.
Example Log:
[Info] C# ServiceBus queue trigger function processed message: { "CarId": 1, "CarModel": "BMW", "Price": "80000" }

## 📖 Code Overview

    public class Function1
    {
        private readonly ILogger _logger;

        public Function1(ILoggerFactory loggerFactory)
        {
            _logger = loggerFactory.CreateLogger<Function1>();
        }

        [Function("Function1")]
        public void Run([ServiceBusTrigger("servicebus-learning-queue", Connection = "ServiceBusConnectionString")] string myQueueItem)
        {
            _logger.LogInformation($"C# ServiceBus queue trigger function processed message: {myQueueItem}");
        }
    }



## 🛡️ License

This project is licensed under the MIT License.
