
# ✅ MySQL Employees Sample Database – Local Setup (Windows)

This README documents how I successfully imported the [employees sample database](https://github.com/datacharmer/test_db) from GitHub into my **local MySQL Server** on a Windows machine.

---

## 📌 Step-by-Step Instructions

### 📁 1. Clone or Download the Repository

I downloaded the repository ZIP from:

```

[https://github.com/datacharmer/test\_db](https://github.com/datacharmer/test_db)

```

Then extracted it to:

```

C:\Users\ARKA\Downloads\test\_db-master

````

---

### 🧩 2. Merge `.dump` Files

The repository had the `salaries` table data split into 3 files:
- `load_salaries1.dump`
- `load_salaries2.dump`
- `load_salaries3.dump`

I merged them using Command Prompt:

```bash
cd C:\Users\ARKA\Downloads\test_db-master\test_db-master
copy /b load_salaries1.dump + load_salaries2.dump + load_salaries3.dump load_salaries.dump
````

This created one complete file: `load_salaries.dump`.

---

### 🛠️ 3. Locate the `mysql.exe` Binary

I used the full path to the MySQL client executable:

```bash
"C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe"
```

---

### 🗄️ 4. Load the Database Using `employees.sql`

I executed the SQL script that:

* Creates the `employees` database
* Creates all tables
* Loads all data from the `.dump` files

Command used:

```bash
"C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" -u root -p < "C:\Users\ARKA\Downloads\test_db-master\test_db-master\employees.sql"
```

✅ When prompted, I entered my MySQL root password.

---

### 📤 5. Output After Successful Execution

I saw this successful log:

```
INFO
CREATING DATABASE STRUCTURE
INFO
LOADING departments
INFO
LOADING employees
INFO
LOADING dept_emp
INFO
LOADING dept_manager
INFO
LOADING titles
INFO
LOADING salaries
data_load_time_diff
00:00:43
```

---

### 🔍 6. Verified the Database in MySQL

Logged into MySQL with:

```bash
mysql -u root -p
```

Ran verification queries:

```sql
SHOW DATABASES;
USE employees;
SHOW TABLES;
SELECT COUNT(*) FROM employees;
SELECT * FROM departments LIMIT 5;
```

Everything was loaded and working correctly ✅

---

## 📦 Tables Created

* `employees`
* `departments`
* `dept_emp`
* `dept_manager`
* `titles`
* `salaries`

---

## 📌 Notes

* All `.dump` files must be in the same directory as `employees.sql`
* The `employees.sql` script expects the `.dump` files to exist and be named correctly
* File paths used are Windows-compatible with double quotes for safety

---

## 👤 Author

**Arka Mazumder**
📍 Windows 10
🛠️ MySQL Server 8.0

---

## 🔗 Source

Forked from the official GitHub repository:
[https://github.com/datacharmer/test\_db](https://github.com/datacharmer/test_db)

````

---

### ✅ Next Steps:
- Save this content as a `README.md` file inside your local Git repo.
- If you forked the repo on GitHub:
  ```bash
  git add README.md
  git commit -m "Added detailed steps for local MySQL setup on Windows"
  git push origin main
````

Want me to help format or push it to your GitHub fork?
