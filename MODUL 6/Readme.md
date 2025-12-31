# <h1 align="center">Laporan Praktikum Modul Singly Linked List</h1>
<p align="center">Adhe Yudho Satrio</p>

## Dasar Teori

Doubly Linked List merupakan struktur data yang setiap elemennya memiliki dua buah pointer, yaitu satu pointer yang mengarah ke node sebelumnya (prev) dan satu pointer lain yang menunjuk ke node berikutnya (next).


### 1. [soal]
doublelylist.h
```
#ifndef DOUBLYLIST_H
#define DOUBLYLIST_H

#include <string>
using namespace std;

#define Nil NULL

struct Kendaraan {
    string nopol;
    string warna;
    int thnBuat;
};

typedef Kendaraan infotype;
typedef struct ElmList *address;

struct ElmList {
    infotype info;
    address next;
    address prev;
};

struct List {
    address first;
    address last;
};

/* PROTOTIPE */
void createList(List &L);
address alokasi(infotype x);
void dealokasi(address &P);

void insertLast(List &L, address P);
void printInfo(List L);

address findElm(List L, string nopol);

void deleteFirst(List &L, address &P);
void deleteLast(List &L, address &P);
void deleteAfter(address Prec, address &P);

#endif

```
DOublylist.cpp
```
#include "Doublylist.h"
#include <iostream>
using namespace std;

void createList(List &L) {
    L.first = Nil;
    L.last = Nil;
}

address alokasi(infotype x) {
    address P = new ElmList;
    P->info = x;
    P->next = Nil;
    P->prev = Nil;
    return P;
}

void dealokasi(address &P) {
    delete P;
    P = Nil;
}

void insertLast(List &L, address P) {
    if (L.first == Nil) {
        L.first = P;
        L.last = P;
    } else {
        P->prev = L.last;
        L.last->next = P;
        L.last = P;
    }
}

void printInfo(List L) {
    address P = L.first;
    if (P == Nil) {
        cout << "List kosong" << endl;
        return;
    }

    while (P != Nil) {
        cout << P->info.nopol << " | "
             << P->info.warna << " | "
             << P->info.thnBuat << endl;
        P = P->next;
    }
}

address findElm(List L, string nopol) {
    address P = L.first;
    while (P != Nil) {
        if (P->info.nopol == nopol) {
            return P;
        }
        P = P->next;
    }
    return Nil;
}

void deleteFirst(List &L, address &P) {
    if (L.first == Nil) {
        P = Nil;
        return;
    }
    P = L.first;
    if (L.first == L.last) { // satu elemen
        L.first = L.last = Nil;
    } else {
        L.first = P->next;
        L.first->prev = Nil;
    }
    P->next = Nil;
    P->prev = Nil;
}

void deleteLast(List &L, address &P) {
    if (L.first == Nil) {
        P = Nil;
        return;
    }
    P = L.last;
    if (L.first == L.last) {
        L.first = L.last = Nil;
    } else {
        L.last = P->prev;
        L.last->next = Nil;
    }
    P->next = Nil;
    P->prev = Nil;
}

void deleteAfter(address Prec, address &P) {
    if (Prec == Nil || Prec->next == Nil) {
        P = Nil;
        return;
    }

    P = Prec->next;
    Prec->next = P->next;

    if (P->next != Nil)
        P->next->prev = Prec;

    P->next = Nil;
    P->prev = Nil;
}
```
main.cpp
```
#include <iostream>
#include "Doublylist.h"
using namespace std;

int main() {
    List L;
    createList(L);

    // insert data
    insertLast(L, alokasi({"D001", "Hitam", 2010}));
    insertLast(L, alokasi({"D002", "Merah", 2015}));
    insertLast(L, alokasi({"D003", "Putih", 2012}));
    insertLast(L, alokasi({"D004", "Biru", 2018}));

    cout << "Data Kendaraan:" << endl;
    printInfo(L);

    cout << "\nCari Nopol D001:" << endl;
    address P = findElm(L, "D001");
    if (P != Nil) {
        cout << "Ditemukan: " << P->info.nopol << ", " << P->info.warna 
             << ", " << P->info.thnBuat << endl;
    } else {
        cout << "Tidak ditemukan" << endl;
    }

    cout << "\nHapus D003:" << endl;
    address del;
    address Prec = L.first;
    while (Prec != Nil && Prec->next != Nil && Prec->next->info.nopol != "D003")
        Prec = Prec->next;

    if (Prec != Nil && Prec->next->info.nopol == "D003") {
        deleteAfter(Prec, del);
        dealokasi(del);
    }

    printInfo(L);

    return 0;
}
```

#### Output:
<img width="564" height="288" alt="image" src="https://github.com/user-attachments/assets/a7650317-9613-4d55-99b7-4ea38d198ed5" />



Dibandingkan singly linked list, doubly linked list memiliki kelebihan karena memungkinkan penelusuran data dari dua arah. Kemampuan ini menjadikan proses penyisipan dan penghapusan data lebih efektif, terutama pada operasi yang memerlukan referensi ke elemen sebelumnya.

#### Full code Screenshot:
<img width="727" height="779" alt="image" src="https://github.com/user-attachments/assets/66403e3f-6ed4-4c22-931d-84b66db70250" />
<img width="608" height="821" alt="image" src="https://github.com/user-attachments/assets/2d97d538-e014-4d53-a1ca-2e889ad6ecd5" />
<img width="450" height="849" alt="image" src="https://github.com/user-attachments/assets/1c676dfe-d4e2-4d59-8eb6-227677a2024c" />



## Kesimpulan
Doubly Linked List menawarkan kemampuan yang lebih unggul dibandingkan Singly Linked List ketika diperlukan akses data dari dua arah, walaupun konsekuensinya adalah penggunaan memori yang lebih besar akibat adanya pointer tambahan. Struktur data ini sangat cocok digunakan pada aplikasi yang sering melakukan operasi penyisipan dan penghapusan elemen di berbagai posisi dalam list.

## Referensi
Mukharil Bachtiar, A. (2012). And 4-Dynamic Array And Linked List (pelengkap).



