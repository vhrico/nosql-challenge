# Unit 12 Homework: Eat Safe, Love
# Module 12 NoSQL 

## Eat Safe, Love

### Introduction

The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

### Part 1: Database and Jupyter Notebook Set Up
** Use NoSQL_setup_starter.ipynb for this section of the challenge.**

Import the data provided in the `establishments.json` file from your Terminal. Name the database `uk_food` and the collection `establishments`.
Within this markdown cell, copy the line of text you used to import the data from your Terminal. This way, future analysts will be able to repeat your process. 

** Import the dataset with `mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json`**

** Dependencies: PyMongo and Pretty Print (pprint).**

Create an instance of the Mongo Client.
	mongo = MongoClient(port=27017)

Confirm that you created the database and loaded the data properly:

1. List the databases you have in MongoDB. Confirm that uk_food is listed.
2. List the collection(s) in the database to ensure that establishments is there.
3. Find and display one document in the establishments collection using find_one and display with pprint.
4.Assign the establishments collection to a variable to prepare the collection for use.

### Part 2: Update the Database

Introduction: 

The magazine editors have some requested modifications for the database before you can perform any queries or analysis for them. Make the following changes to the establishments collection:

An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked you to include it in your analysis. 
Add the following restaurant "Penang Flavours" to the database.

1. Create a dictionary for the new restaurant data
2. Insert the new restaurant into the collection
3. Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the `BusinessTypeID` and `BusinessType` fields.
4. Update the new restaurant with the `BusinessTypeID`.
5. Confirm that the new restaurant was updated

The magazine is not interested in any establishments in Dover, so check how many documents contain the Dover Local Authority. Then, remove any establishments within the Dover Local Authority from the database, and check the number of documents to ensure they were deleted.

6. Find how many documents have LocalAuthorityName as "Dover"
7. Delete all documents where LocalAuthorityName is "Dover"
8. Check if any remaining documents include Dover
9. Check that other documents remain with 'find_one'
5. Some of the number values are stored as strings, when they should be stored as numbers.
6. Use `update_many` to convert `latitude` and `longitude` to decimal numbers.
7. Set non 1-5 Rating Values to Null
8. Change the data type from String to Integer for RatingValue
9. Check that the coordinates and rating value are now numbers

### Part 3: Exploratory Analysis
** Use NoSQL_analysis_starter.ipyn for this section of the challenge**
 
Eat Safe, Love has specific questions they want you to answer, which will help them find the locations they wish to visit and avoid.

Some notes to be aware of while you are exploring the dataset:

RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.
Note: This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating. 
We will coerce non-numeric values to nulls during the database setup before converting ratings to integers.
The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.
Use the following questions to explore the database, and find the answers, so you can provide them to the magazine editors.

Unless otherwise stated, for each question:
--Use count_documents to display the number of documents in the result
--Display the first document in the results using pprint
--Convert the result to a Pandas DataFrame

1. Which establishments have a hygiene score equal to 20?
2. Which establishments in London have a RatingValue greater than or equal to 4?

** Hint: The London Local Authority has a longer name than "London" so you will need to use $regex as part of your search.**

3. What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?

** Hint: You will need to compare the geocode to find the nearest locations. Search within 0.01 degree on either side of the latitude and longitude.**

4. How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.

5. What are the top 5 establishments with a `RatingValue` rating value of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?
a. Search within 0.01 degree on either side of the latitude and longitude.
b. Rating value must equal 5
c. Sort by hygiene score

6. How many establishments in each Local Authority area have a hygiene score of 0?

Create a pipeline that:
a. Matches establishments with a hygiene score of 0
b. Groups the matches by Local Authority
c. Sorts the matches from highest to lowest

The homework instructions and requirements are located in Canvas (or in the 08-Canvas folder for those cohorts not on Canvas).

- - -

© 2022 edX Boot Camps LLC. Confidential and Proprietary. All Rights Reserved.