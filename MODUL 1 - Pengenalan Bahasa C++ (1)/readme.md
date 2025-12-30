# <h1 align="center">Laporan Praktikum Modul Pengenalan Bahasa C++ (1)</h1>
<p align="center">Adhe Yudho Satrio</p>

## Dasar Teori

Berikan penjelasan teori terkait materi modul ini dengan bahasa anda sendiri serta susunan yang terstruktur per topiknya.


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



### 2. [Soal]

```C++
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Masukkan angka (0-100): ";
    cin >> n;

    string angka[] = {"nol", "satu", "dua", "tiga", "empat", "lima",
                      "enam", "tujuh", "delapan", "sembilan"};

    if (n < 10)
        cout << n << " : " << angka[n];
    else if (n == 10)
        cout << n << " : sepuluh";
    else if (n == 11)
        cout << n << " : sebelas";
    else if (n < 20)
        cout << n << " : " << angka[n - 10] << " belas";
    else if (n < 100) {
        int puluh = n / 10;
        int satu = n % 10;
        cout << n << " : " << angka[puluh] << " puluh";
        if (satu != 0)
            cout << " " << angka[satu];
    } else if (n == 100)
        cout << n << " : seratus";
    else
        cout << "Angka di luar jangkauan (0-100)";

    cout << endl;
    return 0;
}

```
#### Output:
<img width="951" height="74" alt="image" src="https://github.com/user-attachments/assets/b43669a6-448a-47ba-80bc-042f13a51764" />


Kode diatas digunakan untuk mengubah angka yang dimasukan oleh pengguna menjadi huruf atau tulisan yang menyatakan angka tersebut.

#### Full code Screenshot:
<img width="614" height="625" alt="image" src="https://github.com/user-attachments/assets/72111e0a-9a59-4b89-9730-1314ae58bbb8" />




### 3. [Soal]

```C++
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Masukkan angka: ";
    cin >> n;

    for (int i = n; i >= 1; i--) {
        for (int s = n; s > i; s--) {
            cout << "  "; 
        }
        for (int j = i; j >= 1; j--) {
            cout << j << " ";
        }
        cout << "* ";
        for (int j = 1; j <= i; j++) {
            cout << j << " ";
        }
        cout << endl;
    }
    for (int s = 0; s < n; s++) {
        cout << "  "; 
    }
    cout << "*\n";

    return 0;
}
```
#### Output:
<img width="976" height="197" alt="image" src="https://github.com/user-attachments/assets/510b4782-2785-445f-9f76-8828d78aa16a" />



Kode diatas membuat pola mirror angka dengan pusat bintang. Kiri turun dan bagian kanan naik, bentuknya simetris vertikal.

#### Full code Screenshot:
<img width="398" height="533" alt="image" src="https://github.com/user-attachments/assets/a3f0fd23-1d30-409d-bb63-bcce220da544" />




## Kesimpulan
Program ini untuk memahami perulangan bersarang, logika pengaturan posisi, dan pola output visual.

## Referensi
[[1] I. Holm, Narrator, and J. Fullerton-Smith, Producer, How to Build a Human [DVD]. London: BBC; 2002.](https://elektro.um.ac.id/wp-content/uploads/2016/05/MODUL-6-ARRAY-DPK-2016.pdf)

