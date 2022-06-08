#Solution
```
def twoSum(self, nums: List[int], target: int) -> List[int]:
        
    m = {}

    for i in range(len(nums)):
        cur = nums[i]
        left = target - cur;
        if left in m:
            return [m[left], i]

        m[cur] = i;
```
#Explanation
- Iterate through nums
- check if the remaining (left - nums) has been seen
  - if yes, return indicies
  - otherwise, add to map
