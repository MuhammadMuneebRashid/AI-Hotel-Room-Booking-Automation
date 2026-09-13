🏨 AI Hotel Room Booking Automation

An AI-powered hotel room booking automation system built with **n8n, Tally Forms, Google Sheets, JavaScript, AI Agents, and Email Automation**.

This project automates the initial hotel booking request process by collecting customer information through a Tally Form, analyzing the request with an AI Agent, checking existing reservations in Google Sheets, validating room availability based on room type and booking dates, storing confirmed bookings, and sending automated email responses.

## 🚀 Workflow

```text
Tally Form
    ↓
n8n Webhook
    ↓
JavaScript Data Extraction
    ↓
AI Agent
    ↓
Request Classification
    │
    ├── Booking
    ├── Availability
    ├── Cancellation
    └── Inquiry
    ↓
Structured Customer Information
    ↓
Google Sheets – Existing Bookings
    ↓
JavaScript Availability Check
    ↓
IF Node
    │
    ├── Room Available
    │      ↓
    │   Save Booking to Google Sheets
    │      ↓
    │   Generate Confirmation Email
    │      ↓
    │   Send Email to Customer
    │
    └── Room Unavailable
           ↓
       Generate Unavailability Email
           ↓
       Send Email to Customer
```

## ✨ Key Features

* 📝 Customer information collection through Tally Forms
* 🔗 Webhook integration with n8n
* 🤖 AI-powered request analysis
* 🧠 AI classification of customer requests
* 📋 Structured extraction of booking information
* ⚠️ Automatic detection of missing information
* 📊 Google Sheets used as a booking database
* 🔎 Existing booking data retrieval
* 🏨 Room availability validation
* 📅 Check-in and check-out date overlap detection
* 🔀 Conditional workflow using IF and Switch nodes
* 💾 Automatic storage of confirmed bookings
* 📧 Automated booking confirmation emails
* 📩 Automated room-unavailability emails
* ⚡ End-to-end workflow automation

## 🧠 AI-Powered Request Analysis

The AI Agent analyzes the submitted customer information and determines the type of request.

Currently, the workflow classifies requests into:

* **Booking**
* **Availability**
* **Cancellation**
* **Inquiry**

The AI Agent also:

* Extracts customer information
* Identifies missing information
* Reviews special requests
* Creates a professional customer summary
* Determines the type of hotel-related request

The AI output is structured using an **n8n Structured Output Parser** so that the following information can be used reliably by the rest of the workflow.

## 📋 Customer Information

The workflow processes the following information:

* Full Name
* Email
* Phone
* Check-in Date
* Check-out Date
* Room Type
* Number of Guests
* Special Request
* Missing Information
* Professional Summary
* Request Type

## 🏨 Room Availability Checking

For booking requests, the workflow retrieves existing reservation records from Google Sheets.

A JavaScript Code Node then checks:

1. Requested room type
2. Requested check-in date
3. Requested check-out date
4. Existing room type
5. Existing booking dates
6. Date overlap between the requested and existing booking

The workflow uses date-overlap logic to determine whether an existing reservation conflicts with the requested stay.

Conceptually, a conflict exists when:

```text
Existing Check-in < Requested Check-out
AND
Existing Check-out > Requested Check-in
```

If a conflict is detected:

```text
Room is not available
```

Otherwise:

```text
Room is available
```

## 🔀 Booking Decision Logic

After the availability check, the workflow uses an **IF Node**.

### ✅ Room Available

If the requested room is available:

```text
Availability Check
      ↓
Room Available
      ↓
Prepare Booking Data
      ↓
Append Booking to Google Sheets
      ↓
AI Generates Confirmation Email
      ↓
Gmail Sends Email
```

The confirmed booking information is stored in Google Sheets before the confirmation email is generated.

### ❌ Room Unavailable

If the requested room is already occupied during the requested dates:

```text
Availability Check
      ↓
Room Not Available
      ↓
AI Generates Professional Unavailability Email
      ↓
Gmail Sends Email
```

The customer receives an automated email explaining that the requested room is unavailable for the requested dates.

## 📊 Google Sheets Integration

Google Sheets is used as the booking database.

The workflow uses Google Sheets for:

* Reading existing booking records
* Checking room availability
* Detecting booking conflicts
* Storing confirmed reservations

Confirmed bookings are appended to the spreadsheet only after the availability check confirms that there is no conflicting reservation.

## 📧 Automated Email System

The workflow uses Gmail for automated customer communication.

### Booking Confirmation

When a room is available, an AI Agent generates a professional confirmation email using the available customer and booking information.

The email includes:

* Customer name
* Check-in date
* Check-out date
* Booking confirmation message

### Room Unavailability

When a room is unavailable, another AI Agent generates a professional email informing the customer that the requested room cannot be booked for the selected dates.

## 🧩 n8n Nodes Used

The workflow includes:

* **Webhook Node**
* **Code Node**
* **AI Agent**
* **Structured Output Parser**
* **Switch Node**
* **Set / Edit Fields Nodes**
* **Google Sheets**
* **IF Node**
* **Gmail**
* **Google Gemini Chat Model**

## 🛠️ Tech Stack

| Technology        | Purpose                                          |
| ----------------- | ------------------------------------------------ |
| **n8n**           | Workflow automation                              |
| **Tally Forms**   | Customer information collection                  |
| **JavaScript**    | Data extraction and availability logic           |
| **Google Gemini** | AI-powered request analysis and email generation |
| **Google Sheets** | Booking database                                 |
| **Gmail**         | Automated customer communication                 |
| **Webhooks**      | Form-to-workflow integration                     |

## 🔄 Current Workflow Status

**Work in Progress**

The core booking workflow is implemented.

Currently, the system can:

* Receive customer requests
* Extract booking information
* Analyze requests using AI
* Detect missing information
* Classify requests
* Retrieve existing bookings
* Check room/date conflicts
* Determine room availability
* Store available bookings
* Send confirmation emails
* Send unavailability emails

Some request types, including cancellation and inquiry handling, are currently classified by the AI but do not yet have complete dedicated processing branches.

## ⚠️ Current Limitations

The current version has the following limitations:

* Multiple physical rooms of the same room type are not yet managed separately.
* Availability is currently checked based on room type and date overlap.
* Cancellation processing is not fully automated yet.
* Inquiry requests do not yet have a dedicated workflow branch.
* Alternative room selection is not automatically implemented.
* Payment processing is not currently included.
* Booking modification is not currently implemented.

## 🚀 Future Improvements

Planned improvements include:

* 🏨 Support multiple rooms of the same room type
* 🔢 Add room numbers and unique booking IDs
* 🔄 Implement complete booking cancellation workflow
* ✏️ Add booking modification workflow
* 💡 Automatically suggest available alternative rooms
* 📱 Add WhatsApp notifications
* 💳 Integrate online payment processing
* 📊 Build a hotel management dashboard
* 🔐 Add stronger booking validation
* 📅 Improve date and timezone handling
* 🧾 Generate automated booking invoices
* 📈 Add booking analytics and reporting

## 🎯 Project Goal

The goal of this project is to demonstrate how **AI and workflow automation can be used to automate real-world hotel booking operations**.

Instead of manually reviewing every customer request, hotel staff can use an automated workflow that:

```text
Collects Customer Data
        ↓
Analyzes the Request
        ↓
Validates Information
        ↓
Checks Existing Bookings
        ↓
Checks Room Availability
        ↓
Stores Confirmed Booking
        ↓
Communicates With Customer
```

This reduces repetitive manual work and creates a more structured and efficient booking process.

## 👨‍💻 Project Objective

This project was developed as part of my journey toward becoming an **AI Automation Specialist**.

It focuses on practical implementation of:

* AI Agents
* Workflow Automation
* Webhooks
* APIs and integrations
* JavaScript automation
* Google Sheets database workflows
* Automated email communication
* Business process automation

The project demonstrates how multiple automation tools can be connected to create a practical **AI-powered hotel booking workflow**.

##Author

Muneeb

<img width="1920" height="1080" alt="99" src="https://github.com/user-attachments/assets/9b77375a-ac09-47ef-8a2d-a4cb1dcc12a6" />



https://github.com/user-attachments/assets/25b9dc3f-6513-42a3-ba29-27780f0e92c8



If you like this project then give it a star⭐ on GitHub.

