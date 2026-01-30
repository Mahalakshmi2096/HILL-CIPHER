# EX. NO: 3 IMPLEMENTATION OF HILL CIPHER
## AIM:

To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. 

STEP-2: Split the plain text into groups of length three.

STEP-3: Arrange the keyword in a 3*3 matrix.

STEP-4: Multiply the two matrices to obtain the cipher text of length three.

STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
#include <stdio.h>
#include <string.h>
int mod26(int x) {
    x = x % 26;
    if (x < 0)
        x += 26;
    return x;
}

int main() {
    char message[100];
    int key[3][3], invKey[3][3];
    int msg[3], result[3];
    int i, j, k;
    // Input message
    printf("Enter the message (uppercase only): ");
    scanf("%s", message);
    // Padding with X
    while (strlen(message) % 3 != 0) {
        strcat(message, "X");
    }
    // Input encryption key
    printf("\nEnter 3x3 encryption key matrix:\n");
    for (i = 0; i < 3; i++)
        for (j = 0; j < 3; j++)
            scanf("%d", &key[i][j]);
    // Input inverse key for decryption
    printf("\nEnter 3x3 inverse key matrix:\n");
    for (i = 0; i < 3; i++)
        for (j = 0; j < 3; j++)
            scanf("%d", &invKey[i][j]);

    // Encryption
    printf("\nEncrypted message: ");
    for (i = 0; i < strlen(message); i += 3) {
        for (j = 0; j < 3; j++)
            msg[j] = message[i + j] - 'A';
        for (j = 0; j < 3; j++) {
            result[j] = 0;
            for (k = 0; k < 3; k++)
                result[j] += key[j][k] * msg[k];
            result[j] = mod26(result[j]);
            printf("%c", result[j] + 'A');
        }
    }
    // Decryption
    printf("\nDecrypted message: ");
    for (i = 0; i < strlen(message); i += 3) {
        for (j = 0; j < 3; j++)
            msg[j] = message[i + j] - 'A';

        for (j = 0; j < 3; j++) {
            result[j] = 0;
            for (k = 0; k < 3; k++)
                result[j] += invKey[j][k] * msg[k];
            result[j] = mod26(result[j]);
            printf("%c", result[j] + 'A');
        }
    }
    return 0;
}
```
## OUTPUT
<img width="1708" height="807" alt="image" src="https://github.com/user-attachments/assets/af8d5bd1-58ae-437a-a594-7984e4d1b845" />

## RESULT
Thus the implementation of Hill Cipher Substitution technique had been executed successfully.
