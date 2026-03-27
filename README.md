<blr>
   ~ Mohammed Feroz
 <blr>

# Linked-list-Delete-At-Beginning-
This repository demonstrates the delete at beginning operation in a singly linked list. It shows how to remove the first node by updating the head pointer and handling edge cases like empty or single-node lists. The implementation is simple and helps in understanding basic data structure concepts.

code 
#include<stdio.h>
#include<stdlib.h>
struct node
{
    int data;
    struct node* next;
};
void insertAtBeg(struct node** head,int val)
{
    struct node* newnode = (struct node*)malloc(sizeof(struct node));
    newnode->data=val;
    newnode->next=*head;
    *head = newnode;
}  
void deleteAtBeg(struct node** head)   // <-- changed parameter to struct node**
{    
    if (*head == NULL) {
        printf("List is empty. Nothing to delete.\n");
        return;
    }

    struct node* temp = *head;
    *head = (*head)->next;
    printf("Deleted element: %d\n", temp->data);   // <-- print before free
    free(temp);
}
void display(struct node* head)
{
    struct node* temp=head;
    while(temp!=NULL) 
    {
        printf("%d->",temp->data);
        temp=temp->next;
    }
    printf("NULL");
}
int main()
{
    struct node* head=NULL;
    int n,val;
    scanf("%d",&n);
    for(int i=0;i<n;i++)
    {
        scanf("%d",&val);
        insertAtBeg(&head,val);
    }
    deleteAtBeg(&head);   // <-- pass &head instead of head
    printf("After Deleting : ");
    display(head);
    
    return 0;
}

