# [1. Two Sum (Easy)](https://leetcode.com/problems/two-sum/)

<p>Given an array of integers <code>nums</code>&nbsp;and an integer <code>target</code>, return <em>indices of the two numbers such that they add up to <code>target</code></em>.</p>

<p>You may assume that each input would have <strong><em>exactly</em> one solution</strong>, and you may not use the <em>same</em> element twice.</p>

<p>You can return the answer in any order.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [2,7,11,15], target = 9
<strong>Output:</strong> [0,1]
<strong>Explanation:</strong> Because nums[0] + nums[1] == 9, we return [0, 1].
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [3,2,4], target = 6
<strong>Output:</strong> [1,2]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> nums = [3,3], target = 6
<strong>Output:</strong> [0,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>2 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= nums[i] &lt;= 10<sup>9</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= target &lt;= 10<sup>9</sup></code></li>
	<li><strong>Only one valid answer exists.</strong></li>
</ul>

<p>&nbsp;</p>
<strong>Follow-up:&nbsp;</strong>Can you come up with an algorithm that is less than&nbsp;<code>O(n<sup>2</sup>)&nbsp;</code>time complexity?

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/)

**Similar Questions**:
* [3Sum (Medium)](https://leetcode.com/problems/3sum/)
* [4Sum (Medium)](https://leetcode.com/problems/4sum/)
* [Two Sum II - Input Array Is Sorted (Medium)](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
* [Two Sum III - Data structure design (Easy)](https://leetcode.com/problems/two-sum-iii-data-structure-design/)
* [Subarray Sum Equals K (Medium)](https://leetcode.com/problems/subarray-sum-equals-k/)
* [Two Sum IV - Input is a BST (Easy)](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/)
* [Two Sum Less Than K (Easy)](https://leetcode.com/problems/two-sum-less-than-k/)
* [Max Number of K-Sum Pairs (Medium)](https://leetcode.com/problems/max-number-of-k-sum-pairs/)
* [Count Good Meals (Medium)](https://leetcode.com/problems/count-good-meals/)
* [Count Number of Pairs With Absolute Difference K (Easy)](https://leetcode.com/problems/count-number-of-pairs-with-absolute-difference-k/)
* [Number of Pairs of Strings With Concatenation Equal to Target (Medium)](https://leetcode.com/problems/number-of-pairs-of-strings-with-concatenation-equal-to-target/)

## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/two-sum/
// Author: kapil vaishnav
// Time: O(nlog(n))
// Space: O(n)
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<vector<int>> temp;
        int n=nums.size();
        int left=0,right=n-1;
        for(int i=0;i<n;i++){
            temp.push_back({nums[i],i});
        }
        sort(temp.begin(),temp.end());
        while(left<right){
            int ans=temp[left][0]+temp[right][0];
            if(ans==target)
                return {temp[left][1],temp[right][1]};
            if(ans<target) left++;
            else right--;
        }
        return {};
    }
};
```

## Solution 2.0

```cpp
// OJ: https://leetcode.com/problems/two-sum/
// Author: kapil vaishnav
// Time: O(n)
// Space: O(n)
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> ans;
        unordered_map<int,int> mpp;
        for(int i=0;i<nums.size();i++){
            if(mpp.find(target-nums[i])!=mpp.end()){
                ans.push_back(mpp[target-nums[i]]);
                ans.push_back(i);
            return ans;
        }
            mpp[nums[i]]=i;
        }
        return ans;
    }
};
```

## Solution 2.1

```cpp
// OJ: https://leetcode.com/problems/two-sum/
// Author: kapil vaishnav
// Time: O(n)
// Space: O(n)
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int,int> mpp;
        int n=nums.size();
        for(int i=0;i<n;i++){
            int ans=target-nums[i];
            if(mpp.count(ans))
                return {mpp[ans],i};
            mpp[nums[i]]=i;
        }
        return {};
    }
};
```
