# [695. Max Area of Island (Medium)](https://leetcode.com/problems/max-area-of-island/)

<p>You are given an <code>m x n</code> binary matrix <code>grid</code>. An island is a group of <code>1</code>'s (representing land) connected <strong>4-directionally</strong> (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.</p>

<p>The <strong>area</strong> of an island is the number of cells with a value <code>1</code> in the island.</p>

<p>Return <em>the maximum <strong>area</strong> of an island in </em><code>grid</code>. If there is no island, return <code>0</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/05/01/maxarea1-grid.jpg" style="width: 500px; height: 310px;">
<pre><strong>Input:</strong> grid = [[0,0,1,0,0,0,0,1,0,0,0,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,1,1,0,1,0,0,0,0,0,0,0,0],[0,1,0,0,1,1,0,0,1,0,1,0,0],[0,1,0,0,1,1,0,0,1,1,1,0,0],[0,0,0,0,0,0,0,0,0,0,1,0,0],[0,0,0,0,0,0,0,1,1,1,0,0,0],[0,0,0,0,0,0,0,1,1,0,0,0,0]]
<strong>Output:</strong> 6
<strong>Explanation:</strong> The answer is not 11, because the island must be connected 4-directionally.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> grid = [[0,0,0,0,0,0,0,0]]
<strong>Output:</strong> 0
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 50</code></li>
	<li><code>grid[i][j]</code> is either <code>0</code> or <code>1</code>.</li>
</ul>


**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Union Find](https://leetcode.com/tag/union-find/), [Matrix](https://leetcode.com/tag/matrix/)

**Similar Questions**:
* [Number of Islands (Medium)](https://leetcode.com/problems/number-of-islands/)
* [Island Perimeter (Easy)](https://leetcode.com/problems/island-perimeter/)
* [Largest Submatrix With Rearrangements (Medium)](https://leetcode.com/problems/largest-submatrix-with-rearrangements/)
* [Detonate the Maximum Bombs (Medium)](https://leetcode.com/problems/detonate-the-maximum-bombs/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/max-area-of-island/
// Author: kapil vaishnav
// Time: O(m*n)
// Space: O(1)
class Solution {
public:
    int maxAreaOfIsland(vector<vector<int>>& grid) {
        int mx=0;
        int m=grid.size(); // number of rows...
        int n=grid[0].size(); // number of columns...
        // iterate through the loop,
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                int cnt=1; // count 
                // check if value is 1 or not?
                if(grid[i][j]==1){
                    count_island(grid,i,j,cnt);
                    mx=max(mx,cnt);
                }
            }
        }
        return mx;
    }
    int count_island(vector<vector<int>>& grid,int i,int j,int& cnt){
        int m=grid.size(); // number of rows...
        int n=grid[0].size(); // number of columns...
        // base boundary case...
        if(i<0 or i>=m or j<0 or j>=n){
            return 0;
        }
        if(grid[i][j]==0) return 0; // for useless neighbour...
        grid[i][j]=0;
        // check neighbour is helpful or not-> by recursive call... in four direction...
        if(count_island(grid,i-1,j,cnt)) cnt++;
        if(count_island(grid,i+1,j,cnt)) cnt++;
        if(count_island(grid,i,j-1,cnt)) cnt++;
        if(count_island(grid,i,j+1,cnt)) cnt++;
        return 1;
    }
};
```
