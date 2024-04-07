## Knapsack
Approach --> pick x not-pick

if wt[i] < knapsack_bag  --> two options --> we can pick and not pick
if et[i] > knapsack_bag --> only one option --> not pick 

we can further memoize to avoid the repeated function calls.

**Time complexity:**
Naive Recursion:

| x | x | x | x | x |
  2   2   2   2   2   --> O(2^n)

**DP:**
O( (n+1)(W+1) )

## subset sum problem  --> Many patterns --> subset sum 1 and subset sum 2 on cns

**Approach** --> pick x not-pick
if arr[i] > sum --> we will not pick 
if arr[i] < sum --> we can pick or not pick arr[i] --> and  
sum --> given 


## equal sum partition
**problem statement** --> whether we can divide the array into two equal halves
so it is subset sum problem with sum = arr.size()/2


## Count of subsets with a given sum 
**Approach** --> same as subset sum

```cpp
class Solution {
public:
    void helper(int index, int sum, vector<int>& nums, int target, int &cnt){
        if (index == nums.size() ){
            if(sum == target){
                cnt++;
            }
            return ;
        }
//         pick
        helper(index+1, sum + nums[index], nums, target, cnt);
//         not pick
        helper(index+1, sum, nums, target, cnt);
        
    }
    int numSubsets(vector<int>& nums, int target) {
     int cnt =0 ;
        helper(0, 0, nums, target, cnt);
        return cnt;
    }
};

```
Also 

```cpp
void helper(int index, int sum, vector<int>& nums, int target, int &cnt){
        if (index_condition){
          return 0;
        }
        if (target == sum ){
            return 1
        }
        return helper(index+1, sum + nums[index], nums, target, cnt) + helper(index+1, sum, nums, target, cnt);
    }
```



## Minimum subset sum difference

let sum of one subset is s1  and sum of other subset will be s2 = sum of array -s1
then **diff** = s1-(arr_sum - s1) = **2s1 - arr_sum** 

Naive Approach --> calcuate all subsets and get the min(2s1- arr_sum)

## Count the subsets with given difference
Problem statement --> d1-d2 = given_sum --> d1 and d2 are subsets
Approach --> 
d1 , d2 = arr_sum - d1
now, i have to get the subset with sum = d1 - ( arr_sum -d1 ) = 2d1-arr_sum = given_sum  => d1 = (given_sum + arr_sum )/2

now apply subset sum problem algorithm with sum = d1

## Target Sum 
return the count 
Input: nums = [1,1,1,1,1], target = 3
Output: 5
Explanation: There are 5 ways to assign symbols to make the sum of nums be target 3.
-1 + 1 + 1 + 1 + 1 = 3
+1 - 1 + 1 + 1 + 1 = 3
+1 + 1 - 1 + 1 + 1 = 3
+1 + 1 + 1 - 1 + 1 = 3
+1 + 1 + 1 + 1 - 1 = 3


Approach -->   at the end we are getting subsets and we have to calculate the difference between them. 
and then we will apply the Count the subsets with given difference
