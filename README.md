
#include<iostream>
using namespace std;
int main()
{
	int n;
	cin>>n;
	int victory=0;
	int defeat=0;
	int mid=0;
	char a,b;
	int solution[2][3];
	
	int i=0;
	int j=0;
	for(i=0;i<2;i++){
		for(j=0;j<3;j++){
			solution[i][j]=0;
		}
	}
	for(i=0;i<n;i++){
		cin>>a>>b;
		if(a==b){
			mid++; 
		}
		else{
			if((a=='C'&&b=='J')||(a=='J'&&b=='B')||(a=='B'&&b=='C')){
				if(a=='C'){
					solution[0][0]++;
				}
				else if(a=='J'){
					solution[0][1]++;
				}
				else{
					solution[0][2]++;
				}
				victory++;
			}
			else if((a=='J'&&b=='C')||(a=='B'&&b=='J')||(a=='C'&&b=='B')){
				if(b=='C'){
					solution[1][0]++;
				}
				else if(b=='J'){
					solution[1][1]++;
				}
				else{
					solution[1][2]++;
				}
				defeat++;
			}
		}
	}
	cout<<victory<<" "<<mid<<' '<<defeat<<endl;
	cout<<defeat<<" "<<mid<<' '<<victory<<endl;
	int max=solution[0][2];
	char result[2];
	for(i=0;i<2;i++){
		result[i]='B';
	}
	for(i=1;i>=0;i--){
		if(solution[0][i]>max){
			if(i==0){
				result[0]='C';
			}
			else{
				result[0]='J';
			}
		}
	}
	max=solution[1][2];
	for(i=1;i>=0;i--){
		if(solution[1][i]>max){
			if(i==0){
				result[1]='C';
			}
			else{
				result[1]='J';
			}
		}
	}
	cout<<result[0]<<' '<<result[1];
	return 0;
}
