# Ex2 Conversion of the infix expression into postfix expression
## DATE: 19/02/2025
## AIM:
To write a C program to convert the infix expression into postfix form using stack by following the operator precedence and associative rule.

## Algorithm
1. Start the program.
2. Read the infix expression.
3. Initialize an empty stack for operators and an empty string for the postfix expression.
4. Scan the infix expression from left to right:
   - If the scanned character is an operand, add it to the postfix expression.
   - If the scanned character is an operator, pop from the stack and add to the postfix expression until the stack is empty or the precedence of the scanned operator is greater than the top of the stack. Then push the scanned operator onto the stack.
   - If the scanned character is '(', push it onto the stack.
   - If the scanned character is ')', pop and add to the postfix expression until a '(' is encountered on the stack (pop '(' but do not add it).
5. After scanning the infix expression, pop and add all remaining operators from the stack to the postfix expression.
6. Display the postfix expression.
7. End the program.

## Program:
```
/*
Program to convert the infix expression into postfix expression
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <ctype.h>
#include <string.h>

#define MAX 100

char stack[MAX];
int top = -1;

void push(char c) {
    stack[++top] = c;
}

char pop() {
    if (top == -1)
        return -1;
    else
        return stack[top--];
}

int precedence(char c) {
    if (c == '^')
        return 3;
    else if (c == '*' || c == '/')
        return 2;
    else if (c == '+' || c == '-')
        return 1;
    else
        return 0;
}

int main() {
    char infix[MAX], postfix[MAX];
    int i, k = 0;
    char c;
    
    printf("Enter the infix expression: ");
    scanf("%s", infix);

    for (i = 0; i < strlen(infix); i++) {
        c = infix[i];
        
        if (isalnum(c)) {
            postfix[k++] = c;
        } 
        else if (c == '(') {
            push(c);
        } 
        else if (c == ')') {
            while (top != -1 && stack[top] != '(') {
                postfix[k++] = pop();
            }
            pop(); // Remove '('
        } 
        else { // Operator encountered
            while (top != -1 && precedence(stack[top]) >= precedence(c)) {
                postfix[k++] = pop();
            }
            push(c);
        }
    }

    while (top != -1) {
        postfix[k++] = pop();
    }

    postfix[k] = '\0';

    printf("Postfix expression: %s\n", postfix);

    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/8062d860-8c4a-4e43-9cac-f1f8ef2922e8)


## Result:
Thus, the C program to convert the infix expression into postfix form using stack by following the operator precedence and associative rule is implemented successfully.
