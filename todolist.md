#include <iostream>
#include <vector>
#include <string>

// Function to display the menu
void displayMenu() {
    std::cout << "===== To-Do List Manager =====" << std::endl;
    std::cout << "1. Add a new task" << std::endl;
    std::cout << "2. Mark a task as done" << std::endl;
    std::cout << "3. List all tasks" << std::endl;
    std::cout << "4. Exit" << std::endl;
    std::cout << "===============================" << std::endl;
}

int main() {
    std::vector<std::string> tasks;
    int choice;

    do {
        displayMenu();
        std::cout << "Enter your choice: ";
        std::cin >> choice;

        switch (choice) {
            case 1:
                {
                    std::string newTask;
                    std::cout << "Enter the new task: ";
                    std::cin.ignore();
                    std::getline(std::cin, newTask);
                    tasks.push_back(newTask);
                    std::cout << "Task added successfully!" << std::endl;
                    break;
                }
            case 2:
                {
                    int taskIndex;
                    std::cout << "Enter the index of the task to mark as done: ";
                    std::cin >> taskIndex;
                    if (taskIndex >= 0 && taskIndex < tasks.size()) {
                        tasks.erase(tasks.begin() + taskIndex);
                        std::cout << "Task marked as done!" << std::endl;
                    } else {
                        std::cout << "Invalid task index!" << std::endl;
                    }
                    break;
                }
            case 3:
                {
                    if (!tasks.empty()) {
                        std::cout << "Tasks:" << std::endl;
                        for (int i = 0; i < tasks.size(); ++i) {
                            std::cout << i << ". " << tasks[i] << std::endl;
                        }
                    } else {
                        std::cout << "No tasks in the list." << std::endl;
                    }
                    break;
                }
            case 4:
                std::cout << "Exiting the To-Do List Manager. Goodbye!" << std::endl;
                break;
            default:
                std::cout << "Invalid choice. Please try again." << std::endl;
        }
    } while (choice != 4);

    return 0;
}
