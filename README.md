# PeerPrep

# Table of Contents

1. [Setup instructions](#setup-instructions)    
2. [Running the application via Docker Desktop](#running-the-application-via-docker-desktop)   
3. [Setting up PostgreSQL Permissions](#setting-up-postgresql-permissions)


# Setup instructions
Follow these steps to run the project:

1. Ensure you have a `.env` file in the `backend` folder.

    Sample `.env` file content in the `backend` folder:
    ```env
    DB_USER=postgres
    DB_HOST=localhost
    DB_PASSWORD=YOUR_POSTGRES_PASSWORD
    DB_PORT=YOUR_POSTGRES_PORT->5432
    DB_DATABASE=cs3219_g47
    POSTGRESQLPORT=4001
    PORT=4000
    MONGO_URI=mongodb+srv://default:1234@g47-assignment-cluster.6vxd6vb.mongodb.net/?retryWrites=true&w=majority
    ACCESS_TOKEN_SECRET=YOUR_ACCESS_TOKEN_SECRET
    REFRESH_TOKEN_SECRET=YOUR_REFRESH_TOKEN_SECRET
    AUTH_EMAIL=cs3219OTPsender@hotmail.com
    AUTH_PASS=cs3219grp47
    ```
<sub>**Note**: `YOUR_ACCESS_TOKEN_SECRET` and `YOUR_REFRESH_TOKEN_SECRET` can be a random string </sub> 

2. Run the following commands in the main directory:

    ```bash
    npm run install-all
    npm run create-db
    npm run dev
    ```
<sub>**Note**: If you are accessing the application via **Docker Desktop**, you may skip this step.

3. The following are the roles and their access:

| Role                | View Question | Add Question | Delete Question | Edit Role (User and SuperUser) | Edit Role (Admin) |
|---------------------|---------------|--------------|------------------|--------------------------------|-------------------|
| Unauthenticated user | No            | No           | No               | No                             | No                |
| User                | Yes           | No           | No               | No                             | No                |
| SuperUser           | Yes           | Yes          | Yes              | No                             | No                |
| Admin               | Yes           | Yes          | Yes              | Yes                            | No                |
| SuperAdmin          | Yes           | Yes          | Yes              | Yes                            | Yes               |

Login Information for testing:
- User: user@example.com, PW: 123456
- SuperUser: superuser@example.com, PW: 123456     
- Admin: admin@example.com, PW: 123456 
- SuperAdmin: superadmin@example.com, PW: 123456


# Running the application via Docker Desktop
Follow these steps to run the project:   

1. Ensure you have installed Docker Desktop
2. Run the following commands in the main directory:
    ```bash
    docker-compose down
    docker-compose up --build
    ```
3. Wait for the docker to fully initialise and connect to all databases before testing
4. Ensure that you use `localhost` instead of `localhost:3000`
5. Login Information for testing:
    - User: user@example.com, PW: 123456
    - SuperUser: superuser@example.com, PW: 123456     
    - Admin: admin@example.com, PW: 123456 
    - SuperAdmin: superadmin@example.com, PW: 123456



## Setting up PostgreSQL Permissions

If you are not using the default PostgreSQL user (`postgres`) for your database operations, follow these steps to grant necessary permissions:

1. Open your terminal and enter the PostgreSQL command-line interface:

    ```bash
    psql -U postgres
    ```

2. Once you're in the PostgreSQL CLI, run the following command to grant superuser privileges to your user:

    ```sql
    ALTER USER your_username WITH SUPERUSER;
    ```

   Replace `your_username` with the actual username you're using for your PostgreSQL database.

These steps ensure that your user has the required permissions to perform CRUD (Create, Read, Update, Delete) operations in PostgreSQL.

Make sure to execute these commands with caution, especially when granting superuser privileges.
