# Solution
```
def find_permutation(str1, pattern):
  # TODO: Write your code here
  if len(str1) < len(pattern):
    return False;

  charsAvail = {}
  toMatch = 0;
  for i in range(len(pattern)):
    add = pattern[i];
    if add not in charsAvail:
      charsAvail[add] = 0;
      toMatch += 1;
    charsAvail[add] += 1;
  print (charsAvail, toMatch)
  windowStart = 0;
  for windowEnd in range(len(str1)):
    add = str1[windowEnd];
    if add in charsAvail:
      charsAvail[add] -= 1;
      if charsAvail[add] == 0:
        toMatch -= 1;

      if toMatch == 0:
        return True;
    
    if windowEnd >= len(pattern) - 1:
      remove = str1[windowStart];
      if remove in charsAvail:
        if charsAvail[remove] == 0:
          toMatch += 1;
        charsAvail[remove] += 1;
      windowStart += 1

  return False

```
# Explanation
- grab required frequencies for characters
- implement a sliding window, with window starting at the first characer
- keep a dictionary of characters seen and its frequency remaining
- for each iteration we add a character in
- we update frequencies accordingly
  - we also update toMatch accordingly
  - we can ignore negatives since it will match regardless
- return true if toMatch is 0
  - decrease the frequency of the first character or remove from dictionary
  - repeat until under distinct character limit
- keep track of largest string length and return
