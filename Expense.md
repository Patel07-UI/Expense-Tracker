# Expense-Tracker
import os

def initialize_file():
    if not os.path.exists('expenses.txt'):
        with open('expenses.txt','w') as file:
            file.write('Date, Amount,Category,Description\n')
            def add_expense(date, amount, category, description):
    with open('expenses.txt', 'a') as file:
        file.write(f'{date},{amount},{category},{description}\n')
    print('Expense added')
    def view_expenses():
    with open('expenses.txt', 'r') as file:
        lines = file.readlines()
        print(lines[0])  # Print the header
        for line in lines[1:]:
            print(line)
            def filter_expenses(filter_by, filter_value):
    with open('expenses.txt', 'r') as file:
        lines = file.readlines()
        print(lines[0])  # Print the header
        for line in lines[1:]:
            data = line.split(',')
            if filter_by == 'date' and filter_value == data[0]:
                print(line)
            elif filter_by == 'category' and filter_value == data[2]:
                def delete_expense(date, amount, category, description):
    lines = []
    with open('expenses.txt', 'r') as file:
        lines = file.readlines()
    with open('expenses.txt', 'w') as file:
        for line in lines:
            if line.strip() != f'{date},{amount},{category},{description}':
                file.write(line)
    print('Expense deleted')
    import datetime

def monthly_summary():
    current_month = datetime.datetime.now().strftime('%Y-%m')
    total_expense = 0.0
    category_expense = {}

    with open('expenses.txt', 'r') as file:
        lines = file.readlines()
        for line in lines:
            data = line.strip().split(',')
            if data[0].startswith(current_month):
                amount = float(data[1])
                category = data[2]
                total_expense += amount
                if category in category_expense:
                    category_expense[category] += amount
                else:
                    category_expense[category] = amount

    print(f'Total expense for {current_month}: {total_expense}')
    for category, amount in category_expense.items():
        print(f'{category}: {amount}')
def main():
    initialize_file()
    while True:
        print('1. Add Expense')
        print('2. View Expense')
        print('3. Filter Expense')
        print('4. Delete Expense')
        print('5. Monthly Summary')
        print('6. Exit')
        print()
        choice = input('Select any one:')

        if choice == '1':
            date = input('Enter date(yyyy-mm-dd):')
            amount = input('Enter amount:')
            category = input('Enter category:')
            description = input('Enter description:')
            add_expense(date, amount, category, description)
            print()

        elif choice == '2':
            view_expenses()
            print()

        elif choice == '3':
            filter_by = input('Filter by(date/category):')
            filter_value = input(f'enter {filter_by}:')
            filter_expenses(filter_by, filter_value)
            print()

        elif choice == '4':
            date = input('Enter date(yyyy-mm-dd):')
            amount = input('Enter amount:')
            category = input('Enter category:')
            description = input('Enter description:')
            delete_expense(date, amount, category, description)
            print()

        elif choice == '5':
            monthly_summary()

        elif choice == '6':
            print('Exit from program')
            break

        else:
            print('Invalid option')

if __name__ == '__main__':
    main()

  
