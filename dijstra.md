```c++
#include<iostream>
#include<cstring>
using namespace std;
int field[20][20];
int dis[20];
int vis[20];
int n,m;
const int inf=0x3f3f3f3f;
int main()
{
	cin>>n>>m;
	memset(field,inf,sizeof(field));
	memset(vis,0,sizeof(vis));
	memset(dis,inf,sizeof(dis));
	for(int i=1;i<=m;i++)
	{
		int a,b,d;
		cin>>a>>b>>d;
		field[a][b]=d;
		if(a==1)	dis[b]=d;
	}
	vis[1]=1;
	dis[1]=0;
	for(int i=1;i<=n;i++)
	{
		int minn=inf;
		int x=-1;
		for(int j=1;j<=n;j++)
		{
			if(!vis[j]&&minn>dis[j])
			{
				minn=dis[j];
				x=j;
			}
		}
		if(minn==inf)	continue;
		vis[x]=1;
		for(int j=1;j<=n;j++)
		{
			if(!vis[j]&&dis[x]+field[x][j]<dis[j])
			{
				dis[j]=dis[x]+field[x][j];
			}
		}
	}
	for(int i=1;i<=n;i++)
		cout<<dis[i]<<" ";
} 
```

