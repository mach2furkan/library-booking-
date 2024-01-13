      #include <iostream>
        using namespace std;
              const int MAX_BOOKS = 10;

      // Structure representing a book chair
      struct BookChair {
    string bookTitle;
    bool isAvailable;
};


      // Function to display the status of book chairs
    void displayBookChairs(BookChair* library, int size) {
    cout << "Library Status:\n";
    for (int i = 0; i < size; ++i) {
        cout << "Chair " << i + 1 << ": ";
        if (library[i].isAvailable) {
            cout << "Available\n";
        } else {
            cout << "Checked Out (Book Title: " << library[i].bookTitle << ")\n";
        }
    }
    cout << endl;
}

    // Function to check out a book chair
    void checkOutBookChair(BookChair* library, int chairNumber, const string& bookTitle) {
    if (chairNumber >= 1 && chairNumber <= MAX_BOOKS) {
        if (library[chairNumber - 1].isAvailable) {
            library[chairNumber - 1].isAvailable = false;
            library[chairNumber - 1].bookTitle = bookTitle;
            cout << "Checked out successfully!\n";
        } else {
            cout << "Chair is already checked out.\n";
        }
    } else {
        cout << "Invalid chair number.\n";
    }
}


      // Function to return a book chair
    void returnBookChair(BookChair* library, int chairNumber) {
    if (chairNumber >= 1 && chairNumber <= MAX_BOOKS) {
        if (!library[chairNumber - 1].isAvailable) {
            library[chairNumber - 1].isAvailable = true;
            library[chairNumber - 1].bookTitle = "";
            cout << "Returned successfully!\n";
        } else {
            cout << "Chair is already available.\n";
        }
    } else {
        cout << "Invalid chair number.\n";
    }
    }

    int main() {
    using namespace std; // Using namespace std

    // Create an array of book chairs
    BookChair library[MAX_BOOKS];

    // Initialize book chairs
    for (int i = 0; i < MAX_BOOKS; ++i) {
        library[i].isAvailable = true;
        library[i].bookTitle = "";
    }

    int choice;
    do {
        // Display menu
        cout << "Library Management System\n";
        cout << "1. Display Book Chairs\n";
        cout << "2. Check Out a Book Chair\n";
        cout << "3. Return a Book Chair\n";
        cout << "0. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                displayBookChairs(library, MAX_BOOKS);
                break;
            case 2: {
                int chairNumber;
                string bookTitle;
                cout << "Enter the chair number and book title: ";
                cin >> chairNumber >> bookTitle;
                checkOutBookChair(library, chairNumber, bookTitle);
                break;
            }
            case 3: {
                int chairNumber;
                cout << "Enter the chair number: ";
                cin >> chairNumber;
                returnBookChair(library, chairNumber);
                break;
            }
            case 0:
                cout << "Exiting program.\n";
                break;
            default:
                cout << "Invalid choice. Please try again.\n";
        }

    } while (choice != 0);

    return 0;
}
