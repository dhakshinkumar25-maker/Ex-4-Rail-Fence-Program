# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h>
#include <string.h>

int main()
{
char text[1000];
char rail[100][1000];
int depth, i, j, dir, row, len;


printf("Enter the plaintext: ");
fgets(text, sizeof(text), stdin);

len = strlen(text);

if (len > 0 && text[len - 1] == '\n')
    text[--len] = '\0';

printf("Enter the number of rails: ");
scanf("%d", &depth);

if (depth < 1 || depth > 100)
{
    printf("Invalid number of rails!\n");
    return 1;
}

for (i = 0; i < depth; i++)
{
    for (j = 0; j < len; j++)
    {
        rail[i][j] = '\0';
    }
}

row = 0;
dir = 1;

for (i = 0; i < len; i++)
{
    rail[row][i] = text[i];

    if (row == 0)
        dir = 1;
    else if (row == depth - 1)
        dir = -1;

    row += dir;
}

printf("Encrypted Text: ");

for (i = 0; i < depth; i++)
{
    for (j = 0; j < len; j++)
    {
        if (rail[i][j] != '\0')
            printf("%c", rail[i][j]);
    }
}

printf("\n");

return 0;


}

```

# OUTPUT
<img width="425" height="162" alt="image" src="https://github.com/user-attachments/assets/e66af506-6b54-4c28-857d-05d01e596924" />

# RESULT
Thus the above program is executed and the output is verified
