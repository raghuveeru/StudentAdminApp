# Student Administrative App

## Overview

This is a simple JSON based REST API, built with Node, Express. It uses MySql database as backend.


## Setup
* What is needed to make the repo run once downloaded?

Clone the repo and install dependencies via NPM:

	npm install

By default, the app looks for a MySQL database on localhost called 'studentadministration'. This can be changed in the db/db_config.js file, by editing the credentials. The default 'root' and '<password>' are supplied as placeholders for the logins, you will need to update these to your localhost database credentials.

Run schema in StudentAdministration_schema.sql, then it will create 'studentadministration' database and its related tables

## Routes / Endpoints
The following routes are set up, and will return JSON data:

#### Register
+ **POST** register student and teacher: /api/register


{
  "teacher": "teacherjoe@gmail.com",
  "students":
    [
      "commonstudent2@example.com"
    ]
}

The successful JSON response code will be 204
#### GetCommonStudents
+ **GET** get students registered to teacher: /api/commonstudents?teacher=teacherken%40gmail.com

The JSON response will contains all students registered under teacher 'teacherken@gmail.com' and response code:200

{
    "students": [
        "studonet1@example.com",
        "studonet2@example.com",
        "commonstudent1@example.com",
        "commonstudent2@example.com"
    ]
}

+ **GET** get common students register to multiple teachers: /api/commonstudents?teacher=teacherken%40gmail.com&teacher=teacherjoe%40gmail.com

The JSON response will contains common students registered under teacher 'teacherken@gmail.com' and response code:200

{
    "students": [
        "commonstudent1@example.com",
        "commonstudent2@example.com"
    ]
}

#### SuspendStudent
+ **POST** teacher can suspend student:/api/suspend


Teacher can suspend student and successful JSON response code will be 204

#### RetrieveForNotifications
+ **POST** teacher can suspend student:/api/retrievefornotifications
Teacher sends notification to students register to him and he can send notifications to others by adding in notification
response code will be 200
request body:

{
  "teacher":  "teacherken@gmail.com",
  "notification": "Hello students! @studentagnes12@exam.gmail.com @studentmiche13@gmail.com"
}

Response:

{
    "students": [
        "studonet2@example.com",
        "commonstudent1@example.com",
        "commonstudent2@example.com",
        "studentagnes12@exam.gmail.com",
        "studentmiche13@gmail.com"
    ]
}


request without email in notification:

{
  "teacher":  "teacherken@gmail.com",
  "notification": "Hello students!"
}

Response:

{
    "students": [
        "studonet2@example.com",
        "commonstudent1@example.com",
        "commonstudent2@example.com"
    ]
}

## Start node server
run below commands to start
npm start

## Testing
Mocha and Chai are using for testing this rest api

run below commands to run test cases 

npm test

