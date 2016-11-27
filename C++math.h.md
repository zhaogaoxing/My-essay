---
title: C++ math.h库
tags: C语言
categories:  C语言学习
---
# math.h库
## abs
原型：extern int abs(int x);

用法：#include <math.h>

功能：求整数x的绝对值

说明：计算|x|, 当x不为负时返回x，否则返回-x

举例：

      // abs.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        int x;
      
        clrscr();        // clear screen
      
        x=-5;
        printf("|%d|=%d\n",x,abs(x));
        x=0;
        printf("|%d|=%d\n",x,abs(x));
        x=+5;
        printf("|%d|=%d\n",x,abs(x));
      
        getchar();
        return 0;
      }
相关函数：fabs

## acos
原型：extern float acos(float x);

用法：#include <math.h>

功能：求x（弧度表示）的反余弦值

说明：x的定义域为[-1.0，1.0]，值域为[0，π]。

举例：

      // acos.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        float x;
      
        clrscr();        // clear screen
        textmode(0x00); // 6 lines per LCD screen
      
        x=0.32;
        printf("acos(%.2f)=%.4f",x,acos(x));
      
        getchar();
        return 0;
      }
    
相关函数：asin,atan,atan2,sin,cos,tan

## asin
原型：extern float asin(float x);

用法：#include <math.h>

功能：求x（弧度表示）的反正弦值

说明：x的定义域为[-1.0，1.0]，值域为[-π/2，+π/2]。

举例：

      // asin.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        float x;
      
        clrscr();        // clear screen
        textmode(0x00); // 6 lines per LCD screen
      
        x=0.32;
        printf("asin(%.2f)=%.4f",x,asin(x));
      
        getchar();
        return 0;
      }
    
相关函数：acos,atan,atan2,sin,cos,tan

## atan
原型：extern float atan(float x);

用法：#include <math.h>

功能：求x（弧度表示）的反正切值

说明：值域为(-π/2，+π/2)。

举例：

      // atan.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        float x;
      
        clrscr();        // clear screen
        textmode(0x00); // 6 lines per LCD screen
      
        x=0.32;
        printf("atan(%.2f)=%.4f",x,atan(x));
      
        getchar();
        return 0;
      }
    
相关函数：asin,acos,atan2,sin,cos,tan

## atan2
原型：extern float atan2(float y, float x);

用法：#include <math.h>

功能：求y/x（弧度表示）的反正切值

说明：值域为(-π/2，+π/2)。

举例：

      // atan2.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        float x,y;
      
        clrscr();        // clear screen
        textmode(0x00); // 6 lines per LCD screen
      
        x=0.064;
        y=0.2;
        printf("atan2(%.3f,%.2f)=%.4f",y,x,atan2(y,x));
      
        getchar();
        return 0;
      }
    
相关函数：asin,acos,atan,sin,cos,tan

## ceil
原型：extern float ceil(float x);

用法：#include <math.h>

功能：求不小于x的最小整数

说明：返回x的上限，如74.12的上限为75，-74.12的上限为-74。返回值为float类型。

举例：

      // ceil.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        float x;
      
        clrscr();        // clear screen
        textmode(0x00); // 6 lines per LCD screen
      
        x=74.12;
        printf("ceil(%.2f)=%.0f\n",x,ceil(x));
        x=-74.12;
        printf("ceil(%.2f)=%.0f\n",x,ceil(x));
      
        getchar();
        return 0;
      }
    
相关函数：floor

## cos
原型：extern float cos(float x);

用法：#include <math.h>

功能：求x（弧度表示）的余弦值

说明：返回值在[-1.0，1.0]之间。

举例：

      // cos.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        float x;
      
        clrscr();        // clear screen
        textmode(0x00); // 6 lines per LCD screen
      
        x=PI/4.;
        printf("cos(%.4f)=%.4f\n",x,cos(x));
      
        getchar();
        return 0;
      }
    
相关函数：asin,acos,atan,atan2,sin,tan

## cosh
原型：extern float cosh(float x);

用法：#include <math.h>

功能：求x的双曲余弦值

说明：cosh(x)=(e^x+e^(-x))/2

举例：

      // cosh.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        float x;
      
        clrscr();        // clear screen
        textmode(0x00); // 6 lines per LCD screen
      
        x=PI/4.;
        printf("cosh(%.4f)=%.4f\n",x,cosh(x));
      
        getchar();
        return 0;
      }
    
相关函数：sinh,tanh

## exp
原型：extern float exp(float x);

用法：#include <math.h>

功能：求e的x次幂

说明：e=2.718281828...

举例：

      // exp.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        clrscr();        // clear screen
        textmode(0x00); // 6 lines per LCD screen
      
        printf("e=%f\n",exp(1.0));
      
        getchar();
        return 0;
      }
    
相关函数：无

## fabs
原型：extern float fabs(float x);

用法：#include <math.h>

功能：求浮点数x的绝对值

说明：计算|x|, 当x不为负时返回x，否则返回-x

举例：

      // fabs.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        float x;
      
        clrscr();        // clear screen
        textmode(0x00); // 6 lines per LCD screen
      
        x=-74.12;
        printf("|%f|=%f\n",x,fabs(x));
        x=0;
        printf("|%f|=%f\n",x,fabs(x));
        x=74.12;
        printf("|%f|=%f\n",x,fabs(x));
      
        getchar();
        return 0;
      }
    
相关函数：abs

## floor
原型：extern float floor(float x);

用法：#include <math.h>

功能：求不大于x的最达整数

说明：返回x的下限，如74.12的下限为74，-74.12的下限为-75。返回值为float类型。

举例：

      // floor.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        float x;
      
        clrscr();        // clear screen
        textmode(0x00); // 6 lines per LCD screen
      
        x=74.12;
        printf("floor(%.2f)=%.0f\n",x,floor(x));
        x=-74.12;
        printf("floor(%.2f)=%.0f\n",x,floor(x));
      
        getchar();
        return 0;
      }
    
相关函数：ceil

## fmod
原型：extern float fmod(float x, float y);

用法：#include <math.h>

功能：计算x/y的余数

说明：返回x-n*y，符号同y。n=[x/y](向离开零的方向取整)

举例：

      // fmod.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        float x,y;
      
        clrscr();        // clear screen
        textmode(0x00); // 6 lines per LCD screen

        x=74.12;
        y=6.4;
        printf("74.12/6.4: %f\n",fmod(x,y));      
        x=74.12;
        y=-6.4;
        printf("74.12/(-6.4): %f\n",fmod(x,y));      
      
        getchar();
        return 0;
      }
    
相关函数：无

## frexp
原型：extern float frexp(float x, int *exp);

用法：#include <math.h>

功能：把浮点数x分解成尾数和指数。

说明：x=m*2^exp，m为规格化小数。返回尾数m，并将指数存入exp中。

举例：

      // frexp.c
    
      #include <syslib.h>
      #include <math.h>

      main()
      {
        float x;
        int exp;
      
        clrscr();        // clear screen
        textmode(0x00); // 6 lines per LCD screen
    
        x=frexp(64.0,&exp);
        printf("64=%.2f*2^%d",x,exp);
      
        getchar();
        return 0;
      }
    
相关函数：ldexp,modf

# 未完待续
