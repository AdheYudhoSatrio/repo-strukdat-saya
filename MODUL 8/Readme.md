# <h1 align="center">Laporan Praktikum Modul Singly Linked List</h1>
<p align="center">Adhe Yudho Satrio</p>

## Dasar Teori

Queue adalah struktur data yang meniru sistem antrean dengan aturan FIFO, sehingga data yang pertama kali dimasukkan akan dikeluarkan lebih dulu. Dalam praktikum ini, queue direalisasikan menggunakan linked list, di mana proses enqueue dilakukan di bagian belakang dan dequeue dilakukan di bagian depan.

### 1. [soal]
queue.h
```
#ifndef QUEUE_H
#define QUEUE_H

const int MAX = 5;
typedef int infotype;

struct Queue {
    infotype info[MAX];
    int head;
    int tail;
};

void createQueue(Queue &Q);
bool isEmptyQueue(Queue Q);
bool isFullQueue(Queue Q);
void enqueue(Queue &Q, infotype x);
infotype dequeue(Queue &Q);
void printInfo(Queue Q);

#endif

```
queue.cpp
```
#include <iostream>
#include "queue.h"
using namespace std;

void createQueue(Queue &Q){
    Q.head = -1;
    Q.tail = -1;
}

bool isEmptyQueue(Queue Q){
    return Q.head == -1;
}

bool isFullQueue(Queue Q){
    return Q.tail == MAX - 1;
}

void enqueue(Queue &Q, infotype x){
    if(isFullQueue(Q)){
        cout << "Queue penuh (penuh semu mungkin terjadi)!\n";
        return;
    }

    if(isEmptyQueue(Q)){
        Q.head = 0;
        Q.tail = 0;
    } else {
        Q.tail++;
    }

    Q.info[Q.tail] = x;
}

infotype dequeue(Queue &Q){
    if(isEmptyQueue(Q)){
        cout << "Queue kosong!\n";
        return -999;
    }

    infotype x = Q.info[Q.head];

    if(Q.head == Q.tail){
        // queue menjadi kosong
        Q.head = -1;
        Q.tail = -1;
    } else {
        Q.head++;
    }

    return x;
}

void printInfo(Queue Q){
    cout << "H = " << Q.head << " | T = " << Q.tail << "\t | Queue: ";

    if(isEmptyQueue(Q)){
        cout << "(kosong)\n";
        return;
    }

    for(int i = Q.head; i <= Q.tail; i++){
        cout << Q.info[i] << " ";
    }
    cout << endl;
}
```
main.cpp
```
#include <iostream>
#include "queue.h"
using namespace std;

int main() {
    Queue Q;
    createQueue(Q);

    cout<<"----------------------"<<endl;
    cout<<" H - T \t | Queue info"<<endl;
    cout<<"----------------------"<<endl;
    printInfo(Q);

    enqueue(Q,5); printInfo(Q);
    enqueue(Q,2); printInfo(Q);
    enqueue(Q,7); printInfo(Q);
    dequeue(Q);  printInfo(Q);
    enqueue(Q,4); printInfo(Q);
    dequeue(Q);  printInfo(Q);
    dequeue(Q);  printInfo(Q);

    return 0;
}
```

#### Output:
<img width="662" height="255" alt="image" src="https://github.com/user-attachments/assets/2a84d8f3-a489-4732-ab45-0e7880f80b33" />


#### Full code Screenshot:
<img width="524" height="445" alt="image" src="https://github.com/user-attachments/assets/b3542c32-3bd6-4540-872c-09846f1c3613" />
<img width="1687" height="578" alt="image" src="https://github.com/user-attachments/assets/319663fe-ec65-4eab-b049-3f1c21491400" />
<img width="349" height="407" alt="image" src="https://github.com/user-attachments/assets/c3ae97db-672f-4927-a2fd-4c89ee4aea00" />

### 2. [soal]
queue.h
```
#ifndef QUEUE_H
#define QUEUE_H

const int MAX = 5;   // kapasitas queue

typedef int infotype;

struct Queue {
    infotype info[MAX]; 
    int head;
    int tail;
};

// PROTOTYPE
void createQueue(Queue &Q);
bool isEmptyQueue(Queue Q);
bool isFullQueue(Queue Q);
void enqueue(Queue &Q, infotype x);
infotype dequeue(Queue &Q);
void printInfo(Queue Q);

#endif

```
queue.cpp
```
#ifndef QUEUE_H
#define QUEUE_H

const int MAX = 5;   // kapasitas queue

typedef int infotype;

struct Queue {
    infotype info[MAX]; 
    int head;
    int tail;
};

// PROTOTYPE
void createQueue(Queue &Q);
bool isEmptyQueue(Queue Q);
bool isFullQueue(Queue Q);
void enqueue(Queue &Q, infotype x);
infotype dequeue(Queue &Q);
void printInfo(Queue Q);

#endif
```
main.cpp
```
#include <iostream>
#include "queue.h"
using namespace std;

int main() {

    Queue Q;
    createQueue(Q);

    cout<<"----------------------"<<endl;
    cout<<" H - T \t | Queue info"<<endl;
    cout<<"----------------------"<<endl;
    printInfo(Q);

    enqueue(Q,5); printInfo(Q);
    enqueue(Q,2); printInfo(Q);
    enqueue(Q,7); printInfo(Q);
    dequeue(Q);  printInfo(Q);
    enqueue(Q,4); printInfo(Q);
    dequeue(Q);  printInfo(Q);
    dequeue(Q);  printInfo(Q);

    return 0;
}
```

#### Output:
<img width="566" height="260" alt="image" src="https://github.com/user-attachments/assets/9daa50ad-76d9-4bb2-88f5-3ffdd34e7ada" />

#### Full code Screenshot:
<img width="415" height="480" alt="image" src="https://github.com/user-attachments/assets/6389031e-376d-49e0-ba39-8668b1ed804a" />
<img width="727" height="905" alt="image" src="https://github.com/user-attachments/assets/a971f0dc-f3ac-4dc7-b936-c9cd0adf752d" />
<img width="439" height="447" alt="image" src="https://github.com/user-attachments/assets/d6066b96-ecbd-4eec-b96e-f3fd30304d86" />

### 3. [soal]
queue.h
```
#ifndef QUEUE_H
#define QUEUE_H

const int MAX = 5;
typedef int infotype;

struct Queue {
    infotype info[MAX];
    int head;
    int tail;
};

void createQueue(Queue &Q);
bool isEmptyQueue(Queue Q);
bool isFullQueue(Queue Q);
void enqueue(Queue &Q, infotype x);
infotype dequeue(Queue &Q);
void printInfo(Queue Q);

#endif

```
queue.cpp
```
#include <iostream>
#include "queue.h"
using namespace std;

void createQueue(Queue &Q){
    Q.head = -1;
    Q.tail = -1;
}

bool isEmptyQueue(Queue Q){
    return Q.head == -1;
}

bool isFullQueue(Queue Q){
    return ( (Q.tail + 1) % MAX ) == Q.head;
}

void enqueue(Queue &Q, infotype x){
    if(isFullQueue(Q)){
        cout << "Queue penuh!\n";
        return;
    }

    if(isEmptyQueue(Q)){
        Q.head = 0;
        Q.tail = 0;
    } else {
        Q.tail = (Q.tail + 1) % MAX;
    }

    Q.info[Q.tail] = x;
}

infotype dequeue(Queue &Q){
    if(isEmptyQueue(Q)){
        cout << "Queue kosong!\n";
        return -999;
    }

    infotype x = Q.info[Q.head];

    if(Q.head == Q.tail){
        // queue menjadi kosong
        Q.head = -1;
        Q.tail = -1;
    } else {
        Q.head = (Q.head + 1) % MAX;
    }

    return x;
}

void printInfo(Queue Q){
    cout << "H = " << Q.head << " | T = " << Q.tail << "\t | Queue: ";

    if(isEmptyQueue(Q)){
        cout << "(kosong)\n";
        return;
    }

    int i = Q.head;
    while(true){
        cout << Q.info[i] << " ";
        if(i == Q.tail) break;
        i = (i + 1) % MAX;
    }
    cout << endl;
}

```
main.cpp
```
#include <iostream>
#include "queue.h"
using namespace std;

int main() {
    Queue Q;
    createQueue(Q);

    cout<<"----------------------"<<endl;
    cout<<" H - T \t | Queue info"<<endl;
    cout<<"----------------------"<<endl;

    printInfo(Q);
    enqueue(Q,5); printInfo(Q);
    enqueue(Q,2); printInfo(Q);
    enqueue(Q,7); printInfo(Q);
    dequeue(Q);  printInfo(Q);
    enqueue(Q,4); printInfo(Q);
    dequeue(Q);  printInfo(Q);
    dequeue(Q);  printInfo(Q);

    return 0;
}

```

#### Output:
<img width="700" height="243" alt="image" src="https://github.com/user-attachments/assets/7ceec077-2e02-4387-bc80-af43267f83a8" />


#### Full code Screenshot:
<img width="473" height="470" alt="image" src="https://github.com/user-attachments/assets/a3452937-bdca-44c4-91cc-6e0c0de3df70" />
<img width="1693" height="632" alt="image" src="https://github.com/user-attachments/assets/3c5f77f8-96ab-4386-b868-c34c26466659" />
<img width="367" height="434" alt="image" src="https://github.com/user-attachments/assets/000ddde6-bd11-456b-a903-ed6b2c460601" />




## Kesimpulan
Queue dapat diterapkan dengan mempertahankan kepala pada indeks 0 dan ekor bergerak ke posisi belakang. Setiap proses dequeue akan menggeser elemen ke kiri sehingga susunan data tetap teratur.
## Referensi
(https://www.dicoding.com/blog/struktur-data-queue/)




