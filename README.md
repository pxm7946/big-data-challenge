# big-data-challenge


This week's homework challenge required us to demonstrate the skills that have been learned in the past few weeks regarding machine learning, as well as utilizing Amazon Web Services, also known as AWS. The purpose of this project was to view the datasets for customer reviews in specific categories, and perform the ETL (Extraction, Transform, and Load) process to these datasets in the cloud. Once this was done, we are expected to upload the dataframe onto a RDS instance. A statistical analysis is meant to be created as a second part of this homework by using either PySpark or SQL. For this specific assignment, the dataset that was used was the DVD reviews that customers had made, and PySpark was the used to accomplish the tasks that were required. 

--------------------------------------------------------------------------
Level 1
--------------------------------------------------------------------------
The first step for this homework assignment was to create a RDS instance on AWS by linking it to postgres. Once the steps were followed to create a database within AWS, a username and password were required to continue, and was, in fact, used to open this same database in pgAdmin. Once I confirmed the database that I had created in AWS looked exactly the same in pgAdmin, I continued with the assignment and began on loading the data onto Google Colaboratory. After importing certain PySpark libraries, I was able to use pandas to view the tables. The link was acquired from a Resource in the homework assignment, directly from Amazon. Because the table had a wide range of values in the columns, it was best to divide it into four (4) different tables. The following were the tables created along with their corresponding columns: 

      - Reviews: 
          - review_id
          - customer_id
          - product_id
          - product_parent
          - review_date
          
      - Products:
          - product_id
          - product_title
          
      - Customers:
          - customer_id
          -customer_count (new column created using the function ".withColumnRenamed")
          
      - Vine:
          - review_id
          -star_rating
          - helpful_votes
          - total_votes
          - vine
          
          
The data was tested to see if there were any duplicate values; in the case that there were duplicate values, we simply needed to drop those values in order to create the results more accurate. Like mentioned above, the ".withColumnRenamed" function helped call a column made out of scratch to be referenced to in a table. Once the cleaning was done, the configuration for RDS instance was performed. All four (4) of the dataframes were written to table by using the ".write.jdbc" function, along with their corresponding parameters. This information was also seen in pgAdmin due to the connection that was made early on in the assignment. 

--------------------------------------------------------------------------
Level 2
--------------------------------------------------------------------------

For the second part of this assignment, a statistical analysis was needed to be made in order to determine the validity and credibility of the reviews. After loading the dataframe onto the notebook, a separate dataframe with only columns regarding the votes (star rating, helpful votes, total votes, vine, and verified purchase) was created. After filtering and manipulating the data to receive accurate scores, a dataframe with filters to determine the total percentage of 5 star reviews was created, and utilized to determine the level of trustworthiness in these vine reviews. Among vine reviews, there seems to be 18% of trustworthiness, whereas an estimated 52% is shown in non-vine related reviews. What does this mean? We can conclude that the vine reviews that Amazon provides may not be as trustworthy as those that are unrelated, and often times, real customers who have gotten a product and were either satisfied or dissatisfied. Although it seems helpful to have people test the product out and provide an unbiased review, Amazon does end up relying on their customers to make the most trustworthy reviews. 






The coding for this assignment may be found on the following files:

  • "level-1.ipynb"
  • "level-2.ipynb"








