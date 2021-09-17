# MAX-COST-TO-FILL-GIVEN-WEIGHT-IN-A-BAG

class Solution{
		

	public:
	int minimumCost(int cost[], int N, int W) 
	{ 
         int t[N+1][W+1];
	    for(int i=0;i<=N;i++){
	        for(int j=0;j<=W;j++){
	            if(j == 0){
	                t[i][j] = 0;
	            }
	            else if(i == 0){
	                t[i][j] = INT_MAX-1;
	            }
	            else if(j-i >= 0 and cost[i-1] != -1 and t[i][j-i] != INT_MAX-1){
	                t[i][j] = min(cost[i-1] + t[i][j-i] , t[i-1][j]);
	            }
	            else{
	                t[i][j] = t[i-1][j];
	            }
	        }
	    }
	    return t[N][W] == INT_MAX-1 ? -1 : t[N][W];
	} 
};
