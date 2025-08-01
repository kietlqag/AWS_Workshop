# CarRentalWeb - Spring Boot Application

## 🚀 AWS Deployment Guide

### Prerequisites
- AWS Account
- GitHub Repository
- Java 21
- Maven

### Local Development
```bash
# Clone repository
git clone <your-repo-url>
cd CarRentalWeb

# Build project
mvn clean package

# Run locally
mvn spring-boot:run
```

### AWS Deployment Steps

#### 1. Setup RDS Database
1. Go to AWS RDS Console
2. Create MySQL 8.0 database
3. Note down the endpoint, username, and password
4. Create database named `carrentalweb`

#### 2. Setup Elastic Beanstalk
1. Go to AWS Elastic Beanstalk Console
2. Create new application: `CarRentalWeb`
3. Create environment: `carrentalweb-prod`
4. Platform: Java 21 (Corretto)
5. Upload initial JAR file

#### 3. Configure Environment Variables
Add these environment variables in Elastic Beanstalk:
```
RDS_URL=jdbc:mysql://[RDS_ENDPOINT]:3306/carrentalweb?useSSL=false&serverTimezone=Asia/Ho_Chi_Minh
RDS_USERNAME=admin
RDS_PASSWORD=[your-rds-password]
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=quockiet3304@gmail.com
MAIL_PASSWORD=cklfbjtjpaitjmqb
SPRING_PROFILES_ACTIVE=prod
```

#### 4. Setup GitHub Actions
1. Go to GitHub repository Settings
2. Add Secrets:
   - `AWS_ACCESS_KEY_ID`
   - `AWS_SECRET_ACCESS_KEY`
3. Push to main branch to trigger deployment

### Security Groups
- RDS Security Group: Allow MySQL (3306) from Elastic Beanstalk
- Elastic Beanstalk Security Group: Allow HTTP (80) and HTTPS (443)

### Monitoring
- Health Check: `/health`
- Application URL: [Elastic Beanstalk URL]
- CloudWatch Logs: Available in AWS Console

### Troubleshooting
1. Check Elastic Beanstalk logs
2. Verify environment variables
3. Test database connectivity
4. Check security group rules

## 🏗️ Architecture
- **Frontend**: Thymeleaf templates
- **Backend**: Spring Boot 3.4.5
- **Database**: MySQL 8.0 (RDS)
- **Security**: Spring Security
- **Email**: Gmail SMTP
- **Deployment**: AWS Elastic Beanstalk
- **CI/CD**: GitHub Actions 