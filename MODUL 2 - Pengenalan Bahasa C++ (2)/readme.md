# <h1 align="center">Laporan Praktikum Modul Pengenalan Bahasa C++ (2)</h1>
<p align="center">Arvinanto Bahtiar</p>

## Dasar Teori

Bahasa C++ merupakan pengembangan dari bahasa C yang mendukung pemrograman prosedural maupun berorientasi objek. 
Penulisan program dilakukan menggunakan Code:
:Blocks dengan struktur dasar berupa header, fungsi main(), serta penggunaan cin dan cout untuk proses input dan output


### 1. [Soal]

```C++
#include <iostream>
using namespace std;

int main() {
    int A[3][3], B[3][3], C[3][3];

    cout << "Masukkan elemen matriks A (3x3):\n";
    for (int i=0; i<3; i++)
        for (int j=0; j<3; j++)
            cin >> A[i][j];

    cout << "Masukkan elemen matriks B (3x3):\n";
    for (int i=0; i<3; i++)
        for (int j=0; j<3; j++)
            cin >> B[i][j];

    cout << "\nA + B:\n";
    for (int i=0; i<3; i++) {
        for (int j=0; j<3; j++)
            cout << A[i][j] + B[i][j] << " ";
        cout << endl;
    }

    cout << "\nA - B:\n";
    for (int i=0; i<3; i++) {
        for (int j=0; j<3; j++)
            cout << A[i][j] - B[i][j] << " ";
        cout << endl;
    }

    cout << "\nA x B:\n";
    for (int i=0; i<3; i++) {
        for (int j=0; j<3; j++) {
            C[i][j] = 0;
            for (int k=0; k<3; k++)
                C[i][j] += A[i][k] * B[k][j];
            cout << C[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}

```
#### Output:
<img width="971" height="624" alt="image" src="https://github.com/user-attachments/assets/9807c7c2-0032-48d2-879b-c034fb00eac8" />



Program tersebut digunakan untuk mengolah dua buah matriks 3×3. Pengguna menginput matriks A dan B serta menentukan jenis operasi yang diinginkan
yaitu penjumlahan, pengurangan, atau perkalian. Setelah proses perhitungan.

#### Full code Screenshot:
<img width="476" height="823" alt="image" src="https://github.com/user-attachments/assets/b97e2d7b-b491-4582-a4f8-23000d3de9fe" />




### 2. [Soal]

```C++
#include <iostream>
using namespace std;

void tukar3(int &x, int &y, int &z) {
    int temp = x;  
    x = y;         
    y = z;          
    z = temp;      
}

int main() {
    int a = 1, b = 2, c = 3;
    int& ref = a; 

    cout << "BEFORE DITUKAR:" << endl;
    cout << "a = " << a << ", b = " << b << ", c = " << c << endl;
    cout << "ref : " << ref << endl;
    cout << "Alamat a  : " << a << endl;
    cout << "Alamat ref : " << ref << endl;

    ref = 4;
    cout << "\nafter ref = 4 :" << endl;
    cout << "a = " << a << ", ref = " << ref << endl;

    tukar3(a, b, c);

    cout << "\nAFTER DITUKAR:" << endl;
    cout << "a = " << a << ", b = " << b << ", c = " << c << endl;

    return 0;
}


```
#### Output:
<img width="950" height="206" alt="image" src="https://github.com/user-attachments/assets/f3bf4db2-8824-4d0f-8fe1-2d96b1db0901" />



Program ini melakukan pertukaran nilai pada tiga variabel secara bergantian dengan memanfaatkan konsep referensi. Nilai awal setiap variabel
ditampilkan terlebih dahulu, kemudian fungsi tukarReference mengalihkan nilai dari x ke y, y ke z, dan z kembali ke x.

#### Full code Screenshot:
<img width="615" height="585" alt="image" src="https://github.com/user-attachments/assets/82980b6d-8761-4f9e-b479-567744cb7722" />






### 3. [Soal]

```C++
#include <iostream>
using namespace std;

int maxArr(int a[], int n){ int m=a[0]; for(int i=1;i<n;i++) if(a[i]>m) m=a[i]; return m; }
int minArr(int a[], int n){ int m=a[0]; for(int i=1;i<n;i++) if(a[i]<m) m=a[i]; return m; }
void rata2(int a[], int n){ float t=0; for(int i=0;i<n;i++) t+=a[i]; cout<<"Rata-rata = "<<t/n<<endl; }

int main(){
    int A[]={1,2,3,4,5,6,7,8,9,10}, n=10, p;
    cout<<"##### MENU PROGRAM ARRAY GWEH  #####\n1.Tampilkan isi array\n2.nilai maks\n3.nilai min\n4.Rata-rata\n5.selesai\nPilih: ";
    cin>>p;
    switch(p){
        case 1: for(int i=0;i<n;i++) cout<<A[i]<<" "; break;
        case 2: cout<<"Maks = "<<maxArr(A,n); break;
        case 3: cout<<"Min = "<<minArr(A,n); break;
        case 4: rata2(A,n); break;
        case 5: cout<<"Sampai jumpa, senang bisa membantu!\n"; break;
        default: cout<<"tidak ada pilihan tersebut!"; 
    }
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

