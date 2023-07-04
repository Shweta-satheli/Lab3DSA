package com.gl;
import java.util.*;
public class BracketBalancing {
	public static boolean isBalanced(char expr[])  {
		
		char ch;
		Stack<Character> stk = new Stack<>();
		 for (int i = 0; i < expr.length; i++) {
	             ch = expr[i];
	 
	            if (ch == '(' || ch == '[' || ch == '{') {
	                
	                stk.push(ch);
	                continue;
	            }
	            if (stk.isEmpty())
	                return false;
	            char top;
	            switch (ch) {
	            case ')':
	                top = stk.pop();
	                if (top == '{' || top == '[')
	                    return false;
	                break;
	 
	            case '}':
	                top = stk.pop();
	                if (top == '(' || top == '[')
	                    return false;
	                break;
	 
	            case ']':
	                top = stk.pop();
	                if (top == '(' || top == '{')
	                    return false;
	                break;
	            }
	        }
	 
	        // Check Empty Stack
	        return (stk.isEmpty());
	    }
		
		
		
	
    public static void main(String[] args) {
    	char[] expr = { '(','[','{','}',']',')'};
    	 if (isBalanced(expr))
             System.out.println("Balanced ");
         else
             System.out.println("Not Balanced ");
}
    }