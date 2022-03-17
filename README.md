# Guide

## Preparation

1. Setup the `config.json` such as below:

   ```json
   {
     "development": {
       "username": "postgres",
       "password": "postgres",
       "database": "grading",
       "host": "172.17.0.2",
       "dialect": "postgres"
     }
   }
   ```

1. Clear the database:

   ```
   drop schema public cascade; create schema public;
   ```

1. Install the dependencies:

   ```
   npm i
   npm i -D nodemon sequelize-cli
   ```

1. Create new seeder for testing purpose:

   ```
   npx sequelize-cli seed:generate --name test-users
   ```

   ```js
   // xxxxxxxxxxxxxx-test-users.js
   "use strict";
   const bcryptjs = require("bcryptjs");
   module.exports = {
     async up(queryInterface, Sequelize) {
       await queryInterface.bulkInsert("Users", [
         {
           username: "testadmin", // optional
           email: "testadmin@mail.com",
           password: bcryptjs.hashSync("password"),
           role: "admin",
           phoneNumber: "12345",
           address: "here",
           createdAt: new Date(),
           updatedAt: new Date(),
         },
         {
           username: "teststaff1", // optional
           email: "teststaff1@mail.com",
           password: bcryptjs.hashSync("password"),
           role: "staff",
           phoneNumber: "12345",
           address: "here",
           createdAt: new Date(),
           updatedAt: new Date(),
         },
         {
           username: "teststaff2", // optional
           email: "teststaff2@mail.com",
           password: bcryptjs.hashSync("password"),
           role: "staff",
           phoneNumber: "12345",
           address: "here",
           createdAt: new Date(),
           updatedAt: new Date(),
         },
       ]);
     },
     async down(queryInterface, Sequelize) {},
   };
   ```

1. Run the migrations:

   ```
   npx sequelize-cli db:migrate
   ```

1. Run the seeds:

   ```
   npx sequelize-cli db:seed:all
   ```

1. Configure the collection variables following challenge's theme:

<table>
    <thead>
        <tr>
            <th>VARIABLE</th>
            <th>INITIAL & CURRENT VALUE</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>host</td>
            <td>http://localhost:3000</td>
        </tr>
        <tr>
            <td>register</td>
            <td>register</td>
        </tr>
        <tr>
            <td>login</td>
            <td>login</td>
        </tr>
        <tr>
            <td>entities</td>
            <td>transportations</td>
        </tr>
        <tr>
            <td>testData</td>
            <td>
                <pre>{
  "name": "test",
  "description": "test description",
  "imgUrl": "http://site.com/test.png",
  "location": "here",
  "price": 500000,
  "typeId": 1
}</pre>
            </td>
        </tr>
        <tr>
            <td>updateData</td>
            <td>
                <pre>{
  "name": "test update",
  "description": "test description update",
  "imgUrl": "http://site.com/update.png",
  "location": "here update",
  "price": 500001,
  "typeId": 1
}</pre>
            </td>
        </tr>
    </tbody>
</table>
