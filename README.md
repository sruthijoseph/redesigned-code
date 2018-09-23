#include<stdio.h>
int main()
{
   int i,j,k,p,r,f,sum[10],max[10][10],alloc[10][10],need[10][10],total[10],avail[10],finish[10],order[10],flag;
   printf("Enter the number of process:");
   scanf("%d",&p);
   printf("Enter the number of Resources:");
   scanf("%d",&r);
   	for(i=0;i<p;i++)
      {
      	finish[i]=0;
      }
   printf("Enter the max matrix\n");
   printf("A B C\n");
   for(i=0;i<p;i++)
    {
      for(j=0;j<r;j++)
      {
        scanf("%d",&max[i][j]);
      }
	}
    printf("Enter the allocation matrix\n");
    printf("A B C\n");
    for(i=0;i<p;i++)
    {
     for(j=0;j<r;j++)
     {
       scanf("%d",&alloc[i][j]);
       need[i][j]=max[i][j]-alloc[i][j];
       sum[j]=sum[j]+alloc[i][j];
     }
	}
    printf("Enter the available resource\n");
    for(i=0;i<r;i++)
    {
      scanf("%d",&avail[i]);
    }
    f=0;
    do
    {
    	for(i=0;i<p;i++)
	{
		if(finish[i]==0)
		{   
			 flag=0;
			 for(j=0;j<r;j++)
			 {
				if(need[i][j]>avail[j])
				{
					flag=1;
					break;	
				}
			}
		        if(flag==0)
		 	{
				for(k=0;k<r;k++)
				{	
					avail[k]=avail[k]+alloc[i][k];	
				}
				order[f++]=i;
				finish[i]=1;	
			}	
		}
    	}
	}while(f<p);
	printf("Safe Sequence for deadlock avoidance:");
	for(i=0;i<p;i++)
	{		
		printf("P(%d)\t",order[i]);
	}
}
 


