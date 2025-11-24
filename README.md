# Library-Book-Management
Giving best positions for books in a library
# 📚 Simple SQLite Library Management System

This is a complete, menu-driven command-line application for managing a library's book inventory. It uses **Python** and the built-in **`sqlite3`** module to perform standard CRUD (Create, Read, Update, Delete) operations on a local database file.

---

## 🚀 Features

* **Database Initialization:** Automatically creates the `library.db` file and the `books` table upon first run.
* **Sample Data:** Automatically populates the library with 4 sample books if the database is empty for easy testing.
* **Book Management (CRUD):**
    * Add new books (Title, Author, unique ISBN).
    * View all books with their current status.
    * Delete books by ID.
* **Status Tracking:**
    * Check out books (changes status to `Checked Out`).
    * Return books (changes status to `Available`).
* **Error Handling:** Prevents adding books with duplicate ISBNs and handles invalid Book IDs during checkout/return/deletion.

---

## ⚙️ Setup and Installation

This system requires only **Python 3.x**. No external libraries need to be installed.

1.  **Save the Code:** Save the entire code block provided as a file named `library_manager.py`.
2.  **Run the Script:** Open your terminal or command prompt, navigate to the directory where you saved the file, and execute the script:

    ```bash
    python library_manager.py
    ```

### Database File

When you run the script, a file named **`library.db`** will be automatically created in the same directory. This file stores all your library data.

---

## 📖 How to Use

The application runs in an interactive loop driven by a main menu.

### Main Menu Options:

| Option | Description | Logic Handled |
| :--- | :--- | :--- |
| **1** | **Add New Book** | Prompts for Title, Author, and ISBN. Fails if the ISBN already exists. |
| **2** | **View All Books** | Lists all books in a formatted table, showing ID, Title, Author, ISBN, and Status. |
| **3** | **Check Out Book** | Requires Book ID. Only allows checkout if the status is `Available`. |
| **4** | **Return Book** | Requires Book ID. Only allows return if the status is `Checked Out`. |
| **5** | **Delete Book** | Requires Book ID. Permanently removes the record from the database. |
| **6** | **Exit** | Closes the application. |

### Example Workflow: Checking out a book

1.  Start the script. The sample books are automatically added.
2.  Choose **2** to view books. Note the ID of a book (e.g., ID 1 for "The Lord of the Rings").
3.  Choose **3** (Check Out Book).
4.  Enter the ID: `1`.
5.  The system will print: `Successfully checked out: The Lord of the Rings by J.R.R. Tolkien`.
6.  Choose **2** again to confirm that the status of ID 1 is now `Checked Out`.

---

## 🔍 Code Structure

The code is organized into three main modules for clarity:

1.  **Configuration and Initialization:** Handles global settings (`DB_NAME`), creates the table (`create_table`), and loads sample data (`insert_sample_books`).
2.  **Database Manager (CRUD Operations):** Contains low-level functions (`add_book`, `get_all_books`, `update_book_status`, `delete_book`) that directly execute SQL commands.
3.  **Library Logic:** Contains high-level business logic (`check_out_book`, `return_book`, `list_all_books`) that calls the Database Manager functions and handles state checks.
4.  **User Interface and Workflow:** Contains the functions that handle input/output and control the main application loop (`run_system`).
