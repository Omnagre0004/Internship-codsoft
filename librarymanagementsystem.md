#include <iostream>
#include <vector>
#include <string>
#include <algorithm>

using namespace std;

class Book {
    string title;
    string author;
    int year;

public:
    Book(string t, string a, int y) : title(t), author(a), year(y) {}

    string getTitle() const {
        return title;
    }

    string getAuthor() const {
        return author;
    }

    int getYear() const {
        return year;
    }
};

class Library {
    vector<Book> books;

public:
    void addBook(const Book& book) {
        books.push_back(book);
    }

    void displayBooks() {
        cout << "Library Books:\n";
        for (const auto& book : books) {
            cout << "Title: " << book.getTitle() << ", Author: " << book.getAuthor() << ", Year: " << book.getYear() << endl;
        }
    }

    void searchBook(const string& title) {
        auto it = find_if(books.begin(), books.end(), [&title](const Book& b) {
            return b.getTitle() == title;
        });

        if (it != books.end()) {
            cout << "Book found - Title: " << it->getTitle() << ", Author: " << it->getAuthor() << ", Year: " << it->getYear() << endl;
        } else {
            cout << "Book not found in the library." << endl;
        }
    }
};

int main() {
    Library library;

    // Add books
    library.addBook(Book("Book1", "Author1", 2000));
    library.addBook(Book("Book2", "Author2", 2010));
    library.addBook(Book("Book3", "Author3", 2020));

    // Display all books in the library
    library.displayBooks();

    // Search for a book by title
    library.searchBook("Book2");

    return 0;
}
