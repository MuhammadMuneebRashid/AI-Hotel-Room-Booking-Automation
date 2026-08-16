# 🏨 AI Hotel Room Booking Automation

An AI-powered hotel room booking automation system built with *n8n, Tally Forms, AI Agent, Google Sheets, and Email*.

The system collects customer booking information through a Tally Form, processes the request using an AI Agent, checks existing booking data, and manages the booking workflow automatically.

## 🚀 Workflow

Tally Form
↓
n8n Webhook
↓
Code Node
↓
AI Agent
↓
Edit Fields
↓
Google Sheets
↓
Availability Check
↓
IF Node
↓
├── Room Available
│   ↓
│   Google Sheets → Append Booking
│   ↓
│   Confirmation Email
│
└── Room Unavailable
    ↓
    Suggest Alternative Room
    ↓
    Email Customer

## ✨ Features

- 📝 Customer booking form using Tally Forms
- 🔗 Webhook integration with n8n
- 🤖 AI-powered booking information processing
- 📊 Google Sheets used as a booking database
- 🏨 Room availability checking
- 🔀 Conditional booking logic using IF Node
- 💾 Automatic booking storage
- 📧 Automated confirmation emails
- 📩 Alternative room suggestions when a room is unavailable

## 🛠️ Tech Stack

- n8n
- Tally Forms
- AI Agent
- Google Sheets
- JavaScript
- Webhooks
- Email Automation

## 📋 Booking Information

The system collects:

- Name
- Email
- Phone
- Room Type
- Number of Days
- Check-in Date
- Check-out Date
- Special Request
- Missing Information
- Professional Summary

## 🎯 Purpose

The goal of this project is to automate the hotel booking process and reduce manual work.

Instead of manually checking booking requests, staff can receive structured customer information, check existing bookings, store confirmed reservations, and send automated responses.

## 🔄 Current Status

*Work in Progress*

The main booking workflow is implemented. Room availability and date-overlap validation are currently being refined to prevent duplicate bookings for the same room and dates.

## 📌 Future Improvements

- Improve date-overlap detection
- Support multiple rooms of the same room type
- Automatically find the best alternative room
- Add booking cancellation workflow
- Add booking modification workflow
- Add WhatsApp notifications
- Add payment integration
- Create a hotel booking dashboard

## 👨‍💻 Project Goal

This project was built as part of my journey toward becoming an *AI Automation Specialist*, focusing on real-world business automation using n8n, AI Agents, APIs, webhooks, and cloud-based tools.


<img width="1920" height="1080" alt="Screenshot 2026-08-15 083115" src="https://github.com/user-attachments/assets/9e654bb7-2dc6-4678-8c2c-889350e9a1d1" />

