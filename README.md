# SPOJ-
Spoj questions


#include <iostream>
#include<stdlib.h>
#include<queue>
#include<bits/stdc++.h>
using namespace std;


/*
4 3
ABC
XYD
PQE
RSF */

bool islimit(int x,int y,int n,int m)
{
	if(x>=0&&x<=n-1&&y>=0&&y<=m-1)
	{
		return true;
	}
	else
	{
		return false;
	}
}


void dfs(vector<vector<char> >arr,vector<vector<int> >&vis,int i,int j,int n,int m)
{
	
	cout<<arr[i][j]<<endl;
	
	if(islimit(i+1,j,n,m)&&arr[i+1][j]-arr[i][j]==1&&vis[i+1][j]==0)
	{
		vis[i+1][j]=1+vis[i][j];
		dfs(arr,vis,i+1,j,n,m);
	}
	
	if(islimit(i-1,j,n,m)&&arr[i-1][j]-arr[i][j]==1&&vis[i-1][j]==0)
	{
		
		vis[i-1][j]=1+vis[i][j];
		dfs(arr,vis,i-1,j,n,m);
	}
	
	if(islimit(i,j+1,n,m)&&arr[i][j+1]-arr[i][j]==1&&vis[i][j+1]==0)
	{
		
		vis[i][j+1]=1+vis[i][j];
		dfs(arr,vis,i,j+1,n,m);
	}
	
	if(islimit(i,j-1,n,m)&&arr[i][j-1]-arr[i][j]==1&&vis[i][j-1]==0)
	{
		vis[i][j-1]=1+vis[i][j];
		dfs(arr,vis,i,j-1,n,m);
	}
	
	
	
	
}

int main()
{
	int n,m;
	
	cin>>n>>m;
	
	vector<vector<char> >arr(n,vector<char>(m));
	
	vector<vector<int> >vis(n,vector<int>(m));
	
	char x;
	
	
	
	for(int i=0;i<n;i++)
	{
		for(int j=0;j<m;j++)
		{
			cin>>x;
			
			vis[i][j]=0;
			arr[i][j]=x;
		}
	}
	
	int ans;
	
	for(int i=0;i<n;i++)
	{
		for(int j=0;j<m;j++)
		{
			if(arr[i][j]=='A')
			{
				vis[i][j]=1;
				dfs(arr,vis,i,j,n,m);
			}
		}
	}
	
	
	
	
	
	
	
	
	
	for(int i=0;i<n;i++)
	{
		for(int j=0;j<m;j++)
		{	
			cout<<vis[i][j]<<" ";
			
		}
		
		cout<<endl;
	}
	
	
	return 0;
	
 
}




A
B
A
B
C
D
E
F
B
C
1 2 6
3 4 5
2 0 0
1 2 3
