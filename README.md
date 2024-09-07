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
    ```sh
    git clone https://github.com/0018akhil/blockchain-price-tracker.git
    cd blockchain-price-tracker
    ```

2. Install dependencies:
    ```sh
    npm install
    ```

3. Create a `.env` file in the root directory with the following content:
    ```env
    DATABASE_URL=postgres://username:password@localhost:5432/blockchain_tracker
    MORALIS_API_KEY=your_moralis_api_key
    SMTP_HOST=your_smtp_host
    SMTP_PORT=your_smtp_port
    SMTP_USER=your_smtp_username
    SMTP_PASS=your_smtp_password
    EMAIL_FROM=your_email_address (email that is verified with SMTP)
    EMAIL_TO=send_email
    ```

4. Start the application:
    ```sh
    npm run start:dev
    ```

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
    ```http
    GET /prices/:chain
    ```
    Where `:chain` is either [`ethereum`](command:_github.copilot.openSymbolFromReferences?%5B%22ethereum%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22a%3A%5C%5Cproject%5C%5Cblockchain-price-tracker%5C%5CREADME.md%22%2C%22_sep%22%3A1%2C%22external%22%3A%22file%3A%2F%2F%2Fa%253A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22path%22%3A%22%2FA%3A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A70%2C%22character%22%3A30%7D%7D%5D%5D "Go to definition") or [`polygon`](command:_github.copilot.openSymbolFromReferences?%5B%22polygon%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22a%3A%5C%5Cproject%5C%5Cblockchain-price-tracker%5C%5CREADME.md%22%2C%22_sep%22%3A1%2C%22external%22%3A%22file%3A%2F%2F%2Fa%253A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22path%22%3A%22%2FA%3A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A70%2C%22character%22%3A44%7D%7D%5D%5D "Go to definition").

2. Set a price alert:
    ```http
    POST /alerts
    ```
    Request body:
    ```json
    {
      "chain": "ethereum",
      "targetPrice": 2000,
      "email": "user@example.com"
    }
    ```

3. Testing:
    Run the test suite with:
    ```sh
    npm run test
    ```

4. Project Structure:
    ```
    blockchain-price-tracker/
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
    ```

5. Environment Variables:
    - [`DATABASE_URL`](command:_github.copilot.openSymbolFromReferences?%5B%22DATABASE_URL%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22a%3A%5C%5Cproject%5C%5Cblockchain-price-tracker%5C%5CREADME.md%22%2C%22_sep%22%3A1%2C%22external%22%3A%22file%3A%2F%2F%2Fa%253A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22path%22%3A%22%2FA%3A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A109%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition"): PostgreSQL connection string
    - [`MORALIS_API_KEY`](command:_github.copilot.openSymbolFromReferences?%5B%22MORALIS_API_KEY%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22a%3A%5C%5Cproject%5C%5Cblockchain-price-tracker%5C%5CREADME.md%22%2C%22_sep%22%3A1%2C%22external%22%3A%22file%3A%2F%2F%2Fa%253A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22path%22%3A%22%2FA%3A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A110%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition"): API key for Moralis
    - [`SMTP_HOST`](command:_github.copilot.openSymbolFromReferences?%5B%22SMTP_HOST%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22a%3A%5C%5Cproject%5C%5Cblockchain-price-tracker%5C%5CREADME.md%22%2C%22_sep%22%3A1%2C%22external%22%3A%22file%3A%2F%2F%2Fa%253A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22path%22%3A%22%2FA%3A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A111%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition"): SMTP server host
    - [`SMTP_PORT`](command:_github.copilot.openSymbolFromReferences?%5B%22SMTP_PORT%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22a%3A%5C%5Cproject%5C%5Cblockchain-price-tracker%5C%5CREADME.md%22%2C%22_sep%22%3A1%2C%22external%22%3A%22file%3A%2F%2F%2Fa%253A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22path%22%3A%22%2FA%3A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A112%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition"): SMTP server port
    - [`SMTP_USER`](command:_github.copilot.openSymbolFromReferences?%5B%22SMTP_USER%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22a%3A%5C%5Cproject%5C%5Cblockchain-price-tracker%5C%5CREADME.md%22%2C%22_sep%22%3A1%2C%22external%22%3A%22file%3A%2F%2F%2Fa%253A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22path%22%3A%22%2FA%3A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A113%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition"): SMTP username
    - [`SMTP_PASS`](command:_github.copilot.openSymbolFromReferences?%5B%22SMTP_PASS%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22a%3A%5C%5Cproject%5C%5Cblockchain-price-tracker%5C%5CREADME.md%22%2C%22_sep%22%3A1%2C%22external%22%3A%22file%3A%2F%2F%2Fa%253A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22path%22%3A%22%2FA%3A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A114%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition"): SMTP password
    - [`EMAIL_FROM`](command:_github.copilot.openSymbolFromReferences?%5B%22EMAIL_FROM%22%2C%5B%7B%22uri%22%3A%7B%22%24mid%22%3A1%2C%22fsPath%22%3A%22a%3A%5C%5Cproject%5C%5Cblockchain-price-tracker%5C%5CREADME.md%22%2C%22_sep%22%3A1%2C%22external%22%3A%22file%3A%2F%2F%2Fa%253A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22path%22%3A%22%2FA%3A%2Fproject%2Fblockchain-price-tracker%2FREADME.md%22%2C%22scheme%22%3A%22file%22%7D%2C%22pos%22%3A%7B%22line%22%3A115%2C%22character%22%3A0%7D%7D%5D%5D "Go to definition"): Email address to send alerts from

This README provides a comprehensive overview of your project, including how to set it up both for local development and using Docker, how to use the API, the project structure, and important environment variables. You may want to adjust some details based on your specific implementation or add more information as needed.