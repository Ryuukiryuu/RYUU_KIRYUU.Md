TUGAS PERTEMUAN KE-10
PRAKTIKUM 6

berikut penjelasan dari kode tersebut :

1. **Struktur Data:**
```python
mahasiswa = {}
```
- Membuat dictionary kosong bernama `mahasiswa` untuk menyimpan data
- Format data dalam dictionary:
  ```python
  {
      "nama_mahasiswa": {
          "tugas": nilai_tugas,
          "uts": nilai_uts,
          "uas": nilai_uas,
          "nilai_akhir": nilai_akhir
      }
  }
  ```

2. **Fungsi tambah_data():**
```python
def tambah_data():
    print("\n=== TAMBAH DATA MAHASISWA ===")
    nama = input("Masukkan Nama: ")
    if nama in mahasiswa:  # Cek apakah nama sudah ada
        print("Data mahasiswa sudah ada!")
        return
    
    try:
        # Input nilai
        tugas = float(input("Nilai Tugas (0-100): "))
        uts = float(input("Nilai UTS (0-100): "))
        uas = float(input("Nilai UAS (0-100): "))
        
        # Validasi rentang nilai
        if not (0 <= tugas <= 100 and 0 <= uts <= 100 and 0 <= uas <= 100):
            print("Nilai harus berada dalam rentang 0-100!")
            return
        
        # Hitung nilai akhir
        nilai_akhir = (tugas * 0.3) + (uts * 0.35) + (uas * 0.35)
        
        # Simpan ke dictionary
        mahasiswa[nama] = {
            "tugas": tugas,
            "uts": uts,
            "uas": uas,
            "nilai_akhir": nilai_akhir
        }
        print("Data berhasil ditambahkan!")
        
    except ValueError:
        print("Masukkan nilai dalam bentuk angka!")
```

3. **Fungsi ubah_data():**
```python
def ubah_data():
    print("\n=== UBAH DATA MAHASISWA ===")
    nama = input("Masukkan Nama: ")
    if nama not in mahasiswa:  # Cek apakah nama ada
        print("Data mahasiswa tidak ditemukan!")
        return
    
    # Proses mirip dengan tambah_data()
    # Tapi menimpa data yang sudah ada
```

4. **Fungsi hapus_data():**
```python
def hapus_data():
    print("\n=== HAPUS DATA MAHASISWA ===")
    nama = input("Masukkan Nama: ")
    if nama in mahasiswa:
        del mahasiswa[nama]  # Hapus data dari dictionary
        print("Data berhasil dihapus!")
    else:
        print("Data mahasiswa tidak ditemukan!")
```

5. **Fungsi tampilkan_data():**
```python
def tampilkan_data():
    print("\n=== DAFTAR NILAI MAHASISWA ===")
    if not mahasiswa:  # Cek apakah dictionary kosong
        print("Belum ada data mahasiswa!")
        return
    
    # Tampilkan header tabel
    print("\nNama\t\tTugas\tUTS\tUAS\tNilai Akhir")
    print("-" * 50)
    # Loop untuk menampilkan setiap data
    for nama, nilai in mahasiswa.items():
        print(f"{nama}\t\t{nilai['tugas']:.1f}\t{nilai['uts']:.1f}\t{nilai['uas']:.1f}\t{nilai['nilai_akhir']:.1f}")
```

6. **Fungsi cari_data():**
```python
def cari_data():
    print("\n=== CARI DATA MAHASISWA ===")
    nama = input("Masukkan Nama: ")
    if nama in mahasiswa:
        nilai = mahasiswa[nama]
        # Tampilkan data mahasiswa yang dicari
        print("\nData ditemukan!")
        print(f"Nama: {nama}")
        print(f"Nilai Tugas: {nilai['tugas']}")
        print(f"Nilai UTS: {nilai['uts']}")
        print(f"Nilai UAS: {nilai['uas']}")
        print(f"Nilai Akhir: {nilai['nilai_akhir']:.1f}")
    else:
        print("Data mahasiswa tidak ditemukan!")
```

7. **Fungsi main() dan Menu Utama:**
```python
def main():
    while True:
        # Tampilkan menu
        print("\n=== PROGRAM NILAI MAHASISWA ===")
        print("1. Tambah Data")
        print("2. Ubah Data")
        print("3. Hapus Data")
        print("4. Tampilkan Data")
        print("5. Cari Data")
        print("0. Keluar")
        
        pilihan = input("\nPilih menu (0-5): ")
        
        # Proses pilihan menu
        if pilihan == "1":
            tambah_data()
        elif pilihan == "2":
            ubah_data()
        # ... dan seterusnya
```

**Penjelasan Fitur Penting:**

1. **Penanganan Error:**
   - Menggunakan `try-except` untuk menangani input nilai yang tidak valid
   - Validasi rentang nilai (0-100)
   - Pengecekan keberadaan data sebelum operasi

2. **Format Output:**
   - Menggunakan `\t` (tab) untuk merapikan tampilan tabel
   - Format angka desimal menggunakan `.1f` untuk 1 angka di belakang koma
   - Garis pemisah `-` * 50 untuk estetika

3. **Dictionary Nested:**
   - Menggunakan dictionary dalam dictionary untuk organisasi data yang baik
   - Memudahkan akses dan modifikasi data

4. **Menu Loop:**
   - Program berjalan terus dalam loop `while True`
   - Baru berhenti jika user memilih menu 0 (Keluar)

5. **Perhitungan Nilai:**
   - Nilai akhir = (Tugas × 30%) + (UTS × 35%) + (UAS × 35%)
   - Menggunakan pembobotan sesuai ketentuan

Apakah ada bagian tertentu yang ingin Anda pahami lebih dalam?
