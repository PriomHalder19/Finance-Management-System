# Finance-Management-System
A simple Python app to track your money in the terminal. Add income and expenses, set a monthly budget, and see where your money goes. It warns you when you spend too much and saves everything in a file, so nothing is lost. No extra installs needed.

Personal Finance Manager
A menu-driven Python console app for tracking income, expenses and a monthly budget. Data is saved in a local JSON file, so it is still there the next time you run the program. No internet, database or extra packages needed.
Features
•	Add income and expenses with amount, category, optional note and date
•	View all transactions in a table, newest first
•	Summary of total income, total expenses and balance, plus current-month totals
•	Expense report by category with percentages and a text bar chart
•	Monthly budget with warnings at 80% usage and when you go over
•	Delete a transaction by ID (asks for confirmation first)
•	Input validation for amounts, dates, categories and menu choices
•	Safe start-up: a missing or corrupted data file will not crash the program
Requirements
•	Python 3.6 or newer (uses f-strings)
•	Standard library only (json, datetime)
How to Run
python finance_manager.py
On Linux/macOS you may need python3 finance_manager.py.
Menu
========== FINANCE MANAGER ==========
 1. Add income
 2. Add expense
 3. View all transactions
 4. Summary
 5. Expense report by category
 6. Set monthly budget
 7. Delete a transaction
 8. Exit
=====================================
Option	What it does
1 / 2	Asks for amount, category number, note (optional) and date (YYYY-MM-DD; press Enter for today). Adding an expense also checks your budget.
3	Lists every transaction with ID, date, type, category, amount and note.
4	Shows overall totals, this month's totals, and the budget left.
5	Shows spending per category, highest first, with a # bar for every 5%.
6	Sets the monthly spending limit.
7	Shows the list, then deletes the ID you enter after a y/n confirmation.
8	Exits. Data is already saved after every change.
Budget Warnings
The budget is compared against the current month's expenses only.
•	80% or more used: ! Careful: you have used 97% of this month's budget.
•	Over the limit: !! WARNING: You are OVER budget by Rs. 9,829.00!
Set the budget to 0 (or never set it) and no warnings are shown.
Default Categories
Type	Categories
Income	Salary, Pocket Money, Scholarship, Gift, Other
Expense	Food, Travel, Books, Shopping, Bills, Entertainment, Other
Customising
Edit the constants at the top of finance_manager.py:
DATA_FILE = "finance_data.json"   # where data is saved
CURRENCY = "Rs."                  # change to $, EUR, etc.
INCOME_CATEGORIES = [...]
EXPENSE_CATEGORIES = [...]
Data Storage
Data is saved to finance_data.json in the folder you run the program from:
{
    "budget": 5000.0,
    "transactions": [
        {
            "id": 1,
            "type": "income",
            "amount": 25000.0,
            "category": "Pocket Money",
            "note": "Monthly pocket money",
            "date": "2026-09-01"
        }
    ]
}
•	Each new transaction gets an ID of highest existing ID + 1, so IDs are not repeated after deletions.
•	Dates are stored as YYYY-MM-DD text.
•	To start fresh, delete finance_data.json.
•	The file is plain text and unencrypted. Keep it private if the data is sensitive.
Sample Session
Enter your choice (1-8): 4

------------- SUMMARY -------------
Total income   : Rs. 25,000.00
Total expenses : Rs. 1,830.00
Balance        : Rs. 23,170.00

This month (2026-09): income Rs. 25,000.00, expenses Rs. 1,830.00
Monthly budget : Rs. 5,000.00 (left: Rs. 3,170.00)
------- EXPENSES BY CATEGORY -------
Shopping           Rs. 1,200.00   65.6%  #############
Travel               Rs. 450.00   24.6%  ####
Food                 Rs. 180.00    9.8%  #
TOTAL              Rs. 1,830.00
Code Structure
Section	Functions
File handling	load_data, save_data
Input helpers	money, get_amount, get_date, choose_category
Calculations	current_month, total, check_budget
Menu features	add_transaction, view_transactions, show_summary, category_report, set_budget, delete_transaction
Entry point	main (menu loop with a dictionary of actions)
Known Limitations
•	No option to edit a transaction (delete it and add it again)
•	Amounts are stored as floats, not Decimal
•	Single user, single currency, no export or import
Possible Improvements
Edit transactions, per-category budgets, date-range filters, CSV export, recurring transactions, charts, automated tests.
Author
Priom, B.Tech CSE (Cloud Computing), VIT Bhopal University

