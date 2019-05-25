#include<cstdio>
#include<algorithm>
#include<cstring>
#include<iostream>
#define INF 100000000
#define LL (0x3f3f3f3f3f3f3f3f)*2
#define lc rt<<1
#define rc rt<<1|1
using namespace std;
const int maxn = 2e5 + 5;
typedef long long ll;

int pos[maxn], val[maxn];
int sum[maxn << 2];
int ans[maxn];
int n;

void pushup(int rt)
{
    sum[rt] = sum[lc] + sum[rc];
}
void build(int rt, int l, int r)
{
    if(l == r) {
        sum[rt] = 1;
        return;
    }
    int m = (l + r) >> 1;
    build(lc, l, m);
    build(rc, m + 1, r);
    pushup(rt);
}
void update(int p, int add, int l , int r , int rt ) {
    if(l == r) {
        sum[rt] = 0;
        ans[l] = add;
        return ;
    }
    int m = (l + r) >> 1;
    if(p <= sum[rt << 1])update(p, add, l,m,lc);
    else update(p - sum[rt << 1], add, m+1,r,rc);
    pushup(rt);
}
int main()
{
   　for(;~scanf("%d", &n);)
    {
        for(int i = 1; i <= n; ++i)
            scanf("%d%d", pos + i, val + i);
        build(1, 1, n);
        for(int i = n; i >= 1; --i)
        {
            int p = pos[i]+1;
            int v = val[i];
            update(p, v, 1, n, 1);
        }
        for(int i = 1; i <= n; ++i)
            printf("%d%c", ans[i], (i ^ n ? ' ' : '\n'));
        memset(ans, 0, sizeof(ans));
    }
}
