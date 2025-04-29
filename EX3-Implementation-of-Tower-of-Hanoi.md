# EX3 Implementation of Tower of Hanoi
## DATE:
## AIM:
To write a C program to implement Tower of Hanoi

## Algorithm
1. Start the program.'
2. Define a recursive function towerOfHanoi(n, source, auxiliary, destination):
   - If n == 1, move the disk from the source rod to the destination rod and return.
   - Recursively move n-1 disks from the source rod to the auxiliary rod using the destination rod.
   - Move the nth disk from the source rod to the destination rod.
   - Recursively move n-1 disks from the auxiliary rod to the destination rod using the source rod.
3. In the main function, input the number of disks.
4. Call the recursive function with appropriate parameters.
5. End the program.  

## Program:
```
/*
Program to implement Tower of Hanoi
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>

void towerOfHanoi(int n, char source, char auxiliary, char destination) {
    if (n == 1) {
        printf("Move disk 1 from %c to %c\n", source, destination);
        return;
    }
    towerOfHanoi(n - 1, source, destination, auxiliary);
    printf("Move disk %d from %c to %c\n", n, source, destination);
    towerOfHanoi(n - 1, auxiliary, source, destination);
}

int main() {
    int n;

    printf("Enter the number of disks: ");
    scanf("%d", &n);

    printf("The sequence of moves involved:\n");
    towerOfHanoi(n, 'A', 'B', 'C');

    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/84158fce-69a8-45ab-a185-6cb0ca64b178)

## Result:
Thus, the C program to implement Tower of Hanoi using recursion is implemented successfully.
