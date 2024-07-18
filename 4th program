#include <stdio.h>
#include <string.h>
#include <ctype.h>

#define MAX_TEXT_LEN 1000

void toUpperCase(char* str) {
    int i;
    for (i = 0; str[i]; i++) {
        str[i] = toupper(str[i]);
    }
}

void removeSpaces(char* str) {
    int i, j;
    for (i = 0, j = 0; str[i]; i++) {
        if (str[i] != ' ') {
            str[j++] = str[i];
        }
    }
    str[j] = '\0';
}

void generateKey(char* key, int textLen, char* newKey) {
    int keyLen = strlen(key);
    int i, j;

    for (i = 0, j = 0; i < textLen; i++, j++) {
        if (j == keyLen) {
            j = 0;
        }
        newKey[i] = key[j];
    }
    newKey[i] = '\0';
}

void encrypt(char* plaintext, char* key, char* ciphertext) {
    int textLen = strlen(plaintext);
    int i;

    for (i = 0; i < textLen; i++) {
        ciphertext[i] = ((plaintext[i] + key[i]) % 26) + 'A';
    }
    ciphertext[i] = '\0';
}

int main() {
    char key[MAX_TEXT_LEN], plaintext[MAX_TEXT_LEN], ciphertext[MAX_TEXT_LEN], newKey[MAX_TEXT_LEN];

    printf("Enter the key: ");
    fgets(key, sizeof(key), stdin);
    key[strcspn(key, "\n")] = '\0'; // Remove trailing newline

    printf("Enter the plaintext: ");
    fgets(plaintext, sizeof(plaintext), stdin);
    plaintext[strcspn(plaintext, "\n")] = '\0'; // Remove trailing newline

    toUpperCase(key);
    toUpperCase(plaintext);
    removeSpaces(key);
    removeSpaces(plaintext);

    generateKey(key, strlen(plaintext), newKey);
    encrypt(plaintext, newKey, ciphertext);

    printf("Encrypted text: %s\n", ciphertext);

    return 0;
}
