# myFirst-repo
package com.mycompany.mavenproject2;

import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;
import java.util.Stack;

class BFS
{
   int G[][];
   int col[];
   int prev[];
   int dis[];
   int n;
   Queue <Integer> q= new LinkedList<Integer>();
  
   BFS(int G[][],int n)
   {
       this.G=G;
       this.n=n;
       col= new int[n];
       prev= new int[n];
       dis= new int[n];
       
   }
   
   void bfs(int s)
   {
       
       for(int i=0;i<n;i++)
       {
           col[i]=0;
           prev[i]=-1;
           dis[i]=9999;
       }
       
       col[s]=1;
       dis[s]=0;
       q.add(s);
       
       while(!q.isEmpty())
       {
           int u=q.remove();
           for(int v=0;v<n;v++)
           {
               if(G[u][v]>0 && col[v]==0)
               {
                   col[v]=1;
                   dis[v]=dis[u]+1;
                   prev[v]=u;
                   q.add(v);
               }
           }
           col[u]=2;
           System.out.print(u+"  ");
          
       }
       
   }
   
   
}

public class Mavenproject2 {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.println("Enter number of vertices: ");
        int n=sc.nextInt();
        
        int G[][] = new int[n][n];
        
        System.out.println("Enter the graph: ");
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<n;j++)
            {
                G[i][j]=sc.nextInt();
            }
        }
        
        BFS bfs= new BFS(G,n);
        bfs.bfs(0);
        
        
        
        
    }
}
