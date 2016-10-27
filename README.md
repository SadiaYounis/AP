package WordLadder;

import java.util.Scanner;
import java.util.*;
import java.io.BufferedReader;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;

public class MainClass {
    String word1 = "";
    String word2 = "";
    int wordlength ;
    int x=1;

    Scanner input = new Scanner( System.in );
    MainClass(){
    System.out.println("ENTER SOURSE WORD : " );
    word1 = input.nextLine();
    System.out.println("ENTER DESTINATION WORD: " );
    word2 = input.nextLine();
    
    }

    public boolean check_strlen(){
     int[] length = new int[2];
     length[0]=word1.length();
     length[1]=word2.length();
     if(length[0]!= 0 && length[1]!= 0 && length[0]==length[1])
      {
          wordlength = length[1];
          return true;
       }
     else
     {
         System.out.println("THE TWO WORDS HAVE UNEQUAL LENGTH.");
         return false;
     }
   }
   

    public void read() throws Exception{
    BufferedReader br;
    do{
        try {
            br = new BufferedReader(new FileReader("/Users/Sadia/dictionary.txt"));
            try {
                String x;
                int counter=0;
                Set <String> set = new HashSet <String>();
                while ( (x = br.readLine()) != null ) {
                 
                    try{
                    if(x.length() == wordlength){
                    set.add(x);
                    counter = counter + 1;
                    }          
                    }              
                    catch(Exception e) {} 
                }
                System.out.println("TOTAL WORDS OF SAME LENGTH ARE:");
                 System.out.println(counter);
                 sort my =new sort();
                 System.out.println(set);
         	     my.sortedlist(set);
                
            } catch (IOException e) {
                e.printStackTrace();
            }
            x=2;
        } catch (FileNotFoundException e) {
            System.out.println(e);
            e.printStackTrace();
        }
    }while(x==1);
    }  
}




package WordLadder;


import java.io.*;
import java.util.*;


public class wordladder {
	    public static void main(String[] args) throws Exception { 	
	      MainClass my =new MainClass();
	      my.check_strlen();
	      my.read();
	    }   
	}




package WordLadder;

import java.util.*;
import java.util.Scanner;
import java.util.Set;
import java.util.Collections;
import java.util.HashSet;

public class sort{
	public void sortedlist(Set<String> set) {
		// Sorting HashSet using List interface
	       List<String> set1 = new ArrayList<String>(set);
	       Collections.sort(set1);           
	       // Displaying list
	       System.out.println("elements after sorting: "+set1+"\n");
	}
}


