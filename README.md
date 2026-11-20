# Campus Mess Feedback System

A simple and useful web application that helps students view the daily campus mess menu and submit feedback about meals.

Students can select a date, view breakfast, lunch, and dinner menus, rate meals, and leave comments. The mess committee can update the daily menu through an admin page.

## Live Project

https://main.d3ab03gpkxzlk0.amplifyapp.com/

## Features

- View the mess menu for a selected date
- View breakfast, lunch, and dinner details
- Submit meal feedback with a rating
- Add optional comments and student name
- View total feedback and average rating
- Update the menu through the admin page
- Store menus and feedback in Amazon DynamoDB
- Serverless backend using AWS Lambda and API Gateway

## AWS Services Used

| AWS Service | Purpose |
|---|---|
| AWS Amplify Hosting | Hosts the static website |
| Amazon API Gateway | Provides the REST API endpoints |
| AWS Lambda | Handles menu and feedback requests |
| Amazon DynamoDB | Stores menu and feedback data |

## Project Structure

```text
campus-mess-feedback/
├── index.html       # Student-facing website
├── admin.html       # Admin page to update menu
├── 404.html         # Custom error page
└── README.md        # Project documentation
```

## How It Works

1. The website is hosted using AWS Amplify.
2. When a student selects a date, the website calls the API Gateway endpoint.
3. API Gateway sends the request to AWS Lambda.
4. Lambda reads or writes data in Amazon DynamoDB.
5. The website displays the menu or feedback summary.

## API Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/menu?date=YYYY-MM-DD` | Get the menu for a selected date |
| POST | `/menu` | Save or update the menu |
| POST | `/feedback` | Submit feedback |
| GET | `/feedback?date=YYYY-MM-DD` | Get feedback summary |

## DynamoDB Tables

### MessMenu

| Attribute | Type | Description |
|---|---|---|
| date | String | Partition key, for example `2026-11-20` |
| breakfast | String | Breakfast menu |
| lunch | String | Lunch menu |
| dinner | String | Dinner menu |

### MessFeedback

| Attribute | Type | Description |
|---|---|---|
| feedbackId | String | Partition key |
| createdAt | String | Sort key |
| date | String | Menu date |
| meal | String | Breakfast, Lunch, or Dinner |
| rating | String | Rating from 1 to 5 |
| comment | String | Student comment |
| studentName | String | Optional student name |

## Admin Page

The admin page is available at:

https://main.d3ab03gpkxzlk0.amplifyapp.com/admin.html

The admin can select a date and update the breakfast, lunch, and dinner menu. The updated menu is saved in DynamoDB and becomes available on the student website.

## Built For

This project was built for the **AWS ShipIt Challenge**, organized by Techfest, IIT Bombay in collaboration with AWS.

## AWS Builder Center

AWS Builder Center alias: `jorwardhiraj`

## Future Improvements

- Add student login using Amazon Cognito
- Add image upload for daily meals
- Add notifications for menu updates
- Add separate admin login
- Add feedback analytics and charts
- Add support for multiple messes or hostels

## Author

Created by **Jorwardhiraj** for the Techfest–AWS ShipIt Challenge.
