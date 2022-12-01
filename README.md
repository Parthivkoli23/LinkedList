#include<iostream>
using namespace std;

struct Node
{
    int data;
    Node *next;
};

class linkedlist

{
    Node *start = NULL;


    public:
    void create();
    void insert_beg();
    void insert_position();
    void insert_end();
    void delete_beg();
    void delete_position();
    void delete_end();
    void display();
    void search();
    int count_nodes();

};

void linkedlist::create()
{
        Node *n;
        int value; 
        n = new Node();
        n->next = NULL;
        cout << "Enter element: ";
        cin >> value;
        n->data = value;
        if(start == NULL)
            start = n;
        else
		{
            Node *ptr;
            ptr = start;
            while(ptr->next != NULL)
                ptr = ptr->next;
            ptr->next = n;
        }
    }


void linkedlist::insert_beg()
{
	    Node *n;
	    int value;
	    n = new Node();
	    cout << "Enter value: ";
	    cin >> value;
	    n->data=value;
	    if(start==NULL)
		{
		    n->next=NULL;
		    start=n;	
		    cout << "\nValue is inserted in beginning." << endl;
	    }
	    else{
		    n->next=start;
		    start=n;
		    cout << "\nValue is inserted in beginning." << endl;
	    }
        display();
    }

void linkedlist::insert_position()
{
        Node *newnode,*temp,*ptr;
	    int value,position;
	    newnode = new Node();
	    
	cout << "\nEnter position: ";
		cin >> position;
    cout << "\nEnter value: ";
    cin >> value;
		newnode->data=value;


		temp=start;
		for(int i=0;i<position-1;i++)
		{
			ptr=temp;
			if(ptr==NULL)
			{
				cout << "\nValue can't be inserted.....Please insert accurate position";
				return;		
			}	
			temp=temp->next;
		}
		newnode->next=temp;
		ptr->next=newnode;
		cout << "\nValue inserted at: " << position << endl;
        display();
    }

void linkedlist::insert_end()
{
	    Node *newnode,*temp;
	    int value;
	    newnode = new Node();
	    
		cout << "\nEnter value: ";
		cin >> value;
		newnode->data=value;
		if(start==NULL)
		{
			newnode->next=NULL;
			start=newnode;
			cout<<"\nValue is inserted at last." << endl;
		}
		else
		{
			temp=start;
			while(temp->next!=NULL)
				temp=temp->next;
			newnode->next=NULL;
			temp->next=newnode;
			cout<<"\nValue is inserted at last." << endl;
		}
        display();
    }

    void linkedlist::delete_beg()
    {
	    Node *temp;
	    if(start==NULL)
		{
		    cout << "\nList empty." << endl;
		    return;
	    }
	    else
		{
		    temp=start;
		    start=temp->next;
		    free(temp);
		    cout << "\nNode deleted from beginning" << endl;
        }
        display();
    }

    void linkedlist::delete_position()
    {
	    Node *temp,*ptr;
	    int position;
	    if(start==NULL)
		{
		    cout << "\nList empty." << endl;
		    return;
	    }
	    else
		{
		    temp=start;
		    cout << "\nEnter position: ";
		    cin >> position;
		
		    for(int i=0;i<position-1;i++)
			{
			    ptr=temp;
			    temp=temp->next;
			    if(ptr==NULL)
				{
				    cout<<"\nCAN'T DELETE." << endl;
				    return;
			    }
		    }
		    ptr->next=temp->next;
		    free(temp);
		    cout<<"\nNode deleted at position " << position << endl;
	    }
        display();
    }

    void linkedlist::delete_end()
    {
       Node *temp,*ptr;
	    if(start==NULL)
		{
		    cout << "\nList Empty." << endl;
		    return;
	    }
	    else if(start->next==NULL)
		{
		    start==NULL;
		    free(start);
		    cout << "\nNode deleted." << endl;
		    return;
	    }
	    else
		{
		    temp=start;
		    while(temp->next!=NULL)
			{
			    ptr=temp;
			    temp=temp->next;
		    }
		    ptr->next=NULL;
		    free(temp);
		    cout << "\nNode deleted from last." << endl;
	    }
        display();
    }

void linkedlist::display()
	{
        Node *temp;
        temp = start;
        while(temp != NULL)
		{
            cout << temp->data << " ";
            temp = temp->next;
        }
    }

void linkedlist::search()
{
        Node *temp;
	    int value,flag=0;
	    if(start==NULL)
		    cout << "\nList is empty." << endl;
	    else
		{
		    temp=start;
		    cout << "\nEnter value: ";
		    cin >> value;
		    for(int i=0;temp!=NULL;i++)
			{
			    if(temp->data==value)
				{
				    cout << "\nValue is found at position " << i+1 << endl;
				    flag=0;
				    return;
			    }
			    else
				    flag=1;
			    temp=temp->next;
		    }
		    if(flag==1)
			    cout << "\nValue not found." << endl;
	    }
        display();   
    }
int linkedlist::count_nodes()
    {
      Node* temp = start;
     int cnt = 0;
      while(temp != NULL)
	  {
        cnt++;
        temp = temp->next;
      }
      return cnt;  
    } 

int main()
{
    int n;
    linkedlist list;
    cout<< "Enter the Number of Elements : ";
    cin >> n;
    for(int i=0; i<n; i++)
    list.create();
    list.display();
    int all=0,insr,del;
	while(all!=6)

	{
		cout<< "\n\n*****MENU*****";

		cout<< "\n 1)Insert \n 2)Delete \n 3)Search \n 4)Display \n 5)Count the nodes \n 6)Exit \n";
		cout<<"ENTER THE CHOICE : ";
		cin>>all;

		switch(all)
		{

			case 1:
			cout<<"\n 1) Insert at the beginning.";
			cout<<"\n 2) Insert at the given position.";
			cout<<"\n 3) Insert at the end.";
			
            cout<<"\n Enter the option to Insert : ";
			cin>>insr;

			switch(insr)

			{
				case 1:
				list.insert_beg();
				break;
                
				case 2:
				list.insert_position();
				break;

				case 3:
				list.insert_end();

				

			}
            break;

			case 2:
			cout<<"\n 1) Delete at the beginning.";
			cout<<"\n 2) Delete at given position.";
			cout<<"\n 3) Delete in last.";

			cout<<"\n Enter the option to Delete : ";
            
			cin>>del;

			switch(del)

			{
				case 1:
				list.delete_beg();
				break;
                
				case 2:
				list.delete_position();
				break;

				case 3:
				list.delete_end();

			}
            break;

			case 3:
			list.search();
			break;    


			case 4:
			list.display();
			break;
            

			case 5:
			cout<<"Total no. of Nodes : "<<list.count_nodes();
			break;
			

			case 6:
			exit(0);
			break;

			

			default:
			cout<<"\n Enter valid choice.";
			break;
		}
	}
}
