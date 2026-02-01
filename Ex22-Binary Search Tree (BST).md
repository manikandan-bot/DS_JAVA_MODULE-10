# Ex22 Searching for a Book ID in a Binary Search Tree (BST)
## DATE: 
## AIM:
To design and implement java program that constructs a Binary Search Tree (BST) using given Book IDs and checks whether a specific Book ID exists in the BST.
## Algorithm
1. Start the program.
   
2. Create a Node class with integer data, and left and right child references.
   
3. Create an insert() method to insert Book IDs into the BST:

   If the tree is empty, insert the new node as the root.

   Otherwise, traverse left or right depending on whether the value is smaller or larger.

4. Create a search() method to find a specified Book ID:

   If the node is null, return false.

   If the key matches, return true.

   Recursively search left or right according to BST rules.

5. Read Book IDs from the user and insert them into the BST.

6. Input a Book ID to search in the tree.

7. Display whether the Book ID exists or not.

8. Stop the program.
  

## Program:
```java
/*
Program to construct a Binary Search Tree (BST) using given Book IDs 
and search for a specific Book ID
Developed by:MANIKANDAN T
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

public class Main {   // <- Make sure the file name is Main.java
    
    public static Node insert(Node root, int value) {
        if (root == null) {
            root = new Node(value);
            return root;
        }
        if (value < root.data) {
            root.left = insert(root.left, value);
        } else if (value > root.data) {
            root.right = insert(root.right, value);
        }
        return root;
    }

    public static boolean search(Node root, int key) {
        if (root == null) return false;
        if (root.data == key) return true;

        if (key < root.data)
            return search(root.left, key);
        else
            return search(root.right, key);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Node root = null;

        System.out.print("Enter number of Book IDs: ");
        int n = sc.nextInt();

        System.out.println("Enter Book IDs:");
        for (int i = 0; i < n; i++) {
            int id = sc.nextInt();
            root = insert(root, id);
        }

        System.out.print("Enter Book ID to search: ");
        int key = sc.nextInt();

        if (search(root, key))
            System.out.println("Book ID Found");
        else
            System.out.println("Book ID Not Found");

        sc.close();
    }
}


```

## Output:
<img width="377" height="246" alt="image" src="https://github.com/user-attachments/assets/c7aa913c-c232-4db1-a309-d8d7d25b588a" />


## Result:
The program has been successfully implemented and executed.
It constructs a Binary Search Tree from the given Book IDs and accurately determines whether a queried Book ID exists in the library system.
