# [733. Flood Fill (Easy)](https://leetcode.com/problems/flood-fill/)

<p>An image is represented by an <code>m x n</code> integer grid <code>image</code> where <code>image[i][j]</code> represents the pixel value of the image.</p>

<p>You are also given three integers <code>sr</code>, <code>sc</code>, and <code>newColor</code>. You should perform a <strong>flood fill</strong> on the image starting from the pixel <code>image[sr][sc]</code>.</p>

<p>To perform a <strong>flood fill</strong>, consider the starting pixel, plus any pixels connected <strong>4-directionally</strong> to the starting pixel of the same color as the starting pixel, plus any pixels connected <strong>4-directionally</strong> to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with <code>newColor</code>.</p>

<p>Return <em>the modified image after performing the flood fill</em>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/06/01/flood1-grid.jpg" style="width: 613px; height: 253px;">
<pre><strong>Input:</strong> image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, newColor = 2
<strong>Output:</strong> [[2,2,2],[2,2,0],[2,0,1]]
<strong>Explanation:</strong> From the center of the image with position (sr, sc) = (1, 1) (i.e., the red pixel), all pixels connected by a path of the same color as the starting pixel (i.e., the blue pixels) are colored with the new color.
Note the bottom corner is not colored 2, because it is not 4-directionally connected to the starting pixel.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> image = [[0,0,0],[0,0,0]], sr = 0, sc = 0, newColor = 2
<strong>Output:</strong> [[2,2,2],[2,2,2]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == image.length</code></li>
	<li><code>n == image[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 50</code></li>
	<li><code>0 &lt;= image[i][j], newColor &lt; 2<sup>16</sup></code></li>
	<li><code>0 &lt;= sr &lt;&nbsp;m</code></li>
	<li><code>0 &lt;= sc &lt;&nbsp;n</code></li>
</ul>


**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Depth-First Search](https://leetcode.com/tag/depth-first-search/), [Breadth-First Search](https://leetcode.com/tag/breadth-first-search/), [Matrix](https://leetcode.com/tag/matrix/)

**Similar Questions**:
* [Island Perimeter (Easy)](https://leetcode.com/problems/island-perimeter/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/flood-fill/
// Author: kapil vaishnav
// Time: O(m*n) m->number of rows and n->number of columns
// Space: O(1)
class Solution {
    void dfs(vector<vector<int>> &image,int sr,int sc,int newColor,int originalcolor){
        int row=image.size();
        int col=image[0].size();
        if(sr<0 or sr>=row or sc<0 or sc>=col or image[sr][sc]!=originalcolor)
            return;
        image[sr][sc]=newColor;
        dfs(image,sr-1,sc,newColor,originalcolor);
        dfs(image,sr+1,sc,newColor,originalcolor);
        dfs(image,sr,sc-1,newColor,originalcolor);
        dfs(image,sr,sc+1,newColor,originalcolor);
    }
public:
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc,int newColor) {
        int originalcolor=image[sr][sc];
        if(newColor==originalcolor)
            return image;
        int rows=image.size();
        int cols=image[0].size();
        dfs(image,sr,sc,newColor,originalcolor);
        return image;
    }
};
```
