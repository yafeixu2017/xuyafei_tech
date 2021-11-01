# 飞达技术博客

## 0 目录

- [飞达技术博客](#------)
  * [1 leetcode题解（C++代码）](#1)
    + [1.1 两数相加](#1_1) 
    + [1.485 两数相加](#1_485) 
    + [1.495 提莫攻击](#1_495) 
    + [1.414 第三大的数](#1_414) 
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


------------------------------------------------------------------------------------------------VVV 485
### 1.485 最大连续 1 的个数 EASY <span id="1_485"></span>
- 211101_1556 finished
> 给定一个二进制数组， 计算其中最大连续 1 的个数  
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

------------------------------------------------------------------------------------------------VVV 495
### 1.495 提莫攻击 EASY <span id="1_495"></span>
- 211101_1556 finished
>在《英雄联盟》的世界中，有一个叫 “提莫” 的英雄，他的攻击可以让敌方英雄艾希（编者注：寒冰射手）进入中毒状态。现在，给出提莫对艾希的攻击时间序列和提莫攻击的中毒持续时间，你需要输出艾希的中毒状态总时长。  

>你可以认为提莫在给定的时间点进行攻击，并立即使艾希处于中毒状态。  

>示例1:  
>输入: [1,4], 2  
>输出: 4  
>原因: 第 1 秒初，提莫开始对艾希进行攻击并使其立即中毒。中毒状态会维持 2 秒钟，直到第 2 秒末结束。  
>第 4 秒初，提莫再次攻击艾希，使得艾希获得另外 2 秒中毒时间。  
>所以最终输出 4 秒。  
   
>示例2:    
>输入: [1,2], 2  
>输出: 3  
>原因: 第 1 秒初，提莫开始对艾希进行攻击并使其立即中毒。中毒状态会维持 2 秒钟，直到第 2 秒末结束。  
>但是第 2 秒初，提莫再次攻击了已经处于中毒状态的艾希。  
>由于中毒状态不可叠加，提莫在第 2 秒初的这次攻击会在第 3 秒末结束。  
>所以最终输出 3   

~~~c++
class Solution {
public:
    int findPoisonedDuration(vector<int>& timeSeries, int duration) {
        int totolTime = 0;
        for(int i = 1; i < timeSeries.size(); i++){
            if(timeSeries[i] - timeSeries[i-1] >= duration){
                totolTime = totolTime + duration;
            }else{
                totolTime = totolTime + timeSeries[i] - timeSeries[i-1] ;
            }
        }
       totolTime = totolTime + duration;

        return totolTime;
    }
};
~~~

给你一个非空数组，返回此数组中 第三大的数 。如果不存在，则返回数组中最大的数。

------------------------------------------------------------------------------------------------VVV 414
### 1.414 三大的数 EASY <span id="1_414"></span>
- finished at 211101_1737
~~~
示例 1：

输入：[3, 2, 1]
输出：1
解释：第三大的数是 1 。
示例 2：

输入：[1, 2]
输出：2
解释：第三大的数不存在, 所以返回最大的数 2 。
示例 3：

输入：[2, 2, 3, 1]
输出：1
解释：注意，要求返回第三大的数，是指在所有不同数字中排第三大的数。
此例中存在两个值为 2 的数，它们都排第二。在所有不同数字中排第三大的数为 1 。
~~~
 
~~~c++
class Solution {
public:
    int thirdMax(vector<int>& nums) {
        set<int> temp_set={};
        for(int i : nums){
            temp_set.insert(i);
            if(temp_set.size() > 3){
                temp_set.erase(temp_set.begin());
            }
        }
        return temp_set.size() == 3 ? *temp_set.begin() : *temp_set.rbegin();
    }   
};
~~~

