# Baileys API

Baileys is a simple, fast and easy to use WhatsApp Web API written in TypeScript. It is designed to be simple to use and is optimized for usage in Node.js.

An implementation of [@WhiskeySockets/Baileys](https://github.com/WhiskeySockets/Baileys) as a simple REST API with multiple device support

Project continued from [@ookamiiixd/baileys-api](https://github.com/ookamiiixd/baileys-api/)

## Requirements

- NodeJS version 18.19.0 or higher
- Prisma [supported databases](https://www.prisma.io/docs/reference/database-reference/supported-databases). Tested on MySQL and PostgreSQL

## Installation

1. Download or clone this repo. If you want to skip the build step, you can download the release (file with the `baileys-api.tgz` name pattern) from the release page
2. Enter to the project directory
3. Install the dependencies

```sh
npm install
npm run postinstall
```

4. Build the project using the `build` script

```sh
npm run build
```

You can skip this part if you're using the prebuilt one from the release page

## Setup

1. Copy the `.env.example` file and rename it into `.env`, then update your [connection url](https://www.prisma.io/docs/reference/database-reference/connection-urls) in the `DATABASE_URL` field
1. Update your [provider](https://www.prisma.io/docs/reference/api-reference/prisma-schema-reference#fields) in the `prisma/schema.prisma` file if you're using database other than MySQL
1. Run your [migration](https://www.prisma.io/docs/reference/api-reference/command-reference#prisma-migrate)

```sh
npx prisma migrate (dev|deploy)
```

or push the schema

```sh
npx prisma db push
```

Don't forget to always re-run those whenever there's a change on the `prisma/schema.prisma` file

## `.env` Configurations

```env
# Listening Host
HOST="localhost"

# Listening Port
PORT="3000"

# API Key (for Authorization Header)
API_KEY="" # Leave it empty if you don't want

# Name browser bot
NAME_BOT_BROWSER="Whatsapp Bot"

# Project Mode (development|production)
NODE_ENV="development"

# Database Connection URL
DATABASE_URL="mysql://root:12345@localhost:3306/baileys_api"

# Reconnect Interval (in Milliseconds)
RECONNECT_INTERVAL="5000"

# Maximum Reconnect Attempts
MAX_RECONNECT_RETRIES="5"

# Maximum SSE QR Generation Attempts
SSE_MAX_QR_GENERATION="10"

# Pino Logger Level
LOG_LEVEL="warn"
```

## Usage

1. Make sure you have completed the **Installation** and **Setup** step
1. You can then start the app using the `dev` for development and `start` script for production

```sh
# Development
npm run dev

# Production
npm run start
```

1. Now the endpoint should be available according to your environment variables configuration. Default is at `http://localhost:3000`

## API Docs

The API Documentation can fork **Postman Collection** in your workspace Postman

[<img src="https://run.pstmn.io/button.svg" alt="Run In Postman" style="width: 128px; height: 32px;">](https://app.getpostman.com/run-collection/14456337-fb3349c5-de0e-40ec-b909-3922f4a95b7a?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D14456337-fb3349c5-de0e-40ec-b909-3922f4a95b7a%26entityType%3Dcollection%26workspaceId%3Dfbd81f05-e0e1-42cb-b893-60063cf8bcd1)

## Notes

- I only provide a simple authentication method, please modify according to your own needs.

## TODO

- [ ] Move ExpressJS to HonoJS
- [ ] Add endpoint for connecting native mobile API
- [ ] Add endpoint for Groups (such as create, change information groups, etc)

## Notice




# PhoneNumberRule.php

## Description
The `PhoneNumberRule` class is a custom validation rule in Laravel that validates phone numbers based on the country code provided. It checks if the phone number matches the specific pattern defined for each country.

## Usage
To use the `PhoneNumberRule`, create an instance of the class and pass the country code as a parameter to the constructor. Then, you can use this rule in your validation logic to validate phone numbers.

```php
use App\Rules\PhoneNumberRule;

$rules = [
    'phone_number' => ['required', new PhoneNumberRule('country_code')],
];

// Implement your validation logic using the PhoneNumberRule
```

## Parameters
- `$countryCode`: The country code for which the phone number validation will be applied.

## Return Values
The `validate` method does not return any value but uses a closure function to handle validation failures.

## Additional Notes
- The `validate` method takes three parameters: `$attribute` (the name of the attribute being validated), `$value` (the value of the attribute), and `$fail` (a closure function to handle validation failures).
- The class contains an array of patterns for different countries along with their respective regular expressions for validating phone numbers.
- It removes any leading plus sign from both the provided country code and phone number before performing validation.
- If the provided country code is not found in the predefined patterns, it fails with a message indicating that the country code is invalid.
- If the phone number does not match the pattern for the specified country, it fails with a message stating that the phone number is not valid for the selected country.
This project is intended for learning purpose only, don't use it for spamming or any activities that's prohibited by **WhatsApp**
