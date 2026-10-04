 Railway-Booking-System
Railway Ticket Booking and Cancellation System is a simple C++ application developed using a Linked List  data structure. The system allows users to book railway tickets, view booked tickets , and cancel tickets using a simple menu-driven switch-case interface.



code off application



#include <iostream>
using namespace std;

struct Node {
    int pnr;
    string name, from, to;
    Node *next;
};

Node *head = NULL;
int pnr = 1001;

void book() {
    Node *n = new Node;

    cin.ignore();

    cout << "Enter Passenger Name: ";
    getline(cin, n->name);

    cout << "Enter From: ";
    cin >> n->from;

    cout << "Enter To: ";
    cin >> n->to;

    n->pnr = pnr++;
    n->next = head;
    head = n;

    cout << "\nTicket Booked Successfully!";
    cout << "\nPNR = " << n->pnr << endl;
}

void display() {
    Node *t = head;

    if (t == NULL) {
        cout << "No Tickets\n";
        return;
    }

    while (t != NULL) {
        cout << "\nPNR: " << t->pnr;
        cout << "\nName: " << t->name;
        cout << "\nPath: " << t->from << " -> " << t->to << endl;
        t = t->next;
    }
}

void cancel() {
    int x;
    cout << "Enter PNR: ";
    cin >> x;

    Node *t = head, *p = NULL;

    while (t != NULL && t->pnr != x) {
        p = t;
        t = t->next;
    }

    if (t == NULL) {
        cout << "Ticket Not Found\n";
        return;
    }

    if (p == NULL)
        head = t->next;
    else
        p->next = t->next;

    delete t;
    cout << "Ticket Cancelled Successfully\n";
}

int main()
   {
    int ch;

    do {
        cout << "\n--- Railway Booking System ---";
        cout << "\n1. Book Ticket";
        cout << "\n2. Display Tickets";
        cout << "\n3. Cancel Ticket";
        cout << "\n4. Exit";
        cout << "\nEnter Choice: ";
        cin >> ch;

        switch (ch) {
            case 1: book(); break;
            case 2: display(); break;
            case 3: cancel(); break;
            case 4: cout << "Thank You!"; break;
            default: cout << "Invalid Choice!";
        }

    } while (ch != 4);

    return 0;
}
