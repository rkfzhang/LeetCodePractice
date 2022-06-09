# Solution
```
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function(prices) {
    let maxprofit = 0;
    
    let smallest = prices[0]
    
    for (let i = 1; i < prices.length; ++i) {
        if (prices[i] < smallest) {
            smallest = prices[i]
        }
        else {
            let profit = prices[i] - smallest;
            maxprofit = profit > maxprofit? profit : maxprofit;
        }
    }
    
    return maxprofit;
};
```
# Explanation
- we go through the list once
- update the smallest price whenever possible
- otherwise we check if the profit of that day is larger than the max profit
- return max profit
