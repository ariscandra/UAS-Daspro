<a name="top"></a>
<img src="https://github.com/user-attachments/assets/3d8e411e-79b1-4cc7-b555-01a8517454ca" alt="" width="100%">

![Forks](https://img.shields.io/github/forks/PA-DasPro-C-Kelompok-3/PA-DasPro-C-Kelompok-3.svg)
![Stars](https://img.shields.io/github/stars/PA-DasPro-C-Kelompok-3/PA-DasPro-C-Kelompok-3.svg?style=social&label=Stars)
[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=fff)](#)
[![Git](https://img.shields.io/badge/Git-F05032?logo=git&logoColor=fff)](#)
![Kopikir Sendiri | Aris](https://img.shields.io/badge/☕%20KopikirSendiri%20%20%7C%20Aris%20-000000?style=flat&logoColor=white&color=brown)

<p align="center">
    Selamat Datang di Panduan Program Coffeshop KopikirSendiri!  
</p>

## 🗒️ Daftar Isi
- [🗒️ Daftar Isi](#️-daftar-isi)
- [👥 Profil](#-profil)
- [🚀 Tentang](#-tentang)
- [🖥️ Penjelasan Output](#️-penjelasan-output)
- [🖱️ Penjelasan Kode](#️-penjelasan-kode)
- [⌨️ Petunjuk Instalasi dan Penggunaan](#️-petunjuk-instalasi-dan-penggunaan)
  - [Persyaratan Sistem](#persyaratan-sistem)
  - [Langkah-Langkah Menjalankan Program](#langkah-langkah-menjalankan-program)

## 👥 Profil
| Aris Candra Muzaffar |
|----------------------|
| **NIM:** 2409116088 <br> **Kelas:** Sistem Informasi C '24 <br> [![Aris](https://img.shields.io/badge/-Aris-FFFFFF?logo=github&logoColor=black)](https://github.com/ariscandra) &nbsp; &nbsp;

## 🚀 Tentang
Program ini adalah aplikasi sederhana yang dikembangkan dengan bahasa pemrograman Python untuk layanan pemesanan kopi di *KopikirSendiri*. Aplikasi ini dirancang untuk memberikan pengalaman seperti memesan di cafe, dengan fitur rotasi menu berdasarkan waktu dan berbagai metode pembayaran.

**1. Library yang Digunakan**
- **`prettytable`**: Menampilkan data dalam bentuk tabel.
- **`os`**: Membersihkan layar terminal dan menentukan lokasi file.
- **`pwinput`**: Menyamarkan input kata sandi.
- **`time`**: Mengatur jeda proses.
- **`json`**: Menyimpan data pengguna, menu, voucher, dan transaksi.
- **`random`** dan **`string`**: Membuat Kode transaksi secara acak dan unik.
- **`datetime`**: Mengatur waktu untuk rotasi menu dan pengelolaan transaksi.

**2. Variabel Global**  
Variabel `tingkat_member`, `keranjang`, dan `member_sekarang` ini digunakan untuk menyimpan data dari member, menu, keranjang, dan transaksi.

**3. Fungsi Utama**
- **Menu Utama**: Mengelola menu utama, registrasi, login, dan akses ke menu member basic/elite.
- **Rotasi Menu**: Menampilkan menu kopi yang berubah berdasarkan waktu: pagi, siang, dan malam.
- **Pengelolaan Keranjang**: Menambah produk ke keranjang, melihat isi keranjang, dan melakukan checkout.
- **Penyimpanan Data**: Menyimpan dan memuat data ke dalam file JSON.
- **Manajemen E-Money dan Poin**: Mengecek saldo, menambah saldo, dan menggunakan poin untuk transaksi.

**4. Fitur di Menu Member**
- **Pemesanan Kopi**: Member dapat memilih produk berdasarkan waktu rotasi menu (pagi, siang, malam).
- **Pengelolaan Keranjang**: Member dapat melihat isi keranjang dan menyelesaikan pembelian.
- **Manajemen Saldo dan Poin**: Member dapat mengecek saldo, menambah saldo, dan menggunakan poin.
- **Upgrade Member ke Elite**: Member dapat meningkatkan status menjadi *elite* untuk mendapatkan diskon 10% di setiap pembelian dan 2 Voucher gratis.

**5. Sistem Rotasi Menu**  
Menu kopi akan berubah berdasarkan waktu:
- **Pagi**: 05:00–12:00
- **Siang**: 12:00–18:00
- **Malam**: 18:00–05:00  

Setiap waktu memiliki pilihan menu yang berbeda untuk memberikan variasi kepada pelanggan.

**6. Validasi Pembayaran dan Keamanan**  
Program mendukung validasi pembayaran melalui autentikasi kata sandi untuk menjaga keamanan transaksi.

**7. Penyimpanan Data**  
Data disimpan dalam format JSON sehingga tetap aman dan tidak hilang meskipun program ditutup.

**8. Kesimpulan**  
Program *KopikirSendiri* memberikan pengalaman memesan kopi ala cafe di rumah dengan fitur yang menarik seperti rotasi menu, sistem poin, dan validasi pembayaran. Aplikasi ini cocok untuk pelanggan yang ingin menikmati kopi berkualitas kapanpun dan dimanapun.

## 🖥️ Penjelasan Output

[![Watch the video](https://github.com/user-attachments/assets/b34d2278-96b5-42ff-acab-044cc3818443)](https://youtu.be/zU1XT0V_KWg?si=dpLqdxWcvcxI2Tkl)

<p align="justify">Output dari Program secara garis besar sudah saya jelaskan dalam video youtube yang bisa ditonton di atas.</p>

## 🖱️ Penjelasan Kode
<details>
<summary><h3>Import Module</h3></summary>

```python
import pwinput, time, json, os, random, string
from prettytable import PrettyTable
from datetime import datetime
```
<p align="justify">Pada baris kode di atas, itu untuk mengimport semua module atau library yang diperlukan untuk menjalankan program. Fungsi dari masing-masing module sendiri sudah dijelaskan di bagian sebelumnya.</p>
</details>

<details>
<summary><h3>Variabel Global</h3></summary>

```python
LOKASI = os.path.abspath(os.curdir)

MEMBER = f"{LOKASI}/data_member.json"
MENU = f"{LOKASI}/data_menu.json"

tingkat_member = None
member_sekarang = None

keranjang = []
```
<p align="justify">Variabel LOKASI menggunakan module os untuk menentukan path direktori file dari JSON yang diperlukan. MEMBER dan MENU itu untuk menyimpan jalur file untuk penyimpanan data.</p>
<p align="justify">tingkat_member, member_sekarang, dan keranjang: Variabel untuk melacak status login pengguna, username pengguna aktif, dan isi keranjang belanja.</p>
</details>

<details>
<summary><h3>Fungsi Menu Utama</h3></summary>

```python
def menu_awal():
    print("+====================================================================+")
    print(r"|  _  __            _  _    _       ___                _  _       _  |")
    print(r"| | |/ / ___  _ __ (_)| |__(_) _ _ / __| ___  _ _   __| |(_) _ _ (_) |")
    print(r"| | ' < / _ \| '_ \| || / /| || '_|\__ \/ -_)| ' \ / _` || || '_|| | |")
    print(r"| |_|\_\\___/| .__/|_||_\_\|_||_|  |___/\___||_||_|\__,_||_||_|  |_| |")
    print(r"|            |_|                                                     |")
    print("+--------------------------------------------------------------------+")
    print("|   Alloooo...!! Welcome to KopikirSendiri. Pengen Ngopi di Rumah    |")
    print("|         dengan Kualitas Caffe? Buruan Pesen disini, Kakak!         |")
    print("|                       (: KAMI BUKA 24/7 :)                         |")
    print("+--------------------------------------------------------------------+")
    print("|                            MENU UTAMA                              |")
    print("+--------------------------------------------------------------------+")
    print("|  [1] Daftar Member KopikirSendiri                                  |")
    print("|  [2] Login Member KopikirSendiri                                   |")
    print("|  [0] Keluar                                                        |")
    print("+====================================================================+")
    while True:
        try:
            pilihan = int(input("\nMau Ngapain, Kak? (0-2): "))
            if pilihan == 1:
                regis()
                break
            elif pilihan == 2:
                login()
                break
            elif pilihan == 0:
                print("\n+====================================================================+")
                print("|                   Maacih Banyak Udah Mampir, Kak!                  |")
                print("|                            Sampai Nanti!                           |")
                print("+====================================================================+\n")
                exit()
            else:
                pesan1()
        except (ValueError, KeyboardInterrupt):
            pesan2()
        except Exception as e:
            print(f"Error Kak: {e}")
```
<p align="justify">Fungsi ini menampilkan menu utama untuk registrasi, login, atau keluar. Masing-masing pilihan akan dialihkan ke fungsi yang sesuai dengan labelnya.</p>
</details>

<details>
<summary><h3>Fungsi Regis</h3></summary>

```python
def regis():
    sapu()
    data_member = load_data_member()
    print("+=========================================+")
    print("|            Registrasi Member            |")
    print("+=========================================+")
    print("|          Udah Jadi Member Kami?         |")
    print("|       Ketik 'login' di Field Input      |")
    print("|               untuk Login               |")
    print("+=========================================+")
    print("|                Ketik '0'                |")
    print("|               Untuk Balik               |")
    print("+=========================================+")
    while True:
        username = input("\nMasukin Username (5-20 karakter): ").strip()
        if username.lower() == "login":
            print('Kakak Bakal Dialihin ke Laman Login...')
            time.sleep(1)
            login()
        elif username == '0':
            print('Kakak Bakal Dialihin ke Menu Utama...')
            time.sleep(1)
            sapu()
            menu_awal()
        elif len(username) < 5 or len(username) > 20:
            print("======================================")
            print("Maaf Kak, Username Harus 5-20 Karakter")
            print("======================================")
        elif any(member["Username"] == username for member in data_member):
            print("======================================================")
            print("Maaf Kak, Username Itu Udah Dipake, Ganti yang Lain Ya")
            print("======================================================")
        else:
            break
    while True:
        password1 = pwinput.pwinput("Masukin Password (8-20 karakter): ").strip()
        password2 = pwinput.pwinput("Masukin Password Lagi: ").strip()
        if len(password1) < 8 or len(password1) > 20:
            print("======================================")
            print("Maaf Kak, Password Harus 8-20 Karakter")
            print("======================================")
        elif password1 != password2:
            print("=======================")
            print("Password Ga Sama Persis")
            print("=======================")
        else:
            break
    member_baru = {
        "Username": username,
        "Password": password1,
        "Tingkat": 'basic',
        "Emoney": 0,
        "Poin": 0,
        "Voucher": [
            {
                "Kode": "Kopikir5",
                "Diskon": 5,
                "Status": "belum"
            }
        ]
    }
    data_member.append(member_baru)
    save_data_member(data_member)
    sapu()
    print("\n+=========================================+")
    print("|           Registrasi Berhasil!          |")
    print("+=========================================+")
    print("\n--- 🎉✨ TERIMA KASIH TELAH BERGABUNG! ✨🎉 ---")
    print(f"\nSebagai token apresiasi, kami memberikan Kak {username.capitalize()}:")
    print("🏷️ Voucher DISKON 5% untuk pembelian pertama!")
    print("🎫 Pakai kode: 'Kopikir5' saat transaksi.")
    print("⚠️ *Voucher cuman sekali pakai, Kak!*")
    input("\nTekan Enter Untuk Untuk Lanjut ke Login...")
    login()
```
<p align="justify">Fungsi ini untuk mendaftarkan member baru, data dari member disimpan dengan memanggil fungsi save_data_member() yang berguna untuk menyimpan data di data_member.json.</p>
</details>

<details>
<summary><h3>Fungsi Login</h3></summary>

```python
def login():
    sapu()
    global tingkat_member, member_sekarang
    data_member = load_data_member()
    sisa_coba = 4

    print("+==========================================+")
    print("|               LOGIN MEMBER               |")
    print("+==========================================+")
    print("|           Belum Jadi Member Kami?        |")
    print("|        Ketik 'regis' di Field Input      |")
    print("|              untuk Mendaftar             |")
    print("+==========================================+")
    print("|                 Ketik '0'                |")
    print("|                Untuk Balik               |")
    print("+==========================================+")

    while sisa_coba > 0:
        try:
            username = input("\nMasukin Usernamenya, Kak: ")
            
            if username.lower() == "regis":
                print('Kakak Bakal Dialihin ke Laman Regis...')
                time.sleep(1)
                regis()
                break
            elif username == "0":
                print('Kakak Bakal Dialihin ke Menu Utama...')
                time.sleep(1)
                sapu()
                menu_awal()
                break
            else:
                password = pwinput.pwinput("Masukin Passwordnya, Kak: ")
                login_berhasil = False

                for member in data_member:
                    if member["Username"] == username and member["Password"] == password:
                        tingkat_member = member["Tingkat"]
                        member_sekarang = member["Username"]
                        print("\n+==========================================+")
                        print("|          --- LOGIN BERHASIL ---          |")
                        print("+==========================================+")
                        print(f"\nWelcome Back, Kak {username.capitalize()}!")
                        input("\nTekan Enter Untuk Untuk Lanjut...")
                        sapu()
                        menu_member()
                        login_berhasil = True
                        break
                
                if not login_berhasil:
                    sisa_coba -= 1
                    sapu()
                    print("\n+==========================================+")
                    print("|            --- LOGIN GAGAL ---           |")
                    print("+==========================================+")
                    print(f"|          Sisa percobaan: {sisa_coba}x, Kak         |")
                    print("+==========================================+")
                    
                    if sisa_coba == 0:
                        sapu()
                        print("\n+==========================================+")
                        print("|     Percobaan Login Udah Nyampe Batas    |")
                        print("|     Maksimal. Tunggu Sebentar Ya, Kak    |")
                        print("+==========================================+")
                        for x in range(3, 0, -1):
                            time.sleep(1)
                            print("\n+==========================================+")
                            print("|    Kakak Bakal Dialihin Ke Menu Utama    |")
                            print(f"|              Dalam {x} Detik               |")
                            print("+==========================================+")
                        sapu()
                        menu_awal()

        except (ValueError, KeyboardInterrupt):
            pesan2()
        except Exception as e:
            print(f"Error Kak: {e}")

```
<p align="justify">Fungsi ini untuk login pengguna sehingga dapat mengakses menu member. Login mempunyai batas percobaan yang awalnya diset 3 dalam variabel sisa coba, kemudian jika login gagal divalidasi, maka percobaan login tersisa 3x. Pengguna dialihkan ke menu utama jika sisa percobaan login habis.</p>
</details>

<details>
<summary><h3>Fungsi Menu Member</h3></summary>

```python
def menu_member():
    data_member = load_data_member()
    global tingkat_member, member_sekarang
    batas_pil = 4 if tingkat_member == 'elite' else 5
    while True:
        print(r"  __  __                    __  __                _               ")
        print(r" |  \/  | ___ _ __  _   _  |  \/  | ___ _ __ ___ | |__   ___ _ __ ")
        print(r" | |\/| |/ _ | '_ \| | | | | |\/| |/ _ | '_ ` _ \| '_ \ / _ | '__|")
        print(r" | |  | |  __| | | | |_| | | |  | |  __| | | | | | |_) |  __| |   ")
        print(r" |_|  |_|\___|_| |_|\__,_| |_|  |_|\___|_| |_| |_|_.__/ \___|_|   ")
        print(r"                                                                  ")
        print("+=========================================+")
        print("|               Mo Ngapain?               |")
        print("+=========================================+")
        print("| [1] Liat Menu                           |")
        print("| [2] Beli                                |")
        print("| [3] Menu E-Money & Poin KopikirSendiri  |")
        print("| [4] Liat Bonus                          |")
        if tingkat_member == "elite":
            print("| [0] Logout                              |")
            print("+=========================================+")
            print("|       Selamat, Khusus Untuk Kakak       |")
            print("|    Member Elite, Nikmati Diskon 10%     |")
            print("|          di Setiap Pembelian            |")
            print("+=========================================+")
        else:
            print("| [5] Upgrade Ke Elite                    |")
            print("| [0] Logout                              |")
            print("+=========================================+")
            print("|                    !!                   |")
            print("|  Upgrade ke Elite untuk nikmati diskon  |")
            print("|   10% di setiap pembelian dan bonus 50  |")
            print("|       Poin KopikirSendiri GRATISS!!     |")
            print("|                    !!                   |")
            print("+=========================================+")

        try:
            pilihan = int(input(f"\nMau Milih yang Mana? (0-{batas_pil}): "))
            if pilihan == 1:
                sapu()
                menu_kopi()
                input("\nTekan Enter Untuk Balik ke Menu...")
                sapu()
            elif pilihan == 2:
                sapu()
                transaksi()
                break
            elif pilihan == 3:
                menu_emoney()
            elif pilihan == 4:
                bonus(data_member)
            elif pilihan == 5 and tingkat_member == "basic":
                up_tingkat()
            elif pilihan == 0:
                tingkat_member = None
                for x in range(3, 0, -1):
                    time.sleep(1)
                    sapu()
                    print("+===============================================================+")
                    print("|               Kakak Bakal Dialihin Ke Menu Utama              |")
                    print(f"|                         Dalam {x} Detik                         |")
                    print("+===============================================================+")
                sapu()
                menu_awal()
                break
            else:
                pesan1()
        except (ValueError, KeyboardInterrupt):
            pesan2()
        except Exception as e:
            print(f"Error Kak: {e}")

```
<p align="justify">Fungsi ini menampilkan menu utama untuk member setelah login. Opsinya mulai dari melihat menu produk, transaksi, e-money/poin, melihat bonus, logout dan jika pengguna adalah member basic maka akan ditampilkan opsi untuk upgrade tier ke elite.</p>
</details>

<details>
<summary><h3>Fungsi Menu Kopi</h3></summary>

```python
def menu_kopi():
    data = muat_produk()
    table = PrettyTable()
    table.field_names = ["ID", "Nama Produk", "Harga (E-Money)", "Harga (Poin)"]

    jam = datetime.now().hour
    kategori_waktu = "Pagi" if 5 <= jam < 12 else "Siang" if 12 <= jam < 18 else "Malam"

    kategori_data = next((k for k in data["Kategori"] if k["Nama Kategori"] == kategori_waktu), None)
    if kategori_data:
        table.title = "Menu KopikirSendiri - " + kategori_waktu
        for produk in kategori_data["Produk"]:
            harga_emoney = "Rp. " + format(produk["Harga Emoney"], ",").replace(",", ".")
            table.add_row([produk["ID"], produk["Nama Produk"], harga_emoney, produk["Harga Poin"]])
    else:
        table.title = "Menu KopikirSendiri"
        table.add_row(["-", "Produk Ga Ada", "-"])

    print(table)
    print("\n===================================================")
    print("*Keterangan*")
    print("Kami melakukan rotasi menu di setiap waktu berikut:")
    print("- Pagi dari Jam 05.00 - 12.00")
    print("- Siang dari Jam 12.00 - 18.00")
    print("- Malam dari Jam 18.00 - 05.00")
    print("===================================================")
```
<p align="justify">Fungsi ini menampilkan daftar produk berdasarkan waktu (rotasi menu). Menu ditampilkan menggunakan module prettytable.</p>
</details>

<details>
<summary><h3>Fungsi Transaksi</h3></summary>

```python
def transaksi():
    global tingkat_member, keranjang, member_sekarang
    data_member = load_data_member()
    data = muat_produk()

    if not data or "Kategori" not in data or not data["Kategori"]:
        print("=====================")
        print("Maaf Kak, Menu Kosong")
        print("=====================")
        menu_member()
        return

    menu_kopi()

    jam = datetime.now().hour
    kategori_waktu = "Pagi" if 5 <= jam < 12 else "Siang" if 12 <= jam < 18 else "Malam"
    kategori_data = next((k for k in data["Kategori"] if k["Nama Kategori"] == kategori_waktu), None)
    if not kategori_data:
        print("===================")
        print("Menu Tidak Tersedia")
        print("===================")
        menu_member()
        return

    while True:
        print("\nIsi Keranjang Kakak:")
        if not keranjang:
            print("======================")
            print("Keranjang Masih Kosong")
            print("======================")
        else:
            tampilkan_keranjang(keranjang)

        try:
            pilihan = int(input("\nMau Pesen yang Mana, Kak? (Masukin ID Produk / 0 untuk selesai): "))
            if pilihan == 0:
                if keranjang:
                    break
                else:
                    ulang = input("Keranjang masih kosong. Mau pesen? (y/n): ").lower()
                    if ulang == 'n':
                        print("\n======================================================")
                        print("--- Transaksi dibatalin. Makasih udah mampir, Kak! ---")
                        print("======================================================")
                        time.sleep(1.5)
                        sapu()
                        menu_member()
                        return
            else:
                produk = next((p for p in kategori_data["Produk"] if p["ID"] == pilihan), None)
                if not produk:
                    pesan1()
                    continue

                jumlah = int(input(f"\n{produk['Nama Produk']}nya Mau Berapa, Kak? (1-10): "))
                if 1 <= jumlah <= 10:
                    item_di_keranjang = next((item for item in keranjang if item["Nama Produk"] == produk["Nama Produk"]), None)
                    if item_di_keranjang:
                        if item_di_keranjang["Jumlah"] + jumlah > 10:
                            print("\n=================================")
                            print("--- Maksimal 10 / Produk ya Kak ---")
                            print("=================================")
                        else:
                            item_di_keranjang["Jumlah"] += jumlah
                            print(f"\n--- {jumlah} {produk['Nama Produk']} berhasil ditambahin ke keranjang! ---")
                    else:
                        keranjang.append({
                            "Nama Produk": produk["Nama Produk"],
                            "Harga Emoney": produk["Harga Emoney"],
                            "Harga Poin": produk["Harga Poin"],
                            "Jumlah": jumlah
                        })
                        print(f"\n--- {jumlah} {produk['Nama Produk']} berhasil ditambahin ke keranjang! ---")
                else:
                    print("\n====================================")
                    print("--- Jumlah harus antara 1 dan 10 ---")
                    print("====================================")
        except ValueError:
            pesan2()

    total_emoney = sum(item["Harga Emoney"] * item["Jumlah"] for item in keranjang)
    total_poin = sum(item["Harga Poin"] * item["Jumlah"] for item in keranjang)

    total_diskon = 0
    diskon_terpakai = {}

    while True:
        gunakan_voucher = input("\nMau Pakai Voucher untuk Diskon? (y/n): ").lower().strip()
        if gunakan_voucher == 'y':
            member = next((m for m in data_member if m["Username"] == member_sekarang), None)
            if member:
                kode_voucher = input("Masukin kode voucher: ").strip()
                voucher_dipakai = next((v for v in member["Voucher"] if v["Kode"] == kode_voucher and v["Status"] == "belum"), None)
                if voucher_dipakai:
                    diskon_voucher = voucher_dipakai["Diskon"] / 100
                    total_diskon += diskon_voucher
                    voucher_dipakai["Status"] = "sudah"
                    diskon_terpakai["Voucher"] = f"{voucher_dipakai['Diskon']}%"
                    time.sleep(1)
                    print("\n==============================================================")
                    print(f"--- Yeay! Voucher Berhasil Diredeem! Diskon {voucher_dipakai['Diskon']}% Diterapkan ---")
                    print("==============================================================")
                    save_data_member(data_member)
                    break
                else:
                    print("\n================================================")
                    print("--- Kode Voucher Ga Valid atau Udah Dipakai ---")
                    print("================================================")
            else:
                print("\n==============================")
                print("--- Data Member Ga Ditemukan ---")
                print("==============================")
                break
        elif gunakan_voucher == 'n':
            break
        else:
            print("\n======================================")
            print("--- Masukin 'y' atau 'n' Aja, Kak! ---")
            print("======================================")

    member = next((m for m in data_member if m["Username"] == member_sekarang), None)
    if member and member["Tingkat"] == "elite":
        diskon_member = 0.10
        total_diskon += diskon_member
        diskon_terpakai["Member"] = "10%"
        time.sleep(1)
        print("\n==================================================")
        print("--- Diskon Khusus Member Elite: 10% Diterapkan ---")
        print("==================================================")

    harga_awal = total_emoney
    total_emoney -= total_emoney * total_diskon
    total_poin = (harga_awal - (harga_awal * total_diskon)) / 1000
    time.sleep(1)
    print("\nIsi Keranjang:")
    tampilkan_keranjang(keranjang)
    print(f"\nTotal Harga (E-Money): Rp. {int(total_emoney)}")
    print(f"Total Harga (Poin): {total_poin} Poin")
    time.sleep(1)
    input("\nTekan Enter untuk Lanjut untuk Milih Opsi Pembayaran...")
    sapu()
    while True:
        print("\n+=========================================+")
        print("|             Opsi Pembayaran             |")
        print("+=========================================+")
        print("| [1] E-Money                             |")
        print("| [2] Poin Kopikir Sendiri                |")
        print("+=========================================+")

        opsi_pembayaran = input("\nMau pakai yang mana, Kak? (1/2): ").strip()

        if opsi_pembayaran == "1":
            for member in data_member:
                if member["Username"] == member_sekarang:
                    if member["Emoney"] < total_emoney:
                        print("\n===================================================")
                        print("--- Saldo E-Money Kakak Ga Cukup Buat Transaksi ---")
                        print("===================================================")
                        print(f"Saldo E-Money Kakak Sekarang: Rp. {int(member['Emoney'])}")
                        print(f"Total yang Dibutuhin: Rp. {int(total_emoney)}")
                        print("===================================================")
                        print(f"Berarti Kurang: Rp. {int(total_emoney - member['Emoney'])}")
                        print("===================================================")

                        while True:
                            topup_pilihan = input("\nApakah Kakak Mau Topup E-Money? (y/n): ").lower()
                            if topup_pilihan == 'y':
                                for x in range(3, 0, -1):
                                    time.sleep(1)
                                    sapu()
                                    print("+===============================================================+")
                                    print("|                Kakak Bakal Dialihin Untuk Topup               |")
                                    print(f"|                         Dalam {x} Detik                         |")
                                    print("+===============================================================+")

                                sapu()
                                topup_emoney()
                                data_member = load_data_member()
                                member = next((m for m in data_member if m["Username"] == member_sekarang), None)

                                if member["Emoney"] >= total_emoney:
                                    print("\n=========================================================")
                                    print("--- Saldo E-Money Kakak Sekarang Cukup Buat Transaksi ---")
                                    print("=========================================================")
                                    member["Emoney"] -= total_emoney
                                    save_data_member(data_member)
                                    input("\nTekan Enter Untuk Lanjut ke Validasi Pembayaran...")
                                    validasi_bayar(opsi_pembayaran, harga_awal, diskon_terpakai, total_emoney, total_poin)
                                    input("Tekan Enter Untuk Balik ke Menu...")
                                    sapu()      
                                    menu_member()
                                    break
                                else:
                                    print(f"\nSaldo E-Money Kakak Sekarang: Rp. {member['Emoney']}. Masih Belom Cukup.")

                            elif topup_pilihan == 'n':
                                print("\n======================================================")
                                print("--- Transaksi dibatalin. Makasih Udah Mampir, Kak! ---")
                                print("======================================================")
                                time.sleep(1)
                                sapu()
                                menu_member()
                            else:
                                print("\n======================================")
                                print("--- Masukin 'y' atau 'n' Aja, Kak! ---")
                                print("======================================")
                    else:
                        validasi_bayar(opsi_pembayaran, harga_awal, diskon_terpakai, total_emoney, total_poin)
                        member["Emoney"] -= total_emoney
                        save_data_member(data_member)
                        input("Tekan Enter Untuk Balik ke Menu...")
                        sapu()      
                        menu_member()
                        break
            break

        elif opsi_pembayaran == "2":
            for member in data_member:
                if member["Username"] == member_sekarang:
                    if member["Poin"] < total_poin:
                        print("\n==========================================")
                        print("--- Poin Kakak Ga Cukup Buat Transaksi ---")
                        print("==========================================")
                        print(f"Poin Kakak Sekarang: {member['Poin']} Poin")
                        print(f"Total yang Dibutuhin: {total_poin} Poin")
                        print("==========================================")
                        print(f"Berarti Kurang: {total_poin - member['Poin']} Poin")
                        print("==========================================")

                        while True:
                            topup_pilihan = input("\nApakah Kakak Mau Topup Poin KopikirSendiri? (y/n): ").lower()
                            if topup_pilihan == 'y':
                                for x in range(3, 0, -1):
                                    time.sleep(1)
                                    print("+===============================================================+")
                                    print("|                Kakak Bakal Dialihin Untuk Topup               |")
                                    print(f"|                         Dalam {x} Detik                         |")
                                    print("+===============================================================+")

                                sapu()
                                topup_poin()
                                data_member = load_data_member()
                                member = next((m for m in data_member if m["Username"] == member_sekarang), None)

                                if member["Poin"] >= total_poin:
                                    print("\n================================================")
                                    print("--- Poin Kakak Sekarang Cukup Buat Transaksi ---")
                                    print("================================================")
                                    member["Poin"] -= total_poin
                                    save_data_member(data_member)
                                    input("\nTekan Enter Untuk Lanjut ke Validasi Pembayaran...")
                                    validasi_bayar(opsi_pembayaran, harga_awal, diskon_terpakai, total_emoney, total_poin)
                                    input("Tekan Enter Untuk Balik ke Menu...")
                                    sapu()      
                                    menu_member()
                                    break
                                else:
                                    print(f"\nPoin Kakak sekarang: {member['Poin']} Poin. Masih belom cukup.")
                            elif topup_pilihan == 'n':
                                print("\n======================================================")
                                print("--- Transaksi dibatalin. Makasih Udah Mampir, Kak! ---")
                                print("======================================================")
                                time.sleep(1)
                                sapu()
                                menu_member()
                            else:
                                print("\n======================================")
                                print("--- Masukin 'y' atau 'n' Aja, Kak! ---")
                                print("======================================")
                    else:
                        input("\nTekan Enter Untuk Lanjut ke Validasi Pembayaran...")
                        validasi_bayar(opsi_pembayaran, harga_awal, diskon_terpakai, total_emoney, total_poin)
                        member["Poin"] -= total_poin
                        save_data_member(data_member)
                        input("Tekan Enter Untuk Balik ke Menu...")
                        sapu()      
                        menu_member()
                        break
            break
        else:
            print("\n=====================================")
            print("--- Pilihan Pembayaran Ga Valid ---")
            print("=====================================")
```
<p align="justify">Fungsi ini untuk mengelola pemesanan, dari menambahkan produk ke keranjang hingga pembayaran.</p>
</details>

<details>
<summary><h3>Fungsi Validasi Bayar</h3></summary>

```python
def validasi_bayar(opsi_pembayaran, harga_awal, diskon_terpakai, total_emoney, total_poin):
    data_member = load_data_member()
    global tingkat_member, member_sekarang, keranjang
    sisa_coba = 4
    val_berhasil = False
    sapu()

    while sisa_coba > 0:
        print("\n+==========================================+")
        print("|            Validasi Pembayaran           |")
        print("+==========================================+")
        try:
            print(f"\nUsername Kakak: {member_sekarang}")
            password = pwinput.pwinput("Masukin Passwordnya, Kak: ")

            for member in data_member:
                if member["Password"] == password:
                    tingkat_member = member["Tingkat"]
                    member_sekarang = member["Username"]
                    print("\n+==========================================+")
                    print("|          --- VALIDASI BERHASIL ---       |")
                    print("+==========================================+\n")
                    for x in range(3, 0, -1):
                        time.sleep(1)
                        print(f'Tunggu sebentar, Kak... Struknya lagi dibuat, selesai dalam {x} detik...')
                    sapu()
                    kode_transaksi = buat_kode_transaksi()
                    tanggal_transaksi = datetime.now().strftime("%d-%m-%Y %H:%M:%S")
                    print("\n+============================================= STRUK TRANSAKSI ========================================+")
                    print("                                 KopikirSendiri - Ngopi di Rumah Ala Cafe                                    ")
                    print("                                     Alamat: Jl. Pramuka VI, Samarinda                                      ")
                    print("                          Instagram: @kopikirsendiri | WA: 0821-4117-2579                                   ")
                    print("+========================================================================================================+")
                    print(f"{'Kode Transaksi':<45}{':':<3}{kode_transaksi:>55}")
                    print(f"{'Tanggal Transaksi':<45}{':':<3}{tanggal_transaksi:>55}")
                    print(f"{'Nama Member':<45}{':':<3}{member['Username'].capitalize():>55}")
                    print(f"{'Metode Pembayaran':<45}{':':<3}{'E-Money' if opsi_pembayaran == '1' else 'Poin KopikirSendiri':>55}")
                    print("+--------------------------------------------------------------------------------------------------------+")
                    print(f"{'Produk':<40}{'Harga E-Money':>15}{'Harga Poin':>15}{'Jumlah':>10}{'Subtotal':>23}")
                    print("+--------------------------------------------------------------------------------------------------------+")
                    for item in keranjang:
                        subtotal_emoney = item["Harga Emoney"] * item["Jumlah"]
                        subtotal_poin = item["Harga Poin"] * item["Jumlah"]
                        subtotal = subtotal_emoney if opsi_pembayaran == '1' else subtotal_poin
                        print(f"{item['Nama Produk']:<40}{'Rp.':<3}{item['Harga Emoney']:>12}{item['Harga Poin']:>15}{item['Jumlah']:>10}{subtotal:>23}")
                    print("+--------------------------------------------------------------------------------------------------------+")
                    print(f"{'Total Harga Awal (E-Money)':<70}: {'Rp.':<3}{harga_awal:>28}")
                    print(f"{'Total Harga Awal (Poin)':<70}: {harga_awal / 1000:>26} Poin")
                    if diskon_terpakai:
                        print("\nDiskon:")
                        for keterangan, nilai_diskon in diskon_terpakai.items():
                            print(f"{keterangan:<70}: {nilai_diskon:>31}")
                    print(f"\n{'Total Setelah Diskon (E-Money)':<70}: {'Rp.':<3}{int(total_emoney):>28}")
                    print(f"{'Total Setelah Diskon (Poin)':<70}: {total_poin:>26} Poin")
                    print("+========================================================================================================+")
                    print("                                     Terima Kasih Udah Belanja di KopikirSendiri!                                      ")
                    print("                                       Kami Tunggu Kunjungan Kakak Selanjutnya!                                        ")
                    print("+========================================================================================================+\n")
                    keranjang.clear()
                    val_berhasil = True
                    return

            if not val_berhasil:
                sisa_coba -= 1
                sapu()
                print("\n+==========================================+")
                print("|          --- VALIDASI GAGAL ---          |")
                print("+==========================================+")
                print(f"|          Sisa percobaan: {sisa_coba}x, Kak         |")
                print("+==========================================+")
                
                if sisa_coba == 0:
                    sapu()
                    print("\n+==========================================+")
                    print("|        Percobaan Udah Nyampe Batas       |")
                    print("|     Maksimal. Tunggu Sebentar Ya, Kak    |")
                    print("+==========================================+")
                    for x in range(3, 0, -1):
                        time.sleep(1)
                        print("\n+==========================================+")
                        print("|     Kakak Bakal Dialihin untuk Login     |")
                        print(f"|             Dalam {x} Detik                |")
                        print("+==========================================+")
                    sapu()
                    login()

        except (ValueError, KeyboardInterrupt):
            print("\n+==========================================+")
            print("|   Proses Dibatalkan atau Ada Kesalahan   |")
            print("+==========================================+")
        except Exception as e:
            print(f"Error Kak: {e}")
```
<p align="justify">Fungsi ini langkah terakhir sebelum transaksi dilakukan. Setelah pengguna melewati validasi, maka struk pembelian akan dicetak oleh program</p>
</details>

<details>
<summary><h3>Fungsi Menu E-Money</h3></summary>

```python
def menu_emoney():
    sapu()
    while True:
        print("+==============================================+")
        print(r"|   _____      __  __                          |")
        print(r"|  | ____|    |  \/  | ___  _ __   ___ _   _   |")
        print(r"|  |  _| _____| |\/| |/ _ \| '_ \ / _ | | | |  |")
        print(r"|  | |__|_____| |  | | (_) | | | |  __| |_| |  |")
        print(r"|  |_____|    |_|  |_|\___/|_| |_|\___|\__, |  |")
        print(r"|                                      |___/   |")
        print("+==============================================+")
        print("| [1] Cek Saldo E-Money & Poin KopikirSendiri  |")
        print("| [2] Tambah Saldo E-Money                     |")
        print("| [3] Tambah Poin KopikirSendiri               |")
        print("+==============================================+")
        try:
            pilihan = int(input("\nMau Ngapain Kak? (1-3 / 0 Untuk Balik): "))
            if pilihan == 1:
                cek_saldo()
            elif pilihan == 2:
                sapu()
                topup_emoney()
                input("\nTekan Enter Untuk Lanjut ke Menu...")
                sapu()
            elif pilihan == 3:
                sapu()
                topup_poin()
                input("\nTekan Enter Untuk Lanjut ke Menu...")
                sapu()
            elif pilihan == 0:
                sapu()
                return
            else:
                pesan1()
        except (ValueError, KeyboardInterrupt):
            pesan2()
        except Exception as e:
            print(f"Error Kak: {e}")
```
<p align="justify">Fungsi ini mengelola menu saldo dan poin.</p>
</details>

<details>
<summary><h3>Fungsi Cek Saldo</h3></summary>

```python
def cek_saldo():
    sapu()
    data_member = load_data_member()
    global tingkat_member, member_sekarang
    saldo = 0

    for member in data_member:
        if member["Tingkat"] == tingkat_member and member["Username"] == member_sekarang:
            saldo_emoney = member["Emoney"]
            saldo_poin = member["Poin"]
            break

    if tingkat_member == 'basic':
        print("+=========================================+")
        print("|        Cek Saldo E-Money & Poin         |")
        print("+=========================================+")
        print("|         Upgrade ke Elite Untuk          |")
        print("|             Nambahin Batas              |")
        print("|           Maksimal Saldo Jadi           |")
        print("|           Rp. 10.000.000 dan            |")
        print("|               10.000 Poin               |")
        print("+=========================================+")
    else:
        print("+=========================================+")
        print("|        Cek Saldo E-Money & Poin         |")
        print("+=========================================+")
        print("|       Selamat Untuk Kakak Member        |")
        print("|       Elite Kami, Batas Maksimal        |")
        print("|           Saldo Kakak Yaitu             |")
        print("|           Rp. 10.000.000 dan            |")
        print("|               10.000 Poin               |")
        print("+=========================================+")

    print("\n=====================================================")
    print(f"Saldo E-Money Kakak Jumlahnya: Rp. {saldo_emoney:,.0f}".replace(',', '.'))
    print(f"Saldo Poin KopikirSendiri Kakak Jumlahnya: {saldo_poin} Poin")
    print("=====================================================")

    input("\nTekan Enter Untuk Kembali ke Menu...")
    sapu()
```
<p align="justify">Fungsi ini mengecek saldo E-Money dan poin pengguna.</p>
</details>

<details>
<summary><h3>Fungsi TopUp E-Money dan Poin</h3></summary>

```python
def topup_emoney():
    data_member = load_data_member()
    global tingkat_member, member_sekarang
    max_saldo = 1000000 if tingkat_member == "basic" else 10000000

    
    while True:
        print("+=========================================+")
        print("|        Mo Topup E-Emoney Berapa?        |")
        print("+=========================================+")

        try:
            nominal = int(input(f"\nMasukin Nominalnya (Rp. 10000 - Rp. {max_saldo} / 0 Untuk Balik): Rp. "))

            if nominal == 0:
                return
            elif tingkat_member == 'elite' and not 10000 <= nominal <= 10000000:
                print("+==========================================+")
                print("|         Angka yang Normal Ya, Kak        |")
                print("+==========================================+")
                print("|        Antara 10.000 - 10.000.000        |")
                print("+==========================================+")
                continue
            elif tingkat_member == 'basic' and not 10000 <= nominal <= 1000000:
                print("+=========================================+")
                print("|        Angka yang Normal Ya, Kak        |")
                print("+=========================================+")
                print("|        Antara 10.000 - 1.000.000        |")
                print("+=========================================+")
                continue

            
            for member in data_member:
                if member["Username"] == member_sekarang:
                    max_saldo = 1000000 if member["Tingkat"] == "basic" else 10000000
                    lebar = 41
                    teks_max_saldo = f"Maksimal: Rp. {max_saldo:,.0f}".replace(',', '.')
                    teks_member = f"Untuk Member {tingkat_member.capitalize()}"

                    if member["Emoney"] + nominal > max_saldo:
                        print("+=========================================+")
                        print("|        Topup Gagal, Karena Nominal      |")
                        print("|           Bakal Ngelebihin Batas        |")
                        print("|           Maksimal Saldo E-Money        |")
                        print(f"|{teks_max_saldo.center(lebar)}|")
                        print(f"|{teks_member.center(lebar)}|")
                        print("+=========================================+")
                        return
                    
                    member["Emoney"] += nominal
                    save_data_member(data_member)
                    print("=====================================")
                    print(f"Rp. {nominal:,.0f}".replace(',', '.') + " Berhasil Ditambahkan!")
                    print("=====================================")
                    return
            else:
                print("====================================")
                print("Waduh, Topup Gagal. Coba Lagi Ya Kak")
                print("====================================")
                continue

        except (ValueError, KeyboardInterrupt):
            pesan2()
            continue
        except Exception as e:
            print(f"Error Kak: {e}")
            break

def topup_poin():
    data_member = load_data_member()
    global tingkat_member, member_sekarang
    konversi = 1000
    max_poin = 1000 if tingkat_member == "basic" else 10000

    while True:
        print("+=========================================+")
        print("|          Mo Topup Berapa Poin?          |")
        print("+=========================================+")
        print("| [1] 100 Poin (Rp. 100.000)              |")
        print("| [2] 200 Poin (Rp. 200.000)              |")
        print("| [3] 500 Poin (Rp. 500.000)              |")
        print("| [4] 1000 Poin (Rp. 1.000.000)           |")
        print("| [5] Nominal Lain                        |")
        print("+=========================================+")

        try:
            pilihan = int(input("Pilih Nominalnya (1-5 / 0 Untuk Balik): "))
            
            if pilihan == 0:
                return
            elif pilihan in [1, 2, 3, 4]:
                pil_nominal = {1: 100, 2: 200, 3: 500, 4: 1000}
                nominal = pil_nominal[pilihan]
            elif pilihan == 5:
                nominal = int(input("Masukin Nominalnya (dalam Poin): "))
                if not 0 < nominal <= max_poin:
                    print("==========================")
                    print("Angka yang Normal Ya, Kak")
                    print("==========================")
                    print(f"Antara 1 - {max_poin:,.0f}")
                    print("==========================")
                    continue
            else:
                pesan1()
                continue

            for member in data_member:
                if member["Username"] == member_sekarang:
                    total_poin = member["Poin"] + nominal
                    total_saldo = member["Emoney"] - (nominal * konversi)
                    teks_max_poin = f"Maksimal: Rp. {max_poin:,.0f}".replace(',', '.')
                    teks_member = f"Untuk Member {tingkat_member.capitalize()}"
                    lebar = 41

                    if total_poin > max_poin:
                        print("+=========================================+")
                        print("|       Topup Gagal, Karena Nominal       |")
                        print("|          Bakal Ngelebihin Batas         |")
                        print("|           Maksimal Jumlah Poin          |")
                        print(f"|{teks_member.center(lebar)}|")
                        print(f"|{teks_max_poin.center(lebar)}|")
                        print("+=========================================+")
                        return
                    
                    if total_saldo < 0:
                        print("+=========================================+")
                        print("|   Maaf, Saldo E-Money Kakak Ngga Cukup  |")
                        print("|        Mohon Topup Dulu Ya, Kak         |")
                        print("+=========================================+")
                        while True:
                            try:
                                tanya = input("\nApakah Kakak Mau Topup E-Money? (y/n): ").lower().strip()
                                if tanya == "y":
                                    sapu()
                                    topup_emoney()
                                    break
                                elif tanya == "n":
                                    return
                                else:
                                    print("+=========================================+")
                                    print("|      Masukin 'y' atau 'n' Aja, Kak      |")
                                    print("+=========================================+")
                                    continue
                            except (ValueError, KeyboardInterrupt):
                                pesan2()
                            except Exception as e:
                                print(f"Error Kak: {e}")
                        return

                    member["Poin"] = total_poin
                    member["Emoney"] = total_saldo
                    save_data_member(data_member)

                    print("====================================")
                    print(f"{nominal} Poin Berhasil Ditambahkan!")
                    print(f"Sisa Saldo: Rp. {member['Emoney']:,.0f}".replace(',', '.'))
                    print("====================================")
                    return
            else:
                print("=====================================")
                print("Waduh, Topup Gagal, Coba Lagi Ya, Kak")
                print("=====================================")
                continue

        except (ValueError, KeyboardInterrupt):
            pesan2()
            continue
        except Exception as e:
            print(f"Error Kak: {e}")
        break

```
<p align="justify">Fungsi ini menambah saldo atau poin pengguna.</p>
</details>

<details>
<summary><h3>Fungsi Up Tingkat</h3></summary>

```python
def up_tingkat():
    sapu()
    data_member = load_data_member() 
    global tingkat_member, member_sekarang

    print("+=========================================+")
    print("|            Upgrade Tier Member          |")
    print("+=========================================+")
    print("|      Keuntungan Jadi Member Elite       |")
    print("|             Kopikir Sendiri             |")
    print("+=========================================+")
    print("| - DURASI SEUMUR HIDUP LO KAK!           |")
    print("| - 10% Diskon di Setiap Pembelian!       |")
    print("| - Bonus 50 Poin KopikirSendiri GRATIS   |")
    print("|   Setelah Upgrade!                      |")
    print("| - Bonus 2 Voucher GRATIS Untuk Diskon   |")
    print(r"|   15% dan 10%!                          |")
    print("| - Aura +100 ;)                          |")
    print("+=========================================+")
    print("|          AYO UPGRADE SEKARANG!          |")
    print("+=========================================+\n")
    print("Biaya Upgrade: Rp. 500.000 / 500 Poin")

    while True:
        try:
            tanya = input("\nApakah Kakak Mau Jadi Member Elite KopikirSendiri? (y/n): ").lower()
            if tanya == "y":
                member = next((member for member in data_member if member["Username"] == member_sekarang), None)
                if not member:
                    print("\nError: Member tidak ditemukan.")
                    return

                if member["Tingkat"] == "elite":
                    print("\n====================================================")
                    print("Kakak Udah Jadi Member Elite, Ga Perlu Upgrade Lagi!")
                    print("====================================================")
                    break

                print("\n+=========================================+")
                print("|             Opsi Pembayaran             |")
                print("+=========================================+")
                print("| [1] E-Money (Rp. 500.000)               |")
                print("| [2] Poin Kopikir Sendiri (500 Poin)     |")
                print("+=========================================+")

                opsi_pembayaran = input("\nMo Pakai yang Mana, Kak? (1/2): ").strip()
                if opsi_pembayaran == "1":
                    if member["Emoney"] >= 500000:
                        member["Emoney"] -= 500000
                    else:
                        time.sleep(1)
                        print("\n====================================================")
                        print("Maaf, Saldo E-Money Kakak Ga Mencukupi Untuk Upgrade")
                        print("Topup Dulu Ya, Kak")
                        print("====================================================")
                        time.sleep(1)
                        input("\nTekan Enter Untuk Lanjut ke Menu...")
                        sapu()
                        break
                elif opsi_pembayaran == "2":
                    if member["Poin"] >= 500:
                        member["Poin"] -= 500
                    else:
                        time.sleep(1)
                        print("\n==================================================")
                        print("Maaf, Jumlah Poin Kakak Ga Mencukupi Untuk Upgrade")
                        print("Topup Dulu Ya, Kak")
                        print("==================================================")
                        time.sleep(1)
                        input("\nTekan Enter Untuk Lanjut ke Menu...")
                        sapu()
                        break
                else:
                    pesan1()
                    continue

                member["Tingkat"] = "elite"
                member["Poin"] += 50
                member["Voucher"].append({"Kode": "Kopikir15", "Diskon": 15, "Status": "belum"})
                member["Voucher"].append({"Kode": "Kopikir10", "Diskon": 10, "Status": "belum"})

                save_data_member(data_member)
                time.sleep(1)
                sapu()
                print("+======================================================+")
                print(r"|        _                           _  ___   ___      |")
                print(r"|       / \  _   _ _ __ __ _     _  / |/ _ \ / _ \     |")
                print(r"|      / _ \| | | | '__/ _` |  _| |_| | | | | | | |    |")
                print(r"|     / ___ | |_| | | | (_| | |_   _| | |_| | |_| |    |")
                print(r"|    /_/   \_\__,_|_|  \__,_|   |_| |_|\___/ \___/     |")
                print(r"|                                                      |")
                print("+======================================================+")
                print("| Selamat, Kakak Sekarang Member Elite KopikirSendiri! |")
                print("+======================================================+")
                print("| - Bonus 50 Poin KopikirSendiri Berhasil Ditambahkan! |")
                print("| - Bonus Voucher Diskon 10% dan 5% Ditambahkan!       |")
                print("+======================================================+")
                time.sleep(1)
                input("\nLogin Ulang Ya, Kak. Tekan Enter Untuk Lanjut...")
                tingkat_member = "elite"
                login()
                break

            elif tanya == "n":
                time.sleep(1)
                print("\n======================================")
                print("(: Owkay, Gajadi. Gapapa, Kak. Nekstim")
                print("======================================")
                input("\nTekan Enter Untuk Lanjut ke Menu...")
                sapu()
                break
            else:
                print("\n======================================")
                print("--- Masukin 'y' atau 'n' aja, Kak! ---")
                print("======================================")
        except (ValueError, KeyboardInterrupt):
            pesan2()
        except Exception as e:
            print(f"Error Kak: {e}")
```
<p align="justify">Fungsi ini adalah Fitur untuk upgrade status member ke elite, termasuk bonus tambahan.</p>
</details>

<details>
<summary><h3>JSON Data Menu</h3></summary>

```bash
{
    "Kategori": [
        {
            "Nama Kategori": "Pagi",
            "Produk": [
                {
                    "ID": 1,
                    "Nama Produk": "Espresso",
                    "Harga Emoney": 25000,
                    "Harga Poin": 25
                },
                {
                    "ID": 2,
                    "Nama Produk": "Americano",
                    "Harga Emoney": 30000,
                    "Harga Poin": 30
                },
                {
                    "ID": 3,
                    "Nama Produk": "Cappuccino",
                    "Harga Emoney": 35000,
                    "Harga Poin": 35
                },
                {
                    "ID": 4,
                    "Nama Produk": "Latte",
                    "Harga Emoney": 40000,
                    "Harga Poin": 40
                },
                {
                    "ID": 5,
                    "Nama Produk": "Flat White",
                    "Harga Emoney": 38000,
                    "Harga Poin": 38
                },
                {
                    "ID": 6,
                    "Nama Produk": "Caramel Macchiato",
                    "Harga Emoney": 45000,
                    "Harga Poin": 45
                },
                {
                    "ID": 7,
                    "Nama Produk": "Mocha",
                    "Harga Emoney": 42000,
                    "Harga Poin": 42
                },
                {
                    "ID": 8,
                    "Nama Produk": "Hazelnut Latte",
                    "Harga Emoney": 47000,
                    "Harga Poin": 47
                },
                {
                    "ID": 9,
                    "Nama Produk": "Vanilla Latte",
                    "Harga Emoney": 45000,
                    "Harga Poin": 45
                },
                {
                    "ID": 10,
                    "Nama Produk": "Affogato",
                    "Harga Emoney": 50000,
                    "Harga Poin": 50
                }
            ]
        },
        {
            "Nama Kategori": "Siang",
            "Produk": [
                {
                    "ID": 1,
                    "Nama Produk": "Cold Brew",
                    "Harga Emoney": 30000,
                    "Harga Poin": 30
                },
                {
                    "ID": 2,
                    "Nama Produk": "Iced Americano",
                    "Harga Emoney": 28000,
                    "Harga Poin": 28
                },
                {
                    "ID": 3,
                    "Nama Produk": "Iced Latte",
                    "Harga Emoney": 35000,
                    "Harga Poin": 35
                },
                {
                    "ID": 4,
                    "Nama Produk": "Iced Mocha",
                    "Harga Emoney": 40000,
                    "Harga Poin": 40
                },
                {
                    "ID": 5,
                    "Nama Produk": "Iced Caramel Macchiato",
                    "Harga Emoney": 45000,
                    "Harga Poin": 45
                },
                {
                    "ID": 6,
                    "Nama Produk": "Vanilla Sweet Cream Cold Brew",
                    "Harga Emoney": 52000,
                    "Harga Poin": 52
                },
                {
                    "ID": 7,
                    "Nama Produk": "Shaken Espresso",
                    "Harga Emoney": 48000,
                    "Harga Poin": 48
                },
                {
                    "ID": 8,
                    "Nama Produk": "Cold Foam Cappuccino",
                    "Harga Emoney": 46000,
                    "Harga Poin": 46
                },
                {
                    "ID": 9,
                    "Nama Produk": "Iced Chocolate",
                    "Harga Emoney": 38000,
                    "Harga Poin": 38
                },
                {
                    "ID": 10,
                    "Nama Produk": "Iced Matcha Latte",
                    "Harga Emoney": 40000,
                    "Harga Poin": 40
                }
            ]
        },
        {
            "Nama Kategori": "Malam",
            "Produk": [
                {
                    "ID": 1,
                    "Nama Produk": "Hot Chocolate",
                    "Harga Emoney": 35000,
                    "Harga Poin": 35
                },
                {
                    "ID": 2,
                    "Nama Produk": "Chai Tea Latte",
                    "Harga Emoney": 38000,
                    "Harga Poin": 38
                },
                {
                    "ID": 3,
                    "Nama Produk": "Matcha Latte",
                    "Harga Emoney": 40000,
                    "Harga Poin": 40
                },
                {
                    "ID": 4,
                    "Nama Produk": "Peppermint Mocha",
                    "Harga Emoney": 45000,
                    "Harga Poin": 45
                },
                {
                    "ID": 5,
                    "Nama Produk": "Hot Caramel Macchiato",
                    "Harga Emoney": 46000,
                    "Harga Poin": 46
                },
                {
                    "ID": 6,
                    "Nama Produk": "Pumpkin Spice Latte",
                    "Harga Emoney": 47000,
                    "Harga Poin": 47
                },
                {
                    "ID": 7,
                    "Nama Produk": "Honey Almond Flat White",
                    "Harga Emoney": 48000,
                    "Harga Poin": 48
                },
                {
                    "ID": 8,
                    "Nama Produk": "Irish Cream Cold Brew",
                    "Harga Emoney": 50000,
                    "Harga Poin": 50
                },
                {
                    "ID": 9,
                    "Nama Produk": "Toasted White Mocha",
                    "Harga Emoney": 52000,
                    "Harga Poin": 52
                },
                {
                    "ID": 10,
                    "Nama Produk": "Gingerbread Latte",
                    "Harga Emoney": 54000,
                    "Harga Poin": 54
                }
            ]
        }
    ]
}
```
<p align="justify">File JSON ini menyimpan daftar produk yang tersedia untuk dipesan. file ini yang dipanggil dalam fungsi muat_produk().</p>
</details>

<details>
<summary><h3>JSON Data Member</h3></summary>

```bash
[
    {
        "Username": "testvip",
        "Password": "testvip123",
        "Tingkat": "elite",
        "Emoney": 42250,
        "Poin": 50,
        "Voucher": [
            {
                "Kode": "Kopikir5",
                "Diskon": 5,
                "Status": "sudah"
            },
            {
                "Kode": "Kopikir15",
                "Diskon": 15,
                "Status": "belum"
            },
            {
                "Kode": "Kopikir10",
                "Diskon": 10,
                "Status": "sudah"
            }
        ]
    },
    {
        "Username": "test1234",
        "Password": "test1234",
        "Tingkat": "elite",
        "Emoney": 0,
        "Poin": 550,
        "Voucher": [
            {
                "Kode": "Kopikir5",
                "Diskon": 5,
                "Status": "belum"
            },
            {
                "Kode": "Kopikir15",
                "Diskon": 15,
                "Status": "belum"
            },
            {
                "Kode": "Kopikir10",
                "Diskon": 10,
                "Status": "belum"
            }
        ]
    }
]
```
<p align="justify">File JSON ini menyimpan data akun pengguna. mulai dari username, password, voucher, tingkat membership, dan saldo.</p>
</details>

## ⌨️ Petunjuk Instalasi dan Penggunaan

### Persyaratan Sistem
Pastikan sistem Anda memenuhi persyaratan berikut sebelum menjalankan program ini:

- **Python**: Versi 3.6 atau terkini. Anda bisa mengunduh Python dari [python.org](https://www.python.org/downloads/).
- **Git**: Pastikan Git terinstal di sistem Anda. Panduan instalasi Git ada di bagian selanjutnya.

### Langkah-Langkah Menjalankan Program

**1. Instalasi Git (Kalau belum terinstal)**

  1. Buka [Git untuk Windows](https://git-scm.com/downloads/win) dan unduh file instalasi. Pilih sesuai dengan spesifikasi atau ketentuan sistem yang anda gunakan.
  2. Jalankan file tersebut dan ikuti petunjuk instalasi.
  3. Setelah selesai, buka **Command Prompt** dan ketik `git --version` untuk memastikan Git terinstal dengan benar.

- **MacOS:**
  1. Buka **Terminal** dan ketik perintah berikut untuk menginstal Git:
     ```bash
     brew install git
     ```
   2. Jika tidak menggunakan Homebrew, Anda bisa mengunduh Git dari [Git-SCM](https://git-scm.com/download/mac).

- **Linux (Ubuntu/Debian):**
  1. Buka **Terminal** dan jalankan:
     ```bash
     sudo apt update
     sudo apt install git
     ```
  2. Ketik `git --version` untuk memastikan Git terinstal.

**2. Clone Repositori Proyek**

Buka terminal atau command prompt, lalu gunakan perintah berikut untuk mengunduh repositori ke komputer Anda:

  ```bash
  git clone https://github.com/ariscandra/UAS-Daspro.git
  ```
Perintah ini akan mengunduh semua file ke folder UAS-Daspro di direktori saat ini.

**3. Masuk ke Direktori Proyek**

Setelah repositori berhasil di-clone, masuk ke direktori proyek dengan perintah berikut:

  ```bash
  cd UAS-Daspro
  ```
**4. Instalasi Library yang Diperlukan**

Proyek ini menggunakan beberapa library eksternal seperti pwinput dan prettytable. Jalankan perintah berikut untuk menginstal library yang diperlukan:

  ```bash
  pip install pwinput prettytable
  ```
Program ini juga menggunakan library seperti json, time, datetime, random, os, dan string, yang tersedia di Python secara default.

**5. Menjalankan Program**

  ```bash
  python main.py
  ```

**6. Tampilan Program Ketika Berhasil Clone & Program Dijalankan**

```
C:\Users\Arcan>git clone https://github.com/ariscandra/UAS-Daspro.git
Cloning into 'UAS-Daspro'...
remote: Enumerating objects: 11, done.
remote: Counting objects: 100% (11/11), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 11 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (11/11), 12.11 KiB | 826.00 KiB/s, done.

C:\Users\Arcan>cd UAS-Daspro

C:\Users\Arcan\UAS-Daspro>python main.py
+====================================================================+
|  _  __            _  _    _       ___                _  _       _  |
| | |/ / ___  _ __ (_)| |__(_) _ _ / __| ___  _ _   __| |(_) _ _ (_) |
| | ' < / _ \| '_ \| || / /| || '_|\__ \/ -_)| ' \ / _` || || '_|| | |
| |_|\_\\___/| .__/|_||_\_\|_||_|  |___/\___||_||_|\__,_||_||_|  |_| |
|            |_|                                                     |
+--------------------------------------------------------------------+
|   Alloooo...!! Welcome to KopikirSendiri. Pengen Ngopi di Rumah    |
|         dengan Kualitas Caffe? Buruan Pesen disini, Kakak!         |
|                       (: KAMI BUKA 24/7 :)                         |
+--------------------------------------------------------------------+
|                            MENU UTAMA                              |
+--------------------------------------------------------------------+
|  [1] Daftar Member KopikirSendiri                                  |
|  [2] Login Member KopikirSendiri                                   |
|  [0] Keluar                                                        |
+====================================================================+

Mau Ngapain, Kak? (0-2):

```

---
> [!NOTE]
> **🎉 Terimakasih! 🎉**
> - Kepada Bapak Putut Pamilih Widagdo, S.Kom., M.Kom. dan Bapak Amin Padmo Azam Masa, S.Kom., M.Cs. Selaku dosen yang sudah membimbing, mengajar, dan mendidik saya dalam mata kuliah Dasar Pemrograman. 
> - Juga kepada teman-teman semua yang sudah membantu saya dalam menyelesaikan program ini. 🙏

---
[⬆️ Kembali ke Atas](#top)
<img src="https://github.com/user-attachments/assets/aebc142a-5c71-4f8c-b32b-b4a3c200bbe0" alt="" width="100%">
