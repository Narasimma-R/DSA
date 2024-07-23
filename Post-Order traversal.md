### Post Order
Given the root of a binary tree, return the postorder traversal of its nodes' values.

### Example 1:

Input: root = [1,null,2,3]
Output: [3,2,1]
### Example 2:

Input: root = []
Output: []
### Example 3:

Input: root = [1]
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
    public void doPostOrder(){
       postOrder(root);
    }

    private void postOrder(Node root){
        if(root==null) return;
        postOrder(root.left);
        postOrder(root.right);
        System.out.print(root.data+" ");
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
        System.out.println("POST ORDER");
        tree.doPostOrder();
    }
}
```
