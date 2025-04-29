# Ex4 Evaluation of prefix expression
## DATE: 19/02/2025
## AIM:
To write a C function to evaluate the given prefix expression using stack and print the output of the given prefix expression from the stack inside the function . 

## Algorithm
1. Start the program.
2. Read the prefix expression.
3. Initialize an empty stack.
4. Scan the expression from right to left:
   - If the character is an operand, push it onto the stack.
   - If the character is an operator, pop two elements from the stack, apply the operator, and push the result back onto the stack.
5. After the entire expression is scanned, the final result will be at the top of the stack.
6. Print the final result.
7. End the program.

 

## Program:
```
/*
Program to evaluate the given prefix expression
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <ctype.h>
#include <math.h>

#define MAX 100

int stack[MAX];
int top = -1;

void push(int c) {
    stack[++top] = c;
}

int pop() {
    return stack[top--];
}

int evaluatePrefix(char prefix[]) {
    int i;
    
    for (i = strlen(prefix) - 1; i >= 0; i--) {
        if (isdigit(prefix[i])) {
            push(prefix[i] - '0'); // Convert char to int
        } else {
            int op1 = pop();
            int op2 = pop();
            
            switch (prefix[i]) {
                case '+': push(op1 + op2); break;
                case '-': push(op1 - op2); break;
                case '*': push(op1 * op2); break;
                case '/': push(op1 / op2); break;
                case '^': push(pow(op1, op2)); break;
            }
        }
    }
    
    return pop();
}

int main() {
    char prefix[MAX];
    int result;

    printf("Enter the prefix expression: ");
    scanf("%s", prefix);

    result = evaluatePrefix(prefix);
    printf("Result of prefix expression: %d\n", result);

    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/641b8022-6f2a-4df4-9f3a-923605a8c51f)

## Result:
Thus, the C program to evaluate the prefix expression using stack and print the output of the given prefix expression from the stack inside the function is implemented successfully.
