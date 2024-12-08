# DFS
# BFS
1. https://leetcode.com/problems/minimum-limit-of-balls-in-a-bag/description/\
Input: nums = [9], maxOperations = 2,
Output: 3\
思路：用bfs的思路，每次找节点list的最大值，然后对于最大值遍历两数知乎，把遍历的list加入children
```python
def minimumSize(nums, maxOperations):
    activate_nodes = [nums]
    while maxOperations:
        children = []
        for nums_node in activate_nodes:
            max_num = max(nums_node)
            nums_node.remove(max_num)
            for i in range(1, max_num//2+1):
                left = i
                right = max_num - i
                children.append(nums_node+[left, right])
        activate_nodes = children
        maxOperations -= 1

    min_max = float('inf')
    for node in activate_nodes:
        if max(node) < min_max:
            min_max = max(node)
    return min_max
print(minimumSize([9],2))
print(minimumSize([2,4,8,2],4))
```