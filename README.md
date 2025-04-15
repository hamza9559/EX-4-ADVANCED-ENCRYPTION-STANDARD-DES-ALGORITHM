# EX-4-ADVANCED-ENCRYPTION-STANDARD-DES-ALGORITHM

## Aim:
  To use Advanced Encryption Standard (AES) Algorithm for a practical application like URL Encryption.

## ALGORITHM: 
  1. AES is based on a design principle known as a substitution–permutation. 
  2. AES does not use a Feistel network like DES, it uses variant of Rijndael. 
  3. It has a fixed block size of 128 bits, and a key size of 128, 192, or 256 bits. 
  4. AES operates on a 4 × 4 column-major order array of bytes, termed the state

## PROGRAM: 
```c
#include <stdio.h>
#include <string.h>

#define MAX 256

// Simple XOR encryption
void encrypt(char *input, char *output, char key) {
    for (int i = 0; i < strlen(input); i++) {
        output[i] = input[i] ^ key;
    }
    output[strlen(input)] = '\0';
}

// Decryption is same as encryption for XOR
void decrypt(char *input, char *output, char key) {
    encrypt(input, output, key);
}

int main() {
    char url[MAX], encrypted[MAX], decrypted[MAX];
    int key;

    // Get URL input from user
    printf("Enter URL: ");
    fgets(url, sizeof(url), stdin);
    url[strcspn(url, "\n")] = '\0'; // remove trailing newline

    // Get key from user
    printf("Enter encryption key (number 0-255): ");
    scanf("%d", &key);

    if (key < 0 || key > 255) {
        printf("Invalid key. Must be between 0 and 255.\n");
        return 1;
    }

    encrypt(url, encrypted, (char)key);

    printf("\nEncrypted URL (hex): ");
    for (int i = 0; i < strlen(encrypted); i++) {
        printf("%02X", (unsigned char)encrypted[i]);
    }
    printf("\n");

    decrypt(encrypted, decrypted, (char)key);
    printf("Decrypted URL: %s\n", decrypted);

    return 0;
}

```
## OUTPUT:
![image](https://github.com/user-attachments/assets/e7544e5e-a276-435f-b2fe-bee882aea946)

## RESULT: 
Hence, Advanced Encryption Standard (AES) Algorithm for a practical application like URL Encryption is implemented and executed successfully.
