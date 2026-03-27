# EX 39 C program to find sum of digits.
## DATE:
## AIM:
To write a C program to find sum of digits.

## Algorithm
1. Start 
2. Declare variables for the number (n), remainder (digit), and sum (sum = 0).
3. Read the number from the user using scanf().
4. Repeat while n > 0:
5. After the loop ends, the variable sum contains the sum of all digits.
6. Display the result using printf().  
7. End.

## Program:
```
/*
C program to find sum of digits.
Developed by: ARAVINDHAN K A P
RegisterNumber:  212222063001
*/

#include <stdio.h>

int main() {
    int n, digit, sum = 0;

    printf("Enter a number: ");
    scanf("%d", &n);

    while (n > 0) {
        digit = n % 10;
        sum += digit;
        n = n / 10;
    }

    printf("Sum of digits = %d\n", sum);

    return 0;
}
```

## Output:

![image](https://github.com/user-attachments/assets/5379dc90-59bc-4083-bd55-859ac2356248)



## Result:
Thus the program was executed and the output was verified successfully.
