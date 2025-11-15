# 实验 3：参考答案

## 回文素数

```c
#include <stdio.h>
#include <stdbool.h>
#include <math.h>

// 判断是否为素数
bool isPrime(int n) {
    if (n <= 1) return false;
    if (n == 2) return true;
    if (n % 2 == 0) return false;
    for (int i = 3; i <= sqrt(n); i += 2) {
        if (n % i == 0) return false;
    }
    return true;
}

// 判断是否为回文数
bool isPalindrome(int n) {
    if (n < 10) return true;  // 一位数都是回文数
    
    int reversed = 0;
    int temp = n;
    
    // 反转数字
    while (temp > 0) {
        reversed = reversed*10 + temp%10;
        temp /= 10;
    }
    
    return reversed == n;
}

int main() {
    int count = 0;
    for (int i = 2; i < 10000; i++) {
        if (isPrime(i) && isPalindrome(i)) {
            // 控制输出格式，第一个数前无空格
            if (count > 0) {
                printf(" ");
            }
            printf("%d", i);
            count++;
        }
    }
    return 0;
}
```

## 哥德巴赫

```c
#include <stdio.h>
#include <stdbool.h>
#include <math.h>

// 判断一个数是否为素数
bool is_prime(int num) {
	if (num <= 1) return false;
	if (num == 2) return true;
	if (num % 2 == 0) return false;
	for (int i = 3; i <= sqrt(num); i += 2) {
		if (num % i == 0) return false;
	}
	return true;
}

int main() {
	int n;
	//printf("输入一个偶数：");
	scanf("%d", &n);
	
	// 判断输入是否为大于2的偶数
	if (n <= 2 || n % 2 != 0) {
		printf("error");
		return 0;
	}
	
	// 处理从4到n的所有偶数
	for (int even = 4; even <= n; even += 2) {
		// 寻找所有可能的素数对（p <= q）
		for (int p = 2; p <= even / 2; p++) {
			int q = even - p;
			if (is_prime(p) && is_prime(q)) {
				printf("%d=%d+%d\n", even, p, q);
			}
		}
	}
	
	return 0;
}
```

## 解方程

```c
#include<stdio.h>
#include<math.h>

// 定义函数和导数
double f(double x) {
    return 3*x*x*x - 3*x*x + x - 6;
}

double df(double x) {
    return 9*x*x - 6*x + 1;
}

void newton_method(double a) {
    double x_prev = a;
    double x_curr;
    int iterations = 0;
    
    for(int i = 0; i < 100; i++) {
        x_curr = x_prev - f(x_prev) / df(x_prev);
        iterations++;
        
        if(fabs(x_curr - x_prev) < 1e-6) {
            break;
        }
        
        x_prev = x_curr;
    }
    
    printf("%.5lf %d\n", x_curr, iterations);
}

// 二分法
void bisection_method(double left_init, double right_init) {
    double left = left_init;
    double right = right_init;
    double mid;
    int iterations = 0;
    
    for(int i = 0; i < 99; i++) {
        mid = (left + right) / 2;
        iterations++;
        
        if(f(mid) * f(left) < 0) {
            right = mid;
        } else {
            left = mid;
        }
        
        if(fabs(right - left) <= 1e-6) {
            break;
        }
    }
    
    printf("%.5f %d\n", mid, iterations);
}

int main() {
    double a;
    scanf("%lf", &a);
    
    newton_method(a);
    bisection_method(-3, 3);
    
    return 0;
}
```