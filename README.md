# Data Transformation With Python Mysql Mongodb Database
This repository is related to a data transformation class. In this particular class, we going to build a code with these steps: Step 1: collect data from MySQL; Step 2: transforma the data; Step 3: Ingest the data into the new model with MongoDB Database


Project: RDBMS to MongoDB Data Transformation

Step 1: Set up the Environment

Ensure you have the required libraries installed. You can install them using pip:

    pip install SQLAlchemy pymongo pandas
    pip install pymysql

(or polars if you choose to use it instead of pandas)

Step 2: Connect to MySQL Database

Use SQLAlchemy to connect to your MySQL database and fetch the data you want to transform. Replace the placeholders in the code below with your actual database connection details:

    from sqlalchemy import create_engine

    # Replace 'mysql://user:password@host:port/database' with your MySQL connection string
    engine = create_engine('mysql://user:password@host:port/database')

    # Example query to fetch data from a table called 'your_table_name'
    data = pd.read_sql_query('SELECT * FROM your_table_name', engine)

Step 3: Data Transformation

Perform any necessary data transformation using pandas or polars (depending on your choice). This might include cleaning, filtering, aggregating, or any other manipulation required to prepare the data for MongoDB insertion.

    # Your data transformation steps here
    # For example:
    # data = data.dropna()  # Drop rows with missing values
    # data['new_column'] = data['old_column'] * 2  # Add a new column

Step 4: Connect to MongoDB

Use PyMongo to establish a connection to your MongoDB server. Replace the placeholders in the code below with your MongoDB connection details:

    from pymongo import MongoClient

    # Replace 'mongodb://user:password@host:port/' with your MongoDB connection string
    client = MongoClient('mongodb://user:password@host:port/')
    db = client['your_database_name']  # Replace 'your_database_name' with your desired database name
    collection = db['your_collection_name']  # Replace 'your_collection_name' with your desired collection name

Step 5: Data Ingestion into MongoDB

Iterate over the transformed data and insert it into MongoDB:

    # Assuming your transformed data is stored in the 'data' DataFrame
    for index, row in data.iterrows():
        document = row.to_dict()
        collection.insert_one(document)

Step 6: Complete the Script

Put everything together into a Python script, and you have your data engineering project ready to go. You can run the script whenever you need to transfer data from MySQL to MongoDB.

Remember to handle any potential errors, add logging, and optimize the code based on the scale of your data.

Please note that the provided steps are just a basic outline, and you can expand the project according to your specific requirements and the complexity of your data transformation needs. Happy coding!
