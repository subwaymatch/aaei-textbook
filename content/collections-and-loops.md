# Collections and Loops

Collections are data structures that can hold multiple items, while loops are used to iterate over these collections. In this section, we will explore lists and dictionaries as examples of collections, and we will learn how to use loops to work with them.

![Collections Cover Image](images/collections-cover.jpg)

&nbsp;

## 📝 Lists

Lists are a fundamental data structure in Python, allowing you to store multiple items in a single variable. Loops are used to iterate over these items, enabling you to perform operations on each element in the list.

---

### 🛠️ List Operations

#### 🆕 Creating Lists

You can create a list by placing items inside square brackets `[]`, separated by commas. Lists can contain items of different data types, including numbers, strings, and even other lists.

```python
# Creating a list of integers (e.g., inventory counts)
inventory_counts = [150, 220, 85, 300, 190]

# Creating a list of strings (e.g., auditing standards)
auditing_standards = ["AU-C 200", "AU-C 315", "AU-C 500", "AU-C 700"]

# Creating a mixed list (e.g., an asset's properties)
# [Asset ID, Description, Cost, Is-Tangible]
asset_info = [101, "Delivery Van", 45000, True]

# Creating a nested list (e.g., simple journal entries [Debit, Credit])
journal_entries = [["Cash", "Common Stock"], ["Inventory", "Accounts Payable"], ["COGS", "Inventory"]]
```

You can check the type of a list using the `type()` function:

```python
print(type([1, 2, 3]))  # Output: <class 'list'>
```

---

#### 📚 Accessing List Elements

```python
# Accessing elements by index
first_count = inventory_counts[0]       # 150
second_standard = auditing_standards[1] # "AU-C 315"
asset_cost = asset_info[2]              # 45000
first_entry = journal_entries[0]        # ["Cash", "Common Stock"]

# Accessing the last element
last_standard = auditing_standards[-1]  # "AU-C 700"

# Slicing a list
subset_counts = inventory_counts[1:4]   # [220, 85, 300]
```

---

#### ✏️ Modifying Lists

```python
inventory_counts[0] = 160
# inventory_counts is now [160, 220, 85, 300, 190]

auditing_standards.append("AU-C 240")
# Adds "AU-C 240" (Fraud) to the end

asset_info.remove(45000)
# asset_info is now [101, "Delivery Van", True]

journal_entries[1][0] = "Equipment"
# journal_entries is now [["Cash", "Common Stock"], ["Equipment", "Accounts Payable"], ["COGS", "Inventory"]]
```

---

#### ✂️ Slicing Lists

You can extract a portion of a list using slicing. Slicing allows you to create a new list that contains a subset of the elements from the original list.

```python
numbers = [1, 2, 3, 4, 5]
sublist = numbers[1:4]      # [2, 3, 4]
```

Note that the starting index is inclusive, while the ending index is exclusive.

---

#### 📏 Length of a List

You can find out how many items are in a list using the `len()` function.

```python
auditing_standards = ["AU-C 200", "AU-C 315", "AU-C 500", "AU-C 700"]
standard_count = len(auditing_standards)  # 4
```

---

### 🔒 Tuples

Tuples are similar to lists, but they are immutable, meaning their elements cannot be changed after creation. Tuples are defined using parentheses `()`.

```python
# Creating a tuple (e.g., a journal entry pair: debit, credit)
journal_pair = ("Cash", "Revenue")

debit_account = journal_pair[0]
credit_account = journal_pair[1]

print(f"Debit: {debit_account}, Credit: {credit_account}")
```

The output of the above code will be:

```
Debit: Cash, Credit: Revenue
```

You can check the type of a tuple using the `type()` function:

```python
print(type(("Cash", "Revenue")))  # Output: <class 'tuple'>
```

Tuples are often used to represent fixed collections of items, such as account pairings, coordinates, or RGB color values.

Although you may not use tuples frequently, it's important to be aware of them as they are commonly used in Python programming.

---

## 🔁 Loops

Loops are used to execute a block of code repeatedly. In Python, there are two main types of loops: `for` loops and `while` loops.

---

### ➡️ For Loops

You can use `for` loops to iterate over the elements of a list. This allows you to perform operations on each item in the list.

```python
auditing_standards = ["AU-C 200", "AU-C 315", "AU-C 500", "AU-C 700"]

for standard in auditing_standards:
    print(standard)
```

Here's the output of the above code:

```
# Output:
AU-C 200
AU-C 315
AU-C 500
AU-C 700
```

You can also use loops to perform operations on each element in a list. For example, you can multiply each number in a list by 2.

```python
asset_costs = [50000, 75000, 30000]
useful_life = 5 # Assume 5-year straight-line, no salvage

for cost in asset_costs:
    # Calculate annual straight-line depreciation
    print(cost / useful_life)
```

Here's the output of the above code:

```
# Output:
10000.0
15000.0
6000.0
```

:::{tip} What is `cost` in the loop?

The `cost` variable in the `for` loop acts as a loop counter that takes on each value in the sequence generated by `range(5)`, which are the numbers 0 through 4. You can name this variable anything you like; it's just a placeholder for the current value in the iteration.

`cost` is commonly used as a convention, but you could use other names like `index`, `num`, or `item` depending on the context of your loop. The name of the variable does not affect the functionality of the loop; it simply represents the current item in the iteration. It is a temporary variable that exists only within the scope of the loop.

:::

#### 🛞 For Loop Examples

---

**🎯 Example: Counting Items in a List**

```{code} python
:label: count-items-in-a-list
:caption: Counting Audit Opinions in a List
:linenos:
:emphasize-lines: 10-12

# A list of audit opinions from various engagements
audit_opinions = ["Unqualified", "Qualified", "Unqualified", "Adverse",
nbsp;         "Unqualified", "Disclaimer", "Qualified", "Unqualified",
nbsp;         "Unqualified", "Unqualified", "Qualified", "Unqualified",
nbsp;         "Adverse", "Unqualified", "Unqualified", "Unqualified"]

num_unqualified = 0

# Counting the number of "Unqualified" opinions in the list
for opinion in audit_opinions:
    if opinion == "Unqualified":
        num_unqualified += 1

print(f"You have {num_unqualified} unqualified opinions.")
# Output: You have 10 unqualified opinions.
```

In @count-items-in-a-list code above, we iterate through the list of audit opinions and increment the `num_unqualified` counter each time we encounter "Unqualified". Finally, we print the total count.

The `+=` operator is a shorthand for incrementing a variable by a certain value. For example, `num_unqualified += 1` is equivalent to `num_unqualified = num_unqualified + 1`. Each time we find "Unqualified" in the list, we increase the count by 1 using this shorthand increment operator.

---

**🎯 Example: Summing Values in a List**

```{code} python
:label: sum-values-in-a-list
:caption: Summing Inventory Costs in a List
:linenos:
:emphasize-lines: 6-7

# Costs of different batches of inventory
inventory_costs = [1200, 1500, 800, 1350, 900]
total_inventory_cost = 0

# YOUR CODE BEGINS
for cost in inventory_costs:
    total_inventory_cost += cost
# YOUR CODE ENDS

print(f"Total inventory cost: ${total_inventory_cost}")
# Output: Total inventory cost: $5750
```

In the @sum-values-in-a-list code above, we iterate through the list of inventory costs and add each value to the `total_inventory_cost` variable. Finally, we print the total inventory cost.

---

**🎯 Example: Summing Negative Transactions**

```{code} python
:label: sum-negative-transactions-in-a-list
:caption: Summing Negative Transactions (e.g., Withdrawals) in a List
:linenos:
:emphasize-lines: 5-7

transactions = [1500, -500, 200, -80, -220, 100]
total_withdrawals = 0

# YOUR CODE BEGINS
for tx in transactions:
    if tx < 0:
        total_withdrawals += tx
# YOUR CODE ENDS

print(f"Sum of negative transactions: {total_withdrawals}") # Output: Sum of negative transactions: -800
```

In the @sum-negative-transactions-in-a-list code above, we iterate through the list of transactions and check if each number is negative (less than 0). If it is, we add it to the `total_withdrawals` variable. Finally, we print the total sum of negative transactions.

---

#### 🔢 Looping with `range()`

The `range()` function generates a sequence of numbers, which is often used in `for` loops to iterate a specific number of times.

```python
print(range(5))  # Output: range(0, 5)
```

The `range` object above represents a sequence of numbers from 0 to 4 (5 is exclusive). You can convert it to a list to see the actual numbers:

```python
for i in range(5):
    print(i)
```

Here's the output of the above code:

```
# Output:
0
1
2
3
4
```

We can use the `range()` function to dynamically generate indices for accessing elements in a list.

```python
tax_forms = ["Form 1040", "Form 1120", "Form 1065", "Form 941"]

for i in range(len(tax_forms)):
    print(f"Index {i}: {tax_forms[i]}")

# Output:
# Index 0: Form 1040
# Index 1: Form 1120
# Index 2: Form 1065
# Index 3: Form 941
```

This code iterates through the indices of the `tax_forms` list and prints each form by accessing it using its index. Note that `len(tax_forms)` returns the length of the list, which is 4 in this case, so `range(len(tax_forms))` generates the sequence 0, 1, 2, 3.

:::{tip} Why use `range(len(...))`?

The two code snippets below achieve the same result, but they do so in different ways.

**🖥️ Snippet 1 - Use a direct iteration over the list**

```python
for form in tax_forms:
    print(form)
```

**🖥️ Snippet 2 - Use `range(len(...))` to get indices**

```python
for i in range(len(tax_forms)):
    print(tax_forms[i])
```

The first snippet is more Pythonic and easier to read, as it directly iterates over the elements of the list. The second snippet, however, is useful when you need to access the index of each element, for example, if you want to print the index alongside the element or if you need to modify elements in place.

Another reason to use `range(len(...))` is when you need to iterate over multiple lists simultaneously by their indices, or when you need to access elements in a list based on their position. See the example below for a practical use case.

:::

&nbsp;

**🎯 Example: Comparing Two Lists Using Positional Indices**

Imagine you are performing an Accounts Receivable confirmation audit.

You are given two lists: `client_balances` and `customer_confirmations`. Each list contains the A/R balance for a customer as recorded by the client and as confirmed by the customer, respectively.

Your task is to compare their values **at each index** using a `for` loop, and count the number of balances that match. A balance is considered matching if the value at a given index in the `client_balances` list matches the value at the same index in the `customer_confirmations` list. Store the count of matching balances in a variable called `num_matching`.

You can assume that both lists have the same length.

You can assume that both lists have the same length (i.e., the same number of elements).

```{code} python
:label: compare-two-lists
:caption: Comparing A/R Balances Using Positional Indices
:linenos:
:emphasize-lines: 4-7

client_balances = [1500, 2200, 800, 5000, 1100]
customer_confirmations = [1500, 2200, 750, 5000, 1100] # Note the discrepancy at index 2

num_matching = 0
for i in range(len(client_balances)):
    if client_balances[i] == customer_confirmations[i]:
        num_matching += 1

print(f"Number of matching balances: {num_matching}")
# Output: Number of matching balances: 4
```

In @compare-two-lists code above, we iterate through the lists using their indices and compare the values at each index. If the values match, we increment the `num_matching` counter. Finally, we print the total number of matching balances.

The `+=` operator is a shorthand for incrementing a variable by a certain value. For example, `num_matching += 1` is equivalent to `num_matching = num_matching + 1`.

---

#### ♻️ Nested Loops

You can also use nested loops, which are loops inside other loops. This is useful for working with multi-dimensional lists.

```python
journal_entries = [["Cash", "Common Stock"], ["Inventory", "Accounts Payable"], ["COGS", "Inventory"]]

for entry in journal_entries:
    print(f"Entry: {entry}")
    for account in entry:
        print(f" -- Account: {account}")
```

Here's the output of the above code:

```
# Output:
Entry: ['Cash', 'Common Stock']
 -- Account: Cash
 -- Account: Common Stock
Entry: ['Inventory', 'Accounts Payable']
 -- Account: Inventory
 -- Account: Accounts Payable
Entry: ['COGS', 'Inventory']
 -- Account: COGS
 -- Account: Inventory
```

---

### 🔄 While Loops

A `while` loop continues to execute as long as a specified condition is `True`. This is useful for scenarios like calculating depreciation until an asset's book value reaches its salvage value.

```python
book_value = 50000 # Initial Cost
annual_depreciation = 8000
salvage_value = 10000
year = 0

while book_value > salvage_value:
    year += 1
    book_value -= annual_depreciation # Reduce book value by depreciation
    print(f"End of Year {year}: Book Value is {book_value}")

print(f"Asset fully depreciated to salvage value in {year} years.")
```

Here's the output of the above code:

```
# Output:
End of Year 1: Book Value is 42000
End of Year 2: Book Value is 34000
End of Year 3: Book Value is 26000
End of Year 4: Book Value is 18000
End of Year 5: Book Value is 10000
Asset fully depreciated to salvage value in 5 years.
```

:::{caution} Infinite Loops

An infinite loop occurs when the loop's condition never becomes `False`. This can cause your program to run indefinitely. In the example above, if we forgot the line `book_value -= annual_depreciation`, the `book_value` would always be 50000, the condition `book_value > salvage_value` would always be true, and the loop would never end.

:::

---

## 📖 Dictionaries

Dictionaries are another important collection type in Python. They store data in key-value pairs, allowing you to quickly retrieve values based on their associated keys.

:::{tip} Why are they called dictionaries?

Dictionaries are named after real-world dictionaries, where you look up a word (the key) to find its definition (the value). Similarly, in a Python dictionary, you use a key (like "Cost" or "Salvage Value") to access its corresponding value.

:::

---

### 🛠️ Dictionary Operations

#### 🆕 Creating Dictionaries

You can create a dictionary by placing key-value pairs inside curly braces `{}`, separated by commas. Each key is separated from its value by a colon `:`.

```python
# A dictionary representing a fixed asset
fixed_asset = {
    "name": "Delivery Van",
    "cost": 30000,
    "salvage_value": 5000,
    "useful_life_years": 5
}
```

You can check the type of a dictionary using the `type()` function:

```python
print(type({"key": "value"}))  # Output: <class 'dict'>
```

#### 🎯 Accessing Dictionary Values

To access a value in a dictionary, you use its key inside square brackets `[]`.

```python
name = fixed_asset["name"]              # "Delivery Van"
cost = fixed_asset["cost"]              # 30000
life = fixed_asset["useful_life_years"] # 5

print(name) # Output: Delivery Van
print(cost) # Output: 30000
print(life) # Output: 5
```

#### ✏️ Modifying Dictionaries

You can add new key-value pairs or update existing ones by assigning a value to a key.

```python
# Add new key-value pair
fixed_asset["acquisition_date"] = "2025-01-15"

# Update existing value
fixed_asset["cost"] = 31000
```

---

### 🧩 Nested Dictionaries

Dictionaries can also contain other dictionaries, allowing you to create complex data structures.

```python
# A dictionary of tax clients
tax_clients = {
    "client_101": {
        "name": "ABC Corp",
        "entity_type": "C-Corp",
        "fiscal_year_end": "12-31"
    },
    "client_102": {
        "name": "Smith LLC",
        "entity_type": "S-Corp",
        "fiscal_year_end": "12-31"
    }
}
```

---

### 🔎 Looping Through Dictionaries

You can use a `for` loop to iterate over the keys in a dictionary. You can then use these keys to access the corresponding values.

```python
for client_id in tax_clients:
    client_data = tax_clients[client_id]
    print(f"Client {client_id}: {client_data['name']} is a {client_data['entity_type']}.")
```

Here's the output of the above code:

```
# Output:
ABC Corp (client_101) is a C-Corp.
Smith LLC (client_102) is a S-Corp.
```

You can also loop through both keys and values using the `.items()` method.

```python
for person_key, person in people.items():
    print(f"{person_key}: {person['name']} is {person['age']} years old.")
```

Here's the output of the above code:

```
# Output:
person1: John is 30 years old.
person2: Jane is 25 years old.
```

---

## 🥣 Mixing Collections and Loops

The real power comes from combining lists and dictionaries.

You can have a **list of dictionaries**. This is perfect for representing a trial balance or a list of customers.

```python
# A list of Accounts Receivable
accounts_receivable = [
    {
        "customer_id": "C-001",
        "name": "Alpha Inc.",
        "balance": 15000
    },
    {
        "customer_id": "C-002",
        "name": "Bravo Co.",
        "balance": 8500
    }
]

for customer in accounts_receivable:
    print(f"{customer['name']} (ID: {customer['customer_id']}) owes ${customer['balance']}.")
```

Here's the output of the above code:

```
# Output:
Alpha Inc. (ID: C-001) owes $15000.
Bravo Co. (ID: C-002) owes $8500.
```

You can also have a dictionary of lists, where each key represents a category and the value is a list of items in that category.

```python
# A simplified Chart of Accounts
chart_of_accounts = {
    "Assets": ["Cash", "Accounts Receivable", "Inventory"],
    "Liabilities": ["Accounts Payable", "Notes Payable"],
    "Equity": ["Common Stock", "Retained Earnings"]
}

for category, acct_list in chart_of_accounts.items():
    print(f"{category.upper()}:")
    for account in acct_list:
        print(f" - {account}")
```

Here's the output of the above code:

```
# Output:
ASSETS:
 - Cash
 - Accounts Receivable
 - Inventory
LIABILITIES:
 - Accounts Payable
 - Notes Payable
EQUITY:
 - Common Stock
 - Retained Earnings
```

---

**🎯 Example: Calculating Total Current Assets**

```{code} python
:label: total-current-assets-in-a-list-of-dictionaries
:caption: Calculate Total Current Assets from a list of accounts
:linenos:
:emphasize-lines: 29-33

balance_sheet_accounts = [
    {
        "name": "Cash",
        "category": "Current Asset",
        "balance": 50000
    },
    {
        "name": "Accounts Receivable",
        "category": "Current Asset",
        "balance": 120000
    },
    {
        "name": "Building",
        "category": "Long-Term Asset",
        "balance": 800000
    },
    {
      _ "name": "Inventory",
        "category": "Current Asset",
        "balance": 75000
    },
    {
        "name": "Accounts Payable",
        "category": "Current Liability",
        "balance": 60000
    }
]

total_current_assets = 0

for acct in balance_sheet_accounts:
    if acct["category"] == "Current Asset":
        total_current_assets += acct["balance"]

print(f"Total current assets: ${total_current_assets}") # Output: Total current assets: $245000
```

In the @total-current-assets-in-a-list-of-dictionaries code above, we iterate through the list of accounts. Each account is a dictionary.

The `if` statement inside the loop allows us to filter the accounts. It checks the value associated with the `"category"` key for each account. If that value is `"Current Asset"`, we add the value from the `"balance"` key to our `total_current_assets` variable.
