# Pendahuluan

Dokumentasi ini menyediakan panduan langkah demi langkah yang disederhanakan mengenai cara mengompilasi skrip Aiken menjadi UPLC. Setelah Anda berhasil mengkompilasi skrip, jalankan _'aiken blueprint convert'_ di terminal. Anda akan melihat UPLC, yang memiliki format CBOR yang akan digunakan secara on-chain.

# Langkah-langkah

Dalam dokumentasi ini, terdapat dua metode untuk menyiapkan environment. Kita dapat menggunakan demeter.run atau mesin lokal kita, pilih salah satu.

## Step-1 Setup Environment

### Demeter

1. Gunakan demeter.run, jika Anda belum memiliki akun, maka buatlah akun baru.
2. Tambahkan resource dan pilih workspace.
3. Pada bagian toolchain, pilih Aiken.
4. Pilih ukuran large workspace.
5. Pilih network. Pada contoh kali ini, kita akan menggunakan Preprod.
6. Jalankan workspace dan tunggu sebentar. Setelah penyiapan selesai, maka buka fitur VSCode browser.

### Lokal

1. Instalasi Cargo / Rust Package Manager
   Jika Anda menggunakan Linux / macOS, eksekusi:

   ```bash
   curl https://sh.rustup.rs -sSf | sh
   ```

   Jika Anda menggunakan Windows, download lalu eksekusi [rustup-init.exe](https://win.rustup.rs/)

   **_Kemudian muncul seperti ini:_**

   ```text
   1. Quick install via the Visual Studio Community installer
      (free for individuals, academic uses, and open source).

   2. Manually install the prerequisites
      (for enterprise and advanced users).

   3. Don't install the prerequisites
      (if you're targeting the GNU ABI).
   ```

   **_Rekomendasi pilih nomor 1_**

   ```text
   1) Proceed with standard installation (default - just press enter)
   2) Customize installation
   3) Cancel installation
   ```

   **_Rekomendasi pilih nomor 1_**

2. Periksa Versi Rust dan Cargo

   **_Petunjuk: Setelah proses instalasi selesai, sebaiknya restart terminal_**

   ```bash
   rustc --version
   cargo --version
   ```

3. Instalasi Aiken

   ```bash
   cargo install aiken --version 1.0.24-alpha
   ```

   **_Catatan: Untuk mendapatkan Aiken versi terbaru, kunjungi [Aiken Installation Intructions Official Site](https://aiken-lang.org/installation-instructions)_**

4. Periksa Versi Aiken

   **_Petunjuk: Setelah proses instalasi selesai, sebaiknya restart terminal_**

   ```bash
   aiken --version
   ```

   **_Catatan: Anda mengetahui bahwa Aiken berhasil terinstall jika dapat melihat versi Aiken tersebut_**

## Step-2 Buka Terminal Bash di VSCode

1. Buat Proyek Aiken Baru

   ```bash
   aiken new aiken-lang/aiken-template
   ```

2. Menuju direktori aiken-template

   ```bash
   cd aiken-template
   ```

3. Membuat File always_succeeds.ak, Yang Merupakan Skrip Validator

   ```bash
   touch validators/always_succeeds.ak
   ```

4. Copy dan Paste Contoh Skrip Validator Berikut ke File always_succeeds.ak

   ```rust
   validator {
     fn always_succeed(_datum: Data, _redeemer: Data, _context: Data) -> Bool {
         True
     }
   }
   ```

   **_Catatan: Ini adalah contoh validator sederhana yang outputnya selalu berlogika true._**

5. Build / Kompilasi Skrip Validator

   ```bash
   aiken build
   ```

## Step-3 Lihat Hasilnya

1. Buat Direktori Output dan File always-succeeds.plutus

   ```bash
   mkdir -p output && touch output/always-succeeds.plutus
   ```

2. Blueprint Convert

   ```bash
   aiken blueprint convert
   ```

   **_Petunjuk: Setelah menjalankan perintah blueprint convert, maka akan muncul di terminal seperti terlihat pada gambar di bawah ini_**

   ![blueprint-convert](public/blueprint-convert.jpg)

3. Copy dan paste template UPLC yang muncul di terminal ke File always-succeeds.plutus

# Demo

Berikut adalah video yang direkam oleh Komunitas Developer Cardano Indonesia di mana saya menjelaskan langkah-langkah di atas. Tonton video yang direkam pada timestamp **_1:27:27_** di [link](https://youtu.be/03hXLZ_07N0?list=PLUj8499OocHiL8gXPv8wMlLW-zIcyYdrQ) berikut ini.

# Referensi

[Gimbalabs PPBL2023 Module 101: Plutus Terminology](https://plutuspbl.io/modules/101/slts)

[Gimbalabs PPBL2023 Module 101.1: Introducing UPLC](https://plutuspbl.io/modules/101/1011)

[Gimbalabs PPBL2023 Module 101.2: The Role of UPLC](https://plutuspbl.io/modules/101/1012)

[Gimbalabs PPBL2023 Module 101.5: Compiling Aiken](https://plutuspbl.io/modules/101/1015)

[Cardano Developers Portal: Plutus](https://developers.cardano.org/docs/smart-contracts/plutus/)

[Demeter](https://demeter.run/)
