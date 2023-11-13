# Nama    : Jesica Trivena Sinaga
# NIM     : A11.2021.13808
# Kelomok : A11.4329

def remove_duplicate_chars(text):
    # Fungsi ini akan menghapus karakter yang duplikat dari teks
    return ''.join(sorted(set(text), key=text.index))

def add_missing_chars(text, key):
    # Fungsi ini akan menambahkan karakter yang hilang dalam kunci
    alphabet = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
    missing_chars = ''.join(sorted(set(alphabet) - set(key)))
    return key + missing_chars

def create_cipher_table(key):
    # Fungsi ini akan membuat tabel enkripsi berdasarkan kunci
    alphabet = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
    cipher_table = {}
    for i in range(26):
        cipher_table[alphabet[i]] = key[i]
    return cipher_table

def encrypt(text, cipher_table):
    # Fungsi ini akan mengenkripsi teks menggunakan tabel enkripsi
    encrypted_text = ''
    for char in text:
        if char in cipher_table:
            encrypted_text += cipher_table[char]
        else:
            encrypted_text += char
    return encrypted_text

# Meminta input dari pengguna
plaintext = input("Masukkan plaintext: ").upper()
key = input("Masukkan kunci: ").upper()

# Menghilangkan karakter duplikat
unique_text = remove_duplicate_chars(plaintext)

# Menambahkan abjad yang belum ada
expanded_key = add_missing_chars(unique_text, key)

# Membuat tabel enkripsi
cipher_table = create_cipher_table(expanded_key)

# Mengenkripsi teks
ciphertext = encrypt(plaintext, cipher_table)

# Menampilkan hasil
print("Text setelah menghilangkan duplikasi:", unique_text)
print("Text setelah ditambahkan abjad yang belum ada:", expanded_key)
print("Tabel enkripsi:")
for char, replacement in cipher_table.items():
    print(f"{char} -> {replacement}")
print("Hasil Ciphertext:", ciphertext)
