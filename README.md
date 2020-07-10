# prime-fibonacci-codevita-
https://www.programmersdoor.com/post/tcs-codevita-prime-fibonacci(in java)
 
 
import java.util.*;
import java.io.*;

public class HelloWorld{

     public static void main(String []args)
     {
         Scanner sc=new Scanner(System.in);
         int n1=sc.nextInt();
         int n2=sc.nextInt();
         System.out.println(check(n1,n2));
     }
     static long check(int n1,int n2)
    {
         List<Integer> li=primeList(n1,n2);
         HashSet<Integer> li1=conCat(li);
       
         int a=li1.size();
        
         int max1=Collections.max(li1);
         int min1=Collections.min(li1);
         long b=fibonacci(a,min1,max1);
         return b;
    }    
    static List<Integer> primeList(int n1,int n2)
    {
        int p=0,count=0;
        List<Integer> li=new ArrayList<>();
        for(int i=n1;i<=n2;i++)
        {
            count=0;
            for(int j=2;j<Math.sqrt(i)+1;j++)
            {
                if(i==2)
                {
                    break;
                }
                if(i%j==0 )
                {
                    count++;
                    break;
                }   
            }
            if(count==0 )
            {
                li.add(i);
            } 
        }
        return li;
    } 
    static HashSet<Integer> conCat(List<Integer> li)
    {
        int count=0;
        HashSet<Integer> li1=new HashSet<>();
        for(int i=0;i<li.size();i++)
        {
             for(int j=0;j<li.size();j++)
             {
                 if(i!=j)
                 {
                     String a=Integer.toString(li.get(i));
                     String b=Integer.toString(li.get(j));
                     String c=a+b;
                     int d=Integer.parseInt(c);
                     for(int k=2;k<Math.sqrt(d)+1;k++)
                     {
                         count=0;
                         if(d==2)
                         {
                             break;
                         }
                         if(d%k==0)
                         {
                             count++;
                             break;
                         }
                     }
                     if(count==0)
                     {
                         li1.add(d);
                     }
                     
                 }
             }
        }
        return li1;
    }
    static long fibonacci(int a,int min,int max)
    {
        long b=min;
        long c=max;
        long d=0;
        for(int i=0;i<a-2;i++)
        {
            d=b+c;
            b=c;
            c=d;
        }
        return d;
    }
}
