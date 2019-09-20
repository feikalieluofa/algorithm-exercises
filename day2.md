# 初级算法 数组4.存在重复

给定一个整数数组，判断是否存在重复元素。
如果任何值在数组中出现至少两次，函数返回 true。如果数组中每个元素都不相同，则返回 false。

**示例1**
```chinese
输入: [1,2,3,1]
输出: true
```

**示例2**
```chinese
输入: [1,2,3,4]
输出: false
```
**JS实现**
```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
    // 用set进行数组去重，如果去重后的数组长度变短，说明数组中有重复元素，返回true
    let newNums = Array.from(new Set(nums))
    if(newNums.length == nums.length){
        return false;
    }else{
        return true;
    }
};
```

# 初级算法 数组5.只出现一次的数字

给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。
说明：
你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

**示例1**
```Chinese
输入: [2,2,1]
输出: 1
```
**示例2**
```Chinese
输入: [4,1,2,1,2]
输出: 4
```
**JS实现**
```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    // 两个相等的数异或为0；一个不为0的数与0异或为这个数本身。
  for (var i = 1; i < nums.length; i++) {
    nums[0] = nums[0] ^ nums[i];    // 把所有的元素都异或到nums[0]上。
  }
  return nums[0];
    
};
```

# 初级算法 数组6.两个数组的交集 II
给定两个数组，编写一个函数来计算它们的交集。

**示例1**
```chinese
输入: nums1 = [1,2,2,1], nums2 = [2,2]
输出: [2,2]
```
**示例2**
```chinese
输入: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
输出: [4,9]
```

**说明**
- 输出结果中每个元素出现的次数，应与元素在两个数组中出现的次数一致。
- 我们可以不考虑输出结果的顺序。

**进阶**
- 如果给定的数组已经排好序呢？你将如何优化你的算法？
- 如果 nums1 的大小比 nums2 小很多，哪种方法更优？
- 如果 nums2 的元素存储在磁盘上，磁盘内存是有限的，并且你不能一次加载所有的元素到内存中，你该怎么办？

**JS实现**
```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
    // 暴力法：循环嵌套判断值相等，相等的就加入新数组，然后两个数组中去除元素继续判断
    let resArr = []
    for(let i = 0;i < nums1.length;i++){
        for(let j = 0;j<nums2.length;j++){
            if(nums1[i] == nums2[j]){
                resArr.push(nums1[i])
                nums1.splice(i,1)
                nums2.splice(j,1)
                i--
                j--
                
                
            }
        }
    }
    return resArr
};
```