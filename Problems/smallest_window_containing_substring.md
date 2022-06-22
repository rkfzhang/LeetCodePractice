# Problem
Given a string and a pattern, find the smallest substring in the given string which has all the character occurrences of the given pattern.
# Solution
```
def find_substring(str1, pattern):
  # TODO: Write your code here
  charsReq = {};
  match = [0, 0, 0];
  toMatch = 0;
  for i in range(len(pattern)):
    if pattern[i] not in charsReq:
      toMatch += 1
      charsReq[pattern[i]] = 0;
    charsReq[pattern[i]] += 1;

  windowStart = 0;
  for windowEnd in range(len(str1)):
    add = str1[windowEnd];
    if add in charsReq:
      charsReq[add] -= 1;
      if charsReq[add] == 0:
        toMatch -= 1;
    
    while toMatch == 0:

      if match[0] == 0 or match[0] > windowEnd - windowStart + 1:
        match[0] = windowEnd - windowStart + 1;
        match[1] = windowStart;
        match[2] = windowEnd + 1;

      remove = str1[windowStart];
      if remove in charsReq:
        if charsReq[remove] == 0:
          toMatch += 1;
        charsReq[remove] += 1;
      windowStart += 1;

  return str1[match[1]: match[2]];
```
# Explanation
- implement a sliding window, with window starting at the first characer
- we keep track of how may chars of the substring are still required (can be negative)
- if a character quota has been reached, we subtract one to match
- when match is zero, we try to shrink the window as much as we can from the front
- keep track of the smallest string that was a match and return
