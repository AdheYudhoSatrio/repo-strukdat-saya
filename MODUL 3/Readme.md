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
<img width="989" height="786" alt="image" src="https://github.com/user-attachments/assets/132a8830-7406-4430-87a8-ff5067cd1ba5" />

Kode ini menyediakan menu interaktif untuk mengolah sebuah array: tampilkan isi, cari maksimum, minimum, atau hitung rata-rata. 
Setiap operasi dikerjakan oleh fungsi terpisah, dan program berulang sampai pengguna memilih keluar.

#### Full code Screenshot:
<img width="1131" height="380" alt="image" src="https://github.com/user-attachments/assets/a3f61bbb-7701-4a95-99c4-69aba5cb86fe" />

## Kesimpulan
Program ini mengelola sebuah array, seperti menampilkan data, menentukan nilai maks dan min, dan menghitung nilai rata-rata.

## Referensi
[[[1] I. Holm, Narrator, and J. Fullerton-Smith, Producer, How to Build a Human [DVD]. London: BBC; 2002.](https://elektro.um.ac.id/wp-content/uploads/2016/05/MODUL-6-ARRAY-DPK-2016.pdf)](https://www.academia.edu/35362129/Pemograman_C_Bab_12_Array_pdf)



