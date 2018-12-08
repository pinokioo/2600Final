[Back To Readme](https://github.com/pinokioo/2600Final/readme.md)

> Binary Search Tree, is a node-based binary tree data structure which has the following properties:
The left subtree of a node contains only nodes with keys lesser than the node’s key.
The right subtree of a node contains only nodes with keys greater than the node’s key.
The left and right subtree each must also be a binary search tree.
There must be no duplicate nodes.

![Pictures](https://cdncontribute.geeksforgeeks.org/wp-content/uploads/BSTSearch.png)

### The above properties of Binary Search Tree provide an ordering among keys so that the operations like search, minimum and maximum can be done fast. If there is no ordering, then we may have to compare every key to search a given key.

Example:
```sh
// A utility function to search a given key in BST 
public Node search(Node root, int key) 
{ 
    // Base Cases: root is null or key is present at root 
    if (root==null || root.key==key) 
        return root; 
  
    // val is greater than root's key 
    if (root.key > key) 
        return search(root.left, key); 
  
    // val is less than root's key 
    return search(root.right, key); 
} 
```
--------------------- 

### Illustration to search 6 in below tree:
<li>Start from root.</li>
<li>Compare the inserting element with root, if less than root, then recurse for left, else recurse for right.</li>
<li>If element to search is found anywhere, return true, else return false.</li>

![Pictures](https://contribute.geeksforgeeks.org/wp-content/uploads/BSTSearch.png)
--------------------- 
### Insertion of a key
A new key is always inserted at leaf. We start searching a key from root till we hit a leaf node. Once a leaf node is found, the new node is added as a child of the leaf node.

Example code:
```sh
// Java program to demonstrate insert operation in binary search tree 
class BinarySearchTree { 
  
    /* Class containing left and right child of current node and key value*/
    class Node { 
        int key; 
        Node left, right; 
  
        public Node(int item) { 
            key = item; 
            left = right = null; 
        } 
    } 
  
    // Root of BST 
    Node root; 
  
    // Constructor 
    BinarySearchTree() {  
        root = null;  
    } 
  
    // This method mainly calls insertRec() 
    void insert(int key) { 
       root = insertRec(root, key); 
    } 
      
    /* A recursive function to insert a new key in BST */
    Node insertRec(Node root, int key) { 
  
        /* If the tree is empty, return a new node */
        if (root == null) { 
            root = new Node(key); 
            return root; 
        } 
  
        /* Otherwise, recur down the tree */
        if (key < root.key) 
            root.left = insertRec(root.left, key); 
        else if (key > root.key) 
            root.right = insertRec(root.right, key); 
  
        /* return the (unchanged) node pointer */
        return root; 
    } 
  
    // This method mainly calls InorderRec() 
    void inorder()  { 
       inorderRec(root); 
    } 
  
    // A utility function to do inorder traversal of BST 
    void inorderRec(Node root) { 
        if (root != null) { 
            inorderRec(root.left); 
            System.out.println(root.key); 
            inorderRec(root.right); 
        } 
    } 
  
    // Driver Program to test above functions 
    public static void main(String[] args) { 
        BinarySearchTree tree = new BinarySearchTree(); 
  
        /* Let us create following BST 
              50 
           /     \ 
          30      70 
         /  \    /  \ 
       20   40  60   80 */
        tree.insert(50); 
        tree.insert(30); 
        tree.insert(20); 
        tree.insert(40); 
        tree.insert(70); 
        tree.insert(60); 
        tree.insert(80); 
  
        // print inorder traversal of the BST 
        tree.inorder(); 
    } 
} 
// This code is contributed by Ankur Narain Verma 
```

Output:
```sh
20
30
40
50
60
70
80
```

### Illustration to insert 2 in below tree:
<li>Start from root.</li>
<li>Compare the inserting element with root, if less than root, then recurse for left, else recurse for right</li>
<li>After reaching end,just insert that node at left(if less than current) else right.</li>

![Pictures](https://contribute.geeksforgeeks.org/wp-content/uploads/BSTSearch.png)

### Time Complexity:
The worst case time complexity of search and insert operations is O(h) where h is height of Binary Search Tree. In worst case, we may have to travel from root to the deepest leaf node. The height of a skewed tree may become n and the time complexity of search and insert operation may become O(n).

[ *Video on Youtube* ](https://www.youtube.com/watch?v=qYo8BVxtoH4)

### Some Interesting Facts:
<li>Inorder traversal of BST always produces sorted output.</li>
<li>We can construct a BST with only Preorder or Postorder or Level Order traversal. Note that we can always get inorder traversal by sorting the only given traversal.</li>
<li>Number of unique BSTs with n distinct keys is Catalan Number</li>
