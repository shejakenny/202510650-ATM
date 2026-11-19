import java.util.Scanner;

public class ATMSimulation {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);

// 1. Predefined PIN and login variables
int correctPin = 1234;
int attempts = 0;
int maxAttempts = 3;
boolean isLoggedIn = false;

// 2. Authentication using a while loop
while (attempts < maxAttempts) {
System.out.print("Enter your PIN: ");
int enteredPin = scanner.nextInt();

if (enteredPin == correctPin) {
isLoggedIn = true;
System.out.println("Login successful!\n");
break;
} else {
attempts++;
System.out.println("Incorrect PIN. Attempts left: " + (maxAttempts - attempts));
}
}

// Stop the program if login failed after 3 attempts
if (!isLoggedIn) {
System.out.println("Maximum attempts reached. Account locked.");
scanner.close();
return;
}

// 3. Variables for balance and array for transaction history
double balance = 1000.0; // Starting balance
String[] transactions = new String[100]; // Array to store up to 100 transactions
int transactionCount = 0;
int choice = 0;

// 4. Main menu loop
while (choice != 5) {
System.out.println("===== ATM MENU =====");
System.out.println("1. Check Balance");
System.out.println("2. Deposit Money");
System.out.println("3. Withdraw Money");
System.out.println("4. View Transactions");
System.out.println("5. Exit");
System.out.print("Choose an option: ");
choice = scanner.nextInt();

if (choice == 1) {
// Check balance
System.out.println("Current Balance: $`" + balance + "\n");

} else if (choice == 2) {
// Deposit money
System.out.print("Enter deposit amount: ");
double deposit = scanner.nextDouble();

if (deposit > 0) {
balance = balance + deposit;
transactions[transactionCount] = "Deposited: `$" + deposit;
transactionCount++;
System.out.println("Deposit successful!\n");
} else {
System.out.println("Invalid amount.\n");
}

} else if (choice == 3) {
// Withdraw money
System.out.print("Enter withdrawal amount: ");
double withdraw = scanner.nextDouble();

if (withdraw > 0 && withdraw <= balance) {
balance = balance - withdraw;
transactions[transactionCount] = "Withdrew: $" + withdraw;
transactionCount++;
System.out.println("Withdrawal successful!\n");
} else {
System.out.println("Error: Insufficient balance or invalid amount.\n");
}

} else if (choice == 4) {
// View transaction history using a for loop
System.out.println("--- Transaction History ---");
if (transactionCount == 0) {
System.out.println("No transactions yet.");
} else {
for (int i = 0; i < transactionCount; i++) {
System.out.println((i + 1) + ". " + transactions[i]);
}
}
System.out.println();

} else if (choice == 5) {
// Exit
System.out.println("Thank you for using the ATM. Goodbye!");

} else {
System.out.println("Invalid option. Please try again.\n");
}

