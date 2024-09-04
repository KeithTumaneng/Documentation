## Quick Guide: Using GitHub Repository & Setting Up Development Environment

### 1. **CLONING THE REPOSITORY**

1. **Access the Repository:**
   - Go to the GitHub page for the repository.
     ```bash
     https://github.com/komunidad-global/komunidad_sustainability
     ```

2. **Copy the Repository URL:**
   - Click on the green "Code" button and copy the URL (either HTTPS or SSH).

3. **Clone the Repository:**
   - Open your terminal or command prompt.
   - Run the command:
     ```bash
     git clone https://github.com/komunidad-global/komunidad_sustainability.git
     ```

4. **Navigate to the Repository Directory:**
   ```bash
   cd komunidad_sustainability
   ```
   - clone the admin repository to the root directory and rename it to admin_material2_pro
     ```bash
     git clone https://github.com/komunidad-global/sustainability_admin.git admin_material2_pro
     ```

### 2. **SETTING UP YOUR DEVELOPMENT ENVIRONMENT**

   1. **Install Dependencies:**
      - If the project uses a dependency manager, follow these steps:
        - create a virtual environment and install dependencies:
          ```bash
          python -m venv venv
          ```
          ```bash
          source venv/bin/activate  # On Windows: venv\Scripts\activate
          ```
          ```bash
          pip install -r requirements.txt
          ```
   
   2. **Configure Environment Variables:**
      - request the .env from the Repository Onwer
      - Edit `.env` to set up necessary environment variables (e.g., `DEBUG`, `DATABASE_URL`, etc.).   
   
   3. **Install MySQL Server:**
      - Ensure MySQL Server is installed on your machine. You can download it from [MySQL Downloads](https://dev.mysql.com/downloads/).
      - **Create a MySQL Database:**
        - Log in to MySQL using the command line or MySQL Workbench:
          ```bash
          mysql -u root -p
          ```
        - Create a new database:
          ```sql
          CREATE DATABASE cas_db;
          ```
        - Create a new user and grant permissions:
          ```sql
          CREATE USER 'myuser'@'localhost' IDENTIFIED BY 'mypassword';
          GRANT ALL PRIVILEGES ON cas_db.* TO 'myuser'@'localhost';
          FLUSH PRIVILEGES;
          ```
        - **Import sql file via CLI:**
           ```bash
           mysql -u <username> -p cas_db < <path_to_sql_file>
           ```
        - **Verify the Import**:
          - Check your database to ensure that the data has been imported correctly. You can use a MySQL client like MySQL Workbench or run SQL queries from the command line.
         - **Export database to sql file via CLI:**
           ```bash
           mysqldump -u <username> -p cas_db > <output_file>.sql
           ```
      - **Exporting a Database to SQL with MySQL Workbench**
         - **Open MySQL Workbench:**
            - Launch MySQL Workbench on your computer.
         
         - **Connect to Your Database:**
            - Open a connection to the MySQL server where your database is located.
         
         - **Open the Data Export Tool:**
            - Go to **Server** in the top menu and select **Data Export**.
         
         - **Select the Database and Tables:**
            - On the left, choose the database you want to export.
            - Select the tables you wish to export or choose the entire database.
         
         - **Configure Export Options:**
            - Under **Export Options**, choose **Export to Self-Contained File**.
            - Specify the path and filename for the output SQL file (e.g., `backup.sql`).
         
         - **Start the Export:**
            - Click the **Start Export** button.
            - Wait for the export process to complete.
         
         - **Verify the SQL File:**
            - Navigate to the location you specified and verify that the SQL file has been created.
      
      - **Importing a SQL File into a Database**
         - **Open MySQL Workbench:**
            - Launch MySQL Workbench on your computer.
         
         - **Connect to Your Database:**
            - Open a connection to the MySQL server where you want to import the SQL file.
         
         - **Open the Data Import Tool:**
            - Go to **Server** in the top menu and select **Data Import**.
         
         - **Select Import Options:**
            - Choose **Import from Self-Contained File**.
            - Click on the **Browse** button and select the SQL file you want to import (e.g., `backup.sql`).
         
         - **Choose the Target Database:**
            - Under **Default Schema to be Imported To**, select the target database where the SQL file will be imported. If the database does not exist, you might need to create it first.
         
         - **Start the Import:**
            - Click the **Start Import** button.
            - Wait for the import process to complete.
         
         - **Verify the Import:**
            - Check the database to ensure that the tables and data have been imported correctly.
     
   4. **Setup Database:**
      - Run the following command to apply database migrations:
        ```bash
        python manage.py makemigrations
        ```
        ```bash
        python manage.py migrate
        ```
   
   5. **Run the Development Server:**
      - Start the Django development server:
        ```bash
        python manage.py runserver
        ```
      - Open your browser and go to `http://127.0.0.1:8000/` to view the application.

### 3. **SETUP PYTHON DEBUGGER**
   1. **Install Required Extensions**
      - **Python Extension:** Ensure you have the Python extension installed in VS Code. You can install it from the Extensions view (`Ctrl+Shift+X`) by searching for "Python" and installing the one provided by Microsoft.
   
      - **Django Extension (optional):** The Python extension generally provides adequate support for Django, but additional Django extensions might enhance your experience.
   
   2. **Create `launch.json`**
   
      - **Open Your Project in VS Code:**
         - Open your Django project folder in VS Code.
   
      - **Open the Debug Panel:**
         - Click on the Debug icon in the Activity Bar on the side of the VS Code window or press `Ctrl+Shift+D`.
   
      - **Create a `launch.json` File:**
         - Click on the gear icon in the Debug panel and select **Add Configuration**.
         - Choose **Python** from the list of environments.
         - Select **Django** from the options presented.
   
      If the Django configuration is not listed, you may need to manually create or edit the `launch.json` file.
   
   3. **Configure `launch.json`**
      - You can manually configure `launch.json` by creating or editing it in the `.vscode` folder of your project. Here's an example configuration for debugging a Django application:
      ```json
      {
          "version": "0.2.0",
          "configurations": [
            {
                "name": "Python Debugger: Django",
                "type": "debugpy",
                "request": "launch",
                "args": [
                    "runserver"
                ],
                "django": true,
                "program": "${workspaceFolder}\\manage.py",
                "console": "integratedTerminal"
            }
          ]
      }
      ```
   4. **Launch Debugging**
      - **Start Debugging:**
         - Select your preferred configuration from the debug dropdown menu in the Debug panel.
         - Click the green play button or press `F5` to start debugging.
   
      - **Set Breakpoints:**
         - Open your Django project files and set breakpoints by clicking in the gutter next to the line numbers.
   
      - Monitor the Debugging Process:
         - The terminal will display the output from the Django development server.
         - You can use the Debug panel to inspect variables, step through code, and evaluate expressions.



### 4. **USING GIT FOR VERSION CONTROL**
   1. **Check Repository Status:**
      ```bash
      git status
      ```
   
   2. **Create a New Branch:**
      ```bash
      git checkout -b <branch-name>
      ```
   
   3. **Add Changes:**
      ```bash
      git add <file-or-directory>
      ```
   
   4. **Commit Changes:**
      ```bash
      git commit -m "Describe your changes"
      ```
   
   5. **Push Changes to GitHub:**
      ```bash
      git push origin <branch-name>
      ```
   
   6. **Create a Pull Request:**
      - Go to the repository on GitHub and navigate to the "Pull Requests" tab.
      - Click "New Pull Request" and follow the prompts to create a PR.
   
   #### 4. **Staying Up-to-Date**
   
   1. **Fetch Latest Changes:**
      ```bash
      git fetch origin
      ```

2. **Merge Changes:**
   ```bash
   git pull origin <main-branch>
   ```
