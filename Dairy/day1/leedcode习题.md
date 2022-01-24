# leedcode习题

###第一题

**题目**

给定一个整数数组 `nums` 和一个整数目标值 `target`，请你在该数组中找出 **和为目标值** *`target`* 的那 **两个** 整数，并返回它们的数组下标。

**代码**

~~~java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int n = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[n] == target) {
                    return new int[]{i, n};
                }
            }
        }
        return new int[0];
    }
}
~~~

**思路**

将数组的第一个数和第一个后面所有数进行相加，第二个和第二个数后面的所有数进行相加，以此类推，并将相加后的结果和target进行比较，如果相加的结果有等于target的，就将方法返回值设为以这两个数下标为值的数组。如果没有，就返回一个空数组。

**问题**

第一次写的时候没有注意到在最后再加一个return防止前面if语句未进行的情况