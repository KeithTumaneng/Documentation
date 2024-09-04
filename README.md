### Quick Guide: Using GitHub Repository & Setting Up Development Environment

#### 1. **Cloning the Repository**

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

#### 2. **Setting Up Your Development Environment**

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
   - Check for a `.env.example` or similar file in the repository.
   - Copy this file to `.env` and update the values as necessary:
     ```bash
     cp .env.example .env
     ```
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


#### 3. **Using Git for Version Control**

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
