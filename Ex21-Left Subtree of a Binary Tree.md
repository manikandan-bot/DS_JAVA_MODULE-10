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
/*
Program to constructs a binary tree from given level order input and counts the number of nodes 
Developed by: MANIKANDAN T
RegisterNumber: 212224110037
*/
import java.util.*;

class Node {
    int data;
    Node left, right;

    Node(int value) {
        data = value;
        left = right = null;
    }
}

public class LeftSubtreeCount {

    public static Node buildTreeLevelOrder(int[] arr) {
        if (arr.length == 0) return null;

        Node root = new Node(arr[0]);
        Queue<Node> queue = new LinkedList<>();
        queue.add(root);

        int i = 1;
        while (!queue.isEmpty() && i < arr.length) {
            Node current = queue.poll();

            // Insert left child
            if (i < arr.length) {
                current.left = new Node(arr[i++]);
                queue.add(current.left);
            }

            // Insert right child
            if (i < arr.length) {
                current.right = new Node(arr[i++]);
                queue.add(current.right);
            }
        }
        return root;
    }

    // Count nodes recursively
    public static int countNodes(Node root) {
        if (root == null) return 0;
        return 1 + countNodes(root.left) + countNodes(root.right);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of nodes: ");
        int n = sc.nextInt();

        int[] arr = new int[n];
        System.out.println("Enter level order elements:");
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        Node root = buildTreeLevelOrder(arr);

        int countLeft = countNodes(root.left);

        System.out.println("Number of nodes in the left subtree: " + countLeft);
        sc.close();
    }
}
```

## Output:
<img width="381" height="365" alt="image" src="https://github.com/user-attachments/assets/763990a7-1e36-489b-a003-4a9be74c0d4c" />



## Result:
The program has been successfully implemented and executed.
