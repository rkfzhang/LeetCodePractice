# Solution
```
def max_sub_array_of_size_k(k, arr):
  # TODO: Write your code here
  maxSum, curSum = 0, 0;
  winStart = 0;
  for winEnd in range(len(arr)):
    curSum += arr[winEnd]
    if (winEnd > k-1):
      curSum -= arr[winStart]
      maxSum = max(maxSum, curSum)
      winStart +=1
    
  return maxSum
```
# Explanation
- We perform this in O(n) time
- Iterate through the list updating the window start and end of size k
- add and subtract the ends
- return the largest window size
