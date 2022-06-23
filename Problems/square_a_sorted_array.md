# Solution
```
def make_squares(arr):
  squares = [0 for i in range(len(arr))];
  # TODO: Write your code here
  left, right = 0, len(arr) - 1
  i = len(arr) - 1;
  while left <= right:
    if arr[left] ** 2 >=  arr[right] ** 2:
      squares[i] = arr[left] ** 2;
      left += 1;
    else:
      squares[i] = arr[right] ** 2;
      right -= 1;
    i -= 1;

  return squares;
```
# Explanation
- have pointers at the start and end of input array
- compare which value is larger squared
- place value at end of return array
- shift pointers accordingly
