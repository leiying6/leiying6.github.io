---
layout: post
title:  "pat 1004 Count Leaves"
date:   2017-12-23 
categories: pat algorithm
tags: algorithm
---





开始按照题意写了一个，但是提交上去显示部分正确，后来想了一下问题可能出在样例输入的时候不一定是按照顺序的，每一行都是parents节点和它的子节点们，但是当前的这个parents节点不一定作为子节点出现过。

所以我直接用邻接矩阵建立了有向图，然后用bfs按层搜索。

写完这几个题，感觉代码力回来了一点。

```
#include<stdio.h>
#include<math.h>
#include<iostream>
#include<string.h>
#include<algorithm>
#include<queue>
using namespace std;
int n,m;
int map[105][105];
int vis[105];
int b[105];
int value[105];
int cnt = 1;

int bfs(int v0) {
	queue<int > Q;
	Q.push(v0);
	vis[v0] = 1;
	while(!Q.empty()) {
		int a = Q.front();
		Q.pop();
		int flag = 0;
		for(int i = 1;i<=n;i++) {
			if(map[a][i] == 1) {
				flag++;
				Q.push(i);
				vis[i] = vis[a] + 1;
				cnt = max(cnt,vis[i]);
			}
		}
		if(flag) vis[a] = 0;
	}
}
int main() 
{
	
	scanf("%d%d",&n,&m);
	for(int i=0;i<m;i++) {
		int root, num;
		scanf("%d%d",&root,&num);
		while(num--) {
			int temp;
			scanf("%d",&temp);
			map[root][temp] = 1;
		}
	}
	if(n==1){
		printf("1\n");
		return 0;
	}
	bfs(1);
	for(int i = 1;i<=n;i++) {
		if(vis[i]){
			b[vis[i]]++;
		}
	}
	for(int i=1;i<=cnt;i++) {
		printf(i==cnt?"%d\n":"%d ",b[i]);
	}
}
```

