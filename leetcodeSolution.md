# 飞达技术博客

## 0 目录

- [飞达技术博客](#------)
  * [1 leetcode题解（C++代码）](#1)
    + [1.1 两数相加](#1_1) 
    + [1.485 两数相加](#1_485) 


## 1 leetcode题解（C++代码）<span id="1"></span>

### 1.1 两数相加 EASY<span id="1_1"></span>
- finished at 211031_2212

~~~c++ 
  class Solution {
  public:
      int findMaxConsecutiveOnes(vector<int>& nums) {
          int resCnt = 0; 
          int maxCnt = 0;

          for(int i = 0; i < nums.size(); i++){
              if(nums[i]==1){
                  resCnt = resCnt + 1;

              }else{
                  maxCnt = max(maxCnt, resCnt);
                  resCnt = 0;

              }
          }
          maxCnt = max(maxCnt, resCnt);
          return maxCnt;

      }};

~~~

### 1.485 最大连续 1 的个数 EASY <span id="1_485"></span>
> 给定一个二进制数组， 计算其中最大连续 1 的个数。
> 示例：
> 输入：[1,1,0,1,1,1]
> 输出：3
> 解释：开头的两位和最后的三位都是连续 1 ，所以最大连续 1 的个数是 3.

~~~c++
  class Solution {
  public:
      int findMaxConsecutiveOnes(vector<int>& nums) {
          int resCnt = 0; 
          int maxCnt = 0;

          for(int i = 0; i < nums.size(); i++){
              if(nums[i]==1){
                  resCnt = resCnt + 1;

              }else{
                  maxCnt = max(maxCnt, resCnt);
                  resCnt = 0;

              }
          }
          maxCnt = max(maxCnt, resCnt);
          return maxCnt;

      }
  };
  
~~~
