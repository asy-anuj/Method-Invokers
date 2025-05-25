# Method-Invokers


#Account Management System (Java Console Application)
This is a simple **Java-based console application** for managing bank accounts using **Object-Oriented Programming (OOP)** principles. It allows users to create accounts, deposit money, withdraw money, and view account details — all via the terminal.


'''java
import java.util.ArrayList;
import java.util.Scanner;
// Account class represents individual bank account
class Account {
    private String accountNumber;     // Unique account number
    private String accountHolder;     // Name of the account holder
    private double balance;           // Current account balance

    // Constructor to initialize account details
    public Account(String accountNumber, String accountHolder, double initialBalance) {
        this.accountNumber = accountNumber;
        this.accountHolder = accountHolder;
        this.balance = initialBalance;
    }

    // Deposit method to add money to account
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposit successful.");
        } else {
            System.out.println("Invalid deposit amount.");
        }
    }

    // Withdraw method to take out money from account
    public void withdraw(double amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
            System.out.println("Withdrawal successful.");
        } else {
            System.out.println("Invalid or insufficient balance.");
        }
    }

    // Display all account details
    public void displayDetails() {
        System.out.println("Account Number: " + accountNumber);
        System.out.println("Account Holder: " + accountHolder);
        System.out.println("Balance: ₹" + balance);
    }

    // Getter method for account number (used to find accounts)
    public String getAccountNumber() {
        return accountNumber;
    }
}

// AccountManager class handles the logic and user interaction


class AccountManager {
    private ArrayList<Account> accounts = new ArrayList<>();  // List to store multiple accounts
    private Scanner scanner = new Scanner(System.in);         // Scanner to take user input

    // Start method to display the main menu and interact with user
    public void start() {
        int choice;
        do {
            // Displaying options
            System.out.println("\n--- Account Management System ---");
            System.out.println("1. Create Account");
            System.out.println("2. Deposit");
            System.out.println("3. Withdraw");
            System.out.println("4. Display Account Details");
            System.out.println("5. Exit");
            System.out.print("Enter choice: ");
            choice = scanner.nextInt();
            scanner.nextLine(); // Consume the newline character

            // Handling user choice
            switch (choice) {
                case 1: createAccount(); break;
                case 2: deposit(); break;
                case 3: withdraw(); break;
                case 4: displayDetails(); break;
                case 5: System.out.println("Exiting..."); break;
                default: System.out.println("Invalid choice.");
            }
        } while (choice != 5);  // Loop until user chooses to exit
    }

    // Method to create a new account and add to list
    private void createAccount() {
        System.out.print("Enter account number: ");
        String accNum = scanner.nextLine();
        System.out.print("Enter account holder name: ");
        String name = scanner.nextLine();
        System.out.print("Enter initial balance: ");
        double balance = scanner.nextDouble();
        scanner.nextLine(); // Consume newline

        // Creating and adding new account
        Account acc = new Account(accNum, name, balance);
        accounts.add(acc);
        System.out.println("Account created successfully.");
    }

    // Method to handle deposit
    private void deposit() {
        Account acc = findAccount();  // Find account using number
        if (acc != null) {
            System.out.print("Enter amount to deposit: ");
            double amount = scanner.nextDouble();
            scanner.nextLine();
            acc.deposit(amount);
        }
    }

    // Method to handle withdrawal
    private void withdraw() {
        Account acc = findAccount();  // Find account using number
        if (acc != null) {
            System.out.print("Enter amount to withdraw: ");
            double amount = scanner.nextDouble();
            scanner.nextLine();
            acc.withdraw(amount);
        }
    }

    // Method to display a specific account's details
    private void displayDetails() {
        Account acc = findAccount();  // Find account using number
        if (acc != null) {
            acc.displayDetails();
        }
    }

    // Method to search for an account by account number
    private Account findAccount() {
        System.out.print("Enter account number: ");
        String accNum = scanner.nextLine();
        for (Account acc : accounts) {
            if (acc.getAccountNumber().equals(accNum)) {
                return acc;
            }
        }
        System.out.println("Account not found.");
        return null;
    }
}

// Main class with main() method to start the application
public class AccountManagementSystem {
    public static void main(String[] args) {
        AccountManager manager = new AccountManager();  // Create manager object
        manager.start();  // Start the system
    }
} '''





