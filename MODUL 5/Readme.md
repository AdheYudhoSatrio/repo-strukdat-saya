# <h1 align="center">Laporan Praktikum Modul Singly Linked List</h1>
<p align="center">Adhe Yudho Satrio</p>

## Dasar Teori

searching pada linked list adalah proses pencarian nilai tertentu dengan mengunjungi setiap node dalam linked list satu per satu, mulai dari node awal (head) sampai node terakhir atau sampai nilai yang dicari ditemukan. Searching dalam linked list biasanya dilakukan dengan metode linear search atau sequential search, di mana setiap node diperiksa nilainya dan dibandingkan dengan nilai yang dicari. Proses ini berhenti jika node dengan nilai yang dicari ditemukan atau jika seluruh linked list telah dikunjungi tanpa hasil (nilai tidak ditemukan). Karena linked list berupa rantai node yang saling terhubung, pencarian harus dilakukan secara berurutan dari awal ke akhir. Kompleksitas waktu operasi searching dalam linked list adalah O(N), dengan N adalah jumlah node dalam list, karena dalam kasus terburuk harus menelusuri seluruh node. Dengan adanya operasi searching ini, operasi dasar lainnya seperti insert after, delete after, dan update menjadi lebih mudah dilakukan karena lokasi node target bisa ditentukan terlebih dahulu.


### 1. ADT SEARCHING
```
#ifndef SINGLYLIST_H
#define SINGLYLIST_H

#include <iostream>
using namespace std;

#define Nil NULL

typedef int infotype;
typedef struct ElmList *address;

struct ElmList {
    infotype info;
    address next;
};

struct List {
    address first;
};

// ==== FUNGSI & PROSEDUR ====
void createList(List &L);
address alokasi(infotype x);
void dealokasi(address &P);
void insertFirst(List &L, address P);
void printInfo(List L);
address findElm(List L, infotype x);
int sumInfo(List L);

#endif

```
```
#include "Singlylist.h"

// Membuat list kosong
void createList(List &L) {
    L.first = Nil;
}

// Alokasi node baru
address alokasi(infotype x) {
    address P = new ElmList;
    P->info = x;
    P->next = Nil;
    return P;
}

// Dealokasi node
void dealokasi(address &P) {
    delete P;
    P = Nil;
}

// Insert di awal list
void insertFirst(List &L, address P) {
    if (L.first == Nil) {
        L.first = P;
    } else {
        P->next = L.first;
        L.first = P;
    }
}

// Menampilkan isi list
void printInfo(List L) {
    address P = L.first;
    cout << "Isi List : ";
    while (P != Nil) {
        cout << P->info << " ";
        P = P->next;
    }
    cout << endl;
}

// Mencari elemen berdasarkan nilai info
address findElm(List L, infotype x) {
    address P = L.first;
    while (P != Nil) {
        if (P->info == x) {
            return P;
        }
        P = P->next;
    }
    return Nil;
}

// Menghitung total semua nilai info dalam list
int sumInfo(List L) {
    int total = 0;
    address P = L.first;
    while (P != Nil) {
        total += P->info;
        P = P->next;
    }
    return total;
}
```
```
#include "Singlylist.h"

int main() {
    List L;
    address P1, P2, P3, P4, P5;

    createList(L);

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
    cout << endl;

    address hasil = findElm(L, 8);
    if (hasil != Nil) {
        cout << "Elemen dengan info 8 ditemukan pada alamat: " << hasil << endl;
    } else {
        cout << "Elemen dengan info 8 tidak ditemukan!" << endl;
    }
    cout << endl;

    cout << "Total = " << sumInfo(L) << endl;

    return 0;
}
```
Kode di atas merupakan program dalam bahasa C++ yang digunakan untuk mengelola data buah menggunakan struktur data Singly Linked List (List Berkait Tunggal). Struktur data ini menyimpan data secara dinamis di dalam node-node yang saling terhubung menggunakan pointer. Setiap node berisi tiga informasi utama, yaitu: 1.Nama buah (tipe string) 2.Jumlah buah (tipe int) 3.Harga buah (tipe float) dan juga memiliki pointer next yang menunjuk ke node berikutnya.

#### Output:
<img width="583" height="143" alt="image" src="https://github.com/user-attachments/assets/2d079bc2-da5b-451c-b1fa-563eb6cf4785" />


Kode diatas adalah program yang dapat digunakan untuk menghitung nilai rata rata dari data mahasiswa maks 10,
dengan cara perulangan dan array yang menyimpan nim, nama, uts, uas, dan nilai akhir dengan ketentuan 0.3uts+0.4uas+0.3*tugas.

#### Full code Screenshot:
<img width="720" height="755" alt="image" src="https://github.com/user-attachments/assets/ffdef578-f9df-4aa2-80c2-0a406b07855f" />
<img width="475" height="855" alt="image" src="https://github.com/user-attachments/assets/60c8b4f3-3b4c-4582-a383-8dfea8d50b25" />
<img width="393" height="595" alt="image" src="https://github.com/user-attachments/assets/44f63404-cc85-40b8-b923-68fcbc6da7e2" />


## Kesimpulan
Pada modul ini mahasiswa mempelajari cara kerja Singly Linked List, yaitu struktur data dinamis yang terdiri dari node-node berisi data dan pointer yang saling terhubung. Melalui praktikum ini, mahasiswa memahami operasi dasar seperti pembuatan list, penambahan, penghapusan, pencarian, dan pembaruan data, serta cara mengelola memori dengan pointer. Modul ini menegaskan bahwa Singly Linked List merupakan dasar penting dalam struktur data dinamis yang memungkinkan pengolahan data secara fleksibel dan efisien.

## Referensi
(https://www.trivusi.web.id/2022/07/struktur-data-linked-list.html)
https://daismabali.com/artikel_detail/53/1/Metode-Searching-dalam-Struktur-Data-dan-Implementasi-Pemrogramannya.html


