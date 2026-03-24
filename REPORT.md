# Laporan Programming Assignment 1: Basic C++

## Pendahuluan
> Apa saja yang telah saya buat pada program kali ini

Program ini dirancang untuk menghitung umur seseorang dalam tahun dan bulan, serta menentukan hari dalam seminggu untuk tanggal tertentu. Program ini ditulis dalam bahasa C++ dan menggunakan struktur data `tm` dari library `<ctime>` untuk memanipulasi dan menghitung tanggal. Untuk menyelesaikan program ini, saya menggunakan tiga fungsi utama yaitu : `yearsOld`, `monthsOld`, dan `dayOfDate`. Berikut ini adalah penjelasan dan implementasi dari masing-masing fungsi:

## Implementasi Fungsi pada Program
### 1. Fungsi `yearsOld`
Fungsi ini akan menghitung selisih tahun antara tanggal saat ini dan tanggal lahir. Jika bulan atau hari pada tanggal saat ini belum mencapai bulan atau hari pada tanggal lahir, maka umur dikurangi 1. Cara kerjanya dengan menghitung umur dalam tahun berdasarkan tanggal lahir `(inputTgl)` dan tanggal saat ini `(currentTgl)`. Berikut ini adalah kode nya :
```c
int yearsOld(tm* inputTgl, tm* currentTgl) {
    int age = currentTgl->tm_year - inputTgl->tm_year;
    if (currentTgl->tm_mon < inputTgl->tm_mon || 
        (currentTgl->tm_mon == inputTgl->tm_mon && currentTgl->tm_mday < inputTgl->tm_mday)) {
        age--;
    }
    return age;
}
```

### 2. Fungsi ```monthsOld``` 
Fungsi ini digunakan untuk menghitung selisih bulan antara tanggal saat ini dan tanggal lahir. Jika hari pada tanggal saat ini belum mencapai hari pada tanggal lahir, maka jumlah bulan dikurangi 1. Fungsi ini akan menghitung umur dalam bulan berdasarkan tanggal lahir ```(inputTgl)``` dan tanggal saat ini ```(currentTgl)``` dengan kode sebagai berikut :
```c
int monthsOld(tm* inputTgl, tm* currentTgl) {
    int ageInMonths = (currentTgl->tm_year - inputTgl->tm_year) * 12;
    ageInMonths += currentTgl->tm_mon - inputTgl->tm_mon;
    if (currentTgl->tm_mday < inputTgl->tm_mday) {
        ageInMonths--;
    }
    return ageInMonths;
}
```

### 3. Fungsi `dayOfDate`
Pada fungsi ini akan menentukan hari dalam seminggu untuk tanggal tertentu dengan menggunakan fungsi `mktime` untuk menormalisasi struktur `tm` dan mengembalikan nama hari berdasarkan nilai `tm_wday`. Kode fungsi tersebut dituliskan sebagai berikut :
```d
string dayOfDate(tm* inputTgl) {
    const char* days[] = {"Minggu", "Senin", "Selasa", "Rabu", "Kamis", "Jumat", "Sabtu"};
    mktime(inputTgl); // Normalisasi tanggal
    return days[inputTgl->tm_wday];
}
```
## Contoh Penggunaan Program
Program ini akan menerima input tanggal lahir dalam format `DD/MM/YYYY` untuk menghitung:
- Umur dalam tahun.
- Umur dalam bulan.
- Hari dalam seminggu untuk tanggal tersebut.

### Contoh
Input :
```
17/05/2006
```
Output :
```
19 238 Rabu
```
### Berikut adalah Penjelasan Output:

18: Umur dalam tahun

223: Umur dalam bulan

Rabu: Hari dalam seminggu untuk tanggal 26 Juli 2006.

## Kesimpulan
Program ini berhasil mengimplementasikan perhitungan umur dalam tahun dan bulan, serta menentukan hari dalam seminggu untuk tanggal tertentu.