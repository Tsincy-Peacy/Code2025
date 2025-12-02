# Lecture 2

Made by 张逸安

> 以下内容为 Lab5 - Lab8 上机作业讲解

## Lab5

### 0-1 背包

有一个背包最大可以容纳 x 重量的物品，现在有 n 个物品，均有各自的重量和价值。问如何将这些物品装入这个背包里，使得背包里物品的价值最大，且其重量不能超过背包的最大容量。

0-1 背包问题：每种物品仅 1 个，不可拆分，只能全部装入或不装入。

```c
// 物品结构体
typedef struct {
    int id;      // 物品编号
    int weight;  // 重量
    int value;   // 价值
    double ratio; // 单位重量价值(价值/重量)
} Item;

// 按价值从大到小排序的比较函数
int compare_value(Item *x, Item *y) {
    return (x->value - y->value);
}

// 按单位重量价值从大到小排序的比较函数
int compare_ratio(Item *x, Item *y) {
    if (x->ratio < y->ratio) return 1;
    if (x->ratio > y->ratio) return -1;
    return 0;
}

// 计算单位重量价值
for (int i = 0; i < n; i++) {
    items[i].ratio = (double)items[i].value / items[i].weight;
}

// 创建一个价值由高到低的 Item 数组
Item value_sorted[N];
for (int i = 0; i < n; i++) {
    value_sorted[i] = items[i];
}
// 感兴趣的同学可以了解一下快排
qsort(value_sorted, n, sizeof(Item), compare_value);
// 价值从大到小选取
for (int i = 0; i < n; i++) {
    if (value_sorted[i].weight <= remaining) {
        remaining -= value_sorted[i].weight;
        total_value += value_sorted[i].value;
    } else {
        break;
    }
}

// 创建一个单位重量价值由高到低的数组
Item ratio_sorted[N];
for (int i = 0; i < n; i++) {
    ratio_sorted[i] = items[i];
}
qsort(ratio_sorted, n, sizeof(Item), compare_ratio);
// 单位重量价值由高到低选取
for (int i = 0; i < n; i++) {
    if (ratio_sorted[i].weight <= remaining) {
        remaining -= ratio_sorted[i].weight;
        total_value += ratio_sorted[i].value;
    } else {
        break;
    }
}
```

### 时间计算

输入时间并对其进行调整

```c
// 时间结构体
struct Time {
    int hours;
    int minutes;
    int seconds;
} t0, t;

// 以秒为基准计算
sec0 = 3600*t0.hours + 60*t0.minutes + t0.seconds;
while (1) {
    if (delta == 0) {
        break;
    }

    sec = (sec0 + delta) % 86400;
    // 处理调整到前几天的情况
    if (sec < 0) {
        sec += 86400;
    }

    t.hours = sec / 3600;
    t.minutes = sec % 3600 / 60;
    t.seconds = sec % 60;
}
```

### 杨辉三角

```c
for (int i = 0; i < N; i++) {
    arr[i][0] = 1; // 每行第一个元素为1
    arr[i][i] = 1; // 每行最后一个元素为1
    for (int j = 1; j < i; j++) {
        // 由上一行的两元素相加得到
        arr[i][j] = arr[i - 1][j - 1] + arr[i - 1][j];
    }
}

for (int i = 0; i < n; i++) {
    for (int j = 0; j <= i; j++) {
        printf("%d", arr[i][j]);
        if (j != i) {
            // 同行非最后一个元素后输出空格
            printf(" ");
        }
    }
    if (i != n - 1) {
        // 非最后一行输出换行
        printf("\n");
    }
}
```

## Lab6

### 约瑟夫环

#### 最简单的写法

```c
int josephus(int n, int k) {
    if (n == 1) {
        return 0;
    } else {
        return (josephus(n-1, k)+k) % n;
    }
}

printf("%d", josephus(n, k)+1);
```

#### 一般的写法

```c
int current = 0; // 自杀之人的下标
// 自杀循环
while (count > 1) {
    current = (current+k-1) % count;
    // 自杀后后面的人依次前移
    for (int i = current; i < count - 1; i++) {
        persons[i] = persons[i + 1];
    }
    count--;
}

printf("%d\n", persons[0]);
```

### 整数反转

要求递归实现

```c
void decimalReverse(unsigned decimal) {
    if (decimal/10==0) {
        printf("%d", decimal);
    } else {
        printf("%d", decimal%10);
        decimalReverse(decimal/10);
    }
}

int main() {
    int decimal;

    scanf("%d", &decimal);
    printf("%s", (decimal>=0)?"":"-");
    decimalReverse(abs(decimal));

    return 0;
}
```

### 数组左旋

```c
void reverse(int arr[], int start, int end) {
    while (start < end) {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}

void leftRotate(int arr[], int n, int k) {
    if (n == 0) return; 
    k = k % n; 
    if (k == 0) return; 
    reverse(arr, 0, k - 1);
    reverse(arr, k, n - 1);
    reverse(arr, 0, n - 1);
}
```

## Lab7

### 字符串拷贝

```c
void copy_string(char dest[], const char src[]) {
    int i = 0;
    while (1) {
        dest[i] = src[i];
        if (src[i] == '\0') {
            break;
        }
        i++;
    }
}

void my_strcpy(char dest[][100], const char src[][100], int n) {
    for (int i = 0; i < n; i++) {
        copy_string(dest[i], src[i]);
    }
}

int main() {
    int n;
    scanf("%d", &n);
    getchar();
    char src[100][100];
    char dest[100][100];

    for (int i = 0; i < n; i++) {
        fgets(src[i], 100, stdin);
        int j = 0;
        while (src[i][j] != '\n' && src[i][j] != '\0') {
            j++;
        }
        src[i][j] = '\0';
    }
    
    my_strcpy(dest, src, n);
    
    for (int i = 0; i < n; i++) {
        printf("%s\n", dest[i]);
    }
    
    return 0;
}
```

### 字符串压缩

```c
// 整数转数字字符数组（如 12 转 "12"）
void int2str(int count, char *buf) {
    if (count == 0) {
        buf[0] = '\0';
        return;
    }
    int i = 0;
    while (count > 0) {
        buf[i++] = count % 10 + '0';
        count /= 10;
    }
    // 反转得到正确顺序
    int left = 0, right = i - 1;
    while (left < right) {
        char temp = buf[left];
        buf[left] = buf[right];
        buf[right] = temp;
        left++;
        right--;
    }
    buf[i] = '\0';
}

char *compressString(char *s) {
    int len = strlen(s);
    if (len == 0) return strdup("");
    // 最坏情况：每个字符都单独出现，长度为 2*len
    char *result = (char *)malloc(2 * len * sizeof(char));
    int idx = 0;
    int i = 0;
    while (i < len) {
        char current = s[i];
        int count = 0;
        // 统计连续相同字符的次数
        while (i < len && s[i] == current) {
            count++;
            i++;
        }
        // 追加当前字符
        result[idx++] = current;
        // 追加次数的数字字符形式
        char countBuf[20] = {0};
        int2str(count, countBuf);
        strcpy(result + idx, countBuf);
        idx += strlen(countBuf);
    }
    result[idx] = '\0';
    
    // 比较长度，返回较短的字符串
    if (strlen(result) >= len) {
        free(result);
        return strdup(s);
    } else {
        return result;
    }
}

int main() {
    char s[1000];
    scanf("%s", s);
    char *compressed = compressString(s);
    printf("%s\n", compressed);
    free(compressed);
    return 0;
}
```

## Lab8

### 回文日期

```c
// 判断是否为闰年
bool isLeapYear(int year) {
    // 能被4整除且不能被100整除，或者能被400整除的年份是闰年
    return (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
}

// (1) 判断日期是否有效
bool isValidDate(unsigned int date) {
    // 从8位数字中提取年、月、日
    int year = date / 10000; // 前4位为年份
    int month = (date % 10000) / 100; // 中间2位为月份
    int day = date % 100; // 后2位为日期
    
    // 基本范围检查
    if (year < 1000 || year > 9999) return false;
    if (month < 1 || month > 12) return false;
    if (day < 1 || day > 31) return false;
    
    // 每月最大天数
    int maxDays;
    switch (month) {
        case 4: case 6: case 9: case 11:
            maxDays = 30;
            break;
        case 2:
            // 2月根据闰年判断天数
            maxDays = isLeapYear(year) ? 29 : 28;
            break;
        default:
            maxDays = 31;
    }
    
    return day <= maxDays;
}

// (2) 判断日期是否是回文日期
int isPalindromeDate(unsigned int date) {
    // 先将数字转换为8位字符串
    char dateStr[9];
    sprintf(dateStr, "%08d", date);
    
    // 检查回文：第1位与第8位相等，第2位与第7位相等，以此类推
    for (int i = 0; i < 4; i++) {
        if (dateStr[i] != dateStr[7 - i]) {
            return 0;  // 不是回文
        }
    }
    return 1;  // 是回文
}

// (3) 主函数测试程序功能
int main() {
    unsigned int date;
    scanf("%u", &date);
    
    // 验证日期有效性
    if (!isValidDate(date)) {
        printf("0");
        return 0;
    }
    
    // 判断是否为回文日期
    if (isPalindromeDate(date)) {
        printf("1");
    } else {
        printf("0");
    }
    
    return 0;
}
```

### 拆分浮点数

```c
char intPart[20] = {0};
char decPart[20] = {0};

void splitFloat(double num) {
    int integer;
    double decimal;
    int isNegative = 0;

    // 处理正负号
    if (num < 0) {
        isNegative = 1;
        num = -num; // 转为正数处理（避免负数小数部分计算错误）
    }

    // 分离整数部分和小数部分
    integer = (int)num;
    decimal = num - integer;

    // 处理整数部分字符串（含负号）
    if (isNegative) {
        sprintf(intPart, "-%d", integer);
    } else {
        sprintf(intPart, "%d", integer);
    }

    // 处理小数部分：直接截取前6位，不四舍五入
    // 小数部分乘以1e6，取整得到前6位数字（不足补0）
    long long decInt = (long long)(decimal * 1000000); // 1e6 = 10^6

    // 将 decInt 转换为字符串（确保至少6位，不足补前导0）
    char decTemp[7]; // 存储6位小数的临时数组
    sprintf(decTemp, "%06lld", decInt); // %06lld 表示不足6位补0

    // 去除末尾多余的0，找到最后一个非0位置
    int lastNonZero = 5; // 初始指向第6位（索引5）
    while (lastNonZero >= 0 && decTemp[lastNonZero] == '0') {
        lastNonZero--;
    }
    // 若所有位都是0，保留一个0
    if (lastNonZero < 0) {
        lastNonZero = 0;
    }

    // 构建最终的小数部分字符串
    decPart[0] = '\0';
    for (int i = 0; i <= lastNonZero; i++) {
        strncat(decPart, &decTemp[i], 1); // 逐个拼接字符
    }
}

int main() {
    double num;
    // 读取输入浮点数
    scanf("%lf", &num);
    // 拆分整数和小数部分
    splitFloat(num);
    // 输出格式：整数部分  .  小数部分
    printf("%s . %s\n", intPart, decPart);

    return 0;
}
```

### 归并排序

```c
while (i < len1 && j < len2) {
    if (arr1[i] < arr2[j]) {
        arr[idx++] = arr1[i++];
    } else {
        arr[idx++] = arr2[j++];
    }
}
if (i != len1) {
    while (i < len1) {
        arr[idx++] = arr1[i++];
    }
}
if (j != len2) {
    while (j < len2) {
        arr[idx++] = arr2[j++];
    }
}
```

### 指针交换元素

```c
// 使用数组地址为指针赋值
ptr = array;
// 寻找最小值
for (i = 1; i < N; i++)
    if (a[i] < *p)
        p = a + i;
// 交换
t = *p, *p = *a, *a = t;

p = array;
// 寻找最大值
for (i = 1; i < N; i++)
    if (a[i] > *p)
        p = a + i;
// 交换
t = *p, *p = *(a+N-1), *(a+N-1) = t;

for (i = 0; i < N; i++)
    printf("%d ", a[i]);
```