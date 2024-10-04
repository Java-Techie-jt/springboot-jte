# Spring Boot-jte (Java Template Engine)

```
@import com.javatechie.entity.Expense
@import java.util.List

@param Expense expense
@param List<Expense> expenses
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BudgetBuddy - Expense Tracker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f9f9f9;
            margin: 0;
            padding: 20px;
        }
        h1 {
            color: #333;
            text-align: center;
        }
        .container {
            width: 80%;
            margin: 0 auto;
        }
        form {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
        }
        label {
            font-weight: bold;
            display: block;
            margin-bottom: 5px;
        }
        input, select {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border-radius: 4px;
            border: 1px solid #ddd;
            box-sizing: border-box;
        }
        button {
            background-color: #28a745;
            color: #fff;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 20px;
        }
        table, th, td {
            border: 1px solid #ddd;
            padding: 10px;
        }
        th {
            background-color: #f2f2f2;
        }
        td {
            text-align: center;
        }
        a {
            text-decoration: none;
            color: #007bff;
        }
        a:hover {
            text-decoration: underline;
        }
        .actions a {
            margin: 0 5px;
        }
    </style>
</head>
<body>
<div class="container">
    <h1>BudgetBuddy - Track Your Expenses</h1>

    <!-- Expense Form for Adding/Editing -->
    <form action="/save" method="post">
        <input type="hidden" name="id" value="${expense.id}">

        <label for="description">Description</label>
        <input type="text" id="description" name="description" value="${expense.description}" required>

        <label for="amount">Amount</label>
        <input type="number" id="amount" name="amount" step="0.01" value="${expense.amount}" required>

        <label for="date">Date</label>
        <input type="date" id="date" name="date" value="${expense.date}" required>

        <label for="category">Category</label>
        <input type="text" id="category" name="category" value="${expense.category}" required>

        <button type="submit">${expense.id == null ? "Add Expense" : "Update Expense"}</button>
    </form>

    <!-- List of Expenses -->
    <h2>Your Expenses</h2>
    <table>
        <thead>
        <tr>
            <th>TxNo</th>
            <th>Description</th>
            <th>Amount</th>
            <th>Date</th>
            <th>Category</th>
            <th>Actions</th>
        </tr>
        </thead>
        <tbody>
        @for(Expense e : expenses)
            <tr>
                <td>${e.id}</td>
                <td>${e.description}</td>
                <td>${e.amount}</td>
                <td>${e.date}</td>
                <td>${e.category}</td>
                <td class="actions">
                    <a href="/edit/${e.id}">Edit</a>
                    <a href="/delete/${e.id}" onclick="return confirm('Are you sure?')">Delete</a>
                </td>
            </tr>
        @endfor
        </tbody>
    </table>
</div>
</body>
</html>

```

![Screenshot 2024-10-04 at 8 49 42 PM](https://github.com/user-attachments/assets/c7e60a03-0555-43e1-90fd-3bfe19a9df39)
![Screenshot 2024-10-04 at 8 49 54 PM](https://github.com/user-attachments/assets/7525ed93-c843-4991-a649-fa12e5b70f17)
![Screenshot 2024-10-04 at 8 50 01 PM](https://github.com/user-attachments/assets/203dcca9-c19d-409f-990f-f9a3b4015324)


