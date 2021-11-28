# BST
## �߶���
�߶���ά������������������ӷ���������е����ʡ����磺����ͣ��ӳ��߶�������gcd�����京�����ĸ�����Ȩֵ�߶������ȡ��߶����Ĳ�����ʱ�临�Ӷȶ���$O(\log_2{n})$�ġ�
1. ά��������ɾ���ģ�
�߶�������ά�������ϵ���Ϣ�����������ڲ�����Ϣ���Զ�̬�ı仯�������߶����������֮�����䳤�Ȳ��ܱ仯�������漰���䳤�ȱ仯ʱ������Ԥ�Ƚ����ڵ㣬�ﵽ�޸����䳤�ȵ�Ŀ�ġ�**���������������˶�̬���ӽڵ�**��

������Ϣ�޸ģ�����**�����޸�**��Ҳ����**�����޸�**��

�����޸ģ�
- ����Ӽ���
- ����˳���
- ����ȡ$min$��$max$����Ҫ�洢��ֵ�ĸ���$cnt$�Լ�����ֵ$sx$
2. ��

�߶����Ĳ�ѯ���õ���������Ϣ�ɼ��ԡ�����漰�����޸ĵ�ʱ��**��Ҫ�ڶ��ֲ����ӽڵ�֮ǰ�������pushdown**������ʱ��ֻҪ�������������Ϣ�ϲ����ɡ�

### Ȩֵ�߶���
�����ڱ������Ϣ�Ǹýڵ���ֵĴ�����������ɵĲ����У�
1. ����Ԫ�� $add$ && ɾ��Ԫ�� $del$
ֻ��Ҫ���¸��½ڵ���Ϣ�����߶��������޸ĵĲ���һ����
2. ��ѯ��k���Ԫ�� $kth$
3. ��ѯx��ǰ������ $rank$
4. ��ѯx��ǰ�� $pre$

�Ȳ�ѯ$x-1$��ǰ����������$[1,x-1]$���ж��ٸ������ٲ�ѯ����Ϊ$rank$�Ľڵ㣬����$kth(rank(x-1))$��

5. ��ѯx�ĺ�� $post$

�Ȳ�ѯ$x$����������$[1,x]$���ж��ٸ������ٲ�ѯ����Ϊ$rank+1$�Ľڵ㣬����$kth(rank(x)+1)$����Ϊ��̿����뵱ǰ�ڵ��ֵ��ͬ��

### �ɳ־û�Ȩֵ�߶���
���ó�������$[l,r]$������Ȩֵ�߶������������в�����

��Ȩֵ�߶�����֮ͬ���Ǳ�������ʷ�汾��Ȩֵ�߶��������磺$rt[l-1]$������l-1ʱ�������ڲ�����Ϣ����$[1,l-1]$�����ڲ�����Ϣ��$rt[r]$������$[1,r]$�����ڲ�����Ϣ����������ǰ׺�ͣ����ǿ��Զ�$[l,r]$���侭��Ȩֵ�߶����Ĳ�����Ҳ��һЩ���������������$[l,r]$�����ڵ����ֵ����Сֵ��ͨ����ѯrank�Լ����ּ�����ɡ�

Ȩֵ�߶����Ľ����ǴӲ������κ���Ϣ��Ȩֵ�߶�����ʼ�ġ�ÿ����һ��Ȩֵ�߶�������Ҫ$O(log_2{n})$�����ԴӶ�β׷��Ԫ�ء�

### �ɳ־û��ӷ��߶���
���ó������ص��߶�������ʷ�汾����ѯ���ǰ汾����Ϣ��

��Ȼ��֧��pushdown�Ĳ���������֧�������޸ĵĲ��������Ծ��������޸Ĺ�����ϯ����Ҫ���޸ķֽ紦����$lazy$���ֽ紦��������ʷ�汾�ڵ㣩������ѯ�Ϳ����ˡ�ע����Ҫ$pushup$

## AVL
AVL����ƽ���������һ�֡�ͨ��$ll,lr,rr,rl$��תʹ��BSTƽ�⡣ͬʱ����BST��һ�й���:$insert,find,del.$

## Splay

## Treap

## ��

### ����ֱ��

#### ����dfs��bfs

#### ����dp

### LCA
����������棬������֮��ľ���
#### ����
$O(log_2{mn})$

#### Tarjan�����ߣ�

#### ����
Ԥ����:$O(n\log{n})$��query:$O(1)$
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
ŷ�����ϲ�ѯ$[l,r]$��$min$

#### �����ʷ�
��������LCA
- dfs1
�ҳ��ض���
- dfs2
�ҳ�����

#### LCT

## ��С������

### ��Сƿ��·
#### def
����һ����Ȩ����ͼ�����ڵ�$u$��$v$����$u$��$v$��һ��·����ʹ��**·���ϱߵ����Ȩֵ��С**��

���ȣ����������ڵ����Сƿ��·һ������С�������ϡ��������ǿ����������С��������Ȼ���$u$��DFS��$v$�㣬����ʵ�ֵ�ʱ�临�Ӷ���$O(\log{n})$����Ȼ��TLE��

�������ǿ����ڲ�ѯ֮ǰ����**Ԥ����**�������нڵ�Ե���߱�����һ��$maxcost$�����У�Ȼ���ѯֻҪ$O(1})$�����ƹ�ʽ���£�
$maxcost[j][u] = max(maxcost[j][fa[u]],maxcost[j][u])$
����$j$��$u$����Сƿ��·��$j$��$fa[u]$��$j$��$u$��Сƿ��·�����ֵ
#### ʵ�ַ���
����prime�㷨
�������С�������Ĺ����н��и�������������ͬʱ������нڵ��$maxcost$
```c++

int prime(){
    int res = 0;
    memset(maxcost,0,sizeof(maxcost));
    for(int i=1;i<=n;i++){
        vis[i]=0 , d[i] = INF , pre[i] = i;
    }
    d[s] = 0;                           //Ԥ��ѡ��s
    for(int i=0;i<n;i++){
        int mx = INF , index = -1;
        for(int j=1;j<=n;j++){
            if(!vis[j]&&d[j]<mx)
                mx = d[index=j];       //ѡ��d��С�ĵ�
        }
        if(index==-1) break;
        for(int j=1;j<=n;j++)    //j->index = j->fa->index
            if(vis[j])
                maxcost[index][j] = maxcost[j][index] = 
                    max(maxcost[pre[index]][j],mx);
        res += mx;
        vis[index] = 1;
        for(int j=1;j<=n;j++){         //��ѡ�е�index���������ڵ�
            if(!vis[j]&&g[index][j]<d[j]){
                d[j] = g[index][j];
                pre[j] = index;
            }
        }
    }
    return res;
}

```

## ���������
```cpp
const int v=2; //��ά��
int d=2;//ʵ��ά��
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