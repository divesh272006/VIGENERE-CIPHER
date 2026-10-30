# VIGENERE-CIPHER
## EX. NO: 4
 Name:Divesh A
 Reg NO :212225040082

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
STEP-4: The keyword and the plain text is read from the user.
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.
STEP-7: The junction character where these two meet forms the cipher character.
STEP-8: Repeat the above steps to generate the entire cipher text.


## PROGRAM
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main()
{
    char text[100], key[100], cipher[100], plain[100];
    int i, j = 0, k, len;

    printf("Enter plaintext: ");
    scanf(" %[^\n]", text);

    printf("Enter key: ");
    scanf("%s", key);

    len = strlen(text);

    for(i = 0; i < len; i++)
    {
        if(isalpha(text[i]))
        {
            k = tolower(key[j % strlen(key)]) - 'a';

            if(isupper(text[i]))
                cipher[i] = (text[i] - 'A' + k) % 26 + 'A';
            else
                cipher[i] = (text[i] - 'a' + k) % 26 + 'a';

            j++;
        }
        else
        {
            cipher[i] = text[i];
        }
    }

    cipher[i] = '\0';

    printf("\nEncrypted text: %s", cipher);

    j = 0;

    for(i = 0; i < len; i++)
    {
        if(isalpha(cipher[i]))
        {
            k = tolower(key[j % strlen(key)]) - 'a';

            if(isupper(cipher[i]))
                plain[i] = (cipher[i] - 'A' - k + 26) % 26 + 'A';
            else
                plain[i] = (cipher[i] - 'a' - k + 26) % 26 + 'a';

            j++;
        }
        else
        {
            plain[i] = cipher[i];
        }
    }

    plain[i] = '\0';

    printf("\nDecrypted text: %s\n", plain);

    return 0;
}
```

## OUTPUT

<img width="297" height="197" alt="image" src="https://github.com/user-attachments/assets/a1f02aa6-8560-412f-be15-d46eb9c495ab" />


## RESULT

Thus, the C program to implement the Vigenère Cipher substitution technique was successfully executed, and the encrypted text was decrypted successfully.
