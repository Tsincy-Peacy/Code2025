# **实验 1：参考答案**

## **Prime Judge and Count**

时间复杂度 $O(N\sqrt{N})$

```c
#include <stdio.h>
#include <math.h>
#include <stdbool.h>

// 判断一个数是否为素数
bool is_prime(int num) {
    if (num < 2) {
        return false;
    }
    if (num == 2) {
        return true;
    }
    if (num % 2 == 0) {
        return false;
    }
    // 只需检查到平方根即可
    int sqrt_num = (int)sqrt(num) + 1;
    for (int i = 3; i <= sqrt_num; i += 2) {
        if (num % i == 0) {
            return false;
        }
    }
    return true;
}

// 统计a到b范围内的素数个数
int count_primes_in_range(int a, int b) {
    int count = 0;
    for (int num = a; num <= b; num++) {
        if (is_prime(num)) {
            count++;
        }
    }
    return count;
}

int main() {
    int n, a, b;
    
    // 读取输入
    scanf("%d", &n);
    scanf("%d %d", &a, &b);
    
    // 输出结果
    printf("%s\n", is_prime(n) ? "YES" : "NO");
    printf("%d\n", count_primes_in_range(a, b));
    
    return 0;
}
```

## **Convert T**

```c
#include <stdio.h>

int main() {
    double temp;
    char direction;
    
    // 读取输入
    scanf("%lf %c", &temp, &direction);
    
    // 根据转换方向计算并输出结果
    if (direction == 'F') {
        // 摄氏度转华氏度
        double result = temp * 1.8 + 32;
        printf("%.2f F\n", result);
    } else if (direction == 'C') {
        // 华氏度转摄氏度
        double result = (temp - 32) / 1.8;
        printf("%.2f C\n", result);
    }
    
    return 0;
}
```