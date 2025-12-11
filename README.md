# Leetcode Problems Solved from Scratch

## 167. Two Sum II - Input Array Is Sorted

Given a 1-indexed array of integers numbers that is already sorted in non-decreasing order, find two numbers such that they add up to a specific target number. Let these two numbers be numbers[index1] and numbers[index2] where 1 <= index1 < index2 <= numbers.length.
Return the indices of the two numbers, index1 and index2, added by one as an integer array [index1, index2] of length 2.
The tests are generated such that there is exactly one solution. You may not use the same element twice.
Your solution must use only constant extra space

**Example :**
```
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].
```

**Code :**

```
import java.util.*;
class Solution {
    public int[] twoSum(int[] n, int t) {
        int arr[] = new int[2];
        arr[0] = 0;
        arr[1] = n.length-1;
        while(arr[0]<arr[1]){
            if(n[arr[0]]+n[arr[1]]==t){
                arr[0]+=1;
                arr[1]+=1;
                return arr;
            }
            else if(n[arr[0]]+n[arr[1]]<t) arr[0]++;
            else if(n[arr[0]]+n[arr[1]]>t) arr[1]--;
        }
        return new int[]{0,0};
    }
    public static void main(String asdf[]){
        Scanner sc = new Scanner(System.in);
        int n[] = new int[sc.nextInt()];
        for(int i=0;i<n.length;i++) n[i] = sc.nextInt();
        int t = sc.nextInt();
        int arr[] = twoSum(n,t);
        System.out.print(arr[0]+" "+arr[1]);
    }
}
```
---
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
**Code**
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
---
