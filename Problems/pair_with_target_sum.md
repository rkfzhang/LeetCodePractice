# Solution
```
def pair_with_targetsum(arr, target_sum):
  # TODO: Write your code here
  pair = [0, len(arr) - 1];

  while pair[0] < pair[1]:
    if arr[pair[0]] + arr[pair[1]] < target_sum:
      pair[0] += 1;
    elif arr[pair[0]] + arr[pair[1]] > target_sum:
      pair[1] -= 1;
    else:
      return pair;
  return [-1, -1]

```
# Explanation
- implement two pointers starting from both ends of array
- if the sum is smaller, move left pointer right
- if sum is larger, move right pointer left
- return pair if matches
