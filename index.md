# 飞达技术博客

## 0 目录

- [飞达技术博客](#------)
  * [1 leetcode题解（C++代码）](#1)
    + [1.1 两数相加](#1_1) 
    + [1.485 两数相加](#1_485) 
    + [1.495 提莫攻击](#1_495) 
    + [1.414 第三大的数](#1_414) 
  * [2 强化学习笔记](#2)
    + [2.1 从1500年代起用的标准Lorem Ipsum段落](#2_1)
    + [2.2 "de Finibus Bonorum et Malorum"章节1.10.32，西塞罗于公元前45年著](#2_2)
    + [2.3 1914年H. Rackham译文](#2_3)


## 1 leetcode题解（C++代码）<span id="1"></span>

### 1_1 两数相加 EASY<span id="1_1"></span>
- finished at 211031_2212

~~~c++
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
~~~

### 1_485 最大连续 1 的个数 EASY  <span id="1_485"></span>
>给定一个二进制数组， 计算其中最大连续 1 的个数。  
>示例：  
>输入：[1,1,0,1,1,1]    
>输出：3  
>解释：开头的两位和最后的三位都是连续 1 ，所以最大连续 1 的个数是 3.  

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



## 2 强化学习笔记 
### 2.1 从1500年代起用的标准Lorem Ipsum段落  
"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."

### 2.2 "de Finibus Bonorum et Malorum"章节1.10.32，西塞罗于公元前45年著 
"Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas nulla pariatur?"

### 2.3 1914年H. Rackham译文 
"But I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system, and expound the actual teachings of the great explorer of the truth, the master-builder of human happiness. No one rejects, dislikes, or avoids pleasure itself, because it is pleasure, but because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful. Nor again is there anyone who loves or pursues or desires to obtain pain of itself, because it is pain, but because occasionally circumstances occur in which toil and pain can procure him some great pleasure. To take a trivial example, which of us ever undertakes laborious physical exercise, except to obtain some advantage from it? But who has any right to find fault with a man who chooses to enjoy a pleasure that has no annoying consequences, or one who avoids a pain that produces no resultant pleasure?"
ditate non provident, similique sunt in culpa qui officia deserunt mollitia animi, id est laborum et dolorum fuga. Et harum quidem rerum facilis est et expedita distinctio. Nam libero tempore, cum soluta nobis est eligendi optio cumque nihil impedit quo minus id quod maxime placeat facere possimus, omnis voluptas assumenda est, omnis dolor repellendus. Temporibus autem quibusdam et aut officiis debitis aut rerum necessitatibus saepe eveniet ut et voluptates repudiandae sint et molestiae non recusandae. Itaque earum rerum hic tenetur a sapiente delectus, ut aut reiciendis voluptatibus maiores alias consequatur aut perferendis doloribus asperiores repellat."
gs of the great explorer of the truth, the master-builder of human happiness. No one rejects, dislikes, or avoids pleasure itself, because it is pleasure, but because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful. Nor again is there anyone who loves or pursues or desires to obtain pain of itself, because it is pain, but because occasionally circumstances occur in which toil and pain can procure him some great pleasure. To take a trivial example, which of us ever undertakes laborious physical exercise, except to obtain some advantage from it? But who has any right to find fault with a man who chooses to enjoy a pleasure that has no annoying consequences, or one who avoids a pain that produces no resultant pleasure?"
