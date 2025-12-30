# <h1 align="center">Laporan Praktikum Modul Singly Linked List</h1>
<p align="center">Adhe Yudho Satrio</p>

## Dasar Teori

Linked List adalah koleksi elemen data linear, di mana elemen-elemennya tidak harus disimpan secara berdekatan (kontigu) di memori fisik.
Keterkaitan antara satu elemen dengan elemen berikutnya diwujudkan melalui pointer (tautan atau referensi) yang disimpan di dalam setiap elemen. 
Elemen-elemen ini sering disebut node (simpul) (Aho, Hopcroft, & Ullman, 1983; Knuth, 1997).


### 1. [Soal]

```singlylist.h
#ifndef SINGLYLIST_H
#define SINGLYLIST_H
#define Nil NULL

#include <iostream>
using namespace std;

typedef int infotype;

struct Elmlist;  
typedef Elmlist* address; 

struct Elmlist {
    infotype data;
    address next;
};

struct List {
    address first;
};


void CreateList(List &L); 
address alokasi(infotype x);
void dealokasi(address P);
void printInfo(List L);
void insertFirst(List &L, address P);

#endif
```
singlylist,cpp
```

#include "Singlylist.h"
#include <iostream>
using namespace std;

void CreateList(List &L) {

    L.first = Nil;
}

address alokasi(infotype x) { 
    address NewNode = new Elmlist ; 
    NewNode->data = x;
    NewNode->next = Nil;
    return NewNode;
}

void dealokasi(address p) {
    delete p;
}

void printInfo(List L) {
    address P = L.first;
    if (P == Nil) {
        cout << "List kosong" << endl;
    } else {
        cout << "Isi List: ";
        while (P != Nil) {
            cout << P->data << " ";
            P = P->next;
        }
        cout << endl;
    }
}

void insertFirst(List &L, address p) {
    p->next = L.first;
    L.first = p;
}
```
main.cpp
```
#include "Singlylist.h"

int main() {
    List L;
    address P1, P2, P3, P4, P5 = Nil;
    CreateList(L);

    P1 = alokasi(2);
    insertFirst(L, P1);

    P2 = alokasi(0);
    insertFirst(L, P2);

    P3 = alokasi(8);
    insertFirst(L, P3);

    P4 = alokasi(12);
    insertFirst(L, P4);

    P5 = alokasi(9);
    insertFirst(L, P5);

    printInfo(L);
    return 0;
}
```
#### Output:
<img width="566" height="71" alt="image" src="https://github.com/user-attachments/assets/546ae92c-1b0d-4a47-9357-c65cad65435f" />

Kode diatas adalah program yang dapat digunakan untuk menghitung nilai rata rata dari data mahasiswa maks 10,
dengan cara perulangan dan array yang menyimpan nim, nama, uts, uas, dan nilai akhir dengan ketentuan 0.3uts+0.4uas+0.3*tugas.

#### Full code Screenshot:
<img width="371" height="502" alt="image" src="https://github.com/user-attachments/assets/f476337b-23cd-4701-b25b-07811db48008" />
<img width="417" height="769" alt="image" src="https://github.com/user-attachments/assets/cdff483f-fc83-4ce4-ab91-be462486830a" />
<img width="369" height="576" alt="image" src="https://github.com/user-attachments/assets/cbeb1709-ddec-4f62-b394-2a2557cac3c2" />







### 2. [Soal]

```list.h
//header guar digunakan untuk mencegah file header yang sama
//di-include lebih dari sekali dalam satu program
#ifndef LIST_H
#define LIST_H
#define Nil NULL

#include<iostream>
using namespace std;

//deklarasi isi data struct mahasiswa
struct mahasiswa {
    string nama;
    string nim;
    int umur;
};

typedef mahasiswa dataMahasiswa; //Memberikan nama alias dataMahasiswa untuk struct mahasiswa

typedef struct node *address; //Mendefinisikan alias address sebagai pointer ke struct node

struct node{ //node untuk isi dari linked listnya,isi setiap node adalah data & pointer new
    dataMahasiswa isidata;
    address next;
};

struct linkedlist{ //ini linked list nya
    address first;
};

//semua function & prosedur yang akan dipakai
bool isEmpty(linkedlist List);
void createList(linkedlist &List);
address alokasi(string nama, string nim, int umur);
void dealokasi(address &node);
void printList(linkedlist List);
void insertFirst(linkedlist &List, address nodeBaru);
void insertAfter(linkedlist &List, address nodeBaru, address Prev);
void insertLast(linkedlist &List, address nodeBaru);

void delFirst(linkedlist &List);
void delLast(linkedlist &List);
void delAfter(linkedlist &List, address nodeHapus, address nodePrev);
int nbList(linkedlist List);
void deleteList(linkedlist &List);

#endif

```
list.cpp
```
#include "list.h"

//I.S = Initial State / kondisi awal
//F.S = Final State / kondisi akhir

//fungsi untuk cek apakah list kosong atau tidak
bool isEmpty(linkedlist List) {
    if(List.first == Nil){
        return true; 
    } else {
        return false;
    }
}

//pembuatan linked list kosong
void createList(linkedlist &List) {
    /* I.S. sembarang
       F.S. terbentuk list kosong */
    List.first = Nil;
}

//pembuatan node baru dengan menerapkan manajemen memori
address alokasi(string nama, string nim, int umur) { 
    /* I.S. sembarang
       F.S. mengembalikan alamat node baru dengan isidata = sesuai parameter dan next = Nil */
    address nodeBaru = new node; 
    nodeBaru->isidata.nama = nama;
    nodeBaru->isidata.nim = nim; 
    nodeBaru->isidata.umur = umur;
    nodeBaru->next = Nil;
    return nodeBaru;
}

//penghapusan node dengan menerapkan manajemen memori
void dealokasi(address &node) {
    /* I.S. P terdefinisi
       F.S. memori yang digunakan node dikembalikan ke sistem */
    node->next = Nil;
    delete node;
}

//prosedur-prosedur untuk insert / menambahkan node baru kedalam list
void insertFirst(linkedlist &List, address nodeBaru) {
    /* I.S. sembarang, P sudah dialokasikan
       F.S. menempatkan elemen list (node) pada awal list */
    nodeBaru->next = List.first; 
    List.first = nodeBaru;
}

void insertAfter(linkedlist &List, address nodeBaru, address Prev) {
    /* I.S. sembarang, nodeBaru dan Prev alamat salah satu elemen list (node)
       F.S. menempatkan elemen (node) sesudah elemen node Prev */
    if (Prev != Nil) {
        nodeBaru->next = Prev->next;
        Prev->next = nodeBaru;
    } else {
        cout << "Node sebelumnya tidak valid!" << endl;
    }
}

void insertLast(linkedlist &List, address nodeBaru) {
    /* I.S. sembarang, nodeBaru sudah dialokasikan
       F.S. menempatkan elemen nodeBaru pada akhir list */
    if (isEmpty(List)) {
        List.first = nodeBaru;
    } else {
        address nodeBantu = List.first;
        while (nodeBantu->next != Nil) {
            nodeBantu = nodeBantu->next;
        }
        nodeBantu->next = nodeBaru;
    }
}

//prosedur-prosedur untuk delete / menghapus node yang ada didalam list
void delFirst(linkedlist &List){
    /* I.S. list tidak kosong
    F.S. node pertama di list terhapus*/
    address nodeHapus;
    if (isEmpty(List) == false) {
        nodeHapus = List.first;
        List.first = List.first->next;
        nodeHapus->next = Nil;
        dealokasi(nodeHapus);
    } else {
        cout << "List kosong!" << endl;
    }
}

void delLast(linkedlist &List){
    /* I.S. list tidak kosong
    F.S. node terakhir di list terhapus */
    address nodeHapus, nodePrev;
    if(isEmpty(List) == false){
        nodeHapus = List.first;
        if(nodeHapus->next == Nil){
            List.first->next = Nil;
            dealokasi(nodeHapus);
        } else { 
            while(nodeHapus->next != Nil){
                nodePrev = nodeHapus; 
                nodeHapus = nodeHapus->next;
            }
            nodePrev->next = Nil; 
            dealokasi(nodeHapus);
        }
    } else {
        cout << "list kosong" << endl;
    }
}

void delAfter(linkedlist &List, address nodeHapus, address nodePrev){
    /* I.S. list tidak kosng, Prev alamat salah satu elemen list
    F.S. nodeBantu adalah alamat dari Prev→next, menghapus Prev→next dari list */
    if(isEmpty(List) == true){
        cout << "List kosong!" << endl;
    } else { //jika list tidak kosong
        if (nodePrev != Nil && nodePrev->next != Nil) { 
            nodeHapus = nodePrev->next;       
            nodePrev->next = nodeHapus->next;  
            nodeHapus->next = Nil;         
            dealokasi(nodeHapus);
        } else {
            cout << "Node sebelumnya (prev) tidak valid!" << endl;
        }
    }
}

//prosedur untuk menampilkan isi list
void printList(linkedlist List) {
    /* I.S. list mungkin kosong
       F.S. jika list tidak kosong menampilkan semua info yang ada pada list */
    if (isEmpty(List)) {
        cout << "List kosong." << endl;
    } else {
        address nodeBantu = List.first;
        while (nodeBantu != Nil) { 
            cout << "Nama : " << nodeBantu->isidata.nama << ", NIM : " << nodeBantu->isidata.nim << ", Usia : " << nodeBantu->isidata.umur << endl;
            nodeBantu = nodeBantu->next;
        }
    }
}

//function untuk menampilkan jumlah node didalam list
int nbList(linkedlist List) {
    /* I.S. list sudah ada
       F.S. menampilkan jumlah node didalam list*/
    int count = 0;
    address nodeBantu = List.first;
    while (nodeBantu != Nil) {
        count++;
        nodeBantu = nodeBantu->next; 
    }
    return count;
}

//prosedur untuk menghapus list (menghapus semua node didalam list)
void deleteList(linkedlist &List){
    /* I.S. list sudah ada
       F.S. menghapus semua node didalam list*/
    address nodeBantu, nodeHapus;
    nodeBantu = List.first;
    while(nodeBantu != Nil){
        nodeHapus = nodeBantu;
        nodeBantu = nodeBantu->next;
        dealokasi(nodeHapus); 
    }
    List.first = Nil; 
    cout << "List sudah terhapus!" << endl;
}
```
main.cpp
```
#include "list.h"

int main(){
    linkedlist List;
    address nodeA, nodeB, nodeC, nodeD, nodeE = Nil;
    createList(List);

    dataMahasiswa mhs;

    nodeA = alokasi("Dhimas", "2311102151", 20);
    nodeB = alokasi("Arvin", "2211110014", 21);
    nodeC = alokasi("Rizal", "2311110029", 20);
    nodeD = alokasi("Satrio", "2211102173", 21);
    nodeE = alokasi("Joshua", "2311102133", 21);

    insertFirst(List, nodeA);
    insertLast(List, nodeB);
    insertAfter(List, nodeC, nodeA);
    insertAfter(List, nodeD, nodeC);
    insertLast(List, nodeE);

    cout << "--- ISI LIST SETELAH DILAKUKAN INSERT ---" << endl;
    printList(List);
    cout << "jumlah node : " << nbList(List) << endl;
    cout << endl;

    delFirst(List);
    delLast(List);
    delAfter(List, nodeD, nodeC);

    cout << "--- ISI LIST SETELAH DILAKUKAN DELETE ---" << endl;
    printList(List);
    cout << "jumlah node : " << nbList(List) << endl;
    cout << endl;

    deleteList(List);
    cout << "--- ISI LIST SETELAH DILAKUKAN HAPUS LIST ---" << endl;
    printList(List);
    cout << "jumlah node : " << nbList(List) << endl;
    cout << endl;

    return 0;
}
```
#### Output:
<img width="573" height="145" alt="image" src="https://github.com/user-attachments/assets/74e5e53a-dd35-4fad-b913-640845efd80f" />





#### Full code Screenshot:
<img width="409" height="638" alt="image" src="https://github.com/user-attachments/assets/f2023fa3-1eab-4873-af70-cf9ec1fec7c1" />
<img width="597" height="903" alt="image" src="https://github.com/user-attachments/assets/740c3776-0693-4819-9a01-691fda897b73" />
<img width="565" height="719" alt="image" src="https://github.com/user-attachments/assets/b8fe24da-5d2c-4923-b57c-66769f36ce12" />







## Kesimpulan
Secara keseluruhan, modul dan praktikum Singly Linked List membahas bagaimana cara mengelola data secara dinamis dengan menggunakan node-node yang saling terhubung. Dalam materi ini, dijelaskan proses menambahkan, menghapus, serta mengolah atau menghitung data di dalam list secara terstruktur dan efisien.

## Referensi
Aho, A. V., Hopcroft, J. E., & Ullman, J. D. (1983). Data structures and algorithms. Addison-Wesley. Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (2009). Introduction to algorithms (3rd ed.). The MIT Press.



