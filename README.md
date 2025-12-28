import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from datetime import datetime, timedelta

books = {
    "Book ID": [1, 2, 3, 4, 5],
    "Title": ["Python Basics", "Data Science 101", "Machine Learning", "AI Concepts", "Statistics"],
    "Author": ["John", "Alice", "Bob", "Carol", "David"],
    "Total Copies": [5, 3, 4, 2, 6]
}

books_df = pd.DataFrame(books)

borrow_data = {
    "Borrower Name": ["Ravi", "Anita", "Ravi", "Suman", "Anita", "Ravi"],
    "Book Title": ["Python Basics", "Data Science 101", "Python Basics",
                   "Machine Learning", "Python Basics", "AI Concepts"],
    "Borrow Date": pd.to_datetime([
        "2025-01-01", "2025-01-03", "2025-01-10",
        "2025-01-05", "2025-01-12", "2025-01-15"
    ])
}

borrow_df = pd.DataFrame(borrow_data)
borrow_df["Due Date"] = borrow_df["Borrow Date"] + timedelta(days=7)

print("\nAvailable Books:\n")
print(books_df)

print("\nBorrowing Records:\n")
print(borrow_df)

book_usage = borrow_df["Book Title"].value_counts()

print("\nBook Usage Count:\n")
print(book_usage)

plt.figure(figsize=(8, 5))
book_usage.plot(kind="bar")
plt.title("Most Borrowed Books")
plt.xlabel("Book Title")
plt.ylabel("Number of Times Borrowed")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

most_popular = book_usage.idxmax()
least_popular = book_usage.idxmin()

print("\nSummary:")
print("Most popular book:", most_popular)
print("Least popular book:", least_popular)
