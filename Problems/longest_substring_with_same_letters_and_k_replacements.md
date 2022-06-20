# Solution
def length_of_longest_substring(str1, k):
  # TODO: Write your code here
  chars = {};
  maxLen, maxFreq = 0, 0;
  windowStart = 0;
  
  for windowEnd in range(len(str1)):
    add = str1[windowEnd];
    if add not in chars:
      chars[add] = 0;
    chars[add] += 1;

    maxFreq = max(maxFreq, chars[add]);

    windowSize = windowEnd - windowStart + 1;
    if windowSize - maxFreq > k:
      remove = str1[windowStart];
      chars[remove] -=1;
      windowStart += 1;
    else:
      maxLen += 1;

  return maxLen
```
# Explanation
- we implement a sliding window starting at 0,0, increasing windowEnd each time
- we keep track of the frequencies of the letters in the window
- we take the maximum between the previous max frequency and the frequency of the letter just added
  - Note we don't care if its inaccurate since we don't decrease window size, the invalid ones will just be filtered out
- if there are more replacements than k (using max frequency), we increase windowStart by 1
  - Note we never decrease window size, only move it. Thus we don't need to worry about invalid entries
- otherwise we update the max length
- return max length
