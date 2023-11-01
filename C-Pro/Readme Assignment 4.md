

# Complex Numbers

## I/O Style - 
- For the input the user is required to input a string either ADD,SUB,DOT,COS at first.
- Then the user is directed to the function created by this program and is required to give the complex number terms.
- The program will ask for the input again and again unless the user decides to input '-1' and then the user will exit out the program.

## Functions Used -
 ### printComplex -
   - It takes the linkedlist head as the input which is typedefed as Complex in my code, and prints the linkedlist upto 2 decimal precision.
 ### add -
 - It takes two linkedlist  as inputs and we make 2 seperate nodes as the head of the both linked list and add them simultaneously and import the data we get into a different linkedlist and we return that linkedlist later.
 ### sub -
 - It takes two linkedlist  as inputs and we make 2 seperate nodes as the head of the both linked list and subtract them simultaneously and import the data we get into a different linkedlist and we return that linkedlist later.
### dot -
- Takes 2 linkedlist as inputs and we have declared a float variable and it uspdates for each term.
### magnitude -
- Takes one LL as input and add the square of each term and return the final square root using math.h.
### cosineSimilarirty
- Takes 2 LL as inputs and finds their magnitude using the magnitude function and returns the output as expected.
### inputfunctions
- User is taken here from the initial input and will be asked to repetetively input as per their desired function.

  ## Code -

  ```c
      #include <stdio.h>
    #include <math.h>
    #include <stdlib.h>
    #include <string.h>

    typedef struct node {
        float term;
        struct node* next;
    } Node;

    typedef struct {
            Node* head;
        int n;
    } Complex;

    void printComplex(Complex c) {
        Node* current = c.head;
            while (current != NULL) {
                printf("%.2f ", current->term);
            current = current->next;
        }
        printf("\n");
    }

    Complex add(Complex c1, Complex c2) {
        Complex ans;
        ans.n = c1.n;
        Node* current1 = c1.head;
        Node* current2 = c2.head;
        Node* currentAns = NULL;
        Node* prevAns = NULL;
                while (current1 != NULL && current2 != NULL) {
                            Node* newNode = (Node*)malloc(sizeof(Node));
                    newNode->term = current1->term + current2->term;
                newNode->next = NULL;
                        if (currentAns == NULL) {
                                ans.head = newNode;
                            currentAns = newNode;
                                                } 
            else {
                        currentAns->next = newNode;
                    currentAns = newNode;
            }
            if (prevAns != NULL) {
                prevAns->next = currentAns;
            }
                prevAns = currentAns;
                current1 = current1->next;
                current2 = current2->next;
        }
        return ans;
    }

    Complex sub(Complex c1, Complex c2) {
        Complex ans;
        ans.n = c1.n;
        Node* current1 = c1.head;
        Node* current2 = c2.head;
        Node* currentAns = NULL;
        Node* prevAns = NULL;
                while (current1 != NULL && current2 != NULL) {
                            Node* newNode = (Node*)malloc(sizeof(Node));
                            newNode->term = current1->term - current2->term;
                    newNode->next = NULL;
                        if (currentAns == NULL) {
                            ans.head = newNode;
                            currentAns = newNode;
                            }
                            else {
                                    currentAns->next = newNode;
                                        currentAns = newNode;
                                }
                            if (prevAns != NULL) {
                                prevAns->next = currentAns;
                                            }
            prevAns = currentAns;
            current1 = current1->next;
            current2 = current2->next;
        }
        return ans;
    }

    float dot(Complex c1, Complex c2) {
        float ans = 0;
        Node* current1 = c1.head;
        Node* current2 = c2.head;
                while (current1 != NULL && current2 != NULL) {
                        ans += current1->term * current2->term;
                            current1 = current1->next;
                        current2 = current2->next;
        }
        return ans;
    }

    float magnitude(Complex c) {
        float ans = 0;
        Node* current = c.head;
                    while (current != NULL) {
                                ans += current->term * current->term;
                                current = current->next;
                            }
        return sqrt(ans);
    }

    float cosineSimilarity(Complex c1, Complex c2) {
        float dotProduct = dot(c1, c2);
        float magc1 = magnitude(c1);
        float magc2 = magnitude(c2);
        return dotProduct / (magc1 * magc2);
    }
    void inputadd(){
         Complex c1, c2, ans;
        
        int n;
           while(1){
            scanf("%d", &n);
            if(n!=-1){
                c1.n = n;
                c1.head = NULL;
                for (int i = 0; i < n; i++) {
                    float term;
                    scanf("%f", &term);
                    Node* newNode = (Node*)malloc(sizeof(Node));
                    newNode->term = term;
                    newNode->next = NULL;
                    if (c1.head == NULL) {
                        c1.head = newNode;
                    } else {
                        Node* current = c1.head;
                        while (current->next != NULL) {
                            current = current->next;
                        }
                        current->next = newNode;
                    }
                }
                c2.n = n;
                c2.head = NULL;
                for (int i = 0; i < n; i++) {
                    float term;
                    scanf("%f", &term);
                    Node* newNode = (Node*)malloc(sizeof(Node));
                    newNode->term = term;
                    newNode->next = NULL;
                    if (c2.head == NULL) {
                        c2.head = newNode;
                    } else {
                        Node* current = c2.head;
                        while (current->next != NULL) {
                            current = current->next;
                        }
                        current->next = newNode;
                    }
                }
                ans = add(c1, c2);
                printComplex(ans);

            }
            else{
                return ;
            }
            
        }
    }
    void inputsub(){
         Complex c1, c2, ans;
        
        int n;
           while(1){
            scanf("%d", &n);
            if(n!=-1){
                c1.n = n;
                c1.head = NULL;
                for (int i = 0; i < n; i++) {
                    float term;
                    scanf("%f", &term);
                    Node* newNode = (Node*)malloc(sizeof(Node));
                    newNode->term = term;
                    newNode->next = NULL;
                    if (c1.head == NULL) {
                        c1.head = newNode;
                    } else {
                        Node* current = c1.head;
                        while (current->next != NULL) {
                            current = current->next;
                        }
                        current->next = newNode;
                    }
                }
                c2.n = n;
                c2.head = NULL;
                for (int i = 0; i < n; i++) {
                    float term;
                    scanf("%f", &term);
                    Node* newNode = (Node*)malloc(sizeof(Node));
                    newNode->term = term;
                    newNode->next = NULL;
                    if (c2.head == NULL) {
                        c2.head = newNode;
                    } else {
                        Node* current = c2.head;
                        while (current->next != NULL) {
                            current = current->next;
                        }
                        current->next = newNode;
                    }
                }
                ans = sub(c1, c2);
                printComplex(ans);

            }
            else{
                return ;
            }
            
        }
    }

    void inputdot(){
         Complex c1, c2;
        
        int n;
           while(1){
            scanf("%d", &n);
            if(n!=-1){
                c1.n = n;
                c1.head = NULL;
                for (int i = 0; i < n; i++) {
                    float term;
                    scanf("%f", &term);
                    Node* newNode = (Node*)malloc(sizeof(Node));
                    newNode->term = term;
                    newNode->next = NULL;
                    if (c1.head == NULL) {
                        c1.head = newNode;
                    } else {
                        Node* current = c1.head;
                        while (current->next != NULL) {
                            current = current->next;
                        }
                        current->next = newNode;
                    }
                }
                c2.n = n;
                c2.head = NULL;
                for (int i = 0; i < n; i++) {
                    float term;
                    scanf("%f", &term);
                    Node* newNode = (Node*)malloc(sizeof(Node));
                    newNode->term = term;
                    newNode->next = NULL;
                    if (c2.head == NULL) {
                        c2.head = newNode;
                    } else {
                        Node* current = c2.head;
                        while (current->next != NULL) {
                            current = current->next;
                        }
                        current->next = newNode;
                    }
                }
               float ans = dot(c1, c2);
                printf("%.2f\n", ans);

            }
            else{
                return ;
            }
            
        }
    }
    void inputcos(){
         Complex c1, c2;
        
        int n;
           while(1){
            scanf("%d", &n);
            if(n!=-1){
                c1.n = n;
                c1.head = NULL;
                for (int i = 0; i < n; i++) {
                    float term;
                    scanf("%f", &term);
                    Node* newNode = (Node*)malloc(sizeof(Node));
                    newNode->term = term;
                    newNode->next = NULL;
                    if (c1.head == NULL) {
                        c1.head = newNode;
                    } else {
                        Node* current = c1.head;
                        while (current->next != NULL) {
                            current = current->next;
                        }
                        current->next = newNode;
                    }
                }
                c2.n = n;
                c2.head = NULL;
                for (int i = 0; i < n; i++) {
                    float term;
                    scanf("%f", &term);
                    Node* newNode = (Node*)malloc(sizeof(Node));
                    newNode->term = term;
                    newNode->next = NULL;
                    if (c2.head == NULL) {
                        c2.head = newNode;
                    } else {
                        Node* current = c2.head;
                        while (current->next != NULL) {
                            current = current->next;
                        }
                        current->next = newNode;
                    }
                }
               float ans = cosineSimilarity(c1, c2);
                printf("%.2f\n", ans);

            }
            else{
                return ;
            }
            
        }
    }

    int main() {
       
        char choice[10];
        scanf("%s", choice);
        char add[10]="ADD";
        char sub[10]="SUB";
        char dot[10]="DOT";
        char cos[10]="COS";
        if(strcmp(choice,add)==0){
          inputadd();
        }
        else if(strcmp(choice,sub)==0){
          inputsub();
        }
        else if(strcmp(choice,dot)==0){
          inputdot();
        }
        else if(strcmp(choice,cos)==0){
          inputcos();
        }
        
     
        return 0;
    }
```

# Banking

- Something to note, here the linkedlist isn't stored inside main, but it is a local variable and struct node is typedef as AccountInfo, so Account Info itself is a linked list.
- Whenever I use Account Deatils I mean it asks for the name, type,balance of the account.

## I/O Style - 
- User is presented with 6 options on what he wants to do, and the user will exit out of the Bank if he presses anything else other than 1-6.
- Most of the things are just written with printf for easier I/O. But preassumed assumptions are using enums and 1 for SAVINGS account and 1 for Current.
- User is expected to display first before deleting an account, it just makes the input of delete easier because delete function asks for account number and name.
- Rest I/O per functions will be explained below.

  ## Functions Used-

 ### insert_at_position-
 - It takes the account type and account deatils and the position it has to be inserted inside the linked list,here position should be given like it is in the Bank Database which is starting from 100..
 - Then we use malloc to allocate the memory for an Account and then use that to insert at our linkedlist.

### insert-
- It does the same thing like insert but it doesn't take account number and just assigns the account no of the person as the prev account number + 1.
- It is the default insert function when the user presses 1, this is where he is taken over here, if the user is found to enter a account that already exist, we return from the function.the array
- It also takes over the fact that when you have a deleted account it inserts the account between the accounts, also the 100th account using conditions.
- We also print the freshly created account.

  ### sort-
  - We take the head from the global variable and use bubblesort algorithm to sort via account number.
 
  ### add_money,withdraw -
  - Parameters are account number and amount, we just do the respective function on the account with conditions mentioned in the questions pdf.

  ### transaction-
  - Parameters are account number, amount and the code on what the user have to do, 0 for adding , 1 for withdrawing the money.
  ### low-balance-
  - Parameter is the amount, we print all the accounts having less amount than the argument given in the function.
 
### lowbalanceAccount -
- Prints out all the accounts having less money than 100 in their account.
- Activates when user presses 6.

### display -
- Displays all the account in the sorted order of account number.
- Activates when user presses 5.


  ## Code -

  ```c

   #include <stdio.h>
   #include <stdlib.h>
   #include <string.h>

    typedef enum Account_Type{
    SAVINGS,
    CURRENT
   }Account_Type;

   typedef struct AccountInfo
  {
    int Account_Number;
    enum Account_Type Account_Type;
    char Name[50];
    float Balance;
    struct AccountInfo *next;
  }AccountInfo;

  AccountInfo *head = NULL;
  int prev = 99;
  void insert_at_position(Account_Type account_type, char *name, float balance, int position){
    AccountInfo *temp = head;
    int count = 1;
    int acn = position; //acount number
    position=100-position;
    while(temp!=NULL && count < position-1){
        temp = temp->next;
        count++;
    }
    if(temp == NULL){
        printf("Invalid position\n");
        return;
    }
    AccountInfo *new_account = (AccountInfo*)malloc(sizeof(AccountInfo));
    new_account->Account_Number = acn;
    new_account->Account_Type = account_type;
    strcpy(new_account->Name,name);
    new_account->Balance = balance;
    new_account->next = temp->next;
    temp->next = new_account;
    printf("Account Number: %d\n",new_account->Account_Number);
    printf("Account Holder: %s\n",new_account->Name);
    printf("Account Type: %s\n",account_type==SAVINGS?"Savings":"Current");
    printf("Balance: Rs %.2f\n",new_account->Balance);
  }

  void insert(Account_Type account_type, char *name, float balance){
    AccountInfo *temp = head;
    int prev_account_number = -1;
    prev = 99; 
    while(temp!=NULL){
        if(temp->Account_Type == account_type && strcmp(temp->Name,name)==0){
            printf("Invalid: User already exists!\n");
            return;
        }
        if(prev_account_number != -1 && temp->Account_Number - prev_account_number > 1){
            insert_at_position(account_type, name, balance, prev_account_number+1);
            return;
        }
        prev_account_number = temp->Account_Number;
        if(prev_account_number == 101  && prev == 99){
            insert_at_position(account_type, name, balance, prev+1);
        }
        prev = temp->Account_Number;
        temp = temp->next;
    }
    AccountInfo *new_account = (AccountInfo*)malloc(sizeof(AccountInfo));
    new_account->Account_Number = prev + 1;
    new_account->Account_Type = account_type;
    strcpy(new_account->Name,name);
    new_account->Balance = balance;
    new_account->next = NULL;
    if(head==NULL){
        head = new_account;
    }
    else{
        temp = head;
        while(temp->next!=NULL){
            temp = temp->next;
        }
        temp->next = new_account;
    }
    printf("Account Number: %d\n",new_account->Account_Number);
    printf("Account Holder: %s\n",new_account->Name);
    printf("Account Type: %s\n",account_type==SAVINGS?"Savings":"Current");
    printf("Balance: Rs %.2f\n",new_account->Balance);
  }



  void delete(int account_number, Account_Type account_type, char *name){
    AccountInfo *temp = head;
    AccountInfo *prev = NULL;
    while(temp!=NULL){
        if(temp->Account_Number == account_number && temp->Account_Type == account_type && strcmp(temp->Name,name)==0){
            if(prev==NULL){
                head = temp->next;
            }
            else{
                prev->next = temp->next;
            }
            free(temp);
            printf("Account deleted successfully\n");
        }
        prev = temp;
        temp = temp->next;
    }
    printf("Invalid: User does not exist\n");
  }
  void sort(){
    AccountInfo *temp = head;
    while(temp!=NULL){
        AccountInfo *temp2 = temp->next;
        while(temp2!=NULL){
            if(temp->Account_Number > temp2->Account_Number){
                int temp_account_number = temp->Account_Number;
                temp->Account_Number = temp2->Account_Number;
                temp2->Account_Number = temp_account_number;
                Account_Type temp_account_type = temp->Account_Type;
                temp->Account_Type = temp2->Account_Type;
                temp2->Account_Type = temp_account_type;
                char temp_name[50];
                strcpy(temp_name,temp->Name);
                strcpy(temp->Name,temp2->Name);
                strcpy(temp2->Name,temp_name);
                float temp_balance = temp->Balance;
                temp->Balance = temp2->Balance;
                temp2->Balance = temp_balance;
            }
            temp2 = temp2->next;
        }
        temp = temp->next;
    }
  }

  void add_money(int account_number, float amount){
    AccountInfo *temp = head;
    while(temp!=NULL){
        if(temp->Account_Number == account_number){
            temp->Balance += amount;
            printf("Updated balance is Rs %.2f\n",temp->Balance);
            return;
        }
        temp = temp->next;
    }
    printf("Invalid: User does not exist\n");
  }

  void withdraw(int account_number, float amount){
    AccountInfo *temp = head;
    while(temp!=NULL){
        if(temp->Account_Number == account_number){
            if(amount < 100){
                printf("Invalid: Minimum withdrawal amount is Rs 100\n");
                return;
            }
            if(temp->Balance >= amount){
                temp->Balance -= amount;
                printf("Updated balance is Rs %.2f\n",temp->Balance);
            }
            else{
                printf("The balance is insufficient for the specified withdrawal.\n");
            }
            return;
        }
        temp = temp->next;
    }
    printf("Invalid: User does not exist\n");
  }

  void transaction(int account_number, float amount, int code){
    if(code == 1){
        add_money(account_number, amount);
    }
    else{
        float withdraw_amount;
        printf("Enter the amount to withdraw: ");
        scanf("%f", &withdraw_amount);
        withdraw(account_number, withdraw_amount);
    }
  }
  
  void low_balance(float amount){
    AccountInfo *temp = head;
    while(temp!=NULL){
        if(temp->Balance < amount){
               printf("-----------------------------------------------------------------\n");
                 printf("| %-15s | %-15s | %-10s | %-10s |\n", "Account Number", "Account Holder", "Account Type", "Balance");
                    printf("-----------------------------------------------------------------\n");
                 
                  printf("| %-15d | %-15s | %-10s | Rs %-8.2f |\n",temp->Account_Number,temp->Name,temp->Account_Type==SAVINGS?"Savings":"Current",temp->Balance);
                printf("-----------------------------------------------------------------\n");
        }
        temp = temp->next;
    }
  }

  void lowBalaceAccounts(){
    low_balance(100);
  }

  void display(){
    sort();
    AccountInfo *temp = head;
    printf("-----------------------------------------------------------------\n");
    printf("| %-15s | %-15s | %-10s | %-10s |\n", "Account Number", "Account Holder", "Account Type", "Balance");
    printf("-----------------------------------------------------------------\n");
    if(temp==NULL){
        printf("| %-15s | %-15s | %-10s | %-10s |\n", "N/A", "N/A", "N/A", "N/A");
    }
    while(temp!=NULL){
        printf("| %-15d | %-15s | %-10s | Rs %-8.2f |\n",temp->Account_Number,temp->Name,temp->Account_Type==SAVINGS?"Savings":"Current",temp->Balance);
        temp = temp->next;
    }
    printf("-----------------------------------------------------------------\n");
  }

  int main(){
   
    printf("-----------------------------------------------------------------\n");
    printf("HELLOOOO FELLOW TRAVELER!\n");
    while(1){
    printf("What would you like to do today?\n");
    printf("1. Create a new account\n");
    printf("2. Delete an existing account\n");
    printf("3. Add money to an existing account\n");
    printf("4. Withdraw money from an existing account\n");
    printf("5. Display all accounts\n");
    printf("6. Display all accounts with balance less than Rs 100\n");
    int n;
    scanf("%d",&n);
    if(n==1){
        printf("Enter the account type (0 for Savings, 1 for Current): ");
        int account_type;
        scanf("%d",&account_type);
        printf("Enter the name of the account holder: ");
        char name[50];
        scanf("%s",name);
        printf("Enter the initial balance: ");
        float balance;
        scanf("%f",&balance);
        insert(account_type==0?SAVINGS:CURRENT,name,balance);
    }
    else if(n==2){
        printf("Enter the account number: ");
        int account_number;
        scanf("%d",&account_number);
        printf("Enter the account type (0 for Savings, 1 for Current): ");
        int account_type;
        scanf("%d",&account_type);
        printf("Enter the name of the account holder: ");
        char name[50];
        scanf("%s",name);
        delete(account_number,account_type==0?SAVINGS:CURRENT,name);
    }
    else if(n==3){
        printf("Enter the account number: ");
        int account_number;
        scanf("%d",&account_number);
        printf("Enter the amount to be added: ");
        float amount;
        scanf("%f",&amount);
        add_money(account_number,amount);
    }
    else if(n==4){
        printf("Enter the account number: ");
        int account_number;
        scanf("%d",&account_number);
        printf("Enter the amount to be withdrawn: ");
        float amount;
        scanf("%f",&amount);
        withdraw(account_number,amount);
    }
    else if(n==5){
        display();
    }
    else if(n==6){
        lowBalaceAccounts();
    }
    else{
        printf("THANK YOU FOR USING OUR BANKKK! HOPE WE NEVER SCAM YOU :p\n");
     return 0;
    
    }
    }

  return 0;
  }
  
 
```



# Beautiful Colors

## I/O Style - 
- For the input the user is required to input the number of colours and will be asked to input that many numbers.

## Functions Used -
 ### insertNode -
   - It takes the linkedlist head as the pointer and takes another integer as the input, and adds it into the linkedlist.
 ### remove duplicates -
- We iterate through the linkedlist and check whether the next block has the same color, if found we remove the duplicate.
  ### sort
  - Sorts through the linked list using bubblesort algorithm.
 ### printinz
 - We use this to print the linkedlist iterating through each element in the manner asked in the pdf.


  ## Code -
  ```c
#include <stdio.h>
#include <stdlib.h>

typedef struct node {
    int color;
    struct node* next;
} Linkedlist;

Linkedlist* newNode(int color) {
    Linkedlist* node = (Linkedlist*) malloc(sizeof(Linkedlist));
                node->color = color;
            node->next = NULL;
    return node;
}

void insertNode(Linkedlist** head, int color) {
    Linkedlist* node = newNode(color);
            if (*head == NULL) {
                *head = node;
            return;
    }
    Linkedlist* current = *head;
        while (current->next != NULL) {
            current = current->next;
        }
    current->next = node;
}
void sort(Linkedlist** head) {
    Linkedlist* current = *head;
    Linkedlist* index = NULL;
    int temp;
    if (*head == NULL) {
        return;
    } 
    else {
        while (current != NULL) {
            index = current->next;
            while (index != NULL) {
                if (current->color > index->color) {
                    temp = current->color;
                    current->color = index->color;
                    index->color = temp;
                }
                index = index->next;
            }
            current = current->next;
        }
    }
}

Linkedlist* removeDuplicates(Linkedlist* head) {
    Linkedlist* current = head;
    while (current != NULL && current->next != NULL) {
                  if (current->color == current->next->color) {
                        Linkedlist* temp = current->next;
                current->next = current->next->next;
                    free(temp);
        } 
    else {
        current = current->next;
        }
    }
return head;
}

void printinz(Linkedlist* head) {
    Linkedlist* current = head;
            while (current != NULL) {
                     if (current->next != NULL) {
                        printf("%d->", current->color);
                         } 
        else {
        printf("%d ", current->color);
        }
    current = current->next;
    }
    printf("\n");
}

int main() {
    int n;
    printf("Enter the number of colors in the list: ");
    scanf("%d", &n);
    Linkedlist* head = NULL;
    printf("Enter the colors: ");
    for (int i = 0; i < n; i++) {
        int color;
        scanf("%d", &color);
        insertNode(&head, color);
    }
    sort(&head);
    head = removeDuplicates(head);
    printf("Modified linked list: ");
    printinz(head);
    return 0;
}
```



  
  
[[Readme Assignment 4]]
# Complex Numbers

  

## I/O Style -

- For the input the user is required to input a string either ADD,SUB,DOT,COS at first.

- Then the user is directed to the function created by this program and is required to give the complex number terms.

- The program will ask for the input again and again unless the user decides to input '-1' and then the user will be sent to the original input if the user types anything other then ADD,SUB,DOT,COS he will be exited out of the program.

  

## Functions Used -

 ### inputoriginal -

 - It takes the input from the user to take him to different input of the function, this is the backbone of the whole code, user comes here when he presses -1 in any of the other input functions, and if user types anything other than ADD,SUB,DOT,COS he will be exited out of the program.

 ### printComplex -

   - It takes the linkedlist head as the input which is typedefed as Complex in my code, and prints the linkedlist upto 2 decimal precision.

 ### add -

 - It takes two linkedlist  as inputs and we make 2 seperate nodes as the head of the both linked list and add them simultaneously and import the data we get into a different linkedlist and we return that linkedlist later.

 ### sub -

 - It takes two linkedlist  as inputs and we make 2 seperate nodes as the head of the both linked list and subtract them simultaneously and import the data we get into a different linkedlist and we return that linkedlist later.

### dot -

- Takes 2 linkedlist as inputs and we have declared a float variable and it uspdates for each term.

### magnitude -

- Takes one LL as input and add the square of each term and return the final square root using math.h.

### cosineSimilarirty

- Takes 2 LL as inputs and finds their magnitude using the magnitude function and returns the output as expected.

### inputfunctions

- User is taken here from the initial input and will be asked to repetetively input as per their desired function.

  

  ## Code -

  

  ```c

#include <stdio.h>

#include <math.h>

#include <stdlib.h>

#include <string.h>

  

void inputoriginal(){

     char choice[10];

        scanf("%s", choice);

        char add[10]="ADD";

        char sub[10]="SUB";

        char dot[10]="DOT";

        char cos[10]="COS";

        if(strcmp(choice,add)==0){

          inputadd();

        }

        else if(strcmp(choice,sub)==0){

          inputsub();

        }

        else if(strcmp(choice,dot)==0){

          inputdot();

        }

        else if(strcmp(choice,cos)==0){

          inputcos();

        }

        else{

          printf("END\n");

          return 0;

        }

}

    typedef struct node {

        float term;

        struct node* next;

    } Node;

  

    typedef struct {

            Node* head;

        int n;

    } Complex;

  

    void printComplex(Complex c) {

        Node* current = c.head;

            while (current != NULL) {

                printf("%.2f ", current->term);

            current = current->next;

        }

        printf("\n");

    }

  

    Complex add(Complex c1, Complex c2) {

        Complex ans;

        ans.n = c1.n;

        Node* current1 = c1.head;

        Node* current2 = c2.head;

        Node* currentAns = NULL;

        Node* prevAns = NULL;

                while (current1 != NULL && current2 != NULL) {

                            Node* newNode = (Node*)malloc(sizeof(Node));

                    newNode->term = current1->term + current2->term;

                newNode->next = NULL;

                        if (currentAns == NULL) {

                                ans.head = newNode;

                            currentAns = newNode;

                                                }

            else {

                        currentAns->next = newNode;

                    currentAns = newNode;

            }

            if (prevAns != NULL) {

                prevAns->next = currentAns;

            }

                prevAns = currentAns;

                current1 = current1->next;

                current2 = current2->next;

        }

        return ans;

    }

  

    Complex sub(Complex c1, Complex c2) {

        Complex ans;

        ans.n = c1.n;

        Node* current1 = c1.head;

        Node* current2 = c2.head;

        Node* currentAns = NULL;

        Node* prevAns = NULL;

                while (current1 != NULL && current2 != NULL) {

                            Node* newNode = (Node*)malloc(sizeof(Node));

                            newNode->term = current1->term - current2->term;

                    newNode->next = NULL;

                        if (currentAns == NULL) {

                            ans.head = newNode;

                            currentAns = newNode;

                            }

                            else {

                                    currentAns->next = newNode;

                                        currentAns = newNode;

                                }

                            if (prevAns != NULL) {

                                prevAns->next = currentAns;

                                            }

            prevAns = currentAns;

            current1 = current1->next;

            current2 = current2->next;

        }

        return ans;

    }

  

    float dot(Complex c1, Complex c2) {

        float ans = 0;

        Node* current1 = c1.head;

        Node* current2 = c2.head;

                while (current1 != NULL && current2 != NULL) {

                        ans += current1->term * current2->term;

                            current1 = current1->next;

                        current2 = current2->next;

        }

        return ans;

    }

  

    float magnitude(Complex c) {

        float ans = 0;

        Node* current = c.head;

                    while (current != NULL) {

                                ans += current->term * current->term;

                                current = current->next;

                            }

        return sqrt(ans);

    }

  

    float cosineSimilarity(Complex c1, Complex c2) {

        float dotProduct = dot(c1, c2);

        float magc1 = magnitude(c1);

        float magc2 = magnitude(c2);

        return dotProduct / (magc1 * magc2);

    }

    void inputadd(){

         Complex c1, c2, ans;

        int n;

           while(1){

            scanf("%d", &n);

            if(n!=-1){

                c1.n = n;

                c1.head = NULL;

                for (int i = 0; i < n; i++) {

                    float term;

                    scanf("%f", &term);

                    Node* newNode = (Node*)malloc(sizeof(Node));

                    newNode->term = term;

                    newNode->next = NULL;

                    if (c1.head == NULL) {

                        c1.head = newNode;

                    } else {

                        Node* current = c1.head;

                        while (current->next != NULL) {

                            current = current->next;

                        }

                        current->next = newNode;

                    }

                }

                c2.n = n;

                c2.head = NULL;

                for (int i = 0; i < n; i++) {

                    float term;

                    scanf("%f", &term);

                    Node* newNode = (Node*)malloc(sizeof(Node));

                    newNode->term = term;

                    newNode->next = NULL;

                    if (c2.head == NULL) {

                        c2.head = newNode;

                    } else {

                        Node* current = c2.head;

                        while (current->next != NULL) {

                            current = current->next;

                        }

                        current->next = newNode;

                    }

                }

                ans = add(c1, c2);

                printComplex(ans);

  

            }

            else{

                inputoriginal() ;

            }

        }

    }

    void inputsub(){

         Complex c1, c2, ans;

        int n;

           while(1){

            scanf("%d", &n);

            if(n!=-1){

                c1.n = n;

                c1.head = NULL;

                for (int i = 0; i < n; i++) {

                    float term;

                    scanf("%f", &term);

                    Node* newNode = (Node*)malloc(sizeof(Node));

                    newNode->term = term;

                    newNode->next = NULL;

                    if (c1.head == NULL) {

                        c1.head = newNode;

                    } else {

                        Node* current = c1.head;

                        while (current->next != NULL) {

                            current = current->next;

                        }

                        current->next = newNode;

                    }

                }

                c2.n = n;

                c2.head = NULL;

                for (int i = 0; i < n; i++) {

                    float term;

                    scanf("%f", &term);

                    Node* newNode = (Node*)malloc(sizeof(Node));

                    newNode->term = term;

                    newNode->next = NULL;

                    if (c2.head == NULL) {

                        c2.head = newNode;

                    } else {

                        Node* current = c2.head;

                        while (current->next != NULL) {

                            current = current->next;

                        }

                        current->next = newNode;

                    }

                }

                ans = sub(c1, c2);

                printComplex(ans);

  

            }

            else{

                inputoriginal();

            }

        }

    }

  

    void inputdot(){

         Complex c1, c2;

        int n;

           while(1){

            scanf("%d", &n);

            if(n!=-1){

                c1.n = n;

                c1.head = NULL;

                for (int i = 0; i < n; i++) {

                    float term;

                    scanf("%f", &term);

                    Node* newNode = (Node*)malloc(sizeof(Node));

                    newNode->term = term;

                    newNode->next = NULL;

                    if (c1.head == NULL) {

                        c1.head = newNode;

                    } else {

                        Node* current = c1.head;

                        while (current->next != NULL) {

                            current = current->next;

                        }

                        current->next = newNode;

                    }

                }

                c2.n = n;

                c2.head = NULL;

                for (int i = 0; i < n; i++) {

                    float term;

                    scanf("%f", &term);

                    Node* newNode = (Node*)malloc(sizeof(Node));

                    newNode->term = term;

                    newNode->next = NULL;

                    if (c2.head == NULL) {

                        c2.head = newNode;

                    } else {

                        Node* current = c2.head;

                        while (current->next != NULL) {

                            current = current->next;

                        }

                        current->next = newNode;

                    }

                }

               float ans = dot(c1, c2);

                printf("%.2f\n", ans);

  

            }

            else{

                inputoriginal();

            }

        }

    }

    void inputcos(){

         Complex c1, c2;

        int n;

           while(1){

            scanf("%d", &n);

            if(n!=-1){

                c1.n = n;

                c1.head = NULL;

                for (int i = 0; i < n; i++) {

                    float term;

                    scanf("%f", &term);

                    Node* newNode = (Node*)malloc(sizeof(Node));

                    newNode->term = term;

                    newNode->next = NULL;

                    if (c1.head == NULL) {

                        c1.head = newNode;

                    } else {

                        Node* current = c1.head;

                        while (current->next != NULL) {

                            current = current->next;

                        }

                        current->next = newNode;

                    }

                }

                c2.n = n;

                c2.head = NULL;

                for (int i = 0; i < n; i++) {

                    float term;

                    scanf("%f", &term);

                    Node* newNode = (Node*)malloc(sizeof(Node));

                    newNode->term = term;

                    newNode->next = NULL;

                    if (c2.head == NULL) {

                        c2.head = newNode;

                    } else {

                        Node* current = c2.head;

                        while (current->next != NULL) {

                            current = current->next;

                        }

                        current->next = newNode;

                    }

                }

               float ans = cosineSimilarity(c1, c2);

                printf("%.2f\n", ans);

  

            }

            else{

                inputoriginal();

            }

        }

    }

  

    int main() {

  

       inputoriginal();

  

        return 0;

    }

  

```

  

# Banking

  

- Something to note, here the linkedlist isn't stored inside main, but it is a local variable and struct node is typedef as AccountInfo, so Account Info itself is a linked list.

- Whenever I use Account Deatils I mean it asks for the name, type,balance of the account.

  

## I/O Style -

- User is presented with 6 options on what he wants to do, and the user will exit out of the Bank if he presses anything else other than 1-6.

- Most of the things are just written with printf for easier I/O. But preassumed assumptions are using enums and 1 for SAVINGS account and 1 for Current.

- User is expected to display first before deleting an account, it just makes the input of delete easier because delete function asks for account number and name.

- Rest I/O per functions will be explained below.

  

  ## Functions Used-

  

 ### insert_at_position-

 - It takes the account type and account deatils and the position it has to be inserted inside the linked list,here position should be given like it is in the Bank Database which is starting from 100..

 - Then we use malloc to allocate the memory for an Account and then use that to insert at our linkedlist.

  

### insert-

- It does the same thing like insert but it doesn't take account number and just assigns the account no of the person as the prev account number + 1.

- It is the default insert function when the user presses 1, this is where he is taken over here, if the user is found to enter a account that already exist, we return from the function.the array

- It also takes over the fact that when you have a deleted account it inserts the account between the accounts, also the 100th account using conditions.

- We also print the freshly created account.

  

  ### sort-

  - We take the head from the global variable and use bubblesort algorithm to sort via account number.

  ### add_money,withdraw -

  - Parameters are account number and amount, we just do the respective function on the account with conditions mentioned in the questions pdf.

  

  ### transaction-

  - Parameters are account number, amount and the code on what the user have to do, 0 for adding , 1 for withdrawing the money.

  ### low-balance-

  - Parameter is the amount, we print all the accounts having less amount than the argument given in the function.

### lowbalanceAccount -

- Prints out all the accounts having less money than 100 in their account.

- Activates when user presses 6.

  

### display -

- Displays all the account in the sorted order of account number.

- Activates when user presses 5.

  
  

  ## Code -

  

  ```c

  

   #include <stdio.h>

   #include <stdlib.h>

   #include <string.h>

  

    typedef enum Account_Type{

    SAVINGS,

    CURRENT

   }Account_Type;

  

   typedef struct AccountInfo

  {

    int Account_Number;

    enum Account_Type Account_Type;

    char Name[50];

    float Balance;

    struct AccountInfo *next;

  }AccountInfo;

  

  AccountInfo *head = NULL;

  int prev = 99;

  void insert_at_position(Account_Type account_type, char *name, float balance, int position){

    AccountInfo *temp = head;

    int count = 1;

    int acn = position; //acount number

    position=100-position;

    while(temp!=NULL && count < position-1){

        temp = temp->next;

        count++;

    }

    if(temp == NULL){

        printf("Invalid position\n");

        return;

    }

    AccountInfo *new_account = (AccountInfo*)malloc(sizeof(AccountInfo));

    new_account->Account_Number = acn;

    new_account->Account_Type = account_type;

    strcpy(new_account->Name,name);

    new_account->Balance = balance;

    new_account->next = temp->next;

    temp->next = new_account;

    printf("Account Number: %d\n",new_account->Account_Number);

    printf("Account Holder: %s\n",new_account->Name);

    printf("Account Type: %s\n",account_type==SAVINGS?"Savings":"Current");

    printf("Balance: Rs %.2f\n",new_account->Balance);

  }

  

  void insert(Account_Type account_type, char *name, float balance){

    AccountInfo *temp = head;

    int prev_account_number = -1;

    prev = 99;

    while(temp!=NULL){

        if(temp->Account_Type == account_type && strcmp(temp->Name,name)==0){

            printf("Invalid: User already exists!\n");

            return;

        }

        if(prev_account_number != -1 && temp->Account_Number - prev_account_number > 1){

            insert_at_position(account_type, name, balance, prev_account_number+1);

            return;

        }

        prev_account_number = temp->Account_Number;

        if(prev_account_number == 101  && prev == 99){

            insert_at_position(account_type, name, balance, prev+1);

        }

        prev = temp->Account_Number;

        temp = temp->next;

    }

    AccountInfo *new_account = (AccountInfo*)malloc(sizeof(AccountInfo));

    new_account->Account_Number = prev + 1;

    new_account->Account_Type = account_type;

    strcpy(new_account->Name,name);

    new_account->Balance = balance;

    new_account->next = NULL;

    if(head==NULL){

        head = new_account;

    }

    else{

        temp = head;

        while(temp->next!=NULL){

            temp = temp->next;

        }

        temp->next = new_account;

    }

    printf("Account Number: %d\n",new_account->Account_Number);

    printf("Account Holder: %s\n",new_account->Name);

    printf("Account Type: %s\n",account_type==SAVINGS?"Savings":"Current");

    printf("Balance: Rs %.2f\n",new_account->Balance);

  }

  
  
  

  void delete(int account_number, Account_Type account_type, char *name){

    AccountInfo *temp = head;

    AccountInfo *prev = NULL;

    while(temp!=NULL){

        if(temp->Account_Number == account_number && temp->Account_Type == account_type && strcmp(temp->Name,name)==0){

            if(prev==NULL){

                head = temp->next;

            }

            else{

                prev->next = temp->next;

            }

            free(temp);

            printf("Account deleted successfully\n");

        }

        prev = temp;

        temp = temp->next;

    }

    printf("Invalid: User does not exist\n");

  }

  void sort(){

    AccountInfo *temp = head;

    while(temp!=NULL){

        AccountInfo *temp2 = temp->next;

        while(temp2!=NULL){

            if(temp->Account_Number > temp2->Account_Number){

                int temp_account_number = temp->Account_Number;

                temp->Account_Number = temp2->Account_Number;

                temp2->Account_Number = temp_account_number;

                Account_Type temp_account_type = temp->Account_Type;

                temp->Account_Type = temp2->Account_Type;

                temp2->Account_Type = temp_account_type;

                char temp_name[50];

                strcpy(temp_name,temp->Name);

                strcpy(temp->Name,temp2->Name);

                strcpy(temp2->Name,temp_name);

                float temp_balance = temp->Balance;

                temp->Balance = temp2->Balance;

                temp2->Balance = temp_balance;

            }

            temp2 = temp2->next;

        }

        temp = temp->next;

    }

  }

  

  void add_money(int account_number, float amount){

    AccountInfo *temp = head;

    while(temp!=NULL){

        if(temp->Account_Number == account_number){

            temp->Balance += amount;

            printf("Updated balance is Rs %.2f\n",temp->Balance);

            return;

        }

        temp = temp->next;

    }

    printf("Invalid: User does not exist\n");

  }

  

  void withdraw(int account_number, float amount){

    AccountInfo *temp = head;

    while(temp!=NULL){

        if(temp->Account_Number == account_number){

            if(amount < 100){

                printf("Invalid: Minimum withdrawal amount is Rs 100\n");

                return;

            }

            if(temp->Balance >= amount){

                temp->Balance -= amount;

                printf("Updated balance is Rs %.2f\n",temp->Balance);

            }

            else{

                printf("The balance is insufficient for the specified withdrawal.\n");

            }

            return;

        }

        temp = temp->next;

    }

    printf("Invalid: User does not exist\n");

  }

  

  void transaction(int account_number, float amount, int code){

    if(code == 1){

        add_money(account_number, amount);

    }

    else{

        float withdraw_amount;

        printf("Enter the amount to withdraw: ");

        scanf("%f", &withdraw_amount);

        withdraw(account_number, withdraw_amount);

    }

  }

  void low_balance(float amount){

    AccountInfo *temp = head;

    while(temp!=NULL){

        if(temp->Balance < amount){

               printf("-----------------------------------------------------------------\n");

                 printf("| %-15s | %-15s | %-10s | %-10s |\n", "Account Number", "Account Holder", "Account Type", "Balance");

                    printf("-----------------------------------------------------------------\n");

                  printf("| %-15d | %-15s | %-10s | Rs %-8.2f |\n",temp->Account_Number,temp->Name,temp->Account_Type==SAVINGS?"Savings":"Current",temp->Balance);

                printf("-----------------------------------------------------------------\n");

        }

        temp = temp->next;

    }

  }

  

  void lowBalaceAccounts(){

    low_balance(100);

  }

  

  void display(){

    sort();

    AccountInfo *temp = head;

    printf("-----------------------------------------------------------------\n");

    printf("| %-15s | %-15s | %-10s | %-10s |\n", "Account Number", "Account Holder", "Account Type", "Balance");

    printf("-----------------------------------------------------------------\n");

    if(temp==NULL){

        printf("| %-15s | %-15s | %-10s | %-10s |\n", "N/A", "N/A", "N/A", "N/A");

    }

    while(temp!=NULL){

        printf("| %-15d | %-15s | %-10s | Rs %-8.2f |\n",temp->Account_Number,temp->Name,temp->Account_Type==SAVINGS?"Savings":"Current",temp->Balance);

        temp = temp->next;

    }

    printf("-----------------------------------------------------------------\n");

  }

  

  int main(){

    printf("-----------------------------------------------------------------\n");

    printf("HELLOOOO FELLOW TRAVELER!\n");

    while(1){

    printf("What would you like to do today?\n");

    printf("1. Create a new account\n");

    printf("2. Delete an existing account\n");

    printf("3. Add money to an existing account\n");

    printf("4. Withdraw money from an existing account\n");

    printf("5. Display all accounts\n");

    printf("6. Display all accounts with balance less than Rs 100\n");

    int n;

    scanf("%d",&n);

    if(n==1){

        printf("Enter the account type (0 for Savings, 1 for Current): ");

        int account_type;

        scanf("%d",&account_type);

        printf("Enter the name of the account holder: ");

        char name[50];

        scanf("%s",name);

        printf("Enter the initial balance: ");

        float balance;

        scanf("%f",&balance);

        insert(account_type==0?SAVINGS:CURRENT,name,balance);

    }

    else if(n==2){

        printf("Enter the account number: ");

        int account_number;

        scanf("%d",&account_number);

        printf("Enter the account type (0 for Savings, 1 for Current): ");

        int account_type;

        scanf("%d",&account_type);

        printf("Enter the name of the account holder: ");

        char name[50];

        scanf("%s",name);

        delete(account_number,account_type==0?SAVINGS:CURRENT,name);

    }

    else if(n==3){

        printf("Enter the account number: ");

        int account_number;

        scanf("%d",&account_number);

        printf("Enter the amount to be added: ");

        float amount;

        scanf("%f",&amount);

        add_money(account_number,amount);

    }

    else if(n==4){

        printf("Enter the account number: ");

        int account_number;

        scanf("%d",&account_number);

        printf("Enter the amount to be withdrawn: ");

        float amount;

        scanf("%f",&amount);

        withdraw(account_number,amount);

    }

    else if(n==5){

        display();

    }

    else if(n==6){

        lowBalaceAccounts();

    }

    else{

        printf("THANK YOU FOR USING OUR BANKKK! HOPE WE NEVER SCAM YOU :p\n");

     return 0;

    }

    }

  

  return 0;

  }

```

  
  
  

# Beautiful Colors

  

## I/O Style -

- For the input the user is required to input the number of colours and will be asked to input that many numbers.

  

## Functions Used -

 ### insertNode -

   - It takes the linkedlist head as the pointer and takes another integer as the input, and adds it into the linkedlist.

 ### remove duplicates -

- We iterate through the linkedlist and check whether the next block has the same color, if found we remove the duplicate.

  ### sort

  - Sorts through the linked list using bubblesort algorithm.

 ### printinz

 - We use this to print the linkedlist iterating through each element in the manner asked in the pdf.

  
  

  ## Code -

  ```c

#include <stdio.h>

#include <stdlib.h>

  

typedef struct node {

    int color;

    struct node* next;

} Linkedlist;

  

Linkedlist* newNode(int color) {

    Linkedlist* node = (Linkedlist*) malloc(sizeof(Linkedlist));

                node->color = color;

            node->next = NULL;

    return node;

}

  

void insertNode(Linkedlist** head, int color) {

    Linkedlist* node = newNode(color);

            if (*head == NULL) {

                *head = node;

            return;

    }

    Linkedlist* current = *head;

        while (current->next != NULL) {

            current = current->next;

        }

    current->next = node;

}

void sort(Linkedlist** head) {

    Linkedlist* current = *head;

    Linkedlist* index = NULL;

    int temp;

    if (*head == NULL) {

        return;

    }

    else {

        while (current != NULL) {

            index = current->next;

            while (index != NULL) {

                if (current->color > index->color) {

                    temp = current->color;

                    current->color = index->color;

                    index->color = temp;

                }

                index = index->next;

            }

            current = current->next;

        }

    }

}

  

Linkedlist* removeDuplicates(Linkedlist* head) {

    Linkedlist* current = head;

    while (current != NULL && current->next != NULL) {

                  if (current->color == current->next->color) {

                        Linkedlist* temp = current->next;

                current->next = current->next->next;

                    free(temp);

        }

    else {

        current = current->next;

        }

    }

return head;

}

  

void printinz(Linkedlist* head) {

    Linkedlist* current = head;

            while (current != NULL) {

                     if (current->next != NULL) {

                        printf("%d->", current->color);

                         }

        else {

        printf("%d ", current->color);

        }

    current = current->next;

    }

    printf("\n");

}

  

int main() {

    int n;

    printf("Enter the number of colors in the list: ");

    scanf("%d", &n);

    Linkedlist* head = NULL;

    printf("Enter the colors: ");

    for (int i = 0; i < n; i++) {

        int color;

        scanf("%d", &color);

        insertNode(&head, color);

    }

    sort(&head);

    head = removeDuplicates(head);

    printf("Modified linked list: ");

    printinz(head);

    return 0;

}

```