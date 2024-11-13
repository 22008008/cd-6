# Ex. No : 6

# IMPLEMENTATION OF THE BACK END OF THE COMPILER 

## Register Number : 212222220049

## Date :  08/11/24

## AIM   

To write a program to implement the back end of the compiler.

## ALGORITHM

1.	Start the program.
2.	Get the three variables from statements and stored in the text file k.txt.
3.	Compile the program and give the path of the source file.
4.	Execute the program.
5.	Target code for the given statement is produced.
6.	Stop the program.

## PROGRAM

## program.c
```
#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>
#include <string.h>

int main() {
    int j = 0;              
    char ip[10], filename[10];
    FILE *fp;

    printf("Enter the filename of the intermediate code: ");
    scanf("%s", filename);

    fp = fopen(filename, "r");
    if (fp == NULL) {
        printf("\nError in opening the file\n");
        return 1;
    }

    printf("\nStatement\tTarget Code\n\n");

    while (fscanf(fp, "%s", ip) != EOF) {
        if (islower(ip[2]) && (ip[3] == '+' || ip[3] == '-') && islower(ip[4]) && ip[1] == '=') {
            printf("%s\tMOV %c, R%d\n", ip, ip[2], j); 
            if (ip[3] == '+') {
                printf("\tADD %c, R%d\n", ip[4], j);      // Addition
            } else if (ip[3] == '-') {
                printf("\tSUB %c, R%d\n", ip[4], j);      // Subtraction
            }

            j++;  
        } else {
            printf("%s\tInvalid format\n", ip);
        }

        for (int i = 0; i < 10; i++) {
            ip[i] = '\0';
        }
    }

    fclose(fp);

    return 0;
}
```

## k.txt
```
X=a-b 
Y=a-c 
Z=a+b 
C=a-b 
C=a-b
```

## commands
```
gcc program.c
./a.out
```

## OUTPUT 

![image](https://github.com/user-attachments/assets/47599059-18b6-4175-a07a-d8c8739a5c14)

## RESULT

The back end of the compiler is implemented successfully, and the output is verified.
