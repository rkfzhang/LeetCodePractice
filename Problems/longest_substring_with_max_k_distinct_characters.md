# Solution
```
def longest_substring_with_k_distinct(str1, k):
  # TODO: Write your code here
  curChars, numChars = {}, 0;
  maxlength, curLength = 0, 0;
  windowStart = 0;

  for windowEnd in range(len(str1)):
    c = str1[windowEnd];
    if c not in curChars:
      curChars[c] = 0;
      numChars += 1;
    
    curChars[c] += 1
    curLength += 1;

    while numChars > k:
      c = str1[windowStart];
      curChars[c] -= 1
      if curChars[c] == 0:
        del curChars[c];
        numChars -=1;
      curLength -= 1;
      windowStart += 1;

    maxlength = max(maxlength, curLength);

  return maxlength
```
# Explanation
- implement a sliding window, with window starting at the first characer
- keep a dictionary of characters seen and its frequency
- for each iteration we add a character in
- if there are too many distinct characters, we slide the start of the window by one
  - decrease the frequency of the first character or remove from dictionary
  - repeat until under distinct character limit
- keep track of largest string length and return
