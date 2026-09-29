# Finance-Management-System
A simple Python app to track your money in the terminal. Add income and expenses, set a monthly budget, and see where your money goes. It warns you when you spend too much and saves everything in a file, so nothing is lost. No extra installs needed.


Personal Finance Manager
A Python console application that uses a text menu to record money coming into and out of your account along with a budget for the month. All data persists in a local JSON file so it's there when you run the app again. No internet, database or third-party libraries required.

Features

Add income and expense with amount, category, optional note, and date
See all transactions in a table, latest first
Summary of total income, total expenses, and balance, as well as current-month totals
Category wise expense report with percentage and text based bar chart
Monthly budget with warning when you reach 80% and when you go over
If you want to erase your transaction on Mercury Mastercard Web page won't title it for you. You are able to delete a transaction by the ID (does ask for confirmation first).
Amount, date, category and menu item input validation
Crash resistant: if a data file is missing or corrupted the software will not crash.

Requirements

Python 3.6 or newer (uses f-strings)
Standard library only (json, datetime)
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

Option What it does

1 / 2 for amount, category number, note (optional) and date (YYYY-MM-DD;press Enter for today). Adding an expense also checks your budget.
3 Lists out any transactions with ID, date, type, category, amount and note.
4 Displays the totals for the whole, this month and your remaining budget.
5 Shows spending by category, highest first, with a # bar for every 5%.
6 Sets the monthly spending limit.
7 Displays the list and then deletes the ID you insert after a y/n confirmation.
8 Exits. Data is stored after each change.

Budget Warnings

The budget is only compared to the current month's expenses.
97% used:! Warning you have used 98% of this month's budget.
Over the limit:!! WARNING: You are OVER budget by Rs. 9,829.00!
Set the budget to 0 (or not to set it at all), and no warnings are displayed.
Default Categories
Type Categories
Income Salary, Pocket Money, Scholarship, Gift, Other
Cost-Effective Food, Transportation, Reading Materials, Shopping, Invoices, Entertainment, Miscellaneous
Customising
Modify these constants at the top of finance_manager.py:
DATAFILE = "financedata.json" #file where data is stored
CURRENCY = "Rs." # change to $, EUR, etc.
INCOME_CATEGORIES = [...]
EXPENSE_CATEGORIES = [...]

Data Storage

The data is saved to finance_data.json in the folder you run the program from:
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
All new transactions will be assigned ID of highest existing ID + 1, so after deleting some transaction, it's not possible to assign ID of the deleted transaction to some new one.
Dates are stored as YYYY-MM-DD text.
To start fresh, delete finance_data.json.
The file is in plain text format and unencrypted. If the data is sensitive please keep the file private.

Sample Session

Enter your choice (1-8): 4

------------- SUMMARY -------------

Total income: Rs. 25,000.00
Total expenses: Rs. 1,830.00
Balance: Rs. 23,170.00
This month (2026-09): income Rs. 25,000.00 expenses Rs. 1,830.00
Monthly budget: Rs. 5,000.00 (Remaining: Rs. 3,170.00)

------- EXPENSES BY CATEGORY -------

Shopping Rs. 1,200.00 65.6% #############
Travel Rs. 450.00 24.6% ####
Food Rs. 180.00 9.8% #
TOTAL Rs. 1,830.00
Code Structure
Section Functions
File handling loaddata, savedata
Input helpers money, getamount, getdate, choose_category
Calculations currentmonth, total, checkbudget
Options Menu addtransaction, viewtransactions, showsummary, categoryreport, setbudget, deletetransaction
ENTRY POINT main (menu loop with dict of actions)

Known Limitations

No ability to delete and re-enter a single transaction.
Amounts are stored as floats, not Decimal
1 user, 1 currency No export/ import.

Possible Improvements

Edit transactions, category budgets, date range filter, CSV export, Recurring transactions, Chart, Automatically test.

Author
Priom, B. Tech CSE (Cloud Computing), VIT Bhopal University


