# Solution
```
def find_string_anagrams(str1, pattern):
  result_indexes = []
  charsAvail = {};
  toMatch = 0;
  for i in range(len(pattern)):
    if pattern[i] not in charsAvail:
      charsAvail[pattern[i]] = 0;
      toMatch += 1;
    charsAvail[pattern[i]] += 1;

  windowStart = 0;
  print(toMatch, charsAvail)
  for windowEnd in range(len(str1)):
    add = str1[windowEnd];
    if add in charsAvail:
      charsAvail[add] -= 1;
      if charsAvail[add] == 0:
        toMatch -= 1;

    if toMatch == 0:
      result_indexes.append(windowStart);
    
    if windowEnd >= len(pattern) -1:
      remove = str1[windowStart];
      if charsAvail[remove] == 0:
        toMatch += 1;
      charsAvail[remove] += 1;
      windowStart += 1;

      if windowStart + len(pattern) > len(str1):
        break;

  return result_indexes


```
# Explanation
- implement a sliding window, with window starting at the first characer
- keep a dictionary of characters and its frequency
- for each iteration we add a character in
- if we have seen exactly the amount of the character requried, we comfirm the match
  - Note we dont care about negatives because that means another character has not met its frequency so we will never match
- if we have matched everything so far, we add the start of the window to the results
- if the window is already the length of the pattern, we remove the first character in the window and shift forward
  - if that character originally had an exact match, we unmatch
- return results
