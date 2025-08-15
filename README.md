# Leetcode-189.-Rotate-Array
# Description
Given an integer array nums, rotate the array to the right by k steps, where k is non-negative.
# Solution
In the given problem we have been  given an array nums along with an integer number k , our aim is to rotate the array k times .

This can be done using 2 approaches:

# 1 approach (Using extra memory (O(n)):

Create an empty array res which will store the final res array , start inserting elements into res from the k position in nums array.

For each index i in nums, place the element at index (i + k) % len(nums) in res.

Copy elements from res back to nums.

Example:

nums = [1, 2, 3, 4, 5, 6, 7], k = 3  

len(nums) = 7  

res[(0+3)%7] = nums[0] → res[3] = 1  

... and so on → res = [5, 6, 7, 1, 2, 3, 4]  

# 2nd approach ( Using In-place: O(n)):

In this approach follow the steps :

Reverse the whole array.

Reverse the first k elements.

Reverse the remaining (len(nums)-1) - k elements.

Example:

nums=[1,2,3,4,5]

Reverse the array:[5,4,3,2,1]

Reverse the first k elements(0,k-1) : [4,5,3,2,1]

Reverse the remaining (len(nums)-1) - k elements: [4,5,1,2,3]

# Algorithm ( for In-place solution)
1. k = k % len(nums) to avoid unnecessary full rotations.
2. Create 2 pointers l and r which is initiliased as 0 and len(nums)-1 respectively.
3. Now use a while loop until l is less than r pointer .
4. Swap values of l and r pointers .
5. Increment l pointer with 1 and decrement r pointer by 1 .
6.  After this , in order to reverse the 1st k-elements of the array , we have to initiliase the l and r pointers as 0 and k-1 respectively.
7.  Now use a while loop until l is less than r pointer .
8. Swap values of l and r pointers .
9. Increment l pointer with 1 and decrement r pointer by 1 .
10. To reverse the remaining n-k elements . Initialise the l and r pointers as k and len(nums)-1 respectively.
11. Now use a while loop until l is less than r pointer .
12.  Swap values of l and r pointers .
13. Increment l pointer with 1 and decrement r pointer by 1 .
# Code
class Solution:

    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        k=k%len(nums)
        l,r=0,len(nums)-1
        while l<r:
            nums[l],nums[r]=nums[r],nums[l]
            l+=1
            r-=1
        
        l,r=0,k-1
        while l<r:
            nums[l],nums[r]=nums[r],nums[l]
            l+=1
            r-=1
        
        l,r=k,len(nums)-1
        while l<r:
            nums[l],nums[r]=nums[r],nums[l]
            l+=1
            r-=1
# Complexity
Time Complexity:

Reversing the array: O(n)

Reversing the first k elements: O(k)

Reversing the remaining n-k elements: O(n-k)

Overall: O(n)

Space Complexity:

In-place reversal requires O(1) extra space.
