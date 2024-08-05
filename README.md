# Hands-on-Lab-Stored-Procedures-in-PostgreSQL-using-PgAdmin

This is a Hands-on Lab on how to create stored procedures in PostgreSQL using PgAdmin

# Software Used in this Lab

PgAdmin 4 (PostgreSQL 15)

# Database Used in this Lab

The dataset used in this lab is an internal dataset belonging to IBM.

PETSALE table

![image](https://github.com/user-attachments/assets/9933cc8a-aea5-4747-94cb-3a8f6905d89e)

# Objectives

The objectives of this project were to:

1. Create stored procedures
2. Execute stored procedures

# Task A: Create and execute a stored procedure to read data from a table on PostgreSQL PgAdmin using SQL.

- In creating the PETSALE table on PostgreSQL PgAdmin, I downloaded the PETSALE-CREATE-v2.sql script below, uploaded it to PgAdmin query tool and ran it.

  The PETSALE-CREATE-v2.sql script is available here: https://drive.google.com/file/d/1QhKBWEcMtC6WjL4UUj2XGEGlNPzHThX2/view?usp=sharing

- To retrieve the PETSALE table, I issued the followwing query:

      SELECT * FROM PETSALE

![image](https://github.com/user-attachments/assets/96c7199a-07b2-4f68-9a65-4b89f27926df)

# Task B: Create a stored procedure routine named RETRIEVE_ALL.

- To create the stored procedure routine in PostgreSQL, I issued the following query:

      CREATE OR REPLACE PROCEDURE retrieve_all()
      LANGUAGE plpgsql
      AS $$
      DECLARE
      my_cursor CURSOR FOR SELECT * FROM PETSALE;
      record RECORD;
      BEGIN
      -- Open the cursor
      OPEN my_cursor;
    
      -- Fetch rows from the cursor
      LOOP
        FETCH my_cursor INTO record;
        EXIT WHEN NOT FOUND;
        -- Process each row (e.g., print to the console)
        RAISE NOTICE 'ID: %, Animal: %, Sale Price: %, Sale Date: %, Quantity: %', 
            record.id, record.animal, record.saleprice, record.saledate, record.quantity;
      END LOOP;

      -- Close the cursor
      CLOSE my_cursor;
    END;
    $$;


# Task c: Calling the Stored Procedure

To call the stored procedure, I used the CALL statement:

      CALL retrieve_all();
   
![image](https://github.com/user-attachments/assets/72b00a9d-7e32-4bf9-a002-9721e5a5841f)
 
    






