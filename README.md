# Design-LRU-Cache
Design a data structure that follows the constraints of a Least Recently Used (LRU) Cache.
Input:  
["LRUCache", "put", "put", "get", "put", "get", "put", "get", "get", "get"]  
[[2], [1, 1], [2, 2], [1], [3, 3], [2], [4, 4], [1], [3], [4]]  
Output:  
[null, null, null, 1, null, -1, null, -1, 3, 4]  
Explanation:  
- Cache capacity = 2.  
- put(1,1), put(2,2) → Cache is {1=1, 2=2}.  
- get(1) → returns 1 (key 1 is recently used).  
- put(3,3) → Evicts key 2 (least recently used). Cache becomes {1=1, 3=3}.  
- get(2) → returns -1 (not found).  
- put(4,4) → Evicts key 1 (least recently used). Cache becomes {3=3, 4=4}.  
- get(1) → returns -1, get(3) → returns 3, get(4) → returns 4.

Optimal Approach:
Hash Map + Doubly Linked List:

Doubly Linked List:

Maintain nodes in the order of their usage (recently used at the head, least recently used at the tail).

Hash Map:

Map keys to their corresponding nodes for O(1) access.

Operations:

get(key): Move the node to the head (mark as recently used).

put(key, value):

If the key exists, update its value and move it to the head.

If the cache is full, remove the tail node (LRU entry).

Add the new key-value pair to the head.

Time Complexity: O(1) for both get and put.
Space Complexity: O(capacity).
