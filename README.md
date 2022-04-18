class BSTNode { 
int key; 
BSTNode left, right; 
public BSTNode(int item) { 
key = item; 
left = right = null; 
} 
} 

class BST_Tree { 

BSTNode root; 
BST_Tree() { 
root = null; 
} 
 boolean search(int key){
 return (searchRec(root, key) != null);
 }
 
 public BSTNode searchRec(BSTNode root, int key) { 

 if (root==null || root.key==key) 
 return root; 
 
 
 if (root.key > key) 
 return searchRec(root.left, key); 
 

 return searchRec (root.right, key); 
 } 

void deleteKey(int key) { 
root = deleteRec(root, key); 
} 

BSTNode deleteRec(BSTNode root, int key) { 

if (root == null) return root; 

if (key < root.key) 
root.left = deleteRec(root.left, key); 
else if (key > root.key) 
root.right = deleteRec(root.right, key);
else { 

if (root.left == null) 
return root.right; 
else if (root.right == null) 
return root.left; 

root.key = minValue(root.right); 

root.right = deleteRec(root.right, root.key); 
} 
return root; 
} 
 
int minValue(BSTNode root) { 
int minv = root.key; 
while (root.left != null) { 
minv = root.left.key; 
root = root.left; 
} 
return minv; 
} 

void insert(int key) { 
root = insertRec(root, key); 
} 

BSTNode insertRec(BSTNode root, int key) { 

if (root == null) { 
root = new BSTNode(key); 
return root; 
} 

if (key < root.key) 
root.left = insertRec(root.left, key); 
else if (key > root.key) 
root.right = insertRec(root.right, key); 

return root; 
} 

void inorder() { 
inorderRec(root); 
} 
 
void inorderRec(BSTNode root) {
    if (root != null) { 
inorderRec(root.left); 
System.out.print(root.key + " "); 
inorderRec(root.right); 
} 
} 
void preorder() { 
preorderRec(root); 
} 
 
void preorderRec(BSTNode root) { 
if (root != null) { 
System.out.print(root.key + " "); 
preorderRec(root.left); 
preorderRec(root.right); 
} 
} 
void postorder() { 
postorderRec(root); 
} 

void postorderRec(BSTNode root) { 
if (root != null) { 
postorderRec(root.left); 
postorderRec(root.right); 
System.out.print(root.key + " "); 
} 
} 
}

public class BST_Recursive { 
public static void main(String[] args) { 
BST_Tree tree = new BST_Tree(); 
System.out.println("Build a tree by inserting :\n 50 30 20 40 70 60 80"); 
tree.insert(50); 
tree.insert(30); 
tree.insert(20); 
tree.insert(40); 
tree.insert(70); 
tree.insert(60); 
tree.insert(80); 
System.out.println("\nPre-order traversal of the given tree"); 
tree.preorder();
System.out.println("\nIn-order traversal of the given tree"); 
tree.inorder(); 
System.out.println("\nPost-order traversal of the given tree"); 
tree.postorder(); 
System.out.println("\n\nDelete 20"); 
tree.deleteKey(20); 
System.out.println("Inorder traversal of the modified tree"); 
tree.inorder();
System.out.println("\nDelete 30"); 
tree.deleteKey(30); 
System.out.println("Inorder traversal of the modified tree"); 
tree.inorder(); 
System.out.println("\nDelete 50"); 
tree.deleteKey(50); 
System.out.println("Inorder traversal of the modified tree"); 
tree.inorder(); 
System.out.println("\nSearch 70"); 
System.out.println("Found ? : " + tree.search(70) ); 
} 
}
