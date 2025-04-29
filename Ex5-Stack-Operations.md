# Ex5 Stack Operations
## DATE: 19/02/2025
## AIM:
To write a C function to perform push and pop operation of the stack in the infix to postfix conversion.

## Algorithm
1. Start the program and define a stack using an array and a top pointer.
2. Define push() to add an element to the top of the stack.
3. Define pop() to remove and return the top element of the stack.
4. In the infix to postfix function:
   - Traverse the infix expression from left to right.
   - If the character is an operand, add it to the postfix expression.
   - If the character is an operator:
     - While the stack is not empty and the precedence of the top of the stack is greater than or equal to the current operator, pop and append to postfix.
     - Push the current operator onto the stack.
   - If the character is an opening parenthesis, push it.
   - If it’s a closing parenthesis, pop and append to postfix until an opening parenthesis is found.
5. After scanning the infix expression, pop and append any remaining operators in the stack to the postfix expression.
6. Print the postfix expression.

## Program:
```
/*
Program to perform push and pop operations of the stack in the infix to postfix conversion
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <ctype.h>
#include <string.h>

#define SIZE 100

char stack[SIZE];
int top = -1;

void push(char item) {
    stack[++top] = item;
}

char pop() {
    if (top == -1)
        return -1;
    else
        return stack[top--];
}

int precedence(char op) {
    if (op == '^')
        return 3;
    else if (op == '*' || op == '/')
        return 2;
    else if (op == '+' || op == '-')
        return 1;
    else
        return 0;
}

void infixToPostfix(char* infix, char* postfix) {
    int i, k = 0;
    char ch;

    for (i = 0; infix[i] != '\0'; i++) {
        ch = infix[i];

        if (isalnum(ch)) {
            postfix[k++] = ch;
        }
        else if (ch == '(') {
            push(ch);
        }
        else if (ch == ')') {
            while (stack[top] != '(') {
                postfix[k++] = pop();
            }
            pop(); // remove '(' from stack
        }
        else {
            while (top != -1 && precedence(stack[top]) >= precedence(ch)) {
                postfix[k++] = pop();
            }
            push(ch);
        }
    }

    while (top != -1) {
        postfix[k++] = pop();
    }

    postfix[k] = '\0';
}

int main() {
    char infix[SIZE], postfix[SIZE];

    printf("Enter infix expression: ");
    scanf("%s", infix);

    infixToPostfix(infix, postfix);
    printf("Postfix expression: %s\n", postfix);

    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/eae68321-54a9-4779-b84e-f6545ce0efc1)

## Result:
Thus the C program to perform push and pop operation of the stack in the infix to postfix conversion is implemented successfully.
