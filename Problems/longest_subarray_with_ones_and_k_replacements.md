# Solution
```
def length_of_longest_substring(arr, k):
  # TODO: Write your code here

  freq = [0, 0];
  windowStart = 0;
  maxSize = 0;

  for windowEnd in range(len(arr)):
    add = arr[windowEnd];
    freq[add] += 1;

    if freq[0] > k:
      remove = arr[windowStart];
      freq[remove] -=1;
      windowStart += 1;
    else:
      maxSize = max(maxSize, windowEnd - windowStart + 1);

  return maxSize
```
# Explanation
- implement a sliding window, with window starting at the first element
- keep track of the frequencies of 1 and 0's
- add a digit each time
- if there are more 0's then 1's in the window, then we move windowStart to the right by 1
  - window size is never shrinking, only moving since we want largest
- return max size
