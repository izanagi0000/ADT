#include <iostream>
using namespace std;

struct ElmList {
    int info;
    ElmList* next;
};

struct List {
    ElmList* first;
};

void createList(List &L);
ElmList* createNewElement(int value);
void insertFirst(List &L, ElmList* P);
void insertLast(List &L, ElmList* P);
void insertAfter(ElmList* Prec, ElmList* P);
void printList(List L);
ElmList* searchElement(List L, int key);
void deleteFirst(List &L);

void createList(List &L) {
    L.first = nullptr;
}

ElmList* createNewElement(int value) {
    ElmList* P = new ElmList;
    P->info = value;
    P->next = nullptr;
    return P;
}

void insertFirst(List &L, ElmList* P) {
    P->next = L.first;   // connect P to the old first node
    L.first = P;         // make P the new first node
}

void insertLast(List &L, ElmList* P) {
    if (L.first == nullptr) {
        L.first = P;
    }
    else {
        ElmList* Q = L.first;
        while (Q->next != nullptr) {
            Q = Q->next;
        }
        Q->next = P;
    }
}

void insertAfter(ElmList* Prec, ElmList* P) {
    P->next = Prec->next;
    Prec->next = P;
}

void printList(List L) {
    ElmList* P = L.first;
    while (P != nullptr) {
        cout << P->info << " ";
        P = P->next;
    }
    cout << endl;
}

ElmList* searchElement(List L, int key) {
    ElmList* P = L.first;
    while (P != nullptr) {
        if (P->info == key) {
            return P;
        }
        P = P->next;
    }
    return nullptr;
}

void deleteFirst(List &L) {
    if (L.first == nullptr) {
        cout << "List is empty" << endl;
        return;
    }
    ElmList* P = L.first;
    L.first = P->next;   // move first to the second node
    P->next = nullptr;   // disconnect P
    delete P;            // deallocate P
}

int main() {
    List L;
    createList(L);

    insertLast(L, createNewElement(10));
    insertLast(L, createNewElement(20));
    insertLast(L, createNewElement(30));
    printList(L);                       // 10 20 30

    insertFirst(L, createNewElement(5));
    printList(L);                       // 5 10 20 30

    ElmList* found = searchElement(L, 20);
    if (found != nullptr) {
        cout << "search 20 -> FOUND" << endl;
    } else {
        cout << "search 20 -> NOT FOUND" << endl;
    }

    deleteFirst(L);
    printList(L);                       // 10 20 30

    // bersihkan sisa node supaya tidak ada memory leak
    while (L.first != nullptr) {
        deleteFirst(L);
    }
    return 0;
}