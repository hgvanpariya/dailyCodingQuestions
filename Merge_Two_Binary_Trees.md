

**Problem Statement**
Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not.

You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.

**Sample Input**
Tree 1: 
```
     1
   /  \
  3    2
 / \  / \
5  4  7  6
```

Tree 2: 
```
   2
  / \
 1   3
 \   \
  4   7
```

**Sample Output**
Merged Tree: 
```
     3
   /  \
  4    5
 / \  / \
5  4  8  7
```

**Solution in Java**
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public TreeNode mergeTrees(TreeNode t1, TreeNode t2) {
        if (t1 == null)
            return t2;
        if (t2 == null)
            return t1;
        t1.val += t2.val;
        t1.left = mergeTrees(t1.left, t2.left);
        t1.right = mergeTrees(t1.right, t2.right);
        return t1;
    }
}
```