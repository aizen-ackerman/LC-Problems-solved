# Leetcode Problems Solved from Scratch

## [26. Remove Duplicate Elements](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.

Consider the number of unique elements in nums to be k​​​​​​​​​​​​​​. After removing duplicates, return the number of unique elements k.

The first k elements of nums should contain the unique numbers in sorted order. The remaining elements beyond index k - 1 can be ignored.

**Example :**

```
Example 1:

Input: nums = [1,1,2]
Output: 2, nums = [1,2,_]
```

**Code :**
```
class Solution {
    public int removeDuplicates(int[] n) {
        int a = 1;
        for(int i=0;i<n.length;i++){
            if(n[a-1]!=n[i]){
                n[a] = n[i];
                a++;
            }
        }
        return a;
    }
    public static void main(String asf[]){
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int arr[] = new int[n];
        for(int i=0;i<n;i++){
            arr[i] = sc.nextInt();
        }
        int n = removeDuplicates(arr);
        System.out.println(n);
    }
}
```
---

### [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. 

Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.

**Example :**
```
Example 1:

Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
Example 2:

Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
```

**Code :**
```
import java.util.*;
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        System.out.println(isPalindrome(s));
    }
    static boolean isPalindrome(String s) {
        String cleaned = s.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();
        String reversed = new StringBuilder(cleaned).reverse().toString();
        return cleaned.equals(reversed);
    }
}
```
---

### [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

Given head, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

Return true if there is a cycle in the linked list. Otherwise, return false

**Example :**
```
        3 → 2 → 0 → -4
              ↑_______|

Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
```

**Code :**

```

Definition for singly-linked list.
class ListNode {
    int val;
    ListNode next;
    ListNode(int x) {
        val = x;
        next = null;
    }
}
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode a = head;
        ListNode b = head;
        while(a!=null && a.next!=null){
            a = a.next.next;
            b = b.next;
            if(a==b){
                return true;
            }
        }
        return false;
    }
}
```
---
### [167. Two Sum II](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

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
### [283. Move Zeros](https://leetcode.com/problems/move-zeroes/description/)

Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.
Using Two Pointer.

**Example :**
```
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
```

**Code :**
```
class Solution {
    public void moveZeroes(int[] nums) {
        int left = 0;
        for(int right  = 0 ; right<nums.length ; right++){
            if(nums[right]!=0){
                int temp = nums[left];
                nums[left] = nums[right];
                nums[right] = temp;
                left++;
            }
        }
    }
    public static void main(String asff[]{
        Scanner sc = new Scanner(System.in);
        int n  = ec.nextInt();
        int arr[]  = new int[n];
        for(int i=0; i<n ; i++)     arr[i]=sc.nextInt();
        movezeros(arr);
        for(int i=0; i<n ; i++)     System.out.print(arr[i]);
    }
}
```
---
### [344. Reverse a String](https://leetcode.com/problems/reverse-string/)

Write a function that reverses a string. The input string is given as an array of characters s.

**Example :**
```
Example 1:

Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
Example 2:

Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```

**Code :**
```
import java.util.*;
class Solution {
    public void reverseString(char[] s) {
        int t = 0;
        int e = s.length-1;
        while(t<s.length/2){
            char temp = s[t];
            s[t] = s[e];
            s[e] = temp;
            t++;
            e--;
        }
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.nextLine();
        char ch[] = s.toCharArray();
        reverseString(ch);
        for(int i=0;i<ch.length;i++){
            System.out.print(ch[i]);
        }
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
