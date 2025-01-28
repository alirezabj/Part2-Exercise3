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
