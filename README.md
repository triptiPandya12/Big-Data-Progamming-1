# Big-Data-Progamming-1

#Name: Tripti Pandya
#Exercise 1

import java.io.IOException;
import java.io.BufferedReader;
import java.io.InputStreamReader;
 
public class  LongestCommonSubsequence
{    
    
    public String lcs(String a, String b)
    {
    	String a1 = a.toLowerCase();
    	String b1 = b.toLowerCase();
    	int l1 = a1.length();
        int l2 = b1.length();
        
        int[][] arr = new int[l1 + 1][l2 + 1];
 
        for (int i = l1 - 1; i >= 0; i--)
        {
            for (int j = l2 - 1; j >= 0; j--)
            {
                if (a1.charAt(i) == b1.charAt(j))
                    arr[i][j] = arr[i + 1][j + 1] + 1;
                else 
                    arr[i][j] = Math.max(arr[i + 1][j], arr[i][j + 1]);
            }
        }
 
        int i = 0, j = 0;
        StringBuffer sb = new StringBuffer();
        while (i < l1 && j < l2) 
        {
            if (a1.charAt(i) == b1.charAt(j)) 
            {
                sb.append(a1.charAt(i));
                i++;
                j++;
            }
            else if (arr[i + 1][j] >= arr[i][j + 1]) 
                i++;
            else
                j++;
            
              }
        return sb.toString();
    }
 
    
    public static void main(String[] args) throws IOException
    {    
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
         
        System.out.println("\nEnter first string:");
        String a1 = br.readLine();
       
 
        System.out.println("\nEnter second string:");
        String b1 = br.readLine();
       
 
        LongestCommonSubsequence obj = new LongestCommonSubsequence(); 
        String result = obj.lcs(a1, b1);
 
        System.out.println("\nLCS string is :"+ result);
    }
}



