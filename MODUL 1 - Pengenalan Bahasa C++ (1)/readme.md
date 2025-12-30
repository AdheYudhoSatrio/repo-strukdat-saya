# <h1 align="center">Laporan Praktikum Modul Pengenalan Bahasa C++ (1)</h1>
<p align="center">Arvinanto Bahtiar</p>

## Dasar Teori

Berikan penjelasan teori terkait materi modul ini dengan bahasa anda sendiri serta susunan yang terstruktur per topiknya.

## Guided 

### 1. Modul Codeblocks IDE & Pengenalan Bahas C++ (1)

```C++
#include <iostream>
using namespace std;

int main() {
    cout << "ini adalah file code guided praktikan" << endl;
    return 0;
}
```
Kode di atas digunakan untuk mencetak teks "ini adalah file code guided praktikan" ke layar menggunakan function cout untuk mengeksekusi nya.

## Unguided 

### 1. [Soal]

```C++
#include <iostream>
using namespace std;

int main() {
    float a, b;

    cout << "Bilangan pertama: ";
    cin >> a;
    cout << "Bilangan kedua: ";
    cin >> b;

    cout << "\nTotal Penjumlahan: " << a + b << endl;
    cout << "Total Pengurangan: " << a - b << endl;
    cout << "Total Perkalian  : " << a * b << endl;
    
    if (b != 0)
        cout << "Total Pembagian  : " << a / b << endl;
    else
        cout << "Pembagian gagal (pembagi = 0)" << endl;

    return 0;
}
```
#### Output:
<img width="977" height="144" alt="image" src="https://github.com/user-attachments/assets/17d7ce5d-74c7-4eb4-8921-335e0c79b0f3" />


Kode di atas digunakan untuk menghitung dan menampilkan hasil operasi aritmatika dua angka. Nilai dimasukkan ke cin dan hasil penjumlahan, pengurangan, perkalian, dan pembagian ditampilkan dengan cout.

#### Full code Screenshot:
<img width="533" height="439" alt="image" src="https://github.com/user-attachments/assets/9e7a1736-88db-4fe4-8102-4bf3ecb6ddce" />



## Kesimpulan
Program ini berisi tentang perulangan bersarang, logika pengaturan posisi, dan pola output visual.

## Referensi
[[1] I. Holm, Narrator, and J. Fullerton-Smith, Producer, How to Build a Human [DVD]. London: BBC; 2002.](https://elektro.um.ac.id/wp-content/uploads/2016/05/MODUL-6-ARRAY-DPK-2016.pdf)
