---
title: object-c
tag: object-c
categories: object-c
---
## Objective-C 是C的衍生语言
继承了所有C语言的特性，但是有一些例外。

### nil
可以完全合法的传输讯息给nil（[nil message];）

### BOOL
包含在Foundation classes(基本类别库)中(即import NSObject.h;nil 也是包括在这个头文件内)。
BOOL在Object-c中的形态为：YES NO。

### #import  #include
用#import

### 编译hello world
`helle.m
#import<stdio.h>

int main(int argc,const char*argv[]){
	printf("hello world/n");
	return 0;
}`

Objective-C的预设扩展名是.m

## 创建classes
### @interface
Fraction.h
#import<Foundation/NSObject.h>

@interface Fraction:NSObject{
	int numerator;
	int denominator;
}

-(void) print;
-(void) setNumerator:(int) n;
-(void) setDenominator:(int) d;
-(int) numerator;
-(int) denominator;
@end

### @implementation
Fraction.m
#import "Fraction.h"
#import <stdio.h>

@implementation Fraction
-(void) print {
	printf("%i/%i",numerator,denominator);
}

-(void) setNumerator:(int) n{
	numerator = n;
}

-(void) setDenominator:(int) d{
	denominator = d;
}

-(void) denominator{
	return denominator;
}

-(int) numerator{
	return numerator;
}
@end

### 凑在一起
main.m
#import <stdio.h>
#import "Fraction.h"

int main(int argc,const char *argv[]){
	//create a new instance
	Fraction *frac = [[Fraction alloc] init];

	//set the values
	[frac setNumerator: 1];
	[frac setDenominator: 3];

	// print it
	printf("The fraction is:");
	[frac print];
	printf("\n");

	//free memory
	[frac release];

	return 0;
}

Fraction *frac = [[Fraction alloc] init];
1. 呼叫methods 的方法是[object method],c++中的object->method()
2. 没有value类型，完全用指针处理对象
3. [Fraction alloc]呼叫Fraction class的alloc method.
4. [object init]是一个建构子(constructor)呼叫，负责初始化对象总的所有变量。
5. [frac setNumerator: 1] 呼叫了frac上的setNumerator method 并传入1为参数。

## 多重参数
Fraction.h
...
-(void)setNumerator: (int) n andDenominator: (int) d;
...
Fraction.m
...
-(void) setNumerator: (int) n andDenomiantor: (int) d
{
	numerator = n;
	denominator = d;
}
...

main.m
#import <stdio.h>
#import "Fraction.h"

int main(int argc,const char *argv[]){
	//create a new instance
	Fraction *frac = [[Fraction alloc] init];
	Fraction *frac2 = [[Fraction alloc] init];

	//set the values
	[frac setNumerator: 1];
	[frac setDenominator: 3];

	//combined set
	[frac2 setNumerator: 1 andDenominator: 5];

	//print it
	printf("The fraction is:");
	[frac print];
	printf("\n");

	//print it
	printf("Fraction 2 is:");
	[frac2 print];
	printf("\n");

	//free memory
	[frac release];
	[frac2 release];

	return 0;
}

## 构建子(Constructors)
