# Blockchain Price Tracker

This project is a NestJS-based API for tracking blockchain prices and setting price alerts. It supports Ethereum and Polygon chains, fetches prices every 5 minutes, and allows users to set email alerts for specific price targets.

## Features

- Track prices of Ethereum and Polygon every 5 minutes
- Set email alerts for specific price targets
- Get hourly price data for the last 24 hours
- Dockerized for easy deployment
- Swagger API documentation

## Prerequisites

- Node.js (v14 or later)
- npm
- Docker and Docker Compose (for containerized deployment)
- PostgreSQL (if running without Docker)

## Setup

### Local Development

1. Clone the repository:
git clone https://github.com/0018akhil/blockchain-price-tracker.git
cd blockchain-price-tracker

2. Install dependencies:
npm install

3. Create a `.env` file in the root directory with the following content:
DATABASE_URL=postgres://username:password@localhost:5432/blockchain_tracker
MORALIS_API_KEY=your_moralis_api_key
SMTP_HOST=your_smtp_host
SMTP_PORT=your_smtp_port
SMTP_USER=your_smtp_username
SMTP_PASS=your_smtp_password
EMAIL_FROM=your_email_address (email that is verified with SMTP)
EMAIL_TO=send_email

4. Start the application:
npm run start:dev

### Docker Deployment

1. Make sure Docker and Docker Compose are installed on your system.

2. Create a `.env` file as described in the Local Development section.

3. Build and start the Docker containers:
docker-compose up --build
Copy
The application will be available at `http://localhost:3000`.

## API Usage

After starting the application, you can access the Swagger UI at `http://localhost:3000/api` for interactive API documentation.

### Endpoints

1. Get hourly prices:
GET /prices/:chain
CopyWhere `:chain` is either `ethereum` or `polygon`.

2. Set a price alert:
POST /alerts
CopyRequest body:
```json
{
  "chain": "ethereum",
  "targetPrice": 2000,
  "email": "user@example.com"
}
Testing
Run the test suite with:
Copynpm run test
Project Structure
Copyblockchain-price-tracker/
├── src/
│   ├── main.ts
│   ├── app.module.ts
│   ├── price/
│   │   ├── price.module.ts
│   │   ├── price.service.ts
│   │   ├── price.controller.ts
│   │   └── price.entity.ts
│   ├── alert/
│   │   ├── alert.module.ts
│   │   ├── alert.service.ts
│   │   ├── alert.controller.ts
│   │   └── alert.entity.ts
│   └── email/
│       ├── email.module.ts
│       └── email.service.ts
├── Dockerfile
├── docker-compose.yml
├── .env
└── package.json

Environment Variables

DATABASE_URL: PostgreSQL connection string
MORALIS_API_KEY: API key for Moralis
SMTP_HOST: SMTP server host
SMTP_PORT: SMTP server port
SMTP_USER: SMTP username
SMTP_PASS: SMTP password
EMAIL_FROM: Email address to send alerts from

This README provides a comprehensive overview of your project, including how to set it up both for local development and using Docker, how to use the API, the project structure, and important environment variables. You may want to adjust some details based on your specific implementation or add more information as needed.