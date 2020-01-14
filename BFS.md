# Template
```
var bfs = function(root) {
    const results = [];
    // base case
    if(!root) {
        return results;
    }
    const queue = [];
    // Initialize queue
    queue.push(root);
    // iterate until queue is empty
    while(queue.length > 0) {
        // read the length of queue
        const n = queue.length;
        const result = [];
        // process each queue node
        for(let i=0; i <n; i++ ) {
            const node = queue.shift(); // dequeue first node
            // add node into result
            result.push(node.val);

            // add children into queue
            if(node.left) {
                queue.push(node.left);
            }
            if(node.right) {
                queue.push(node.right)
            }
        }
        // process your result
        results.push(result);
    }
    
    return results;
};
```