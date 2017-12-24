---
layout: post
title:  "pat 1031 Hello World for U"
date:   2017-12-23 
categories: pat algorithm
tags: algorithm
---



1031. Hello World for U (20)

这道题的坑在于，嗯，理解上的一些细微的误差；

Sample Input:

```
helloworld!

```

Sample Output:

```
h   !      1   11
e   d      2   10
l   l      3   9
lowor      45678
```
题目中定义的n1，n3是这个U型的高1-4，11-8的距离。n2是这个U型的宽4-8的距离。

题目中的意思是是让n1,n2,n3的值尽可能接近。

但是我在写代码的时候理解上出了一些偏差，我设定的n1=n3为1-3，11-9这一段的距离。所以出了一些偏差，有两个测试点没过。

```
#include<stdio.h>
#include<math.h>
#include<iostream>
#include<string.h>
#include<algorithm>
#include<queue>
#include<map>
using namespace std;

int main() 
{
	char str[85];
	scanf("%s",str);
	int len = strlen(str);
	int base = (len+2)/3;
	int rest = (len+2)%3;
	
	int n1 = base;
	int n2 = base+rest;
	int cnt = n2-2;
	for(int i=0;i<n1-1;i++) {
		printf("%c",str[i]);
		for(int j=0;j<cnt;j++) {
			printf(" ");
		}
		printf("%c\n",str[len-i-1]);
	}
	for(int i=n1-1;i<n2+n1-1;i++) {
		printf("%c",str[i]);
	}
	printf("\n");
}
```

