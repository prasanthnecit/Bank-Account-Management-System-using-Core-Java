import java.util.*;

class Account {
    private String accountNumber;
    private String accountHolder;
    private double balance;

    public Account(String accountNumber, String accountHolder, double balance) {
        this.accountNumber = accountNumber;
        this.accountHolder = accountHolder;
        this.balance = balance;
    }

    public String getAccountNumber() {
        return accountNumber;
    }

    public String getAccountHolder() {
        return accountHolder;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposit successful. New balance: " + balance);
        } else {
            System.out.println("Invalid deposit amount.");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawal successful. New balance: " + balance);
        } else {
            System.out.println("Invalid withdrawal amount or insufficient balance.");
        }
    }

    public void transfer(Account recipient, double amount) {
        if (amount > 0 && amount <= balance) {
            this.withdraw(amount);
            recipient.deposit(amount);
            System.out.println("Transfer successful to " + recipient.getAccountHolder());
        } else {
            System.out.println("Invalid transfer amount or insufficient balance.");
        }
    }
}

class Bank {
    private Map<String, Account> accounts = new HashMap<>();

    public void createAccount(String accountNumber, String accountHolder, double initialDeposit) {
        if (!accounts.containsKey(accountNumber)) {
            Account account = new Account(accountNumber, accountHolder, initialDeposit);
            accounts.put(accountNumber, account);
            System.out.println("Account created successfully.");
        } else {
            System.out.println("Account number already exists.");
        }
    }

    public Account getAccount(String accountNumber) {
        return accounts.get(accountNumber);
    }
}

public class BankManagementSystem {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Bank bank = new Bank();

        while (true) {
            System.out.println("\nBank Account Management System");
            System.out.println("1. Create Account");
            System.out.println("2. Deposit");
            System.out.println("3. Withdraw");
            System.out.println("4. Transfer");
            System.out.println("5. Check Balance");
            System.out.println("6. Exit");
            System.out.print("Choose an option: ");

            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter Account Number: ");
                    String accNum = scanner.nextLine();
                    System.out.print("Enter Account Holder Name: ");
                    String accHolder = scanner.nextLine();
                    System.out.print("Enter Initial Deposit: ");
                    double deposit = scanner.nextDouble();
                    bank.createAccount(accNum, accHolder, deposit);
                    break;
                case 2:
                    System.out.print("Enter Account Number: ");
                    Account depositAcc = bank.getAccount(scanner.next());
                    if (depositAcc != null) {
                        System.out.print("Enter Amount to Deposit: ");
                        depositAcc.deposit(scanner.nextDouble());
                    } else {
                        System.out.println("Account not found.");
                    }
                    break;
                case 3:
                    System.out.print("Enter Account Number: ");
                    Account withdrawAcc = bank.getAccount(scanner.next());
                    if (withdrawAcc != null) {
                        System.out.print("Enter Amount to Withdraw: ");
                        withdrawAcc.withdraw(scanner.nextDouble());
                    } else {
                        System.out.println("Account not found.");
                    }
                    break;
                case 4:
                    System.out.print("Enter Your Account Number: ");
                    Account sender = bank.getAccount(scanner.next());
                    if (sender != null) {
                        System.out.print("Enter Recipient Account Number: ");
                        Account receiver = bank.getAccount(scanner.next());
                        if (receiver != null) {
                            System.out.print("Enter Amount to Transfer: ");
                            sender.transfer(receiver, scanner.nextDouble());
                        } else {
                            System.out.println("Recipient account not found.");
                        }
                    } else {
                        System.out.println("Sender account not found.");
                    }
                    break;
                case 5:
                    System.out.print("Enter Account Number: ");
                    Account balanceAcc = bank.getAccount(scanner.next());
                    if (balanceAcc != null) {
                        System.out.println("Account Holder: " + balanceAcc.getAccountHolder());
                        System.out.println("Current Balance: " + balanceAcc.getBalance());
                    } else {
                        System.out.println("Account not found.");
                    }
                    break;
                case 6:
                    System.out.println("Exiting... Thank you!");
                    scanner.close();
                    System.exit(0);
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}
