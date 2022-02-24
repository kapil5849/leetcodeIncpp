# [15. 3Sum (Medium)](https://leetcode.com/problems/3sum/)

<p>Given an integer array nums, return all the triplets <code>[nums[i], nums[j], nums[k]]</code> such that <code>i != j</code>, <code>i != k</code>, and <code>j != k</code>, and <code>nums[i] + nums[j] + nums[k] == 0</code>.</p>

<p>Notice that the solution set must not contain duplicate triplets.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [-1,0,1,2,-1,-4]
<strong>Output:</strong> [[-1,-1,2],[-1,0,1]]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = []
<strong>Output:</strong> []
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [0]
<strong>Output:</strong> []
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= nums.length &lt;= 3000</code></li>
	<li><code>-10<sup>5</sup> &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>


**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Two Pointers](https://leetcode.com/tag/two-pointers/), [Sorting](https://leetcode.com/tag/sorting/)

**Similar Questions**:
* [Two Sum (Easy)](https://leetcode.com/problems/two-sum/)
* [3Sum Closest (Medium)](https://leetcode.com/problems/3sum-closest/)
* [4Sum (Medium)](https://leetcode.com/problems/4sum/)
* [3Sum Smaller (Medium)](https://leetcode.com/problems/3sum-smaller/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/3sum/
// Author: kapil vaishnav
// Time: O(n^2) -> sort->O(n*lon(n)) and O(n^2)... so, O(n^2)...
// Space: O(1)
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        vector<vector<int>> ans;
        int n=nums.size();
        for(int i=0;i<n-2;i++){
            if(i and nums[i]==nums[i-1])
                continue;
            int left=i+1,right=n-1;
            while(left<right){
                int sum=nums[i]+nums[left]+nums[right];
                if(sum==0) ans.push_back({nums[i],nums[left],nums[right]});
                if(sum>=0){
                    right--;
                    while(left<right and nums[right]==nums[right+1])
                        right--;
                }
                if(sum<=0){
                    left++;
                    while(left<right and nums[left]==nums[left-1])
                        left++;
                }
            }
        }
        return ans;
    }
};
```
