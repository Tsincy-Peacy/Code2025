# 实验 4：参考答案

## 改进冒泡排序

```c
#include <stdio.h>
#include <stdbool.h>

#define ARRAY_SIZE 11
#define INIT_SIZE 10

int main(void) {
    int array[ARRAY_SIZE] = {0};
    int k = 0;
    for (int i = 0; i < INIT_SIZE; i++) {
        scanf("%d", array+i);
    }
    scanf("%d", &k);

    for (int i = 0; i < INIT_SIZE-1; i++) {
        bool swapped = false;
        for (int j = 0; j < INIT_SIZE-1-i; j++) {
            if (array[j] > array[j+1]) {
                int temp = array[j];
                array[j] = array[j+1];
                array[j+1] = temp;
                swapped = true;
            }
        }
        if (!swapped) {
            break;
        }
    }

    printf("%d", array[0]);
    for (int i = 1; i < INIT_SIZE; i++) {
        printf(" %d", array[i]);
    }
    
    int index = -1;
    for (int i = 0, j = INIT_SIZE-1; i <= j; NULL) {
        int mid = (i+j) / 2;
        if (array[mid] < k) {
            i = mid + 1;
        } else if (array[mid] > k) {
            j = mid - 1;
        } else {
            index = mid;
            break;
        }
    }
    if (index == -1) {
        for (int i = ARRAY_SIZE-1; i > 0; i--) {
            if (array[i-1] > k) {
                array[i] = array[i-1];
            } else {
                array[i] = k;
                break;
            }
        }
        printf("\n%d", array[0]);
        for (int i = 1; i < ARRAY_SIZE; i++) {
            printf(" %d", array[i]);
        }
    } else {
        printf("\n%d", index);
    }

    return 0;
}
```

## 字符串替换

```c
#include <stdio.h>

int main()
{
    char str[255];
    int  i, j, k;

    for (i=0; i<3; i++) {
        printf("输入一个字符串:");
        scanf("%s", str);

        for (j=0; str[j]; j++)
            if (str[j]>='0' && str[j]<='9')
                str[j] = '*';

        printf("正序:");
        printf("%s\n", str);
        printf("逆序:");
        for (k=j-1; k>=0; k--)
            putchar(str[k]);
        putchar('\n');
    }

    return 0;
}
```