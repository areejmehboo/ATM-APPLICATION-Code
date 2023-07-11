# ATM-APPLICATION-Code
OOP Project about ATM Application using java ..
All code available
#code for ATM Application
import java.util.Scanner;

public class ATM {

private int balance;

private final int pincode;
//CONSTRUCTOR FOR MAIN CLASS
public ATM(int initialBalance, int pincode) {

this.balance = initialBalance;

this.pincode = pincode;

}

public int getBalance() {

return this.balance;

}

public boolean withdraw(int amount, int pin) {

if(pin != this.pincode) {

return false;

}

if(amount > this.balance) {

return false;

}

this.balance -= amount;

return true;

}

public void deposit(int amount) {

this.balance += amount;

}

public boolean transfer(int amount, ATM recevier, int pin){

if(pin != this.pincode) {

return false;

}

boolean success = this.withdraw(amount,pin);

if(success) {

recevier.deposit(amount);

return true;

}

else {

return false;

}

}

public static void waitForEnter() {

Scanner ins = new Scanner(System.in);

ins.nextLine();

}

public static void main(String[] args) {

// TODO Auto-generated method stub

Scanner ins = new Scanner(System.in);

ATM atm = new ATM(1000,1234);

while(true) {

System.out.println("1. View Balance");

System.out.println("2. Withdraw");

System.out.println("3. Deposit");

System.out.println("4. Transfer");

System.out.println("5. Exit");

System.out.print("Enter Your Choice :");

int choice = ins.nextInt();

switch(choice) {

case 1 -> {
    System.out.println("Your Balance is :"+atm.getBalance());
    
    waitForEnter();
        }

case 2 -> {
    System.out.println("Enter the Amoutn to Withdraw :");
    
    int wdamount = ins.nextInt();
    
    boolean success = atm.withdraw(wdamount,1234);
    
    if(success) {
        
        System.out.println("Withdraw Successfull");
        
    }else {
        
        System.out.println("Insufficient Balance...");
        
    }
    
    waitForEnter();
        }

case 3 -> {
    System.out.println("Enter the amout to deposite :");
    
    int dpamount = ins.nextInt();
    
    atm.deposit(dpamount);
    
    System.out.println("Deposit Successfull..");
    
    waitForEnter();
        }

case 4 -> {
    System.out.print("Enter The amout to Transfer:");
    
    int tsamount = ins.nextInt();
    
    System.out.print("Enter the receiver Pin Code:");
    
    int rpin = ins.nextInt();
    
    ATM receiver = new ATM(0,rpin);
    
    boolean transfersucceess = atm.transfer(tsamount, receiver, rpin);
    
    if(transfersucceess) {
        
        System.out.println("Transfer Successfull...");
        
    }
    
    else {
        
        System.out.println("Invalid pin or insuffecient ballance");
        
    }
    
    waitForEnter();
        }

case 5 -> {
    System.out.println("Thanks of using ATM..");
    
    System.exit(0);
        }

default -> System.out.println("Invalid Choice");

}

}

}

}
