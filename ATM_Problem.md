# ATM Machine

You are tasked with designing an ATM machine that allows users to perform various operations such as checking their balance, withdrawing cash, depositing cash, and transferring funds between accounts. The ATM should maintain a record of each user's account balance and should handle multiple users.

## Problem Statement

Implement a class `ATM` that simulates the operations of an ATM machine. The ATM should support the following operations:

1. **Check Balance**: Return the current balance of the user.
2. **Withdraw Cash**: Withdraw a specified amount of cash from the user's account if sufficient funds are available. If the withdrawal is successful, return true; otherwise, return false.
3. **Deposit Cash**: Deposit a specified amount of cash into the user's account.
4. **Transfer Funds**: Transfer a specified amount of cash from the current user's account to another user's account. If the transfer is successful, return true; otherwise, return false.

### Class Definition

```java
class ATM {
    // Constructor to initialize the ATM
    public ATM();

    // Method to check the balance of the user
    public int checkBalance();

    // Method to withdraw cash from the user's account
    // Returns true if the withdrawal is successful, false otherwise
    public boolean withdraw(int amount);

    // Method to deposit cash into the user's account
    public void deposit(int amount);

    // Method to transfer funds to another user's account
    // Returns true if the transfer is successful, false otherwise
    public boolean transfer(ATM other, int amount);
}
```
## Input Format

    The ATM class should be initialized without any parameters.
    The withdraw, deposit, and transfer methods will receive an integer amount as input.

## Output Format

    The checkBalance method should return the current balance as an integer.
    The withdraw and transfer methods should return true or false based on the success of the operation.
	
```java	
ATM atm1 = new ATM();
ATM atm2 = new ATM();
atm1.deposit(1000);
System.out.println(atm1.checkBalance()); // Output: 1000
System.out.println(atm1.withdraw(500));   // Output: true
System.out.println(atm1.checkBalance());   // Output: 500
System.out.println(atm1.transfer(atm2, 200)); // Output: true
System.out.println(atm1.checkBalance());   // Output: 300
System.out.println(atm2.checkBalance());   // Output: 200
```

## Output

```
1000
true
500
true
300
200

```

## Constraints

- The balance of the user will always be a non-negative integer.
- The amount for withdrawal, deposit, and transfer will be a positive integer.
- The ATM should handle multiple users, but for simplicity, you can assume only one user is interacting with the ATM at a time.

## Solution
```java
class ATM {
    private int balance;

    // Constructor to initialize the ATM
    public ATM() {
        this.balance = 0;
    }

    // Method to check the balance of the user
    public int checkBalance() {
        return this.balance;
    }

    // Method to withdraw cash from the user's account
    public boolean withdraw(int amount) {
        if (amount <= this.balance) {
            this.balance -= amount;
            return true;
        }
        return false;
    }

    // Method to deposit cash into the user's account
    public void deposit(int amount) {
        this.balance += amount;
    }

    // Method to transfer funds to another user's account
    public boolean transfer(ATM other, int amount) {
        if (this.withdraw(amount)) {
            other.deposit(amount);
            return true;
        }
        return false;
    }
}

```
