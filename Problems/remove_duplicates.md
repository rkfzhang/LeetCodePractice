# Problem
Given an array of sorted numbers, remove all duplicate number instances from it in-place, such that each element appears only once. The relative order of the elements should be kept the same and you should not use any extra space so that that the solution have a space complexity of O(1).
Move all the unique elements at the beginning of the array and after moving return the length of the subarray that has no duplicate in it.
# Solution
```
def remove_duplicates(arr):
  # TODO: Write your code here
  cur = 1;
  for n in range(1, len(arr)):
    if arr[n] != arr[n-1]:
      arr[cur] = arr[n];
      cur += 1;

  return cur
```
# Explanation
- keep track of the next location to swap to
- start on second item
- if this is not the same as previous, switch with swap location and increment
- return swap index
