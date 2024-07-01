# JSON API with OpenAI and Zod

This repository contains a JSON API built with Next.js that accepts any input data and returns all the information in JSON format. The API leverages the OpenAI API for processing and the Zod library for schema validation.

## Features

- Accepts JSON data via POST requests.
- Utilizes the OpenAI API to process the input data.
- Validates and transforms the input data into the desired JSON format using Zod.
- Implements retry logic for robust error handling.

## Prerequisites

- Node.js (>= 14.x)
- npm or yarn
- OpenAI API key

## Getting Started

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/Anonymous096/Json-API.git
   cd Json-API
   ```

2. Install all dependencies:
   ```bash
   npm install
   # or
   yarn install
   ```
3. Create a .env.local file in the root directory and add your OpenAI API key:
   ```bash
   OPENAI_API_KEY=your_openai_api_key
   ```

### Running the Development Server

Start the Next.js development server:

    npm run dev
    # or
    yarn dev

The server will start on http://localhost:3000.

## API Endpoint

### POST /api/json

This endpoint accepts a JSON object and returns the processed JSON data.

#### Important Note

This project is just an API and does not include a user interface. It will not run in the browser. It is designed to be used with API platforms such as Postman or Bruno.

### Request

- Method: POST

- URL: `http://localhost:3000/api/json`

- Headers:

  - Content-Type: `application/json`

- Body: Select raw and set the type to JSON. Provide a sample input JSON, such as:
  ```bash
  {
  "data": "my name is sam",
  "format": {
      "name": {"type": "string"}
      }
  }
  ```

### Response

- Status: 200 OK
- Body: JSON object containing the processed data.

### Example Request in Postman or Bruno

1. Set the request method to POST.
2. Set the request URL to `http://localhost:3000/api/process-json`.
3. Add the `Content-Type: application/json header`.
4. In the body, select raw and set the type to JSON.
5. Provide a sample input JSON:
   ```bash
   {
   "data": "my name is sam",
   "format": {
       "name": {"type": "string"}
       }
   }
   ```

### Example Response

    {
    "name": "sam"
    }

### Code Explanation

- `pages/api/process-json.ts`: The API route handler that processes the input data and returns the JSON response.
- `lib/openai.ts`: Contains the configuration and setup for the OpenAI API client.
- `example.ts`: Provides example prompt and answer data for the OpenAI API.

### Core Logic

- The API endpoint parses the input data and format.
- It dynamically generates a Zod schema based on the provided format.
- It sends a request to the OpenAI API with the input data and expected format.
- It validates and transforms the response using the dynamically generated Zod schema.
- It returns the validated JSON data as the response.

### Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Acknowledgements

- [OpenAI](https://openai.com/) for providing the API.
- [Zod](https://zod.dev/) for the powerful schema validation library.
- [Next.js](https://nextjs.org/) for the robust framework.
