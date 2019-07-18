title: '[WOJ2820 Or]题解'
author: Catty2014
tags:
  - OI
  - 线段树
  - 题解
categories: []
date: 2019-05-04 15:26:00
---
[PORTAL](http://192.168.110.251/problempage.php?problem_id=2820)

本题要求每一个给定区间内按位或得到指定值的有效序列

而且是构造一个序列(可以有多组方案,由SPJ判断正确性)

所以我们可以初始化每一个数为INF($2^{29}-1$)

(INF的二进制是0b 00111111 11111111 11111111 11111111)

然后对于每一个条件，对区间内的数进行处理：

    如果or的值(p[i])的二进制中某一位的值为0
    则区间内所有的值对应二进制位都为0
    如果or的值(p[i])为1
    则区间内至少有一个数对应二进制位为1
    
    
最后判断:
	
    如果在处理后有一组(及以上)条件不再满足
    则说明不可能有指定的序列
    (此时跳出循环输出No)
    如果所有条件仍然满足
    则输出Yes和序列元素
    
~~其实只输出No就有20分~~

Code:
```cpp
/****************************************
 * W2820 [SPJ]or
 * Segment Tree Or
 ****************************************/


#include <cstdio>

typedef long long ll;
const int N=123333;
const int INF=((2<<29)-1); //INF=1073741823
//INF=0b00111111 11111111 11111111 11111111
//Binary value after "0b"
#define lc (p<<1)
#define rc ((p<<1)|1)

int m,n;
int l[N],r[N],p[N];

struct T
{
    int l,r,lz,v;
}t[(N<<3)];

void bd(int p,int l,int r)  //Build
{
    t[p].l=l;
    t[p].r=r;
    t[p].v=INF;
    t[p].lz=INF;
    if(l==r) return;
    int m=(l+r)/2;  //"int m=(l+r)>>1;"is also avaliable 
    bd(lc,l,m);
    bd(rc,m+1,r);
    return ;
}

void pu(int p)  //Pushup
{
    t[p].v=t[rc].v|t[lc].v;  //<--OR
    return ;
}

void pd(int p)  //Pushdown
{
    if(t[p].lz==INF) return;
    t[lc].v&=t[p].lz;
    t[rc].v&=t[p].lz;
    t[lc].lz&=t[p].lz;
    t[rc].lz&=t[p].lz;
    t[p].lz=INF;
}

void add(int p,int l,int r,int v)  //add
{
    if(l<=t[p].l&&t[p].r<=r)
    {
        t[p].lz&=v;
        t[p].v&=v;
        return;
    }
    pd(p);
    int m=(t[p].l+t[p].r)/2;
    if(m>=l) add(lc,l,r,v);
    if(m<r) add(rc,l,r,v);
    pu(p);
    return;
}

int qur(int p,int l,int r)  //Query
{
    if(l<=t[p].l&&t[p].r<=r)
    {
        return t[p].v;
    }
    pd(p);
    int m=(t[p].l+t[p].r)/2;
    int ans=0;
    if(m>=l) ans|=qur(lc,l,r);
    if(m<r) ans|=qur(rc,l,r);
    pu(p);
    return ans;
}

int main()
{
    scanf("%d %d",&n,&m);
    bd(1,1,n);
    for(int i=1;i<=m;i++)
    {
        scanf("%d %d %d",&l[i],&r[i],&p[i]);
        add(1,l[i],r[i],p[i]);
    }
    for(int i=1;i<=m;i++)
    {
        if(qur(1,l[i],r[i])!=p[i])  //Answer mismatch
        {
            printf("No\n");
            return 0;
        }
    }
    printf("Yes\n");
    for(int i=1;i<=n;i++)
    {
        printf("%d ",qur(1,i,i));
    }
    printf("\n");
    return 0;
}
```