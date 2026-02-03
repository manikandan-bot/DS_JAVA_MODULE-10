# Ex21 Count the Number of Nodes in the Left Subtree of a Binary Tree

## DATE: 
## AIM:
To design and implement a java program that constructs a binary tree from given level order input and counts the number of nodes present in the left subtree of the root node

## Algorithm
1. Start the program.
   
2. Define a Node class containing data, left child, and right child references.
   
4. Construct the binary tree using level order input:

   Use a queue to insert nodes level by level.
   
   For each node, assign left and right children based on input values.

4. Create a function to count the nodes in the left subtree of the root:

   Recursively count nodes using: count = 1 + count(left child) + count(right child)

5. Call the function using the left child of the root node.

6. Display the total number of nodes in the left subtree.

7. Stop the program.
   
## Program:
```java

Program to constructs a binary tree from given level order input and counts the number of nodes 

import java.util.*;

class Node {
    int data;
    Node left, right;
    Node(int data) {
        this.data = data;
        this.left = this.right = null;
    }
}

public class Main {

    // Build binary tree in level-order fashion
    static Node buildTree(int[] arr) {
        if (arr.length == 0) return null;
        Node root = new Node(arr[0]);
        Queue<Node> q = new LinkedList<>();
        q.add(root);
        int i = 1;

        while (!q.isEmpty() && i < arr.length) {
            Node current = q.poll();
            if (i < arr.length) {
                current.left = new Node(arr[i++]);
                q.add(current.left);
            }
            if (i < arr.length) {
                current.right = new Node(arr[i++]);
                q.add(current.right);
            }
        }

        return root;
    }

    static int countNodes(Node root) {
        if (root == null) return 0;
        return 1 + countNodes(root.left) + countNodes(root.right);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) arr[i] = sc.nextInt();
        Node root = buildTree(arr);

        if (root.left == null) {
            System.out.println(0);
        } else {
            System.out.println(countNodes(root.left));
        }
    }
}

```

## Output:
<img width="496" height="367" alt="image" src="https://github.com/user-attachments/assets/02ffb2c5-1a55-4cdc-866f-9a664dac2cdf" />




## Result:
The program has been successfully implemented and executed.
