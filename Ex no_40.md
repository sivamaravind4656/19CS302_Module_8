## Given an array of strings sorted in lexicographical order, print all of its permutations in strict lexicographical order. If two permutations look the same, only print one of them. See the 'note' below for an example.

Complete the function next_permutation which generates the permutations in the described order.

## For example, s=[ab,bc,cd]. The six permutations in correct order are:

ab bc cd
ab cd bc
bc ab cd
bc cd ab
cd ab bc
cd bc ab
Note: There may be two or more of the same string as elements of .
## For example, s=[ab,bc,cd]. Only one instance of a permutation where all elements match should be printed. In other words, if s[0]==s[1], then print either s[0]  or s[1] but not both.

A three element array having three distinct elements has six permutations as shown above. In this case, there are three matching pairs of permutations where ab and ba are switched. We only print the three visibly unique permutations:

ab ab bc
ab bc ab
bc ab ab
## Input Format

The first line of each test file contains a single integer , the length of the string array .

Each of the next  lines contains a string .

Constraints

 contains only lowercase English letters.
Output Format

Print each permutation as a list of space-separated strings on a single line.

## Sample Input 0

2
ab
cd
## Sample Output 0

ab cd
cd ab
## Sample Input 1

3
a
bc
bc
## Sample Output 1

a bc bc
bc a bc
bc bc a


## AIM:
To determine an array of strings sorted in lexicographical order, print all of its permutations in strict lexicographical order. If two permutations look the same, only print one of them.


## ALGORITHM:
1. Start
2. Sort the array of strings lexicographically.
3. Use next_permutation (like in C++ STL) to generate permutations.
4. Store or track printed permutations to avoid duplicates.
5. Print each unique permutation as a space-separated string.
6. End


## PROGRAM:
```
/*
C program to find the smallest among three numbers using Structure.
Developed by: ARAVINDHAN K A P
RegisterNumber:  212222063001
*/
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define MAX 100

// Function to compare two strings for qsort
int cmpstr(const void *a, const void *b) {
    return strcmp(*(const char **)a, *(const char **)b);
}

// Swap two strings
void swap(char **a, char **b) {
    char *temp = *a;
    *a = *b;
    *b = temp;
}

// Function to generate next lexicographical permutation
int next_permutation(char *arr[], int n) {
    int i = n - 2;

    while (i >= 0 && strcmp(arr[i], arr[i + 1]) >= 0) {
        i--;
    }
    if (i < 0) return 0;

    int j = n - 1;
    while (strcmp(arr[j], arr[i]) <= 0) {
        j--;
    }

    swap(&arr[i], &arr[j]);

    // Reverse the suffix
    int l = i + 1, r = n - 1;
    while (l < r) {
        swap(&arr[l], &arr[r]);
        l++;
        r--;
    }

    return 1;
}

// Function to print the permutation
void print_perm(char *arr[], int n) {
    for (int i = 0; i < n; i++) {
        printf("%s", arr[i]);
        if (i < n - 1) printf(" ");
    }
    printf("\n");
}

// Function to check if two arrays are equal
int equal_perm(char *a[], char *b[], int n) {
    for (int i = 0; i < n; i++) {
        if (strcmp(a[i], b[i]) != 0)
            return 0;
    }
    return 1;
}

int main() {
    int n;
    scanf("%d", &n);

    char buffer[n][MAX];
    char *arr[n];

    for (int i = 0; i < n; i++) {
        scanf("%s", buffer[i]);
        arr[i] = buffer[i];
    }

    // Sort initially to start from the smallest lex permutation
    qsort(arr, n, sizeof(char *), cmpstr);

    char *last_printed[n];
    for (int i = 0; i < n; i++) {
        last_printed[i] = strdup(arr[i]);
    }
    print_perm(arr, n);

    while (next_permutation(arr, n)) {
        // Only print if this permutation is not a duplicate
        int is_dup = equal_perm(arr, last_printed, n);
        if (!is_dup) {
            print_perm(arr, n);
            for (int i = 0; i < n; i++) {
                strcpy(last_printed[i], arr[i]);
            }
        }
    }

    return 0;
}
```

## OUTPUT:

![image](https://github.com/user-attachments/assets/0624fa55-44b2-4d13-b148-d1d21c73b719)


## RESULT:
Thus, the program is executed and verified successfully.































