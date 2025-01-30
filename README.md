# Part2-Exercise3

The program will be developed using two classes:
1. `MortgageCalculator`: Handles the logic of calculating the monthly installment
2. `UserInterface`: Manages user input and output 

## Class: `MortgageCalculator`
Purpose: Encapsulates the logic for calculating the monthly installment.

Methods: `calculateMonthlyInstallment(double principal, int loanTerm)`

Purpose: Calculates the monthly installment for the given principal and loan term.

Signature:`public static double calculateMonthlyInstallment(double principal, int loanTerm) throws IllegalArgumentException`

Preconditions:
1. `principal > 0`: Principal amount must be positive.
2. `loanTerm > 0 && loanTerm <= 300`: Loan term must be between 1 and 300 months.

Postconditions:
1. Returns the calculated monthly installment as a double.
2. Throws an exception if preconditions are not met.

Special Cases:
1. If loanTerm is 0, an `IllegalArgumentException` is raised to avoid division by zero.
2. If `principal` is 0, the method should return 0.
   

## Class: `UserInterface`
Purpose: Handles interactions with the user, ensuring valid inputs and displaying results.

### Methods:
`getUserInput()`
   Purpose: Prompts the user to input the principal amount and loan term.

  Signature:`public static double[] getUserInput()`

  Preconditions: 
  1. User must provide valid numerical inputs via the command line.

  Postconditions:
  1. Returns an array containing the principal and loan term as [principal, loanTerm].
  2. Prints an error message and reprompts the user if inputs are invalid.
   
  Special Cases:
  1. If the user doesnt enter numerical data, prompt again until valid input is entered.

`displayResult(double result)`

   Purpose: Displays the calculated monthly installment.
   
   Signature: `public static void displayResult(double result)`

   Preconditions:
   
   1. `result >= 0`: The result must not be negative.
  
   Postconditions:
   
   1. Prints the result to the console in a user friendly format.
  

### Specifications: 
#### `calculateMonthlyInstallment`
```java
/**
 * Calculates the monthly installment based on the provided principal and loan term
 * @param principal The loan amount (must be positive)
 * @param loanTerm The loan term in months (must be between 1 and 300)
 * @return The monthly installment as a double
 * @throws IllegalArgumentException if the inputs are invalid
 * @.pre principal > 0 && loanTerm > 0 && loanTerm <= 300
 * @.post RESULT == (principal / loanTerm + principal / 240)
 */
public static double calculateMonthlyInstallment(double principal, int loanTerm) throws IllegalArgumentException 
```

#### `getUserInput`
```java
/**
 * Prompts the user for principal and loan term
 * @return An array containing the principal and loan term as [principal, loanTerm]
 * @.pre true
 * @.post RESULT.length == 2 && RESULT[0] > 0 && RESULT[1] > 0 && RESULT[1] <= 300
 */
public static double[] getUserInput() 
```

#### `displayResult`
```java
/**
 * Displays the calculated monthly installment to the user
 * @param result The calculated monthly installment
 * @.pre result >= 0
 * @.post The result is displayed to the console in a user-friendly format
 */
public static void displayResult(double result) 
```



Therefore the progrm flow is like this: 
1. The main() method is located in the UserInterface class.
2. The user is prompted to enter the principal amount and loan term.
3. Inputs are validated to ensure they meet the preconditions.
4. The calculateMonthlyInstallment method in MortgageCalculator is called to compute the monthly installment.
5. The result is displayed to the user using the displayResult method.




