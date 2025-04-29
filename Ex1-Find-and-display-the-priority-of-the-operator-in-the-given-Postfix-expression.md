# EX 1 Display operator precedence in the infix expression.
## DATE:
## AIM:
To write a C program to find and display the priority of the operator in the given Postfix expression

## Algorithm
1. Start the program.
2. Read the postfix expression.
3. Traverse each character of the expression:
4. If the character is an operator (+, -, *, /, ^):
   Display its precedence.
   Assign priorities:
   ^ → 3
   * and / → 2
   * + and - → 1
    If the character is an operand, skip it.
5. End the program.

## Program:
```
/*
Program to find and display the priority of the operator in the given Postfix expression
Developed by: Joel John Jobinse
Register Number: 212223240062
*/

#include <stdio.h>

int precedence(char operator) {
    switch (operator) {
        case '^': return 3;
        case '*':
        case '/': return 2;
        case '+':
        case '-': return 1;
        default: return -1; // Not an operator
    }
}

int main() {
    char expr[100];
    int i, p;
    
    printf("Enter the postfix expression: ");
    scanf("%s", expr);
    
    printf("\nOperator Precedence:\n");
    for (i = 0; expr[i] != '\0'; i++) {
        p = precedence(expr[i]);
        if (p != -1) {
            printf("Operator '%c' has precedence %d\n", expr[i], p);
        }
    }
    
    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/928b4f46-4ad5-497e-819c-80c51705a80b)


## Result:
Thus the C program to find and display the priority of the operator in the given Postfix expression is implemented successfully
