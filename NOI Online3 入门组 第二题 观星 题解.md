# NOI Online3 入门组 第二题 观星 题解

## Part1 前言

NOI Online3 比 NOI Online2 良心！

## Part2 题面

这道题的题面有点绕，我来再总结一下：

- 一颗星星旁边所有的星星跟这颗星星是同一个星座。
- 同样大小（星星数量相同）的星座叫做星系，这些星座不必连接。
- 求出一共有多少个星系和最大的星系大小。

## Part3 思路

数据范围很小，天空最大有 $1500 \times 1500$，可以使用搜索的方法来做。深搜的方法可以是递归，每次扫描这个星星周围的所有星星，当旁边所有的地方都不是星星或已经扫过了，就停止。宽搜其实就是队列，“拉网式搜索”，跟深搜差不多，扫描周围的星星，当有一颗没扫描过的星星就放入队列。

我们发现，深搜的层数与宽搜队列长度仅有 $100000$，不可能得到 `MLE` 的结果。然后再看时间。深搜与宽搜最惨**总时间复杂度**为 $\operatorname{O}\left(NM\right)$，也就是 $1500 \times 1500$，不会超。外部套一个枚举起始点，对时间复杂度没有影响。

## Part4 代码

给出深搜的代码（宽搜作者其实不太熟，怕被喷就不挂上了）：

```cpp
#include<iostream>
#include<cstdio> 
#include<set>
#include<map>
using namespace std;
int n,m;
char c[1501][1501];
int cnt;
int mo[3][9]={{0,0,0,0,0,0,0,0,0},{0,1,1,1,0,-1,-1,-1,0},{0,-1,0,1,1,1,0,-1,-1}};
void dfs(int i,int j){
	++cnt;
	c[i][j]='.';
	for(int k=1;k<=8;++k){
		int nx=i+mo[1][k];
		int ny=j+mo[2][k];
		if(nx>=1&&nx<=n&&ny>=1&&ny<=m&&c[nx][ny]=='*')
			dfs(nx,ny);
	}
}
int main(){
	freopen("star.in","r",stdin);
	freopen("star.out","w",stdout);
	cin>>n>>m;
	for(int i=1;i<=n;++i)
		for(int j=1;j<=m;++j)
			cin>>c[i][j];
	int maxv=0;
	set<int>s;
	map<int,int>ma;
	for(int i=1;i<=n;++i)
		for(int j=1;j<=m;++j)
			if(c[i][j]=='*'){
				cnt=0;
				dfs(i,j);
				ma[cnt]+=cnt;
				maxv=max(maxv,ma[cnt]); 
				s.insert(cnt);
			}
	cout<<s.size()<<' '<<maxv<<endl;
	return 0;
}
```

不要喷我qwq

## Part5 结语

其实，看到这道题的时候数据范围小，只管爆搜。接下来，我给大家赠上一个给大家参考的数据范围与算法关系的表：

| 100以下 | 100~500                            | 501~8000                           | 8001~500000                            | 500000以上                                                   |
| ------- | ---------------------------------- | ---------------------------------- | -------------------------------------- | ------------------------------------------------------------ |
| 搜索    | $\operatorname{O}\left(N^3\right)$ | $\operatorname{O}\left(N^2\right)$ | $\operatorname{O}\left(N\log N\right)$ | $\operatorname{O}\left(N\right)$ 或 $\operatorname{O}\left(1\right)$ |