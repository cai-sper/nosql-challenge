# NoSQL Challenge - Eat Safe, Love

## Project Overview

This project focuses on analyzing the UK Food Standards Agency's food hygiene rating data to support the editors of Eat Safe, Love, a food magazine. The objective is to assess the rating data and provide insights to guide the magazine's journalists and food critics in selecting article topics.

## Table of Contents

- [Part 1: Database and Jupyter Notebook Set Up](#part-1-database-and-jupyter-notebook-set-up)
- [Part 2: Update the Database](#part-2-update-the-database)
- [Part 3: Exploratory Analysis](#part-3-exploratory-analysis)
- [Summary](#summary)

## Part 1: Database and Jupyter Notebook Set Up

To set up the environment and database:

1. Import the provided data from the "establishments.json" file into a MongoDB database named "uk_food" with a collection named "establishments." The import command is as follows:

   ```shell
   mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json

### Import and Setup

1. Import the required libraries, including PyMongo and Pretty Print (pprint), and create a Mongo Client instance.
2. Confirm the setup by:
   - Listing the available databases in MongoDB, ensuring "uk_food" is present.
   - Listing the collections within the "uk_food" database, verifying the existence of "establishments."
   - Retrieving and displaying one document from the "establishments" collection using find_one() and pprint.
   - Assigning the "establishments" collection to a variable for subsequent use.

## Part 2: Update the Database

In this section, database modifications are made in response to the magazine's requests:

1. Add a new halal restaurant, "Penang Flavours," to the database with the provided information. Utilize the insert_one method for this purpose.
2. Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and update the "Penang Flavours" document with the correct BusinessTypeID using update_one.
3. Exclude establishments within the Dover Local Authority, as requested by the magazine. Verify the removal by checking the document count using count_documents before and after deletion.
4. Convert specific number values stored as strings to their respective data types. This includes converting latitude and longitude to decimal numbers and RatingValue to integers using update_many.

## Part 3: Exploratory Analysis

In this section, an exploratory analysis of the data is conducted to answer questions posed by Eat Safe, Love:

1. Identify establishments with a hygiene score equal to 20 using find and count_documents.
   - Conclusion: There are 41 such establishments.
2. Locate establishments in London with a RatingValue greater than or equal to 4, accounting for variations in London's Local Authority name.
   - Conclusion: There are 34 such establishments.
3. Find the top 5 establishments with a RatingValue of 5, sorted by the lowest hygiene score, and nearest to the new restaurant "Penang Flavours" using a combination of find, sort, and limit.
   - Conclusion: These establishments are determined based on proximity and hygiene scores.
4. Determine the number of establishments in each Local Authority area with a hygiene score of 0 using aggregation, sort the results from highest to lowest, and list the top ten local authority areas.
   - Conclusion: The top ten areas with establishments having a hygiene score of 0 are presented.

## Summary

This README provides a comprehensive overview of the project's key steps and findings. It highlights the database setup, updates made, and results obtained from the exploratory analysis. For in-depth details and code implementation, please refer to the corresponding Jupyter notebooks.
