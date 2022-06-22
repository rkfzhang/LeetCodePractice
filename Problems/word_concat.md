# Problem
Given a string and a list of words, find all the starting indices of substrings in the given string that are a concatenation of all the given words exactly once without any overlapping of words. It is given that all words are of the same length.

# Solution
```
def find_word_concatenation(str1, words):
  result_indices = []
  # TODO: Write your code here
  wordLen = len(words[0]);
  totalLen = len(words) * wordLen;
  wordReqs = {};
  for w in words:
    if w not in wordReqs:
      wordReqs[w] = 0;
    wordReqs[w] += 1;
  
  for windowStart in range(len(str1) - totalLen + 1):
    
    wordSeen = {}
    windowEnd = windowStart;
    while windowEnd < windowStart + totalLen:
      word = str1[windowEnd: windowEnd + wordLen];

      if word not in wordReqs:
        break;
      
      if word not in wordSeen:
        wordSeen[word] = 0;
      wordSeen[word] += 1;

      if wordSeen[word] > wordReqs[word]:
        break;
      
      windowEnd += wordLen;
    
    if windowEnd - windowStart == totalLen:
      result_indices.append(windowStart);

  return result_indices
```
# Explanation
- implement a sliding window, with window starting at the first characer
- keep a dictionary of characters used and its frequency
- we make a dictionary of characters seen and its frequency
- for each character, we check if the subsequent characters are a concat of the words
  - increase the window size every time it is
- we add the index if the window size matches the final desired length
- otherwise we move to the next character
- return the indicies
