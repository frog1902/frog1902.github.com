---
layout: post
category : SRM 500 - 500
tagline: CheckerExpansion
tags : [ACM, TC, search]
---
{% include JB/setup %}

# 题目链接
[http://community.topcoder.com/stat?c=problem_statement&pm=11995](http://community.topcoder.com/stat?c=problem_statement&pm=11995

# 题目大意
A、B对局，无限棋盘。
第一步A 在(0,0)除下一子。
之后两人交替。
在每一轮，所有满足以下条件的空格子(x, y)都要下子：
(x-1, y-1)为对方棋子，(x-2, y)为空
(x-2, y) 为对方棋子，(x-1, y-1)为空
最终要求输出t 轮后棋盘上一个边长不超过50的矩阵上的下子情况

# 算法
这道题描述的是一种分形：[Sierpinski_triangle](http://en.wikipedia.org/wiki/Sierpinski_triangle)
根据分形本身的特点分治即可。

对于当前大三角形，判断所求点在三角形的哪个子三角形里，如果不属于子三角形则是空点。

然后不断递归下去，每次把当前坐标调整为相对于子三角区域左下角的相对坐标，递归到只剩一个点的时候自然就是有棋子的。
最后如果发现这个点有棋子，那么(x + y)是偶数的是Alice的棋子，(x + y)是奇数的是Bob的棋子，这个观察条件就可以发现。
每次递归三角形高度减半，所以每次判断是log(t)级的。

# 代码

#include <string>
#include <cstdio>
#include <iostream>
#include <algorithm>
#include <sstream>
#include <cstdlib>
#include <cstring>
#include <string>
#include <climits>
#include <cmath>
#include <queue>
#include <vector>
#include <stack>
#include <set>
#include <map>
#define INF 0x3f3f3f3f
#define eps 1e-8
using namespace std;

#define PB push_back
#define MP make_pair

typedef vector <int> VI;
typedef vector <string> VS;
typedef vector <double> VD;
typedef long long LL;
typedef pair <int,int> PII;

class CheckerExpansion
{
	public:

		bool cal(long long x, long long y, long long lim)
		{
			if(lim == 1)
			{
				return true;
			}
			if(x >= 2 * lim - 1)
			{
				return false;
			}
			if(x < y)
			{
				return false;
			}
			if(y >= 2 * lim - x - 1)
			{
				return false;
			}
			if((y < lim / 2) && (x >= lim - y - 1 && x <= lim + y - 1))
			{
				return false;
			}
			if(y < lim / 2)
			{
				if(x < lim)
				{
					return cal(x, y, lim / 2);
				}
				else
				{
					return cal(x - lim, y, lim / 2);
				}
			}
			return cal(x - lim / 2, y - lim / 2, lim / 2);
		}

		vector <string> resultAfter(long long t, long long x0, long long y0, int w, int h)
		{
			VS ans;
			ans.clear();
			string str = "";
			for(int i = 0; i < w; i ++)
			{
				str += '.';
			}
			for(int i = 0; i < h; i ++)
			{
				ans.PB(str);
			}
			for(int i = 0; i < h; i ++)
			{
				for(int j = 0; j < w; j ++)
				{
					if(x0 + j + y0 + h - i - 1 > t * 2 - 2)
					{
						continue;
					}
					if(cal(x0 + j, y0 + h - i - 1, 1LL << 50))
					{
						if(((x0 + j + y0 + h - i - 1) >> 1) & 1)
						{
							ans[i][j] = 'B';
						}
						else		                                       
						{
							ans[i][j] = 'A';						
						}
					}
				}
			}
			return ans;
		}
};