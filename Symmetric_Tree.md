

# Problem Statement

Given a binary tree, check whether it is a symmetric tree or not.

**Input**: A binary tree  
**Output**: True if it's a symmetric tree, False otherwise  

**Example**  
Input: 
        1
       / \
      2   2
     / \ / \
    3  4 4  3

Output: True

## Solution

```java
public class Solution {
    public boolean isSymmetric(TreeNode root) {
        if(root == null)
            return true;
        return isSymmetric(root.left, root.right);
    }
    
    private boolean isSymmetric(TreeNode left, TreeNode right){
        if(left == null || right == null)
            return left == right;
        if(left.val != right.val)
            return false;
        return isSymmetric(left.left, right.right) && isSymmetric(left.right, right.left);
    }
}
```