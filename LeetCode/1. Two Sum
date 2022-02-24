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
