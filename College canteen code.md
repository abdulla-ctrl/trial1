#include<iostream>
#include<cmath>
using namespace std;
float fact(float n);
float queue(float j);
float ar,sr,arr1,avtt,nsa,z;
double la,lb;
double extt=10;
double ta,NL,T;
double ma,mb;
int z1;
int main()
{
	
cout<<"arival rate : ";
cin>>arr1;
cout<<"no of seats : ";
cin>>nsa;
cout<<"average time to finish eating : ";
cin>>avtt;

if((nsa/avtt)-arr1<=1 && (nsa/avtt)-arr1>0)
	{
	 	sr=nsa/avtt;
	 	ar=arr1;
	 	ma=queue(1);
	 	ar=sr;
	 	mb=queue(2);
	 	cout<<"service rate at mm1: "<<sr<<"\n";
	 	cout<<"service rate at mm2: "<<sr<<"\n"<<"\n";
	 	cout<<"Huge crowd at M/M/1 "<<"\n"<<"\n";
	 	cout<<"Increase the number of seats to "<<(arr1+1.5)*avtt<<" to reduce the queues"<<"\n"; 
	 	cout<<"so that the service rate at M/M/1 and M/M/2 becomes:"<<arr1+1.5<<"\n";
	 	
	 }

	 for(int z1=1;z1<=2;z1++)
	 {
	if((nsa/avtt)-arr1>1 && (nsa/avtt)-arr1<=2)
	{
	 if(z1==1)
	 {
	 	sr=nsa/avtt;
	     ar=arr1;
	 	ma=queue(1);
	 	cout<<"optimum service rate at mm1: "<<sr<<"\n";
	 }
	 if(z1==2)
	 {
	 	sr=nsa/avtt;
	 	ar=sr;
	 	mb=queue(2);
	 	cout<<"optimum service rate at mm2: "<<sr;
	 }
	 
	}
	 
if((nsa/avtt)-arr1>2)
	{
	 if(z1==1)
	 {
	 	sr=arr1+1.5;
	 	ar=arr1;
	 	ma=queue(1);
	 	cout<<"optimum service rate at mm1: "<<sr<<"\n";
	 }
	 if(z1==2)
	 {
	 	sr=arr1+1.5;
	 	ar=sr;
	 	mb=queue(2);
	 	cout<<"optimum service rate at mm2: "<<sr;	
}
		 
if((nsa/avtt)<arr1 || (nsa/avtt)-arr1==0)	 
{
	 cout<<"\n"<<"Not enough space"<<"\n";
	 cout<<"You need atleast "<<arr1*avtt+1<<" seats";
	 cout<<"Huge crowd at M/M/1";
	 exit(0);
	 
}
}
	 }
	 cout<<"\n"<<"\n";
	 cout<<"Enter the length at counter 1: ";
    cin>>la;
    cout<<"Enter the length at counter 2: ";
    cin>>lb;
    cout<<"\n";
    ta =((la + 1)/ma)+(extt/60);
   
    NL =(la+lb)- (ta*mb);
    
    
       if(NL>0)
       {
           T= ta+((NL+(0.5))/mb);
           cout<<"you will be served between : ";
           int T1= T-(1/mb);
      double T2=(T-T1)*60+(60/mb);
      if(T2>=60)
      {
      	T1+=1;
      T2-=60;
      }
      else if( T2<0)
      {
      	T1-=1;
      	T2+=60;}
      	
      int T3= T+(1/mb);
      double T4=(T-T3)*60-(60/mb);
       if(T4>=60)
      {
      	T3+=1;
      T4-=60;
      }
      else if( T4<0)
      {
      	T3-=1;
      	T4+=60;}
           cout<< T1<<" minutes " <<T2<<" seconds "<<" and "<< T3 <<" minutes "<<T4<<" seconds";
           
       }
      else if(NL<=0)
      {
      T= ta+(2/mb);
      cout<<"you will be served after : ";
      int T1= T;
      float T2=(T-T1)*60;
      cout<< T1 << " minutes "<<T2<<"  seconds ";
      }
      return 0;
}

float fact(float n)
{
    if(n > 1)
        return n * fact(n - 1);
    else
        return 1;
}
float queue(float j)
{
	float x,q,z,y,ls,lq,ws,wq,a,po1=0,po;
	z=j;
	q=(ar/(sr));
	a=1-(q/z);
	for(int i=0;i<z;i++)
	{
		x=pow(q,i)/fact(i);
		
		po1+=x;
		
	}
		y=pow(q,z)/(fact(z)*a);

	po=1/(po1+y);
	ls=(((pow(q,z)*po)/(sr*fact(z)*z*pow(a,2))) + (1/sr))*ar;
	lq=ls-q;
	ws=ls/ar;
	wq=ws-(1/sr);
	return (1/(ws-wq));
}
