# <h1 align="center">Laporan Praktikum Modul Singly Linked List</h1>
<p align="center">Adhe Yudho Satrio</p>

## Dasar Teori

Doubly Linked List merupakan struktur data yang setiap elemennya memiliki dua buah pointer, yaitu satu pointer yang mengarah ke node sebelumnya (prev) dan satu pointer lain yang menunjuk ke node berikutnya (next).


### 1. [soal]
stack.h
```
#ifndef STACK_H
#define STACK_H

#define MAX 50

struct Stack {
    int top;
    int data[MAX];
};

// Membuat stack kosong
void createStack(Stack &S);

// Mengecek apakah stack kosong
bool isEmpty(Stack S);

// Mengecek apakah stack penuh
bool isFull(Stack S);

// Menambah elemen (push)
void push(Stack &S, int x);

// Menghapus elemen (pop)
int pop(Stack &S);

// Mencetak isi stack
void printStack(Stack S);

#endif

```
stack.cpp
```
#include "Stack.h"
#include <iostream>
using namespace std;

void createStack(Stack &S) {
    S.top = -1;
}

bool isEmpty(Stack S) {
    return S.top == -1;
}

bool isFull(Stack S) {
    return S.top == MAX - 1;
}

void push(Stack &S, int x) {
    if (isFull(S)) {
        cout << "Stack penuh!" << endl;
    } else {
        S.top++;
        S.data[S.top] = x;
    }
}

int pop(Stack &S) {
    if (isEmpty(S)) {
        cout << "Stack kosong!" << endl;
        return -1;
    } else {
        int x = S.data[S.top];
        S.top--;
        return x;
    }
}

void printStack(Stack S) {
    if (isEmpty(S)) {
        cout << "Stack kosong!" << endl;
    } else {
        cout << "Isi stack: ";
        for (int i = S.top; i >= 0; i--) {
            cout << S.data[i] << " ";
        }
        cout << endl;
    }
}
```
main.cpp
```
#include <iostream>
#include "Stack.h"
using namespace std;

int main() {
    Stack S;
    createStack(S);

    push(S, 10);
    push(S, 20);
    push(S, 30);

    cout << "Setelah push 3 data:" << endl;
    printStack(S);

    cout << "Pop: " << pop(S) << endl;

    cout << "Setelah pop 1 data:" << endl;
    printStack(S);

    return 0;
}
```

#### Output:
<img width="348" height="92" alt="image" src="https://github.com/user-attachments/assets/24770005-3b5a-4542-8d35-3e3f5e239ef9" />




membuat sebuah stack berisi angka 4729601. Isi stack ditampilkan atas ke bawah, lalu dibalik dengan bantuan stack sementara, sehingga urutannya berubah dan hasil akhir ditampilkan kembali.

#### Full code Screenshot:
<img width="480" height="444" alt="image" src="https://github.com/user-attachments/assets/d4e8e4d0-35e7-4d13-9d77-42684b90c25f" />
<img width="402" height="479" alt="image" src="https://github.com/user-attachments/assets/d005db9c-0b10-4036-9eef-3759441f890e" />
<img width="402" height="575" alt="image" src="https://github.com/user-attachments/assets/6fcdb30a-a749-48c9-b2d5-40bb6eddb570" />




## Kesimpulan
Stack menggunakan prinsip "last in, first out" dengan Percobaan push, pop, tampilkan, dan balik urutan.

## Referensi
(https://sisfo.itp.ac.id/bahanajar/BahanAjar/Anisya/Modul%203%20-%20Tumpukan.pdf)



