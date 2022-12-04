# Gugun Gunawan TI.22.B1
# function-lambda
Latihan menggunakan Function dan Lambda pada python dan membuat program crud sederhana
1. Pertama kita buat folder 11-function-lambda dan didalam file tersebut kita buat file Latihan.py dan Praktikum6.py.
![sabtu](https://user-images.githubusercontent.com/115931631/205458234-1a4e05c4-ed59-4d32-93b4-f8e302624052.png)

2. Lalu buka Latihan.py dan input codingan sebagai berikut lalu run dengan mengetikan perintah berikut diterminal python Latihan.py
   
```
import math


def a(n): return lambda x: x**n


lambdaA = a(4)
print(lambdaA(4))


def b(i, j):
    return lambda x, y: math.sqrt(x**i + y**j)


lambdaB = b(4, 0)
print(lambdaB(3, 0))


def c(*args):
    return lambda *params: sum(args) / len(params)


lambdaC = c(1, 2, 3, 4, 5)
print(lambdaC(2, 2, 5))


def d(firstname):
    return lambda *lastname: "".join(set(firstname)) + "".join(set(lastname))


lambdaD = d("Gugun")
print(lambdaD("Gunawan"))
```

Dan hasilnya seperti berikut ini :

![poe ieu1](https://user-images.githubusercontent.com/115972485/205479834-57417346-d323-4c04-9a10-1ae28451748d.PNG)


3. Selanjutnya kita akan membuat program crud sederhana dan berikut flowchart program yang akan kita buat.
![Flow](https://user-images.githubusercontent.com/115931631/205458349-68054e29-f4ac-4e8f-87aa-ef901175f5a5.png)

4. Langkah selanjutnya buka file Praktikum6.py dan masukan inputan sebagai berikut lalu run dengan mengetikan perintah berikut terminal python Praktikum6.py :
```
# Gugun Gunawan
# TI.22.B1
# 312210280

#Import tabulate
from tabulate import tabulate

dictmahasiswa = {
    'No': [],
    'Nim': [],
    'Nama': [],
    'Tugas': [],
    'UTS': [],
    'UAS': [],
    'Nilai Akhir': [],
}
no = 0
# Fungsi untuk menambahkan data


def tambahData(no):
    # Menginput data
    nim = int(input("Masukan Nim : "))
    nama = input("Masukan Nama : ")
    tugas = int(input("Masukan Nilai Tugas : "))
    uts = int(input("Masukan Nilai UTS : "))
    uas = int(input("Masukan NIlai UAS : "))
    nial_akhir = int(input("Masukan Nilai Tugas Akhir : "))
    # Menambah data
    dictmahasiswa['No'].append(no)
    dictmahasiswa['Nim'].append(nim)
    dictmahasiswa['Nama'].append(nama)
    dictmahasiswa['Tugas'].append(tugas)
    dictmahasiswa['UTS'].append(uts)
    dictmahasiswa['UAS'].append(uas)
    dictmahasiswa['Nilai Akhir'].append(nial_akhir)
    # print(tabulate(dictmahasiswa, headers=[
    #       'NIM', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))

# fungsi untuk mengedit data


def editData (nim):
    # cek jika ada nim tersebut di dictmahasiswa
    if nim in dictmahasiswa['Nim']:
        # cari posisi indexnya lalu simpan du nimIndex
        nimIndex = dictmahasiswa['Nim'].index(nim)
        print("Pilih data yang mau diedit")
        # perulangan mengedit data dalam bentuk pilihan
        while True:
            editApa = int(input(
                "(1) Nim, \n (2) Nama, \n (3) Nilai Tugas, \n (4) Nilai UTS, \n (5) Nilai UAS, \n (0) Simpan Perubahan & Exit \n :"))
            if editApa == 1:
                # Merubah Nim
                newNim = int(input("Masukan Nim :"))
                dictmahasiswa['Nim'][nimIndex] = newNim
            elif editApa == 2:
                # Merubah Nama
                newNama = input("Masukan Nama :")
                dictmahasiswa['Nama'][nimIndex] = newNama
            elif editApa == 3:
                # Merubah nilai tugas & nilai akhir
                newTugas = int(input("Masukan Nilai Tugas :"))
                nilai_akhir = (newTugas * 30 / 100) + (dictmahasiswa['UTS'][nimIndex] * 35 / 100) + (
                    dictmahasiswa['UAS'][nimIndex] * 35 / 100)
                dictmahasiswa['Tugas'][nimIndex] = newTugas
                dictmahasiswa['Nilai Akhir'][nimIndex] = nilai_akhir
            elif editApa == 4:
                # Meeubah nilai uts & nilai akhir
                newUTS = int(input("Masukan Nilai UTS :"))
                nilai_akhir = (dictmahasiswa['Tugas'][nimIndex] * 30 / 100) + (newUTS * 35 / 100) + (
                    dictmahasiswa['UAS'][nimIndex] * 35 / 100)
                dictmahasiswa['UTS'][nimIndex] = newUTS
                dictmahasiswa['Nilai Akhir'][nimIndex] = nilai_akhir
            elif editApa == 5:
                # Menambah nilai uas & nilai akhir
                newUAS = int(input("Masukan Nilai UAS :"))
                nilai_akhir = (dictmahasiswa['Tugas'][nimIndex] * 35 / 100) + (dictmahasiswa['UTS'][nimIndex] * 35 / 100) + (
                    newUAS * 35 / 100)
                dictmahasiswa['UAS'][nimIndex] = newUAS
                dictmahasiswa['Nilai Akhir'][nimIndex] = nilai_akhir
            elif editApa == 0:
                break
    else:
        print("Data tidak ditemukan")

# Fungsi menghapus data
def deleteData(nim):
    if nim in dictmahasiswa['Nim']:
        nimIndex = dictmahasiswa['Nim'].index(nim)
        # Menghapus data berdasarkan position index pada nim
        del dictmahasiswa['No'][nimIndex]
        del dictmahasiswa['Nim'][nimIndex]
        del dictmahasiswa['Nama'][nimIndex]
        del dictmahasiswa['Tugas'][nimIndex]
        del dictmahasiswa['UTS'][nimIndex]
        del dictmahasiswa['UAS'][nimIndex]
        del dictmahasiswa['Nilai Akhir'][nimIndex]
        print("Data berhasil dihapus")
    else:
        print("Data tidak dapat ditemukan")

# Fungsi untuk mencari data

def cariData(nim):
    if nim in dictmahasiswa['Nim']:
        nimIndex = dictmahasiswa['Nim'].index(nim)
        # MEnuimpan data hasil pencarian berdasarkan nim
        hasilCari = {
            'No': dictmahasiswa['No'][nimIndex],
            'Nim': dictmahasiswa['Nim'][nimIndex],
            'Nama': dictmahasiswa['Nama'][nimIndex],
            'Tugas': dictmahasiswa['Tugas'][nimIndex],
            'UTS': dictmahasiswa['UTS'][nimIndex],
            'UAS': dictmahasiswa['UAS'][nimIndex],
            'Nilai Akhir': dictmahasiswa['Nilai Akhir'][nimIndex],
        }
        print(hasilCari)
    else:
        print("Data tidak ditemukan")

# Melakukan perulangan menggunakan while sampai user menekan huruf K perulangan akan berhenti
while True:
    # Opsi input pilihan C,R,U,D,F,Q
    tanya = input(
        "(C) Menambah Data,\n (R) Melihat semua Data,\n (U) Mengubah Data,\n (D) Menghapus Data,\n (F) Mencari Data,\n (Q) Keluar Program : ")
    
    if tanya == "C":
        while True:
            no =+ 1
            # Memanggil fungsi tambahData dan memparsing data no
            tambahData(no)
            tambahDataLagi = input("Tambah Data lagi? (y/n) :")
            if tambahDataLagi == 'n':
                break
    elif tanya == "R":
        # Menampilkan data dalam bentuk table package tabulate
        print(tabulate(dictmahasiswa, headers=[
            'No', 'Nim', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid")) 
    elif tanya == "U":
        print(tabulate(dictmahasiswa, headers=[
            'No', 'Nim', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid")) 
        nim = int(input('Masukan NIM untuk edit data :'))
        editData(nim)
    elif tanya == "D":
        print(tabulate(dictmahasiswa, headers=[
            'No', 'Nim', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))
        nim = int(input('Masukan NIM yang mau dihapus :'))
    elif tanya == "F":
        nim = int(input('masukan NIM untuk melihat detail Data :'))
        cariData(nim)
    elif tanya == "Q":
        break
```


Dan hasilnya seperti berikut ini :

![POE IEU2](https://user-images.githubusercontent.com/115972485/205480095-28e62471-d5d4-40a2-85c9-dbed6b46e666.PNG)

# SELESAI

Demikianlah sedikit penjelasan dari saya tentang program crud sederhana.
mohon maaf jika ada kesalahan, kurang lebihnya mohon maaf

# TERIMA KASIH
