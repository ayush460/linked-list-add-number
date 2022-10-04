# linked-list-add-number
import java.util.*;
import java.lang.*;
import java.io.*;

public class Main
{
        public static Node reverse(Node head){
                Node curr=head;
                Node prev=null;
                Node next=null;
                while(curr!=null){
                        next=curr.next;
                        curr.next=prev;
                        prev=curr;
                        curr=next;
                }
                head=prev;
                return head;
        }
        public static void combine(Node a,Node b,check ans){
                int carry=0;
                while(a!=null && b!=null){
                        int sum=a.data+b.data+carry;
                        ans.add(sum%10);
                        carry=sum/10;
                        a=a.next;
                        b=b.next;
                }
                while(a!=null){
                        int sum=a.data+carry;
                        ans.add(sum%10);
                        carry=sum/10;
                        a=a.next;
                        
                }
                while(b!=null){
                        int sum=b.data+carry;
                        ans.add(sum%10);
                        carry=sum/10;
                        b=b.next;
                }
                if(carry>0){
                        ans.add(carry);
                }
        
        }
           
	public static void main (String[] args) throws java.lang.Exception
	{
                Scanner sc=new Scanner(System.in);
                int n=sc.nextInt();
                int m=sc.nextInt();
                check a=new check();
                check b=new check();
                for(int i=0;i<n;i++){
                        a.add(sc.nextInt());
                        
                }
		for(int i=0;i<m;i++){
                b.add(sc.nextInt());
                }
              
                a.head=reverse(a.head);
              
                b.head=reverse(b.head);
            
                check ans=new check();
                combine(a.head,b.head,ans);
                ans.head=reverse(ans.head);
                Node curr=ans.head;
                while(curr!=null){
                        System.out.print(curr.data+" ");
                        curr=curr.next;
                }
      
	}
      
}
class check{
        Node head;
        Node tail;
        void add(int data){
                Node newnode=new Node(data);
                if(head==null){
                        head=newnode;
                        tail=newnode;
                        
                }
                tail.next=newnode;
                tail=newnode;
        }
       
        }



   class Node{
        Node next;
        int data;
        Node(int data){
                this.next=null;
                this.data=data;
        }
}
