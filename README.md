# DNA1
#include <iostream>
#include <stdlib.h>
#include <string.h>

using namespace std;
int min(int a,int b)
{
	int c=(a>b?b:a);
	return c;
}

int main(int argc,char *argv[])
{
	string a,b,c;
	cin>>a;
	cin>>b;
	cin>>b;
	int gap,mismatch,match;
	//cout<<a<<"  "<<b<<endl;
	if(atoi(argv[1])==1)
	{
          gap=6;
          mismatch=4;
	  match=-1;
	}
	else if(atoi(argv[1])==2)
	{
		gap=4;
		mismatch=6;
		match=-1;
	}
	int lena=a.size();cout<<gap;
	int lenb=b.size();cout<<mismatch;
	int matrix[lena+1][lenb-1];
	for(int i=0;i<lena+1;i++)
	{
		matrix[i][0]=i*gap;
	}
	for(int i=0;i<lenb-1;i++)
	{
		matrix[0][i]=i*gap;
	}
    for(int j=1;j<lenb+1;j++)
    {
    	for(int i=1;i<lena+1;i++)
    	{
    		//int min1=min(gap+matrix[i-1,j],gap+matrix[i,j-1]);
    		if(a[i-1]!=b[j-1])
            matrix[i][j]=min(mismatch+matrix[i-1][j-1],min(gap+matrix[i-1][j],gap+matrix[i][j-1]));
        else
        	matrix[i][j]=min(matrix[i-1][j-1],min(matrix[i-1][j],matrix[i][j-1]));
            cout<<matrix[i][j]<<" ";
    	}
    	cout<<endl;
    }
    int cost=matrix[lena][lenb];
    cout<<"Cost="<<cost<<endl;
	return 0;
}
