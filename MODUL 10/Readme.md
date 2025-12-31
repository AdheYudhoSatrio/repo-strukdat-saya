
<p align="center">Adhe Yudho Satrio</p>

## Dasar Teori

Doubly Linked List merupakan struktur data yang setiap elemennya memiliki dua buah pointer, yaitu satu pointer yang mengarah ke node sebelumnya (prev) dan satu pointer lain yang menunjuk ke node berikutnya (next).


### 1. [soal]
bstree.h
```
#ifndef BSTREE_H
#define BSTREE_H 

#include <iostream>
using namespace std;

#define Nil NULL

typedef int infotype;
typedef struct Node* address;

struct Node {
    infotype info;
    address left;
    address right;
};

address alokasi(infotype x);

void insertNode(address &root, infotype x);

void printInOrderStrip(address root);

int hitungJumlahNode(address root);
int hitungTotalInfo(address root);
int hitungKedalaman(address root);

#endif

```
bstree.cpp
```
#include "bstree.h"

address alokasi(infotype x) {
    address p = new Node;
    p->info = x;
    p->left = Nil;
    p->right = Nil;
    return p;
}

void insertNode(address &root, infotype x) {
    if (root == Nil) {
        root = alokasi(x);
    } 
    else if (x < root->info) {
        insertNode(root->left, x);
    }
    else if (x > root->info) {
        insertNode(root->right, x);
    }
    else {
        // duplikat: diabaikan
    }
}

address findNode(address root, infotype x) {
    if (root == Nil) return Nil;
    if (root->info == x) return root;
    if (x < root->info) return findNode(root->left, x);
    return findNode(root->right, x);
}

void InOrder(address root) {
    if (root != Nil) {
        InOrder(root->left);
        cout << root->info << " ";
        InOrder(root->right);
    }
}

int hitungJumlahNode(address root) {
    if (root == Nil) return 0;
    return 1 + hitungJumlahNode(root->left) + hitungJumlahNode(root->right);
}

int hitungTotalInfo(address root) {
    if (root == Nil) return 0;
    return root->info + hitungTotalInfo(root->left) + hitungTotalInfo(root->right);
}

int hitungKedalaman(address root) {
    if (root == Nil) return 0;
    int L = hitungKedalaman(root->left);
    int R = hitungKedalaman(root->right);
    return 1 + max(L, R);
}
```
main.cpp
```
#include <iostream>
#include "bstree.h"
using namespace std;

int main() {
    address root = Nil;

    insertNode(root,1);
    insertNode(root,2);
    insertNode(root,6);
    insertNode(root,4);
    insertNode(root,5);
    insertNode(root,3);
    insertNode(root,6); // duplikat
    insertNode(root,7);

    cout << "Inorder : ";
    InOrder(root);

    cout << "\nKedalaman: " << hitungKedalaman(root) << endl;
    cout << "Jumlah Node: " << hitungJumlahNode(root) << endl;
    cout << "Total Info: " << hitungTotalInfo(root) << endl;

    return 0;
}
```

#### Output:
<img width="611" height="130" alt="image" src="https://github.com/user-attachments/assets/d38d1abb-f9be-4907-b2f6-9e4f5e179b32" />


#### Full code Screenshot:
<img width="600" height="497" alt="image" src="https://github.com/user-attachments/assets/dd5f1670-56c5-4561-8ee3-a1d748e6b8a5" />
<img width="1691" height="671" alt="image" src="https://github.com/user-attachments/assets/6a930333-58a6-4c35-bf03-a96462f012f3" />
<img width="506" height="655" alt="image" src="https://github.com/user-attachments/assets/7c963758-b3df-4765-86f3-b7605f2e33d7" />


### 2. [soal]
bstree.h
```
#ifndef BSTREE_H
#define BSTREE_H 

#include <iostream>
using namespace std;

#define Nil NULL

typedef int infotype;
typedef struct Node* address;

struct Node {
    infotype info;
    address left;
    address right;
};

address alokasi(infotype x);

void insertNode(address &root, infotype x);

void printInOrderStrip(address root);

int hitungJumlahNode(address root);
int hitungTotalInfo(address root);
int hitungKedalaman(address root);

#endif

```
bstree.cpp
```
#include "bstree.h"

address alokasi(infotype x) {
    address p = new Node;
    p->info = x;
    p->left = Nil;
    p->right = Nil;
    return p;
}

void insertNode(address &root, infotype x) {
    if (root == Nil) {
        root = alokasi(x);
    } 
    else if (x < root->info) {
        insertNode(root->left, x);
    }
    else if (x > root->info) {
        insertNode(root->right, x);
    }
    else {
        // duplikat: diabaikan
    }
}

address findNode(address root, infotype x) {
    if (root == Nil) return Nil;
    if (root->info == x) return root;
    if (x < root->info) return findNode(root->left, x);
    return findNode(root->right, x);
}

void InOrder(address root) {
    if (root != Nil) {
        InOrder(root->left);
        cout << root->info << " ";
        InOrder(root->right);
    }
}

int hitungJumlahNode(address root) {
    if (root == Nil) return 0;
    return 1 + hitungJumlahNode(root->left) + hitungJumlahNode(root->right);
}

int hitungTotalInfo(address root) {
    if (root == Nil) return 0;
    return root->info + hitungTotalInfo(root->left) + hitungTotalInfo(root->right);
}

int hitungKedalaman(address root) {
    if (root == Nil) return 0;
    int L = hitungKedalaman(root->left);
    int R = hitungKedalaman(root->right);
    return 1 + max(L, R);
}
```
main.cpp
```
#include <iostream>
#include "bstree.h"
using namespace std;

int main() {
    address root = Nil;

    insertNode(root,1);
    insertNode(root,2);
    insertNode(root,6);
    insertNode(root,4);
    insertNode(root,5);
    insertNode(root,3);
    insertNode(root,6); // duplikat
    insertNode(root,7);

    cout << "Inorder : ";
    InOrder(root);

    cout << "\nKedalaman: " << hitungKedalaman(root) << endl;
    cout << "Jumlah Node: " << hitungJumlahNode(root) << endl;
    cout << "Total Info: " << hitungTotalInfo(root) << endl;

    return 0;
}
```

#### Output:

<img width="564" height="288" alt="image" src="https://github.com/user-attachments/assets/a7650317-9613-4d55-99b7-4ea38d198ed5" />


#### Full code Screenshot:
<img width="627" height="495" alt="image" src="https://github.com/user-attachments/assets/95454c52-c594-4a4a-80a7-1d8a7c115f9f" />
<img width="1691" height="899" alt="image" src="https://github.com/user-attachments/assets/6151fe2b-3622-4d67-9391-7dbadc1c9da9" />
<img width="442" height="561" alt="image" src="https://github.com/user-attachments/assets/f482a48a-429a-4517-b870-33cea4361df3" />







## Kesimpulan
Pendekatan rekursif digunakan untuk mengolah Binary Search Tree (BST). Struktur BST memungkinkan data tersimpan secara teratur dan dapat ditampilkan berurutan melalui traversal inorder. Dengan memanfaatkan beberapa fungsi rekursif, program juga dapat menghitung kedalaman pohon, jumlah node, serta total nilai yang ada. Selain itu, pemisahan program ke dalam beberapa file membuat kode lebih terstruktur dan mudah dikelola.

## Referensi
Sarno, R., & Rahutomo, F. (2008). Penerapan algoritma weighted tree similarity untuk pencarian semantik. JUTI: Jurnal Ilmiah Teknologi Informasi, 39-46.




