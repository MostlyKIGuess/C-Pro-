![[Pasted image 20231011115351.png]]
- Basically it’s like an array without the contiguousness of the array, they are linked using pointers. It forms a series of connected notes, where each node is going to store some data and the address of the next node.
- It is kind of like an vector for ease of the imagination, the tail points to NULL and that’s why I think the code→ 

```c
void printList(struct Node* node) {
    while (node != NULL) {
	        printf("%d ", node->data);
        node = node->next;
    }
}```

Stops when you point to NULL, because the tail points to nowhere(NULL).
- Similarly we can also calculate the size of the linked list.

- **Node Structure:** A node in a linked list typically consists of two components:  
- **Data:** It holds the actual value or data associated with the node.  
- **Next Pointer:** It stores the memory address (reference) of the next node in the sequence.  
- **Head and Tail:** The linked list is accessed through the head node, which points to the first node in the list. The last node in the list points to NULL or nullptr, indicating the end of the list. This node is known as the tail node.


```c

#include <stdio.h>

#include <stdlib.h>

#include <string.h>

  
  

typedef struct Person

{

    char name[50];

    int age;

}Person;

  

// Define the structure of a node in the linked list

struct Node {

    Person data;

    struct Node* next;

};

  

// Function to print the linked list

void printList(struct Node* node) {

    int i = 0;

    while (node != NULL) {

        printf("%s %d\n", node->data.name, node->data.age);

        node = node->next;

        i++;

    }

}

  

Person* element_at(int pos,struct  Node* list){

    int i=0;

    while(i<pos){

        list=list->next;

        i++;

    }

    return &list->data;

}

LinkedList insert(Person p, int pos, LinkedList l) {

    LinkedList new_node = (LinkedList)malloc(sizeof(struct Node));

    new_node->data = p;

    if (pos == 0) {

        new_node->next = l;

        return new_node;

    }

    LinkedList temp = l;

    int i = 0;

    while (i < pos - 1) {

        temp = temp->next;

        i++;

    }

    new_node->next = temp->next;

    temp->next = new_node;

    return l;

}

LinkedList insert_recursion(Person p,int pos,LinkedList l){

    if(pos==0){

        LinkedList new_node = (LinkedList)malloc(sizeof(struct Node));

        new_node->data = p;

        new_node->next = l;

        return new_node;

    }

    l->next=insert_recursion(p,pos-1,l->next);

    return l;

}

  

LinkedList concat(LinkedList l1, LinkedList l2) {

    LinkedList temp = l1;

    while (temp->next != NULL) {

        temp = temp->next;

    }

    temp->next = l2;

    return l1;

}

LinkedList concat_recursion(LinkedList l1,Linkedlist l2){

    if(l1==NULL){

        return l2;

    }

    l1->next=concat_recursion(l1->next,l2);

    return l1;

}

LinkedList reverse(LinkedList l) {

    LinkedList prev = NULL;

    LinkedList curr = l;

    LinkedList next = NULL;

    while (curr != NULL) {

        next = curr->next;

        curr->next = prev;

        prev = curr;

        curr = next;

  

    }

    return prev;

}

LinkedList reverse_recursion(LinkedList l){

    if(l==NULL || l->next==NULL){

        return l;

    }

    LinkedList rest=reverse_recursion(l->next);

    l->next->next=l;

    l->next=NULL;

    return rest;

}

  

int main() {

     struct Person people[3];

  

    // Fill the array with data

    strcpy(people[0].name, "Charlie");

    people[0].age = 25;

  

    strcpy(people[1].name, "Bob");

    people[1].age = 30;

  

    strcpy(people[2].name, "Alice");

    people[2].age = 27;

  

    // Create three nodes

    struct Node* head = NULL;

    struct Node* second = NULL;

    struct Node* third = NULL;

  

    // Allocate memory for the nodes

    head = (struct Node*)malloc(sizeof(struct Node));

    second = (struct Node*)malloc(sizeof(struct Node));

    third = (struct Node*)malloc(sizeof(struct Node));

  

    // Assign data values to the nodes

    head->data = people[0];

    head->next = second;

  

    second->data = people[1];

    second->next = third;

  

   third->data = people[2];

    third->next = NULL;

  

    // Print the linked list

    printList(head);

    printf("%s\t%d\n",element_at(1,head)->name,element_at(1,head)->age);

  

    return 0;

}
```