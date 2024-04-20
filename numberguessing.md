#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

int main() {
    srand(time(NULL)); // Seed for random number generation
    int secretNumber = rand() % 100 + 1; // Generate a random number between 1 and 100
    int guess;
    int attempts = 0;

    cout << "Welcome to the Number Guessing Game!\n";
    cout << "I have chosen a number between 1 and 100. Try to guess it.\n\n";

    do {
        cout << "Enter your guess: ";
        cin >> guess;
        attempts++;

        if (guess > secretNumber) {
            cout << "Too high! Try again.\n\n";
        } else if (guess < secretNumber) {
            cout << "Too low! Try again.\n\n";
        } else {
            cout << "\nCongratulations! You've guessed the number (" << secretNumber << ") correctly in " << attempts << " attempts.\n";
        }
    } while (guess != secretNumber);

    return 0;
}
 
