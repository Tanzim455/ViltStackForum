
# Project Setup Guide

Follow these steps to set up the project:

## 1. Install Dependencies

Navigate to the project directory and install the PHP dependencies:

```bash
composer install
```
## 2.Environment Configuration
Then in cli run cp .env .env.example

## 3. Generate keys
 php artisan key:generate

## 4.Database Setup
Create a database and write similar name of database in .env file

## 5.Database migration

php artisan migrate

## 6.Seeding The Database

php artisan db:seed --class=RoleSeeder
php artisan db:seed --class=CategorySeeder


## 7.Install and run npm 
npm install and npm run dev

## 8.Generate dummy 10 users 

User::factory(10)->create();





