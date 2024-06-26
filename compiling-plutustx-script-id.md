# Pendahuluan

Dokumentasi ini menyediakan panduan langkah demi langkah yang disederhanakan mengenai cara mengompilasi skrip PlutusTx menjadi UPLC. Jika Anda berhasil mengompilasi skrip, Anda akan menemukan file dengan ekstensi **_.plutus_**, yang merupakan UPLC atau Plutus Script, Skrip ini memiliki format CBOR yang akan digunakan secara on-chain.

Ketika menginstal Plutus environment di mesin lokal kita, hal itu membutuhkan usaha yang signifikan. Namun, ada alternatifnya, kita dapat menggunakan [demeter.run](https://demeter.run/) yang menyediakan infrastruktur, tools, library di Cardano, dan tentu saja ada Plutus environment.

# Langkah-langkah

## Step-1 Setup Demeter

1. Gunakan [demeter.run](https://demeter.run/), jika Anda belum memiliki akun, maka buatlah akun baru.
2. Tambahkan resource dan pilih workspace.
3. Pada bagian toolchain, pilih PlutusTx.
4. Pilih ukuran large workspace.
5. Pilih network. Pada contoh kali ini, kita akan menggunakan Preprod.
6. Jalankan workspace dan tunggu sebentar. Setelah penyiapan selesai, maka buka fitur VSCode browser.

## Step-2 Buka Terminal Bash di VSCode

1. Clone Dari Repositori Gimbalabs PPBL2023 Plutus Template

   ```bash
   git clone https://gitlab.com/gimbalabs/ppbl-2023/ppbl2023-plutus-template.git
   ```

2. Menuju Direktori PPBL2023 Plutus Template

   ```bash
   cd ppbl2023-plutus-template
   ```

3. Buat Direktori Output Dimana Ini Adalah Tempatnya File .plutus

   ```bash
   mkdir output
   ```

4. Jalankan Cabal

   ```bash
   cabal update
   cabal repl
   ```

5. Ketika masuk repl, jalankan:

   ```repl
   writeAlwaysSucceedsScript
   ```

## Step-3 Lihat Hasilnya

Jika Anda berhasil menjalankan skrip writeAlwaysSucceedsScript, di terminal akan muncul **_right()_**, dan di dalam direktori output, Anda akan menemukan sebuah file bernama **_always-succeeds.plutus_**, seperti yang ditunjukkan dalam gambar di bawah ini:

![right-result](public/right-result.png)

![always-succeeds.plutus](public/plutustx-script-compiled.png)

Selamat! Anda telah berhasil mengompilasi skrip validator PlutusTx menjadi UPLC.

# Demo

Berikut adalah video yang direkam oleh Komunitas Developer Cardano Indonesia di mana saya menjelaskan langkah-langkah di atas. Tonton video yang direkam pada timestamp **_1:27:27_** di [link](https://youtu.be/03hXLZ_07N0?list=PLUj8499OocHiL8gXPv8wMlLW-zIcyYdrQ) berikut ini.

# Referensi

[Gimbalabs PPBL2023 Module 101: Plutus Terminology](https://plutuspbl.io/modules/101/slts)

[Gimbalabs PPBL2023 Module 101.1: Introducing UPLC](https://plutuspbl.io/modules/101/1011)

[Gimbalabs PPBL2023 Module 101.2: The Role of UPLC](https://plutuspbl.io/modules/101/1012)

[Gimbalabs PPBL2023 Module 101.3: Compiling PlutusTx](https://plutuspbl.io/modules/101/1013)

[Cardano Developer Portal: Plutus](https://developers.cardano.org/docs/smart-contracts/plutus/)

[Demeter](https://demeter.run/)
