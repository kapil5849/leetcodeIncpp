# [200. Number of Islands (Medium)](https://leetcode.com/problems/number-of-islands/)

<p>Given an <code>m x n</code> 2D binary grid <code>grid</code> which represents a map of <code>'1'</code>s (land) and <code>'0'</code>s (water), return <em>the number of islands</em>.</p>

<p>An <strong>island</strong> is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == grid.length</code></li>
	<li><code>n == grid[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 300</code></li>
	<li><code>grid[i][j]</code> is <code>'0'</code> or <code>'1'</code>.</li>
</ul>


**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Union Find](https://leetcode.com/tag/union-find/), [Matrix](https://leetcode.com/tag/matrix/)

**Similar Questions**:
* [Surrounded Regions (Medium)](https://leetcode.com/problems/surrounded-regions/)
* [Walls and Gates (Medium)](https://leetcode.com/problems/walls-and-gates/)
* [Number of Islands II (Hard)](https://leetcode.com/problems/number-of-islands-ii/)
* [Number of Connected Components in an Undirected Graph (Medium)](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/)
* [Number of Distinct Islands (Medium)](https://leetcode.com/problems/number-of-distinct-islands/)
* [Max Area of Island (Medium)](https://leetcode.com/problems/max-area-of-island/)
* [Count Sub Islands (Medium)](https://leetcode.com/problems/count-sub-islands/)
* [Find All Groups of Farmland (Medium)](https://leetcode.com/problems/find-all-groups-of-farmland/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/number-of-islands/
// Author: kapil vaishnav
// Time: O()
// Space: O()
class Solution {
    // create function of dfs
    void dfscall(vector<vector<char>> &grid,int i,int j,int rows,int cols){
        // boundary case of gri :)
        if(i<0 or j<0 or i>=rows or j>=cols or grid[i][j]!='1')
            return;
        // mark for visited island...
        grid[i][j]='2';
        // call fuction...
        dfscall(grid,i+1,j,rows,cols);
        dfscall(grid,i-1,j,rows,cols);
        dfscall(grid,i,j+1,rows,cols);
        dfscall(grid,i,j-1,rows,cols);
    }
public:
    int numIslands(vector<vector<char>>& grid) {
        int rows=grid.size();
        //base case
        if(rows==0)
            return 0;
        int cols=grid[0].size();
        //number of island...
        int ans=0;
        for(int i=0;i<rows;i++){
            for(int j=0;j<cols;j++){
                if(grid[i][j]=='1'){
                    dfscall(grid,i,j,rows,cols);
                    ans+=1;
                }
            }
        }
        return ans;
    }
};
```
