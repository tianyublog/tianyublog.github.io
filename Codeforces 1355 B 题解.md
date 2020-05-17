# Codeforces 1355 B 题解

## Part1 前言

这一道题我觉得第一眼看上去时比 A 题简单一些，所以在比赛的时候我就先做了这道题。印象还是不错的。

## Part2 题面

有 $N\left(1 \leq N \leq 2 \cdot 10^{5}\right)$ 个小探险家，第 $i$ 个小探险家的经验值为 $e_i$，满足 $1 \leq e_{i} \leq N$ 。

然后老师们规定，如果一个小探险家的值为 $e$，那么他的队伍人数必须大于或等于 $e$。

求最多这些小探险家能组成多少队伍。

你需要回答 $T\left(1 \leq T \leq 2 \cdot 10^{5}\right)$ 组数据，所有的 $N$ 不会超过 $3 \cdot 10^{5}$。

## Part3 思路

这一道题其实是一道贪心题。我们可以分析一下 Codeforces 这道题给的样例。

```
2
3
1 1 1
5
2 3 1 2 2
```

看第二组数据。我们可以想到解法：

1. 首先将 $1$ 分成单独的一组；
2. 然后看 $2$，发现有 $3$ 个 $2$。那么我们就把其中 $2$ 个 $2$ 结成一组，另一个 $2$ 跟 $3$ 来配对。
3. 接下来看见有 $3$ 来了。我们用 $3$ 和上一轮剩下来的 $2$ 来结对，可最后还是不够 $3$ 个，只好留下来，与 $4$ 看看。
4. 可是发现没有 $4$，那么直接打印输出 $2$。剩下的两个 $2$ 和 $3$ 只需要跟着前面两组混混即可，一定可以混到自己的队伍。

所以，这道题就很简单了，只需要按照步骤模拟即可。

## Part4 代码

请不要抄袭！

```c++
#include<iostream>
using namespace std;
int main(){
	int t;
	cin>>t;
	while(t--){
		int n;
		cin>>n;
		int e[n+1];
		for(int i=1;i<=n;++i)
			cin>>e[i];
		int sum[n+1];
		for(int i=0;i<=n;++i)
			sum[i]=0;
		for(int i=1;i<=n;++i)
			++sum[e[i]];
		int ans=0;
		int left=0;
		for(int i=1;i<=n;++i){
			ans+=(sum[i]+left)/i;
			left=(sum[i]+left)%i;
		}
		cout<<ans<<endl;
	}
}
```

## Part5 结语

我给大家看看另一位同学的 TLE 代码，大家来看看是什么问题。

![另一位同学的代码](\另一位同学的代码.PNG)

没错，问题就出在 `memset` 上面。`memset` 的复杂度并不是大家以为的 $\operatorname{O}\left(1\right)$ 啊！是 $\operatorname{O}\left(N\right)$ 的复杂度。大家用的原因可能是它的常数较小。但在这道题中，`System Test` 就把 `memset` 卡掉了。这是件好事，提醒更多的人。~~不过我没有被卡掉，我是现场定义的哈哈！~~