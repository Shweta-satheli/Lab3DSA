package com.gl;
import java.util.*;

public class FindindPair {
    
    static class Node {
        int data;
        Node left, right;
        Node(int val){
        	data=val;
        	
        }
    }
 

 
    static boolean findpair(Node root, int sum, HashSet<Integer> set){
          // base case
        if (root == null) return false;
 
        if (findpair(root.left, sum, set)) return true;
 
        if (set.contains(sum - root.data)){
            System.out.println("Pair is found (" + (sum - root.data) + ", " + root.data + ")");
            return true;
        }
        else set.add(root.data);
 
        return findpair(root.right, sum, set);
    }
 
    static void findPair(Node root, int sum){
        HashSet<Integer> set = new HashSet<Integer>();
        if (!findpair(root, sum, set))
            System.out.print("Pairs do not exit \n");
    }
 
   
    public static void main(String[] args){
        Node root = new Node(15);
        root.left=new Node(8);
        root.right=new Node(20);
        root.left.left=new Node(6);
        root.left.right=new Node(12);
        root.right.left=new Node(18);
        root.right.right=new Node(25);
     
 
        int sum = 43;
        findPair(root, sum);
    }
}