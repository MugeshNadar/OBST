# OBST
its an obst code created by me


#include <stdio.h>
#include <stdlib.h>
#define inf 1000
int main()
{
	int *p,*q,nodes,n,i=0,x,y,flag,k,min,itr;
	int w[10][10]={0},c[10][10]={0},r[10][10]={0};
	printf("Enter the no of nodes :");
	scanf("%d",&nodes);
	n=nodes;
	p=(int*)calloc(n+1,sizeof(int));
	q=(int*)calloc(n+1,sizeof(int));
	printf("Enter the required details");
	for(i=1;i<=n;i++)
	{
		printf("\np%d: ",i);
		scanf("%d",&p[i]);
	}
	for(i=0;i<=n;i++)
	{
		printf("\nq%d: ",i);
		scanf("%d",&q[i]);
	}
	
	/*calculating the weight matrix*/
	
	x=0;y=0;
	for(i=0;i<=nodes;i++)
	{	flag=1;
		while(flag)
		{
			if(x==y)
				w[x][y]=q[y];
			else	
				w[x][y]=p[y]+q[y]+w[x][y-1];
			x++;
			y++;
			if(y>nodes)
			{
				y=i+1;
				x=0;
				flag=0;
			}	
		}
	}
	
/*CALCULATIONG THE COST and ROOT*/

	x=0;y=1;
	for(i=0;i<=nodes;i++)
	{	flag=1;
		while(flag)
		{	int count;
			min=inf;
			k=0;
			itr=x;
			for(count=0;count<=i-1;count++)
			{	n=min;
				min=min>(c[x][itr]+c[itr+1][y])?c[x][itr]+c[itr+1][y]:min;
				printf("\n%d for x=%d and y=%d and itr=%d",min,x,y,itr);
				if(n!=min)
					k=itr+1;
				itr++;	
			}
			c[x][y]=w[x][y]+min;
			r[x][y]=k;
			x++;
			y++;
			if(y>nodes)
			{
				y=i+1;
				x=0;
				flag=0;
			}	
		}

	}
	
	
/*	for(i=0;i<=nodes;i++)
	{	for(x=0;x<=nodes;x++)
		{
			printf("%d\t",w[i][x]);
		}
		printf("\n");
	}
	printf("\n");
	printf("\n");
	for(i=0;i<=nodes;i++)
	{	for(x=0;x<=nodes;x++)
		{
			printf("%d\t",c[i][x]);
		}
		printf("\n");
	}
	printf("\n");
	printf("\n");
	for(i=0;i<=nodes;i++)
	{	for(x=0;x<=nodes;x++)
		{
			printf("%d\t",r[i][x]);
		}
		printf("\n");
	}		*/
/*	for(i=0;i<=n;i++)
	{
		printf("\nq%d: %d",i,q[i]);
	}
	*/
	return 0;
}

