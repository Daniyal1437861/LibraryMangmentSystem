# LibraryMangmentSystem
books = []

def add_book():
    title = input("Enter book title: ")
    author = input("Enter author name: ")
    books.append({'title': title, 'author': author, 'issued': False})
    print("Book added successfully.\n")

def view_books():
    if not books:
        print("No books in library.\n")
    else:
        for i, book in enumerate(books):
            status = "Issued" if book['issued'] else "Available"
            print(f"{i+1}. {book['title']} by {book['author']} - {status}")
        print()

def issue_book():
    view_books()
    try:
        book_no = int(input("Enter book number to issue: ")) - 1
        if not books[book_no]['issued']:
            books[book_no]['issued'] = True
            print("Book issued successfully.\n")
        else:
            print("Book is already issued.\n")
    except (IndexError, ValueError):
        print("Invalid book number.\n")

def return_book():
    view_books()
    try:
        book_no = int(input("Enter book number to return: ")) - 1
        if books[book_no]['issued']:
            books[book_no]['issued'] = False
            print("Book returned successfully.\n")
        else:
            print("Book is not issued.\n")
    except (IndexError, ValueError):
        print("Invalid book number.\n")

def menu():
    while True:
        print("Library Menu:")
        print("1. Add Book")
        print("2. View Books")
        print("3. Issue Book")
        print("4. Return Book")
        print("5. Exit")
        choice = input("Enter your choice (1-5): ")
        if choice == '1':
            add_book()
        elif choice == '2':
            view_books()
        elif choice == '3':
            issue_book()
        elif choice == '4':
            return_book()
        elif choice == '5':
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Try again.\n")

menu()
