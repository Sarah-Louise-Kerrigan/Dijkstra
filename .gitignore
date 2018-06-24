#include <cstdio>
#include <iostream>
#include <cstring>
#include <algorithm>
#include <cstdlib>
#include <queue>
using std::priority_queue;
using std::max;
using std::min;
const int maxN=1e5;
struct Edge {
    int from,to,val,next;
    void init(int x,int y,int d,int cnt,int *pos){
        from=x;to=y;val=d;
        next=pos[from];pos[from]=cnt;    
    }
};
struct QNode {
    int u,val;
    QNode(int x,int d){
        u=x;val=d;
    }
    bool operator <(const QNode &a)const {
        return val>a.val;
    }
};
priority_queue<QNode> q;
int n,m,cnt,s,pos[maxN],dist[maxN],used[maxN];
Edge edges[maxN*20];
void re_assign(){
    freopen("dij.in","r",stdin);
    freopen("dij.out","w",stdout);
}
void init(){
    scanf("%d%d%d",&n,&m,&s);
    for(int i=1,x,y,d;i<=m;i++){
        scanf("%d%d%d",&x,&y,&d);
        ++cnt;edges[cnt].init(x,y,d,cnt,pos);
    	//++cnt;edges[cnt].init(y,x,d,cnt,pos);
    }
}
QNode make(int u,int val){
    QNode a(u,val);
    return a;
}
void dij(int s){
    memset(dist,127,sizeof(dist));
    q.push(make(s,0));
    dist[s]=0;
    while(!q.empty()){
    	int u=q.top().u;q.pop();
    	for(int x=pos[u];x;x=edges[x].next){
    		if(dist[edges[x].to]>dist[u]+edges[x].val){
    			dist[edges[x].to]=dist[u]+edges[x].val;
    			q.push(make(edges[x].to,dist[edges[x].to]));
    		}
    	}
    }
}
void print(){
    for(int i=1;i<=n;i++)
        if(dist[i]>21e8) printf("2147483647 ");
        else printf("%d ",dist[i]);
}
int main(){
    re_assign();
    init();
    dij(s);
    print();
    return 0;
}
