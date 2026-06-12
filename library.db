import sqlite3

conn = sqlite3.connect("library.db")
cursor = conn.cursor()

cursor.execute("""
CREATE TABLE IF NOT EXISTS books (
    id INTEGER PRIMARY KEY,
    title TEXT,
    author TEXT
)
""")
conn.commit()

while True:
    print("\n--- Library Management System ---")
    print("1. Add Book")
    print("2. View Books")
    print("3. Search Book")
    print("4. Delete Book")
    print("5. Exit")

    choice = input("Enter choice: ")

    if choice == "1":
        book_id = int(input("Enter Book ID: "))
        title = input("Enter Book Title: ")
        author = input("Enter Author Name: ")

        cursor.execute(
            "INSERT INTO books VALUES (?, ?, ?)",
            (book_id, title, author)
        )
        conn.commit()
        print("Book Added Successfully")

    elif choice == "2":
        cursor.execute("SELECT * FROM books")
        books = cursor.fetchall()

        if books:
            print("\nBooks List:")
            for book in books:
                print("ID:", book[0], "Title:", book[1], "Author:", book[2])
        else:
            print("No Books Found")

    elif choice == "3":
        title = input("Enter Book Title to Search: ")

        cursor.execute(
            "SELECT * FROM books WHERE title=?",
            (title,)
        )
        book = cursor.fetchone()

        if book:
            print("Book Found:")
            print("ID:", book[0], "Title:", book[1], "Author:", book[2])
        else:
            print("Book Not Found")

    elif choice == "4":
        book_id = int(input("Enter Book ID to Delete: "))

        cursor.execute(
            "DELETE FROM books WHERE id=?",
            (book_id,)
        )
        conn.commit()

        print("Book Deleted Successfully")

    elif choice == "5":
        print("Thank You")
        break

    else:
        print("Invalid Choice")

conn.close()