**Database and Jupyter Notebook Set Up**  

-Includes the mongoimport command text used to import establishments.json in a markdown cell at the beginning of Jupyter notebook file.  

-The mongoimport command text correctly drops any existing establishments collection before importing establishments.json into MongoDB.  

-The database is named uk_food and the collection is named establishments.  

-Correctly imports PyMongo and Pretty Print.  

-An instance of the Mongo Client is created.  

-Lists the databases you have in Mongo, which includes uk_food.  

-Lists the collection(s) in the uk_food database, which includes establishments in the output.  

-Uses find_one() and pprint to display one document in the establishments collection.  

-The establishments collection is assigned to a variable.  

**Update the Database**  

-The supplied data for the "Penang Flavours" restaurant is correctly inserted into the establishments collection.  

-A query is performed to find the BusinessTypeID for "Restaurant/Cafe/Canteen" and returns only the BusinessTypeID and BusinessType fields.  

-The "Penang Flavours" document is updated with the correct value for BusinessTypeID.  

-A query is correctly performed to delete all the documents in the collection where "Dover Local Authority" is the value for LocalAuthorityName.  

-A count_documents() check is performed before and after the removal of the Dover documents to ensure the documents were removed.  

-An update_many() query is performed to convert the latitude and longitude fields from strings to decimal numbers and RatingValue to integers.  

**Exploratory Analysis**  

Question 1: Which establishments have a hygiene score equal to 20?  

  &ensp;-A query is correctly performed to find the establishments with a hygiene score of 20.  
  &ensp;-count_documents() is used to list the correct number of documents (answer: 41).  
  &ensp;-The first result is printed using pprint.  
  &ensp;-The results are converted to a Pandas DataFrame and displays the first 10 rows.  

Question 2: Which establishments in London have a RatingValue greater than or equal to 4?  

  &ensp;-A query is correctly performed to find the establishments in London with a RatingValue greater than or equal to 4.  
  &ensp;-The query uses the $regex operator to locate the London establishments.  
  &ensp;-count_documents() is used to list the correct number of documents (answer: 33).  
  &ensp;-The first result is printed using pprint.  
  &ensp;-The results are converted to a Pandas DataFrame and displays the first 10 rows.  

Question 3: What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?  

  &ensp;-A query is correctly performed to find the establishments within 0.01 degree of the "Penang Flavours" restaurant.  
  &ensp;-The query also limits the results to establishments with a RatingValue of 5.  
  &ensp;-The query uses the sort() method in PyMongo to sort in ascending order on the hygiene score.  
  &ensp;-The query uses the limit() method in PyMongo to limit the results to 5.  
  &ensp;-All five results are printed using pprint.  
  &ensp;-The results are converted to a Pandas DataFrame and displayed.  

Question 4: How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas.  

  &ensp;-An aggregation pipeline is built to include a match query, group, and sort.  
  &ensp;-The match query matches documents with a hygiene score of 0.  
  &ensp;-The group step of the pipeline is grouped on LocalAuthorityName and counts the number of documents.  
  &ensp;-The sort step of the pipeline sorts the count of the documents in descending order.  
  &ensp;-The aggregation pipeline is correctly sent to the aggregate() method.  
  &ensp;-The results from the aggregation query is cast as a list and then saved to a variable.  
  &ensp;-The first ten results are printed using pprint.  
  &ensp;-The results are converted to a Pandas DataFrame and displays the first 10 rows.  
