# 实验 2：参考答案

## 点是否位于正方形内

```c
#include <stdio.h>
int main() {
    int x, y;
    scanf("%d%d", &x, &y);
    if (-2<=x && x<=2 && -2<=y && y<=2) {
        printf("Yes");
    } else {
        printf("No");
    }
}
```

## 分段函数

```c
#include <stdio.h>

int main() {
    int xi, yi;
    float xf, yf;
    printf("输入一个整数:");
    scanf("%d", &xi);
    switch (xi/10) {
      case 0:
        switch(xi>=0) {
          case 0:
            printf("x输入错误, 要求0<=x<30\n");
            return 0; 
        }
        yi = xi;
        break;
      case 1:
        yi = xi*xi + 1;
        break;
      case 2: 
        yi = xi*xi*xi + xi*xi + 1;
        break;
      default:
        printf("x输入错误, 要求0<=x<30\n");
        return 0;
    }
    printf("x=%d时, y=%d\n", xi, yi);
    printf("输入一个实数:");
    scanf("%f", &xf);
    if (0<=xf && xf<10)
        yf = xf;
    else if (10<=xf && xf<20)
        yf = xf*xf + 1;
    else if (20<=xf && xf<30)
        yf = xf*xf*xf + xf*xf + 1;
    else {
        printf("x输入错误, 要求0<=x<30\n");
        return 0;
    }
    printf("x=%f时, y=%f\n", xf, yf);
}
```

## 三角形的判定

```c
#include <stdio.h>
#include <math.h>

int main() {
    double x, y, z;
    printf("输入三角形的3个边：");
    scanf("%lf%lf%lf", &x, &y, &z);

    // 检查是否能构成三角形
    if (x+y>z && x+z>y && y+z>x) {
        printf("边长为%lf,%lf,%lf的三角形是 ", x, y, z);
        // 计算面积
        double area = 0.25 * sqrt((x+y+z)*(x+y-z)*(x+z-y)*(y+z-x));
        // 判断三角形类型
        if (x==y && y==z) {
            printf("等边三角形");
        } else if (x==y || y==z || x==z) {
            printf("等腰三角形");
        } else if (fabs(x*x+y*y-z*z)<1e-6 || fabs(x*x+z*z-y*y)<1e-6 || fabs(y*y+z*z-x*x)<1e-6) {
            printf("直角三角形");
        } else {
            printf("一般三角形");
        }
        printf(",其面积为:%lf\n", area);
    } else {
        printf("Error\n");
    }

    return 0;
}
```