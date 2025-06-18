# ATM
This is a internship task with codsoft .codsoft is a dynamic tech company specializing in software development. It is a provider of IT management.
import java.util.Scanner;

public class ATM {
    static class BankAccount {
        private double balance;

        public BankAccount(double initialBalance) {
            this.balance = initialBalance;
        }

        public double getBalance() {
            return balance;
        }

        public void setBalance(double balance) {
            this.balance = balance;
        }
    }

    static class ATMInterface {
        private BankAccount account;

        public ATMInterface(BankAccount account) {
            this.account = account;
        }

        public void withdrawAmount(double amount) {
            if (amount <= 0) {
                System.out.println("Invalid amount. Please enter a positive value.");
            } else if (amount > account.getBalance()) {
                System.out.println("Insufficient balance.");
            } else {
                account.setBalance(account.getBalance() - amount);
                System.out.println("Withdrawal successful. New balance: " + account.getBalance());
            }
        }

        public void depositAmount(double amount) {
            if (amount <= 0) {
                System.out.println("Invalid amount. Please enter a positive value.");
            } else {
                account.setBalance(account.getBalance() + amount);
                System.out.println("Deposit successful. New balance: " + account.getBalance());
            }
        }

        public void checkBalance() {
            System.out.println("Current balance: " + account.getBalance());
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        BankAccount account = new BankAccount(1000.0);
        ATMInterface atm = new ATMInterface(account);

        while (true) {
            System.out.print("Enter 1 to withdraw, 2 to deposit, 3 to check balance, 0 to exit: ");
            int choice = scanner.nextInt();

            if (choice == 0) {
                break;
            } else if (choice == 1) {
                System.out.print("Enter amount to withdraw: ");
                double amount = scanner.nextDouble();
                atm.withdrawAmount(amount);
            } else if (choice == 2) {
                System.out.print("Enter amount to deposit: ");
                double amount = scanner.nextDouble();
                atm.depositAmount(amount);
            } else if (choice == 3) {
                atm.checkBalance();
            } else {
                System.out.println("Invalid choice.");
            }
        }

        scanner.close();
    }
}
