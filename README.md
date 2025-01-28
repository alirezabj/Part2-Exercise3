# Part2-Exercise3

The program will be modeled using two classes:
1. `MortgageCalculator`: Handles the core logic of calculating the monthly installment
2. `UserInterface`: Manages user input and output via the command line

## Class: `MortgageCalculator`
Purpose: Encapsulates the logic for calculating the monthly installment.
Attributes: None 

Methods: `calculateMonthlyInstallment(double principal, int loanTerm)`
Purpose: Calculates the monthly installment for the given principal and loan term.

Signature:`public static double calculateMonthlyInstallment(double principal, int loanTerm) throws IllegalArgumentException`

Preconditions:
1. `principal > 0`: Principal amount must be positive.
2. `loanTerm > 0 && loanTerm <= 300`: Loan term must be between 1 and 300 months.

Postconditions:
1. Returns the calculated monthly installment as a double.
2. Throws an exception if preconditions are violated.

Special Cases:
1. If loanTerm is 0 (though invalid by design), an `IllegalArgumentException` is raised to avoid division by zero.
2. If `principal` is 0, the method should return 0.
   

## Class: `UserInterface`
Purpose: Handles interactions with the user, ensuring valid inputs and displaying results.
Attributes: None

### Methods:
1. `getUserInput()`
   Purpose: Prompts the user to input the principal amount and loan term.

  Signature:`public static double[] getUserInput()`

  Preconditions: 
  1. User must provide valid numerical inputs via the command line.

  Postconditions:
  1. Returns an array containing the principal and loan term as [principal, loanTerm].
  2. Prints an error message and reprompts the user if inputs are invalid.
   
  Special Cases:
  1. If the user enters non-numerical data, reprompt until valid input is entered.


2. `displayResult(double result)`
   Purpose: Displays the calculated monthly installment.
   Signature: `public static void displayResult(double result)`

   Preconditions:
   1.`result >= 0`: The result must be non-negative.
  
   Postconditions:
   1. Prints the result to the console in a user-friendly format.
  

### Specifications: 
#### `calculateMonthlyInstallment`
```java
/**
 * @param principal The loan amount (must be positive).
 * @param loanTerm The loan term in months (must be between 1 and 300).
 * @return The monthly installment as a double.
 * @throws IllegalArgumentException if the inputs are invalid.
 * @.pre principal > 0 && loanTerm > 0 && loanTerm <= 300
 * @.post RESULT == (principal / loanTerm + principal / 240)
 */
public static double calculateMonthlyInstallment(double principal, int loanTerm) throws IllegalArgumentException {
    if (principal <= 0 || loanTerm <= 0 || loanTerm > 300) {
        throw new IllegalArgumentException("Invalid inputs: principal must be > 0 and loanTerm must be in range 1-300.");
    }
    return principal / loanTerm + principal / 240;
}

```

#### `getUserInput`
```java
/**
 * @return An array containing the principal and loan term as [principal, loanTerm].
 * @.pre true
 * @.post RESULT.length == 2 && RESULT[0] > 0 && RESULT[1] > 0 && RESULT[1] <= 300
 */
public static double[] getUserInput() {
    Scanner scanner = new Scanner(System.in);
    double principal = 0;
    int loanTerm = 0;
    boolean valid = false;

    while (!valid) {
        try {
            System.out.print("Enter the loan principal amount: ");
            principal = Double.parseDouble(scanner.nextLine());
            System.out.print("Enter the loan term in months (1-300): ");
            loanTerm = Integer.parseInt(scanner.nextLine());

            if (principal > 0 && loanTerm > 0 && loanTerm <= 300) {
                valid = true;
            } else {
                System.out.println("Invalid inputs. Please ensure principal > 0 and loan term is between 1 and 300.");
            }
        } catch (NumberFormatException e) {
            System.out.println("Invalid input format. Please enter valid numbers.");
        }
    }
    return new double[]{principal, loanTerm};
}
```

#### `displayResult`
```java
/**
 * @param result The calculated monthly installment.
 * @.pre result >= 0
 * @.post The result is displayed to the console in a user-friendly format.
 */
public static void displayResult(double result) {
    System.out.printf("The monthly installment is: %.2f%n", result);
}
```




