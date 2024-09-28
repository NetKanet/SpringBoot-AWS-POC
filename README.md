
# SpringBoot-AWS-POC

## Overview

SpringBoot-AWS-POC is a Proof of Concept (POC) project that demonstrates how to integrate
AWS services such as S3 (Simple Storage Service), RDS (Relational Database Service),
SNS (Simple Notification Service), and SQS (Simple Queue Service) into a Java Spring Boot application.
This project provides examples of uploading files to S3, interacting with a MySQL database hosted on RDS,
sending messages to an SQS queue, and publishing notifications via SNS.

## Features

- **AWS S3**: Upload and download files to/from an S3 bucket.
- **AWS RDS**: Perform CRUD operations on a MySQL database hosted on AWS RDS.
- **AWS SQS**: Send and receive messages to/from an AWS SQS queue.
- **AWS SNS**: Publish messages to an SNS topic.

## Technologies Used

- **Java 17**: The main programming language.
- **Spring Boot 3.x**: For building the REST API.
- **AWS SDK**: For interacting with AWS services.
- **Spring Data JPA**: For database operations.
- **MySQL**: Used as the database, hosted on AWS RDS.
- **Maven**: Dependency management and build automation.

## Prerequisites

- Java 17
- Maven 3.8+
- AWS CLI (optional for configuring credentials)
- AWS Account (for S3, RDS, SQS, SNS)
- MySQL client (for accessing the RDS database)

### AWS Setup

1. **S3 Bucket**: Create an S3 bucket for file storage.
2. **RDS Instance**: Set up a MySQL instance on AWS RDS.
3. **SQS Queue**: Create an SQS queue for messaging.
4. **SNS Topic**: Create an SNS topic for message publishing.

## How to Run the Project

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/SpringBoot-AWS-POC.git
   cd SpringBoot-AWS-POC
   ```

2. **Configure AWS Credentials**:
   Make sure your AWS credentials are set up in `~/.aws/credentials`:
   ```ini
   [default]
   aws_access_key_id = YOUR_ACCESS_KEY
   aws_secret_access_key = YOUR_SECRET_KEY
   region = YOUR_REGION
   ```

3. **Update Database Configuration**:
   Edit the `src/main/resources/application.properties` file with your RDS information:
   ```properties
   spring.datasource.url=jdbc:mysql://<rds-endpoint>:3306/mydb
   spring.datasource.username=myuser
   spring.datasource.password=mypassword
   ```

4. **Build and run the application**:
   ```bash
   mvn clean install
   mvn spring-boot:run
   ```

## API Endpoints

| Endpoint          | Method | Description                        |
|-------------------|--------|------------------------------------|
| `/api/upload`     | POST   | Uploads a file to the S3 bucket    |
| `/api/sqs/send`   | POST   | Sends a message to the SQS queue   |
| `/api/sns/publish`| POST   | Publishes a message to an SNS topic|

## Project Structure

```
SpringBoot-AWS-POC/
│
├── src/
│   ├── main/
│   │   ├── java/com/example/aws/
│   │   │   ├── controller/        # REST controllers
│   │   │   ├── service/           # Services for AWS interactions
│   │   │   └── model/             # Entities for RDS
│   │   └── resources/
│   │       └── application.properties  # Configuration
├── pom.xml                         # Maven dependencies
└── README.md                       # Project documentation
```