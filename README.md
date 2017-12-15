# Setup Saveory Mongo Databases

1. Create a MongoDB database for Saveory
 - If you do not already have mongo setup, please refer to these instructions https://docs.mongodb.com/v3.4/installation/
    - Either community or enterprise editions work
 - In the mongo shell run `use <DB_NAME>`
 - Give a user read and write permissions to the new database
    - If you do not already have a mongo user setup, refer here https://docs.mongodb.com/v3.4/tutorial/enable-authentication/
    - Run these commands
        ```
        use admin
        db.grantRolesToUser("<USER_NAME>",
              [
                { role: "readWrite", db: "<DB_NAME>" }
              ])
        ```
2. Restore saveory data to your database
  - Get the saveory_setup_db.zip
  - run `unzip saveory_setup_db.zip`
  - run `mongorestore --host <MONGO_HOST> --username <USER_NAME> --password <USER_PASS> --db <DB_NAME> --authenticationDatabase admin saveory_setup_db`
  - There should be an output line that appears as follows
    ```
      finished restoring <DB_NAME>.recipes (911 documents)
    ```
3. In the saveory.users.microservice, saveory.pantry.microservice, and saveory.recipes.microservice repositories, there are instructions on how to update the environment to use your own MongoDB setup.
