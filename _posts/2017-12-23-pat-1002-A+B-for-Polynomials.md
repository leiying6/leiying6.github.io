---
layout: post
title:  "pat 1002 A+B for Polynomials"
date:   2017-12-23 
categories: pat algorithm
tags: algorithm
---



1002.A+B for Polynomials (25)

手感回来了一点，一遍过

还是有一个问题，就是double型变量输入的时候如果用%f，输入值是不成功的，要用%lf才行。

```
#include<stdio.h>
#include<math.h>
#include<iostream>
#include<string.h>
using namespace std;

int main()
{
	int n,m,number;
	double a[1005] = {0}, coefficients;
	
	scanf("%d",&n);
	while(n--) {
		scanf("%d",&number);
		scanf("%lf",&coefficients);
		//printf("coefficients = %f\n",coefficients);
		a[number] += coefficients;
		//printf("a[number] = %f\n",a[number]);
	} 
	
	scanf("%d",&m);
	while(m--) {
		scanf("%d",&number);
		scanf("%lf",&coefficients);
		a[number] += coefficients;
		//printf("a[number] = %f\n",a[number]);
	}
	
	int count = 0;
	for(int i = 1000; i>=0; i--) {
		
		if(a[i] != 0) {
			count++;
		}
		//printf("*********\n");
	}
	printf("%d",count);
	for(int i=1000; i>=0; i--) {
		
		if(a[i] != 0) {
			printf(" %d %.1f",i,a[i]);
		}
	}
} 
```

