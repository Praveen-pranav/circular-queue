CIRCULAR-QUEUE:-

#include<stdio.h>
# define SIZE 5
int queue[SIZE];
int front=-1;
int rear=-1;

int Is_Full()
     {
         if(((rear+1)%SIZE==front)||(front==0&&rear==(SIZE-1)))
                return 1;
         else
            return 0;
     }
int Is_Empty()
     {
         if(front==-1)
               return 1;
         else
            return 0;
     }
void enqueue(int x)
   {
        if(Is_Full())
          {
               printf("QUEUE IS FULL!!\n");
          }
        else
         {
           if(rear==-1&&front==-1)
           {
              front=rear=0;
           }
           else
           {
              rear=(rear+1)%SIZE;
           }
        queue[rear]=x;
         }
}
int dequeue()
   {   
        int a;
        if(Is_Empty())
          {
              printf("QUEUE IS EMPTY!!\n");
          }
        else
        {
           a=queue[front];
        if(rear==front)
          {
              rear=front=-1;
          }
        else if(front==(SIZE-1))
          {
              front=0;
          }
        else
           {   
                front=(front+1)%SIZE;
           }
        printf("The DEQUEUED element is..%d\n",a);
         return a;
         }
}
void display()
  {
      int i,j;
      if(Is_Empty())
       {
           printf("QUEUE IS EMPTY!!\n");
       }
       else if(front>rear)
       {
        for(j=front;j<=(SIZE-1);j++)
          {
            printf("%d--",queue[j]);
          }
        for(j=0;j<=rear;j++)
          {
            printf("%d--",queue[j]);
          }
          printf("\nREAR is at %d\tFRONT is at %d\n",rear,front);
         printf("\n");
       }
       else if(rear>=front)
        {
        for(i=front;i<=rear;i++)
          {
             printf("%d--",queue[i]);
          }
        printf("\nREAR is at %d\tFRONT is at %d\n",rear,front);
        printf("\n");
      }
     
  }
 main()
   {
      int choice;
      do
      {
          printf("QUEUE OPERATIONS :-\n1.ENQUEUE\n2.DEQUEUE\n3.DISPLAY\n4.EXIT\nENTER YOUR CHOICE..");
          scanf("%d",&choice);
          switch(choice)
            {
                case 1:
                       {
                           int a;
                           printf("Enter the Element to be ENQUEUED...");
                           scanf("%d",&a);
                           enqueue(a);
                           display();
                           break;
                       }
                case 2:
                       {
                           dequeue();
                           display();
                           break;
                       }
                case 3:
                       {
                           display();
                           break;
                       }
                case 4:
                       {
                           printf("THANK U!!!\n");
                           break;
                       }
                default:
                       {
                           printf("Please Enter a Valid Choice !!\n");
                           break;
                       }
            }
      }while(choice!=4);
   }
