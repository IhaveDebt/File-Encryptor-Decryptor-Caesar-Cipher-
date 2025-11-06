#include <stdio.h>
#include <stdlib.h>

void encryptFile(const char *input, const char *output, int key) {
    FILE *in = fopen(input, "r");
    FILE *out = fopen(output, "w");
    char ch;

    if (!in || !out) {
        printf("File error!\n");
        exit(1);
    }

    while ((ch = fgetc(in)) != EOF) {
        fputc(ch + key, out);
    }

    fclose(in);
    fclose(out);
    printf("File encrypted successfully!\n");
}

void decryptFile(const char *input, const char *output, int key) {
    FILE *in = fopen(input, "r");
    FILE *out = fopen(output, "w");
    char ch;

    if (!in || !out) {
        printf("File error!\n");
        exit(1);
    }

    while ((ch = fgetc(in)) != EOF) {
        fputc(ch - key, out);
    }

    fclose(in);
    fclose(out);
    printf("File decrypted successfully!\n");
}

int main() {
    int choice, key;
    char input[50], output[50];
    printf("1. Encrypt\n2. Decrypt\n> ");
    scanf("%d", &choice);
    printf("Input file: ");
    scanf("%s", input);
    printf("Output file: ");
    scanf("%s", output);
    printf("Enter key: ");
    scanf("%d", &key);

    if (choice == 1)
        encryptFile(input, output, key);
    else
        decryptFile(input, output, key);

    return 0;
}
