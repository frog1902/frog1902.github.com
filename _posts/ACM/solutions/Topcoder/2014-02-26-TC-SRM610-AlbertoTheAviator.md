---
layout: post
title: "TC SRM552-550 AlbertoTheAviator"
description: "TC SRM552-550 AlbertoTheAviator"
category: ACM-solutions
tags: [ACM,solution,TC,DP]
---

## 题目链接
暂无

## 题目大意
有n个任务需要完成，初始具有F的能量。
任务i开始之前至少要具有的能量duration[i]，任务结束后可以得到refuel[i]的能量补充，refuel[i]严格小于duration[i]。
完成任务的顺序不限，问至多完成多少个任务。

## 算法
先排序再背包
排序的时候要先按照refuel[i]从大到小，再按照duration[i]从大到小。
因为我们排序的目的是要保证背包的过程中，得到的解的顺序一定是最优顺序。
也就是说，如果a,b任务都被正解选中，那么a,b在排序后序列中的相对位置一定要是它们在正解中的相对位置。
那么我们不妨假设任务已经被选中，这时要怎样排序呢？
排序的任务实际上是要使得，对于任意i, F - <pre xml:lang="latex">\sum_{i=0}^{i-1}-duration[i] + refuel[i]</pre> - duration[i] 尽量大
那么若x在y前，y受到的影响是-duration[x] + refuel[x] - duration[y]
若y在x前，x受到的影响是-duration[y] + refuel[y] - duration[x]
两者相消，可知用refuel排序，refuel相同时，显然duration大的在前。

##代码
	typedef pair<int,int> PII;
	#define fi first
	#define nd second

	const int maxn = 55;
	const int maxm = 5100;
	PII a[maxn];
	int dp[maxm];

	bool cmp(const PII &a, const PII &b)
	{
    	return a.nd != b.nd ? a.nd > b.nd : a.fi - a.nd > b.fi - b.nd;
	}

	class AlbertoTheAviator
	{
    	    public:
        	int MaximumFlights(int F, vector <int> duration, vector <int> refuel)
        	{
            	int ans = 0;
            	int n = duration.size();
            	for (int i = 0; i < n; i ++)
           		{
                	a[i] = make_pair(duration[i], refuel[i]);
            	}
            	sort(a, a + n, cmp);
            	memset(dp, -1, sizeof(dp));
            	dp[0] = 0;
            	for (int i = 0; i < n; i ++)
            	{
                	for (int j = F - a[i].fi; j >= 0; j --)
                	{
                    	if (dp[j] != -1)
                    	{
                        	dp[j + a[i].fi - a[i].nd] = max(dp[j + a[i].fi - a[i].nd], dp[j] + 1);
                        	ans = max(ans, dp[j + a[i].fi - a[i].nd]);
                    	}
                	}
            	}
            	return ans;
        	}
	};