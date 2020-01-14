# Top down dfsHelper Template
- Child doesn't return anything
- Parent doesn't expect to do any calculation
- Parent only pass smaller problem to child
- Child update the global answer if found
```
var dfs = function(root, sum) {
    if(!root) {
        return false;
    }
    let foundPathSum = false;
    const dfsHelper = (node, total) => {
        // Base condition i.e. leaf node
        if(!node.left && !node.right) {
            total+= node.val;
            if(total === sum) {
              foundPathSum = true;  
            }
            return;
        }
        // check left path
        if(node.left) {
            dfsHelper(node.left, total + node.val);
        }
        // check right path
        if(node.right){
            dfsHelper(node.right, total + node.val);
        }
        
    }
    dfsHelper(root, 0);
    return foundPathSum
};
```
# Bottom Up dfsHelper
Conceptually separate following two concepts
- Compute local answer
- Update global answer
- dfs doesn't return the answer
- dfs returns the value is used to compute the answer
- parent needs to use the value return by child and compute the answer
```
var diameterOfBinaryTree = function(root) {
    if(!root) {
        return 0;
    }
    let diameter = 0;
    const dfs = (node) => {
        // Base case for leaf node
        if(!node.left && !node.right) {
            return 1; // leaf node will have height as 1
        }
        let lHeight = 0;
        let rHeight = 0;
        // explore left
        if(node.left) {
            lHeight = dfs(node.left)
        }
        // explore right
        if(node.right) {
            rHeight = dfs(node.right)
        }
        
        const localDiameter = lHeight + rHeight;
        // update global
        diameter = Math.max(diameter, localDiameter);
        return Math.max(lHeight, rHeight) + 1; // Return new height
    }
    dfs(root);
    return diameter;
};
```
# Boundary Walk
- It is combining both top down and bottom up
- Parent uses value returned by child
# Implement DFS using Stack