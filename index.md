

# 飞达技术博客

## 1 leetcode题解（C++代码）
- 题目顺序主要参考 https://leetcode-cn.com/circle/article/48kq9d/

### 1.1 两数相加 
- finished at 211031_2212
``` c++

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> temp;
        for(int i = 0; i<nums.size()-1; i++){
            for(int j=i+1; j<nums.size(); j++){
                if(nums[i]+nums[j]==target){
                    temp.push_back(i);
                    temp.push_back(j);
                    return temp;
                }
            }
        }
        return temp;
    }
};
 
```
## 2 强化学习笔记
