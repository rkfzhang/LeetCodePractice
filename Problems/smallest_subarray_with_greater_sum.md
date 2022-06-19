# Solution
```
def smallest_subarray_sum(s, arr):
  # TODO: Write your code here

  minSize = len(arr) + 1;
  curSum = 0;
  windowStart = 0;

  for windowEnd in range(len(arr)):
    curSum += arr[windowEnd];
    
    while s <= curSum:
      windowSize = windowEnd - windowStart + 1;
      minSize = min(minSize, windowSize);
      curSum -= arr[windowStart];
      windowStart += 1;
  
  if minSize > len(arr):
    return 0;
  return minSize
};
```
# Explanation
- Implement sliding window starting at just the first element
- for each iteration, we increase the window by 1 and add the element to a sum
- if the sum is greater then the inputed value, we compare and update the minimum size
  - we remove the first element, move window start by 1 and repeat previous step
- return the minimum size at the end, or 0 if none were found
