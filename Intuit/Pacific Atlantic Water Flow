class Solution {
public:

	bool isValid(int x, int y, int n, int m){
        return !(x < 0 || y < 0 || x >= n || y >= m);
    }
	
    void bfs(int n, int m, queue<pair<int,int>>& q, vector<vector<bool>> &visited, vector<vector<int>> heights){
        int dx[] = {-1,0,0,1};
        int dy[] = {0,-1,1,0};
        while(!q.empty()){
            auto ele = q.front();
            q.pop();
            for(int iter = 0 ; iter < 4 ; iter++){
                int nx = ele.first+dx[iter];
                int ny = ele.second+dy[iter];
                if(isValid(nx,ny,n,m) && heights[ele.first][ele.second] <= heights[nx][ny] && !visited[nx][ny]){
                    q.push({nx,ny});
                    visited[nx][ny] = true;
                }
            }
        }
    }
	
    vector<vector<int>> pacificAtlantic(vector<vector<int>>& heights) {
        int n = heights.size();
        int m = heights[0].size();
		queue<pair<int,int>> atlantic_queue;
        queue<pair<int,int>> pacific_queue;
        vector<vector<bool>> atlantic(n,vector<bool>(m,false));
        vector<vector<bool>> pacific(n,vector<bool>(m,false));
        vector<vector<int>> res;
        for(int i = 0 ; i < n; i++){
            for(int j = 0 ; j < m; j++){
                if(i == 0 || j == 0){
                    pacific_queue.push({i,j});
                    pacific[i][j] = true;
                }
                if(i == n-1 || j == m-1){
                    atlantic_queue.push({i,j});
                    atlantic[i][j] = true;
                }
            }
        }
        bfs(n, m, atlantic_queue, atlantic, heights);
        bfs(n, m, pacific_queue, pacific, heights);
        for(int i = 0; i < n; i++){
            for(int j = 0; j < m; j++){
                if(atlantic[i][j] && pacific[i][j]){
                    res.push_back({i,j});
                }
            }
        }
        return res;
    }
};
