# Lab 0：参考答案

## To Upper

```c
#include <stdio.h>

int main(void) {
    char c = '\0';
    scanf("%c", &c);

    if (c >= 'a' && c <= 'z') {
        printf("%c", c - 'a' + 'A');
    } else {
        printf("Not lowercase");
    }

    return 0;
}
```