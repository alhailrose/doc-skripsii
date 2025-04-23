---

# Dokumentasi API

## Gambaran Umum

API ini memungkinkan pengguna untuk mendaftar, masuk, dan keluar dari sistem. API ini menyediakan tiga endpoint utama:  
1. **/signup** - Mendaftar pengguna baru.  
2. **/signin** - Memvalidasi kredensial pengguna dan menghasilkan token akses.  
3. **/signout** - Keluar dari sistem dengan membatalkan token autentikasi.

## Deskripsi Endpoint

### 1. Mendaftar Pengguna (POST /signup)

- **Deskripsi**: Mendaftarkan pengguna baru ke dalam sistem dengan menyediakan nama, email, dan kata sandi.
- **Metode**: `POST`
- **Format Permintaan**:
```json
{
  "name": "Test",
  "email": "test1@gmail.com",
  "password": "Baguskeren77"
}
```
- **Respons (Sukses)**:
```json
{
  "status": "success",
  "message": "Pengguna berhasil dibuat",
  "data": {
    "name": "Test",
    "email": "test1@gmail.com"
  }
}
```
- **Respons (Error)**:
```json
{
  "status": "failed",
  "message": "error.message"
}
```

### 2. Masuk Pengguna (POST /signin)

- **Deskripsi**: Masuk ke sistem menggunakan email dan kata sandi. Jika kredensial valid, token akses akan dikembalikan untuk digunakan dalam permintaan berikutnya.
- **Metode**: `POST`
- **Format Permintaan**:
```json
{
  "email": "test1@gmail.com",
  "password": "Baguskeren77"
}
```
- **Respons (Sukses)**:
```json
{
  "status": "success",
  "user_id": "nqKeaO1vLxHM",
  "name": "Test",
  "email": "test1@gmail.com",
  "access_token": "your_access_token",
  "message": "Login sukses"
}
```
- **Respons (Error)**:
```json
{
  "status": "failed",
  "message": "error.message"
}
```

### 3. Keluar Pengguna (POST /signout)

- **Deskripsi**: Keluar dari sistem dengan membatalkan token autentikasi. Token harus disertakan di header Authorization sebagai Bearer token.
- **Metode**: `POST`
- **Header**:
  - `Authorization: Bearer <access_token>`
- **Format Permintaan**:
```json
{}
```
- **Respons (Sukses)**:
```json
{
  "status": "success",
  "message": "Keluar sukses",
  "data": null
}
```
- **Respons (Error)**:
```json
{
  "status": "failed",
  "message": "error.message"
}
```

## Penanganan Error

Semua respons error akan memiliki struktur sebagai berikut:
```json
{
  "status": "failed",
  "message": "error.message"
}
```

## Catatan

- Pastikan pengguna menyediakan kredensial yang valid selama proses pendaftaran dan masuk.
- Token Bearer harus disertakan di header untuk endpoint keluar (signout) agar dapat berfungsi dengan baik.

---
