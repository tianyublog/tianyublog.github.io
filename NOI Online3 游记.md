# NOI Online3 游记

## Day $-2$​

看到自己的准考证号和密码了。入门组是 JS-00404，真的好不吉利啊！

## Day $-1$

周五的作业超级多，打算不写，养足精力给明天刷题用。很早就睡了。

## Day $0$

比赛明天就开始了，用昨天养了一晚上的精力全用来刷题了。先在洛谷上刷了一些简单题，然后又跑到 AcWing 上刷了一些动态规划的模板题，最后跟 b6e0 大佬打 AC Saber 练一练手速，完败啊！不刷了，走人！

晚上就是编程课，因为不太难所以觉得还好，压力减少了一点点。

## Day $1$

### 考试前

这里是考试前的 Day $1$。早上起来，刚刚有意识了就想到了昨天下午跟 b6e0 大佬打 AC Saber 完败的场景，大叫道：

> 每天起床第一句，stO b6e0 Orz！

然后吃完早饭后后就准备，这时候是早上 $8$ 点，还有半个小时，反正大家都不打提高组（还在睡觉），打算看一会儿书，选了《算法竞赛》和《算法笔记》两本书，看了一小会儿就看不下去了，因为马上提高组开始了，激动地不得了。

马上提高组开始了，咱们看下一个章节。

### 提高组

考试一开始，我蹦出来一句：

> 完了完了，我这个小学生才普及组一等水平，这个提高组不是要爆零了？

对啊，我不是要爆零了吗？先做好心理准备。

#### 第一题

我打开了第一题。紧张的我看了半天才看懂什么意思，接下来尽是往难得算法想。DP？贪心？枚举优化？后来发现这些想法都是多余的嘛！其实这道题就是求出一个数列中连续 $K+1$ 个数的和，最大能多少。就是简单的前缀和呀！

```c++
#include<iostream>
#include<cstdio>
using namespace std;
int main(){
	int n;
	int k;
	cin>>n>>k;
	int a[n+1];
	a[0]=0;
	for(int i=1;i<=n;++i)
		cin>>a[i];
	int sum[n+1];
	sum[0]=a[0];
	for(int i=1;i<=n;++i)
		sum[i]=a[i]+sum[i-1];
	int maxv=0;
	for(int i=k+1;i<=n;++i)
		maxv=max(maxv,sum[i]-sum[i-k-1]);
	cout<<maxv<<endl;
	return 0;
}
```

#### 第二题

然后看了看第二题，没看懂。

#### 第三题

又看了看第三题，没看懂。

#### 最后 & 总结

由于 $2, 3$ 两道题都看不懂，我对自己说：

> 没关系，没有零蛋就不错了！

的确啊，已经超出我比赛前对自己的要求了，居然没有爆零！然后我就开开心心地写文化课去了。

提高组结束前，我再检查了一下题目，惊奇地发现第一题每加文件操作！好险，差点就爆零了，还好及时补上啊！

提交后就去吃午饭了，比赛结束了。

### 午间休息

先吃完了午饭，然后回到电脑上。

看完了 ix35 大佬写的题解，链接：<https://www.luogu.com.cn/blog/ix-35/noi-online-3-post>。

> EA nb！EA nb！EA nb！

但是第二题和第三题的题解看了也白看，毕竟题目都没弄懂。

在洛谷上把第一题民间数据测了一下，$100$ 分，很开心。

然后想到了在电脑旁边堆积如山的文化课作业，先去搞文化课吧……

搞了大概一个小时文化课，现在是 $1$ 时 $30$ 分，还有一个小时。下午打的人就多了，看了看 QQ，消息 $99+$。大家问的都是关于 NOI Online3 的问题，我不得不耐心地回复。最后实在是受不了了，挤出来一句：

> $\color{white}\text{STFW}$

有人问为啥上不去 <http://online3.noi.cn>（我们这里在江苏，刚刚准考证号也说了），这个问题很奇怪，比赛开始还有很久，怎么能让你上去呢？~~明显没打过 NOI Online2。~~

然后又发了好多条 $\color{white}\text{STFW}$，不过大家基本上都在网上找到了结果。

## 入门组

入门组让我心惊肉跳，有一群人跟我一起打咧！

#### 第一题

第一题很水的，几分钟就切掉了，纯模拟，不用多说。

```c++
#include<iostream>
#include<cstdio>
#include<vector>
using namespace std;
int main(){
	freopen("save.in","r",stdin);
	freopen("save.out","w",stdout);
	int n;
	cin>>n;
	string name[n+1];
	string sos[n+1];
	for(int i=1;i<=n;++i)
		cin>>name[i]>>sos[i];
	int num[n+1];
	for(int i=1;i<=n;++i){
		num[i]=0;
		for(int j=2;j<sos[i].size();++j)
			if(sos[i][j-2]=='s'&&sos[i][j-1]=='o'&&sos[i][j]=='s')
				++num[i];
	}
	int maxi=1;
	vector<int>ans;
	ans.push_back(1);
	for(int i=2;i<=n;++i)
		if(num[i]>=num[maxi]){
			if(num[i]>num[maxi]){
				maxi=i;
				ans.clear();
			}
			ans.push_back(i);
		}
	for(int i=0;i<ans.size();++i)
		cout<<name[ans[i]]<<' ';
	cout<<endl<<num[maxi]<<endl;
	return 0;
}
```

开心极了，$100$ 分到手！~~这一回终于没有忘记加文件操作啊！~~

#### 第三题

为啥突然跳到第三题了呢，我来给大家说一下：

> 因为服务器经常崩掉，就像 NOI Online2 一样，<http://online3.noi.cn> 的入门组第二题只剩下半个题面，所以我就先把每道题目都存了下来。而存下来后没有排序，所以误以为这道题时第二题，吭哧吭哧做了好久。

我刚刚看完这道题的时候居然 $0.1$ 秒想到了有限背包问题，然后觉得的确是这个 DP 的板子题，就直接开始写代码。代码不长，很快就写完了。

下面放上我的代码：

```c++
#include<iostream>
#include<cstdio> 
using namespace std;
int main(){
	int n,m;
	cin>>n>>m;
	bool b[500001];
	for(int i=1;i<=500000;++i)
		b[i]=0;
	b[0]=1;
	int k,a;
	for(int i=1;i<=n;++i){
		cin>>k>>a;
		for(int f=500000;f>=k;--f)
			b[f]=b[f]||b[f-k];
	}
	int x;
	for(int i=1;i<=m;++i){
		cin>>x;
		if(b[x])
			cout<<"Yes"<<endl;
		else
			cout<<"No"<<endl;
	}
}
```

细心的人应该发现我又没加文件操作。不过编完后查出来了，又差点一道题 $0$ 分。

#### 第二题

然后我终于发现我看错题了，把第三题看成了第二题。看第二题的时候我快没耐心了，以语文老师教的“快速阅读”方法读题，结果怎么读都读不懂。半个小时后，我终于明白了，就是求连通块的一系列操作。

```c++
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

#### 最后 & 总结

最后看了看第三题，发现我这个背包会超时。我记得在 AcWing 上做过类似的题，当时要加优化，我写完一次后就没有再巩固，结果还真的考到了……

所以，刷完了题一定要巩固啊！

### 晚上

测了一下入门组，我是二百五。

这不是骂人的话，因为分数的确是这样~~残酷~~：
$$
100 + 100 + 50 = 250 \left( 分 \right)
$$
然后发现大家都是二百五。不过 b6e0 大佬好像第三题零分，我说不清怎么回事。

期待我的真实分数~~大于~~等于这个民间分数吧！

## Day $2$

作业在学校写完了，回到家看到了 NOI 官网上已经给了题S解，先转到了 QQ 群里然后看了入门组的第一题。

这时候发现 ducati 菜鸡（他让大家叫他菜鸡，那么就这样吧）已经写好了游记，自己也搞了一篇。

然后就写完了，我该继续看一下其他的视频题解了。

对了，还记得上面有空白字吗？想看的自己右键查看网页源代码吧！我就是不告诉你这是啥 $\rightarrow$ $\color{white}\text{STFW}$ 

再见！:stuck_out_tongue_winking_eye: