# Codeforces 1355 C 题解

## Part1 前言

C 挺烦，又是一大堆式子，而且我推了好久结果居然 `Wrong Answer` 了。最后还是求助了一下大佬 `Accepted` 的。~~现在你知道我有多菜了吧。~~

## Part2 题面

给定四个数 $A, B, C, D\left(1 \leq A \leq B \leq C \leq D \leq 5 \cdot 10^5\right)$，让你求 $x, y, z$。首先，必须满足 $A \leq x \leq B \leq y \leq C \leq z \leq D$，接下来，还要满足 $x, y, z$ 为三条边，这三条边能组成三角形。求出一共有多少种方法。**本题不是多测。**

## Part3 思路

我们可以枚举 $x, y$ 的和。接下来，我们发现，$x$ 和 $y$ 的方案数为 $\min\left(i-b, b\right)-\max\left(i-c,a\right)+1$。然后我们继续推算。$z$ 的方案数为 $\min\left(d+1, i\right)-c$，意思是在 $d+1-c$（也就是总范围）和 $i-c$ （受 $x, y$ 的和影响的范围）中取小的值，正好就是 $z$ 的方案数。

## Part4 代码

代码就很简单啦~

```c++
#include<iostream>
#define int long long
using namespace std;
signed main(){
	int a,b,c,d;
	cin>>a>>b>>c>>d;
	int tot=0;
	for(int i=max(c+1,a+b);i<=b+c;++i)
		tot+=(min(d+1,i)-c)*(min(i-b,b)-max(i-c,a)+1);
	cout<<tot<<endl;
}
```

## Part5 结语

送上一首藏头诗：

```
我与故人同老去，
好书无计寄邮亭。
菜花狼籍今何在，
啊为天涯涕泪零。
```

