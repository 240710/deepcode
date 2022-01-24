#leetcode

#### 88. 合并两个有序数组

**题解：**

~~~Java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n){
        for (int i = 0; i<m; ++i) {
            nums2[n + i] = nums1[i];
        }
        Arrays.sort(nums1);
    }
}
~~~

**思路**：

将数组2中的所有元素都加到数组1中，再利用jdk中的数组排序方法将新组成的数组1排序，偷了点懒。