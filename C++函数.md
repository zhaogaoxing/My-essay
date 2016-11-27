<!-- ---
title: C++函数
tags: C语言
categories:  C语言学习
---
# 函数定义与使用
形式参数表
<type1> name1, <type2> name2, ..., <typen> namen
函数的返回值
由 return 语句给出，例如：return  0
无返回值的函数（void类型），不必写return语句

## 1.一个求X的n次方的函数
double power (double x,int n)
{
	double val = 1.0;
	while(n--)
	{
		val = val * x;
	}
	return(val);
}

## 2.数制转换
输入一个8位二进制，转换为十进制输出
double power (double x,int n);
void main (void)
{
	int i;
	int value = 0;
	char ch;
	cout << "Enter an 8 bit binary number";
	for (i = 7;i>=0;i--)
	{
		cin >> ch;
		if(ch == '1')
		value += int(power(2,i));
}
cout <<"Decimal value is"<<value<<endl;
}

double power (double x,int n)
{
	double val = 1.0;
	while (n--)
		val *= x;
	return(val);
}

## 3.求π的值
π ＝16arctan(1/5)-4arctan(1/239)
Arctan(x)=x-x3/3+x5/5-x7/7+…..
直到数级某项绝对值不大于10的-15次方；π和x都为double
void main ()
{
	double a,b;
	double  Arctan(double x);
	a = 16.0*arctan(1/5.0);
	b = 4.0*arctan(1/239.0);
	注意：因为整数相除结果取整，
    如果参数写1/5，1/239，结果就都是0
    cout<<"PI = "<<a-b<<endl;
}
double arctan(double x)
{
	int i;
	double r,e,f,sqr;
	sqr = x*x;
	r = 0;e = x;i=1;
	while(e/i>1e-15)
	{
		f=e/i;
		r=(i%4==1)?r+f:r-f;
		e=e*sqr;  
		i+=2;
	} 
	return r;
}

## 4.寻找并输出11~999之间的数m，它满足m、m的次方和m三次方均为回文数。
回文：各位数字左右对称的整数。例如：11满足上述条件112=121，113=1331。
分析：
10取余的方法，从最低位开始，依次取出该数的各位数字。按反序重新构成新的数，比较与原数是否相等，若相等，则原数为回文。
void main（ ）
{
  bool symm(long n);
  long m;
  for(m=11; m<1000; m++)
  {if (symm(m)&&symm(m*m)&&symm(m*m*m)) 
    cout<<"m="<<m<<"  m*m="<<m*m<<"  m*m*m="<<m*m*m<<endl;
  }
}

bool symm(long n)
{
  long i, m;
  i=n ;  m=0 ;
  		while(i)
  		{
   			m=m*10+i%10;
   			i=i/10   ;
 		 }
  return ( m==n );
}

## 5.
![%E5%87%BD%E6%95%B05](http://obmrysrv0.bkt.clouddn.com/%E5%87%BD%E6%95%B05.png)
其中r、s的值由键盘输入。SIN x的近似值按如下公式计算，计算精度为10-6：
![%E5%87%BD%E6%95%B05-2](http://obmrysrv0.bkt.clouddn.com/%E5%87%BD%E6%95%B05-2.png)
void main（ ）
{
  double k,r,s;
  double tsin(double x);
  cout<<"r=";
  cin>>r;
  cout<<"s=";
  cin>>s;
  if (r*r<=s*s)
    k=sqrt(tsin(r)*tsin(r)+tsin(s)*tsin(s))  ;
  else
    k=tsin(r*s)/2;
  cout<<k<<endl;
}

double tsin(double x)
{
  double p=0.000001,g=0,t=x;
  int n=1;
  do {
     g=g+t;
     n++;
     t=-t*x*x/(2*n-1)/(2*n-2);
  }while(fabs(t)>=p); 
  return g;
}

## 6.投骰子的随机游戏
游戏规则是：每个骰子有六面，点数分别为1、2、3、4、5、6。游戏者在程序开始时输入一个无符号整数，作为产生随机数的种子。
每轮投两次骰子，第一轮如果和数为7或11则为胜，游戏结束；和数为2、3或12则为负，游戏结束；和数为其它值则将此值作为自己的点数，继续第二轮、第三轮...直到某轮的和数等于点数则取胜，若在此前出现和数为7则为负。
由rolldice函数负责模拟投骰子、计算和数并输出和数。
int rolldice(void);
void main()
{
	int gamestatus,sum,mypoint;
	unsigned seed;
	cout<<"Please enter an unsigned integer";
	cin>>seed;  //输入随机数种子
	srand(seed); //将种子传递给rand()
	sum = rolldice(); //第一轮投色子、计算和数
	switch(sum)
	{
		case 7:  //如果和数为7或者11则为胜，状态为1
		case 11:  gamestatus = 1;
		break;
		case 2:  //和数为2、3、12则为负，状态为2
		case 3:
		case 12: gamestatus = 2;
		break;
		default:  //其他状况，游戏尚未结束，状态为0，记下点数，为下一轮做准备
			gamestauts = 0;
			mypoint = sum;
			cout<<"point is"<<mypoint<<endl;
			break;
	}
	while (gamestatus==0) //只要状态为0就继续下一轮
	{
		sum = rolldice();
		if(sum==mypoint) //某轮的和数等于点数就胜利状态为1
			gamestatus = 1;
		else
			if(sum==7)   //和数为7就为负，状态为2
			gamestatus = 2;
	}
	if(gamestatus==1)
		cout<<"WIN\n"
	else
		cout<<"LOSE\n"
}

int rolldice(void)
{//投色子、计算和数、输出和数
	int die1,die2,worksum;
	die1 = 1+rand() %6;
	die2 = 1+rand() %6;
	worksum = die1+die2;
	cout<<worksum<<endl;
	return worksum;
}

# 函数嵌套调用

## 输入两个整数，求平方和
void main(void)
{
	int a,b;
	int fun1(int x,int y);
	cin>>a>>b;
	cout<<fun1(a,b)<<endl;
}
int fun1(int x,int y)
{
	int fun2(int m);
	return(fun2(x)+fun2(y));
}
int fun2(int m)
{
	return(m*m);
}

# 递归调用
函数直接或间接地调用自身，称为递归调用。
递归过程的两个阶段：递推，回归

## 求n！
![%E5%87%BD%E6%95%B03-8](http://obmrysrv0.bkt.clouddn.com/%E5%87%BD%E6%95%B03-8.png)
long fac(int n)
{
	long f;
	if(n<0)
		cout<<"n<0,data error"<<endl;
	else if(n==0) f==1;
	else f=fac(n-1)*n;
	return(f);
}
void main()
{
	long fac(int n);
	int n;
	long y;
	cout<<"enter a positive integer:";
	cin>>n;
	y=fac(n);
	cout<<n<<"!="<<y<<endl;
}

## 用递归法计算从n个人中选择k个人组成一个委员会的不同组合数。
分析：
由n个人里选k个人的组合数=由n-1个人里选k个人的组合数+由n-1个人里选k-1个人的组合数
当n==k或k==0时，组合数为1
void main()
{
	int n,k;
	int comm(int n,int k);
	cin>>n>>k;
	cout<<comm(n,k)<<endl;
}
int comm(int n,int k)
{
	if(k>n)
	return 0;
	else if(n==k||k==0)
	return 1;
	else
	return comm(n-1,k)+comm(n-1,k-1);
}

递归的条件
（1）要有完成函数任务的语句
（2）一个确定是否能避免递归调用的测式
（3）一个递归调用语句
（4）先测试，后递归调用
 -->