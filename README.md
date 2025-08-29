# Marksheet Extraction API

![API Status](https://img.shields.io/badge/status-active-success.svg)


A robust REST API service for extracting, parsing, and structuring academic marksheet data from images using OCR technology.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
  - [API Endpoints](#api-endpoints)
  - [Request Examples](#request-examples)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

## 🔍 Overview

The Marksheet Extraction API is designed to automate the process of extracting academic information from marksheet images. It uses advanced OCR (Optical Character Recognition) technology to identify and extract key data points such as student details, course information, and grades, and returns this information in a structured JSON format.

## ✨ Features

- **Image Upload**: Support for uploading marksheet images in various formats (JPEG, PNG, PDF)
- **OCR Processing**: Automated text extraction from uploaded images
- **Data Structuring**: Intelligent parsing of extracted text into organized JSON data
- **Student Information Extraction**: Extract name, roll number, registration number, etc.
- **Grade Extraction**: Process and organize course grades and credit information
- **CGPA/Percentage Calculation**: Automatic calculation of overall performance metrics
- **Secure API**: Authentication and authorization for secure access
- **Error Handling**: Robust error handling with informative messages

## 🛠️ Tech Stack

- **Backend**: Node.js, Express.js
- **OCR Engine**: Tesseract.js
- **Image Processing**: Sharp
- **Authentication**: JWT (JSON Web Tokens)
- **Documentation**: Swagger/OpenAPI
- **Testing**: Jest

## 🚀 Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- Node.js (v14.0.0 or higher)
- npm (v6.0.0 or higher)
- Git

### Installation

1. Clone the repository:

```bash
git clone https://github.com/Aditi7273/marksheet-extraction-api.git
cd marksheet-extraction-api
```

2. Install dependencies:

```bash
npm install
```

3. Set up environment variables:

```bash
cp .env.example .env
```

Edit the `.env` file with your configuration details.

4. Run the application:

```bash
# Development mode
npm run dev

# Production mode
npm start
```

The API will be available at `http://localhost:3000` (or the port specified in your environment variables).

## 📝 Usage

### API Endpoints

| Method | Endpoint | Description | Authentication Required |
|--------|----------|-------------|-------------------------|
| POST | `/api/upload` | Upload marksheet image | Yes |
| GET | `/api/results/:id` | Get extraction results by ID | Yes |
| POST | `/api/auth/register` | Register new user | No |
| POST | `/api/auth/login` | Login user | No |
| GET | `/api/user/profile` | Get user profile | Yes |

### Request Examples

#### Upload a Marksheet

```bash
curl -X POST \
  http://localhost:3000/api/upload \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'Content-Type: multipart/form-data' \
  -F 'marksheet=@/path/to/marksheet.jpg'
```

Response:

```json
{
  "success": true,
  "message": "Marksheet uploaded successfully",
  "data": {
    "id": "12345",
    "status": "processing",
    "uploadedAt": "2025-08-29T17:00:00.000Z"
  }
}
```

#### Get Extraction Results

```bash
curl -X GET \
  http://localhost:3000/api/results/12345 \
  -H 'Authorization: Bearer YOUR_TOKEN'
```

Response:

```json
{
  "success": true,
  "data": {
    "id": "12345",
    "status": "completed",
    "result": {
      "studentName": "John Doe",
      "rollNumber": "CS2021001",
      "institution": "Sample University",
      "courses": [
        {
          "code": "CS101",
          "name": "Introduction to Programming",
          "credits": 4,
          "grade": "A"
        },
        {
          "code": "CS102",
          "name": "Data Structures",
          "credits": 4,
          "grade": "B+"
        }
      ],
      "cgpa": 8.5,
      "percentage": 85.0,
      "totalCredits": 8
    },
    "processedAt": "2025-08-29T17:05:00.000Z"
  }
}
```

## 📚 Documentation

The API is documented using Swagger/OpenAPI. Once the application is running, you can access the interactive documentation at:

```
http://localhost:3000/api-docs
```

This documentation provides detailed information about all available endpoints, request/response formats, and authentication requirements.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request


## 🙏 Acknowledgements

- [Tesseract.js](https://github.com/naptha/tesseract.js) for OCR capabilities
- [Express.js](https://expressjs.com/) for the web framework
- All contributors who have helped shape this project
