#Solution
```
def isValid(self, s):
    if (len(s) % 2 == 1):
        return False

    brackets = { ")": "(", "}": "{", "]": "[" }
    stack = []
    for i in range(len(s)):
        c = s[i]

        if c in brackets:
            if len(stack) == 0 or brackets[c] != stack[-1]:
                return False
            stack.pop(-1)
        else:
            stack.append(c)

    return len(stack) == 0
```
#Explanation
- Add elements to a stack
- If it is a closing bracket, check the previous entry
  - Last entry must be matching oopenning bracket to be valid 
