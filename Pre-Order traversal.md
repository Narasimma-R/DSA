### Pre order traversal
Given the root of a binary tree, return the preorder traversal of its nodes' values.
### Example 1:

Input:
root = [1,-1,2,3]
Output:
[1,2,3]

### Example 2:

Input: 
root = []
Output: []

### Example 3:

Input: root = [1,-1,-1]
Output: [1]
### Code :
```java
package Trees;

import java.util.*;

public class BinaryTree {
    Node root;
    private int size=-1;
    Queue<Node> queue=new LinkedList<>();
    public Node buildTree(int[]nodes){
        if(nodes[++size]==-1) return null;
        Node newNode=new Node(nodes[size]);
        newNode.left=buildTree(nodes);
        newNode.right=buildTree(nodes);
        root=newNode;
        return newNode;
    }
    public void doPreOrder(){
        preOrder(root);
    }
    private void preOrder(Node root){
        if(root==null) return;
        System.out.print(root.data+" ");
        preOrder(root.left);
        preOrder(root.right);
    }
}
```

### Code :
``` java
package Trees;

import java.util.ArrayList;

public class BinaryTreeImplementation {
    public static void main(String[] args) {
        Scanner ip=new Scanner(System.in);
        int num=ip.nextInt();
        int[]nodes=new int[num];
        for(int i=0;i<num;i++) nodes[i]=ip.nextInt();
        BinaryTree tree=new BinaryTree();
        Node root=tree.buildTree(nodes);
        System.out.println("PRE ORDER");
        tree.doPreOrder();
```
