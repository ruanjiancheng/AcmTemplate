# BST
## 线段树
线段树维护的是区间满足区间加法的区间具有的性质。例如：区间和（加乘线段树），gcd，区间含有数的个数（权值线段树）等。线段树的操作的时间复杂度都是$O(\log_2{n})$的。
1. 维护（增，删，改）
线段树用于维护区间上的信息，所以区间内部的信息可以动态的变化。但是线段树建立完成之后，区间长度不能变化。所以涉及区间长度变化时，可以预先建立节点，达到修改区间长度的目的。**仅限于在区间两端动态增加节点**。

区间信息修改：可以**单点修改**，也可以**区间修改**。

区间修改：
- 区间加减法
- 区间乘除法
- 区间取$min$或$max$：需要存储最值的个数$cnt$以及次最值$sx$
2. 查

线段树的查询利用的是区间信息可加性。如果涉及区间修改的时候，**需要在二分查找子节点之前，先完成pushdown**。返回时，只要将左右区间的信息合并即可。

### 权值线段树
区间内保存的信息是该节点出现的次数。可以完成的操作有：
1. 增加元素 $add$ && 删除元素 $del$
只需要向下更新节点信息，与线段树单点修改的操作一样。
2. 查询第k大的元素 $kth$
3. 查询x当前的排名 $rank$
4. 查询x的前驱 $pre$

先查询$x-1$当前的排名，即$[1,x-1]$内有多少个数。再查询排名为$rank$的节点，即：$kth(rank(x-1))$，

5. 查询x的后继 $post$

先查询$x$的排名，即$[1,x]$内有多少个数。再查询排名为$rank+1$的节点，即：$kth(rank(x)+1)$，因为后继可能与当前节点的值相同。

### 可持久化权值线段树
运用场景：做$[l,r]$区间内权值线段树能做的所有操作。

与权值线段树不同之处是保存了历史版本的权值线段树。例如：$rt[l-1]$保留了l-1时刻区间内部的信息，即$[1,l-1]$区间内部的信息。$rt[r]$保留了$[1,r]$区间内部的信息。所以利用前缀和，我们可以对$[l,r]$区间经行权值线段树的操作。也有一些特殊操作，例如求$[l,r]$区间内的最大值或最小值。通过查询rank以及二分即可完成。

权值线段树的建立是从不含有任何信息的权值线段树开始的。每建立一棵权值线段树都需要$O(log_2{n})$。所以从队尾追加元素。

### 可持久化加法线段树
运用场景：回到线段树的历史版本；查询历是版本的信息。

虽然不支持pushdown的操作，但是支持区间修改的操作。所以具有区间修改功能主席树需要在修改分界处加上$lazy$（分界处以下是历史版本节点）继续查询就可以了。注意需要$pushup$

## AVL
AVL树是平衡二叉树的一种。通过$ll,lr,rr,rl$旋转使得BST平衡。同时具有BST的一切功能:$insert,find,del.$

## Splay

## Treap

## 树

### 树的直径

#### 两次dfs或bfs

#### 树形dp

### LCA
求最近公共祖，求两点之间的距离
#### 暴力
$O(log_2{mn})$

#### Tarjan（离线）

#### 倍增
预处理:$O(n\log{n})$，query:$O(1)$
```c++
inline void pre(){
    for(int j=1;j<=floor(log(n));j++)
        for(int i=1;i<=n;i++)
            parent[i][j] = parent[parent[i][j-1][j-1]];
}
inline int getlca(int x,int y){
    if(dep[x]<dep[y]) swap(x,y);
    int deep=dep[y];
    for(int i=floor(log()))
}

```
#### RMQ
欧拉序上查询$[l,r]$的$min$

#### 树链剖分
跳重链求LCA
- dfs1
找出重儿子
- dfs2
找出重链

#### LCT

## 最小生成树

### 最小瓶颈路
#### def
给定一个加权无向图两个节点$u$和$v$，求$u$到$v$的一条路径，使得**路径上边的最大权值最小**。

首先，任意两个节点的最小瓶颈路一定在最小生成树上。所以我们可以先求出最小生成树。然后从$u$点DFS到$v$点，这样实现的时间复杂度是$O(\log{n})$。显然会TLE。

所以我们考虑在查询之前进行**预处理**，将所有节点对的最长边保存在一个$maxcost$数组中，然后查询只要$O(1})$。递推公式如下：
$maxcost[j][u] = max(maxcost[j][fa[u]],maxcost[j][u])$
更新$j$到$u$的最小瓶颈路是$j$到$fa[u]$或$j$到$u$最小瓶颈路的最大值
#### 实现方法
基于prime算法
在求解最小生成树的过程中将有根树建立起来，同时求出所有节点的$maxcost$
```c++

int prime(){
    int res = 0;
    memset(maxcost,0,sizeof(maxcost));
    for(int i=1;i<=n;i++){
        vis[i]=0 , d[i] = INF , pre[i] = i;
    }
    d[s] = 0;                           //预先选中s
    for(int i=0;i<n;i++){
        int mx = INF , index = -1;
        for(int j=1;j<=n;j++){
            if(!vis[j]&&d[j]<mx)
                mx = d[index=j];       //选中d最小的点
        }
        if(index==-1) break;
        for(int j=1;j<=n;j++)    //j->index = j->fa->index
            if(vis[j])
                maxcost[index][j] = maxcost[j][index] = 
                    max(maxcost[pre[index]][j],mx);
        res += mx;
        vis[index] = 1;
        for(int j=1;j<=n;j++){         //用选中的index更新其他节点
            if(!vis[j]&&g[index][j]<d[j]){
                d[j] = g[index][j];
                pre[j] = index;
            }
        }
    }
    return res;
}

```

## 矩阵快速幂
```cpp
const int v=2; //开维数
int d=2;//实际维数
const int mod = 998244353;
struct matrix
{
    ll m[v][v];
    void init() {memset(m,0,sizeof(m));for(int i=0;i<d;++i) m[i][i]=1;}
    void clear() {memset(m,0,sizeof(m));}
    matrix operator +(const matrix &o) const
    {
        matrix res={};
        for(int i=0;i<d;++i)
            for(int j=0;j<d;++j)
                res.m[i][j]=(m[i][j]+o.m[i][j])%mod;
        return res;
    }
    matrix operator *(const matrix &o) const
    {
        matrix res={};
        for(int i=0; i<d; i++)
            for(int j=0; j<d; j++)
                for(int k=0; k<d; k++)
                    res.m[i][j]=(res.m[i][j]+m[i][k]*o.m[k][j]%mod)%mod;
        return res;
    }
    matrix operator -(const matrix &o) const
    {
        matrix res={};
        for(int i=0;i<d;++i)
            for(int j=0;j<d;++j)
                res.m[i][j]=(m[i][j]-o.m[i][j]+mod)%mod;
        return res;
    }
}Ans, base;
inline void mat_quick(ll p)
{
    Ans.init();
    base={1,1,1,mod-1};
    while(p)
    {
        if(p & 1) Ans = Ans*base;
        base = base*base;
        p >>= 1;
    }
}
```