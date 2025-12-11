# Leetcode Problems Solved in new ID
## 938. Range Sum of BST
**Problem Statement**
Given the root node of a binary search tree and two integers low and high, return the sum of values of all nodes with a value in the inclusive range [low, high].
**Example**
```text
            10
           /  \
         5     15
        / \      \
       3   7      18

Input: root = [10,5,15,3,7,null,18], low = 7, high = 15
Output: 32
Explanation: Nodes 7, 10, and 15 are in the range [7, 15]. 7 + 10 + 15 = 32.
```
```Code
import java.util.*;

class Node {
    int val;
    Node right, left;
    Node(int value) {
        val = value;
    }
}

public class BST {
    static Node root;
    public static void insert(int v) {
        root = insertRec(root, v);
    }

    private static Node insertRec(Node r, int v) {
        if (r == null)
            return new Node(v);
        if (v < r.val)
            r.left = insertRec(r.left, v);
        if (v > r.val)
            r.right = insertRec(r.right, v);
        return r;
    }

    public static int rangeSumBST(Node root, int low, int high) {
        if (root == null)
            return 0;
        int c = (root.val >= low && root.val <= high) ? root.val : 0;
        int l = rangeSumBST(root.left, low, high);
        int r = rangeSumBST(root.right, low, high);
        return c + l + r;
    }

    public static void main(String asdf[]) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter the no. of nodes you are gonna give - ");
        int n = sc.nextInt();
        for (int i = 0; i < n; i++) {
            insert(sc.nextInt());
        }
        System.out.println("All Nodes are inserted");
        System.out.print("Enter the lowest value should be in the range : ");
        int low1 = sc.nextInt();
        System.out.print("Enter the highest value should be in the range : ");
        int high1 = sc.nextInt();
        int range = rangeSumBST(root, low1, high1);
        System.out.print("The sum of the nodes that are in the range is "+range);
    }
}
```
