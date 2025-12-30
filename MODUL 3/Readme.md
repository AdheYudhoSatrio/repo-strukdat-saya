# <h1 align="center">Laporan Praktikum ABSTRACT DATA TYPE (ADT)</h1>
<p align="center">Arvinanto Bahtiar</p>

## Dasar Teori

ADT merupakan suatu tipe data yang disertai dengan sekumpulan operasi dasar (primitif) yang dapat diterapkan pada tipe tersebut. 
Pada ADT yang lengkap, juga terdapat penjelasan mengenai invarian tipe serta aksioma yang mengatur perilakunya.
ADT sendiri bersifat sebagai definisi statik.


### 1. [Soal]

```C++
#include <iostream>
using namespace std;

struct mhs{
    string NAMA,NIM;
    float UTS,UAS,TUGAS,nilaiAkhir;
};

float hitung(float u,float a,float t){
    return (0.3*u)+(0.4*a)+(0.3*t);
}

int main(){
    mhs M[10];
    int n;
    cout<<"JUMLAH MAHASISWA (10): ";
    cin>>n;
    if(n>10){
        cout<<"MAHASISWA TERLALU BANYAK\n";
        return 0;
    }
    for(int i=0;i<n;i++){
        cout<<"\nMahasiswa ke-"<<i+1<<endl;
        cout<<"NAMA : ";
        cin.ignore();
        getline(cin,M[i].NAMA);
        cout<<"NIM  : ";
        cin>>M[i].NIM;
        cout<<"NILAI UTS  : ";
        cin>>M[i].UTS;
        cout<<"NILAI UAS  : ";
        cin>>M[i].UAS;
        cout<<"NILAI TUGAS: ";
        cin>>M[i].TUGAS;
        M[i].nilaiAkhir=hitung(M[i].UTS,M[i].UAS,M[i].TUGAS);
    }
    cout<<"\nDaftar Nilai Mahasiswa\n";
    cout<<"-----------------------------\n";
    cout<<"No\tNIM\t\tNama\t\tNilAkhir\n";
    for(int i=0;i<n;i++){
        cout<<i+1<<"\t"<<M[i].NIM<<"\t\t"<<M[i].NAMA<<"\t\t"<<M[i].nilaiAkhir<<endl;
    }
    return 0;
}
```
#### Output:
<img width="1101" height="514" alt="image" src="https://github.com/user-attachments/assets/7619663f-3240-46f5-a704-7294a387c561" />




Kode di atas digunakan untuk menyimpan dan menampilkan data mahasiswa sebanyak maks 10 orang, menggunakan struct Mahasiswa untuk menyimpan data seperti nama, NIM, nilai UTS, UAS, dan tugas.

#### Full code Screenshot:
<img width="744" height="834" alt="image" src="https://github.com/user-attachments/assets/4487b0f1-7f2c-4995-ac00-dbbc77569e3a" />





### 2. [Soal]
pelajaran.h

```
#ifndef PELAJARAN_H_INCLUDED
#define PELAJARAN_H_INCLUDED

#include <iostream>
#include <string>
using namespace std;

struct pelajaran {
    string namaMapel;
    string kodeMapel;
};

pelajaran create_pelajaran(string namapel, string kodepel);
void tampil_pelajaran(pelajaran pel);

#endif

```
pelajaran.cpp
```
#include "pelajaran.h"
#include <iostream>
using namespace std;

pelajaran create_pelajaran(string namapel, string kodepel) {
    pelajaran p;
    p.namaMapel = namapel;
    p.kodeMapel = kodepel;
    return p;
}

void tampil_pelajaran(pelajaran pel) {
    cout << "=== Data Pelajaran ===" << endl;
    cout << "Nama Mata Pelajaran : " << pel.namaMapel << endl;
    cout << "Kode Mata Pelajaran : " << pel.kodeMapel << endl;
}
```
main.cpp
```
#include <iostream>
#include "pelajaran.h"
using namespace std;

int main() {
    string namapel = "Struktur Data";
    string kodepel = "STD";
    pelajaran pel = create_pelajaran(namapel, kodepel);
    tampil_pelajaran(pel);
    return 0;
}
```

#### Output:
<img width="628" height="106" alt="image" src="https://github.com/user-attachments/assets/33e3f315-03ed-45ed-b4b7-da4872b3f2d4" />

Program ini melakukan pertukaran nilai pada tiga variabel secara bergantian dengan memanfaatkan konsep referensi. Nilai awal setiap variabel
ditampilkan terlebih dahulu, kemudian fungsi tukarReference mengalihkan nilai dari x ke y, y ke z, dan z kembali ke x.

#### Full code Screenshot:
<img width="552" height="303" alt="image" src="https://github.com/user-attachments/assets/59a64beb-dc64-42c5-8a9f-a5d08b42d6fd" />
<img width="582" height="303" alt="image" src="https://github.com/user-attachments/assets/c6d80381-6fec-4993-98e3-d7aa690ac232" />
<img width="524" height="212" alt="image" src="https://github.com/user-attachments/assets/1747f6a8-67c3-4581-8e3f-a10d497bb07a" />






### 3. [Soal]

```C++
#include <iostream>
using namespace std;

struct mhs{
    string nama,nim;
    float uts,uas,tugas,nilaiAkhir;
};

float hitung(float u,float a,float t){
    return (0.3*u)+(0.4*a)+(0.3*t);
}

int main(){
    mhs M[10];
    int n;
    cout<<"Masukkan jumlah mahasiswa (max 10): ";
    cin>>n;
    if(n>10){
        cout<<"Kebanyakan, max 10 aja\n";
        return 0;
    }
    for(int i=0;i<n;i++){
        cout<<"\nMahasiswa ke-"<<i+1<<endl;
        cout<<"Nama : ";
        cin.ignore();
        getline(cin,M[i].nama);
        cout<<"NIM  : ";
        cin>>M[i].nim;
        cout<<"UTS  : ";
        cin>>M[i].uts;
        cout<<"UAS  : ";
        cin>>M[i].uas;
        cout<<"Tugas: ";
        cin>>M[i].tugas;
        M[i].nilaiAkhir=hitung(M[i].uts,M[i].uas,M[i].tugas);
    }
    cout<<"\nDaftar Nilai Mahasiswa\n";
    cout<<"-----------------------------\n";
    cout<<"No\tNIM\t\tNama\t\tNilAkhir\n";
    for(int i=0;i<n;i++){
        cout<<i+1<<"\t"<<M[i].nim<<"\t\t"<<M[i].nama<<"\t\t"<<M[i].nilaiAkhir<<endl;
    }
    return 0;
}


```
#### Output:
<img width="1168" height="543" alt="image" src="https://github.com/user-attachments/assets/9d918909-f035-439d-89a8-87f24b786b62" />


Kode di atas untuk menampilkan dua array 2 dimensi, kemudian menukar seluruh isi dari kedua array tersebut. 
Setelah pertukaran program akan menampilkan hasil akhir dari masing-masing array untuk memperlihatkan perubahan nilainya.

#### Full code Screenshot:
<img width="755" height="841" alt="image" src="https://github.com/user-attachments/assets/9882fd08-69ff-4da3-9fdf-c60f1957fd7e" />


## Kesimpulan
Sebagai kesimpulan, praktikum ini membuktikan bahwa bahasa C++ mampu digunakan untuk mengelola data secara terstruktur melalui pemanfaatan variabel, fungsi, struct, array, dan pointer, sekaligus membantu memisahkan bagian program sehingga kode menjadi lebih terorganisir dan mudah dipahami.

## Referensi
Susilo, D., Nistrina, K., & Hartati, S. (2025). Buku Ajar Struktur Data. PT. Sonpedia Publishing Indonesia



