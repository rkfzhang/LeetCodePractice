# Solution
```
def non_repeat_substring(str):
  # TODO: Write your code here
  chars = {};
  maxLen = 0;
  windowStart = 0;

  for windowEnd in range(len(str)):
    add = str[windowEnd];
    if add in chars:
      windowStart = chars[add] + 1;
    chars[add] = windowEnd;

    curLen = windowEnd - windowStart + 1;
    maxLen = max(maxLen, curLen);
  return maxLen
```
# Explanation
- We implement a sliding window and a dictionary to store indicies of the chars' last location
- everytime we see a repeat, we move the window to the last location
