# Network Security

## 1. Tujuan Keamanan

Keamanan jaringan dirancang untuk:

* Membatasi komunikasi antar-VLAN
* Mengisolasi jaringan Guest
* Melindungi Server
* Membatasi akses antar-departemen
* Mengamankan akses administrasi perangkat
* Mengurangi akses jaringan yang tidak diperlukan

## 2. Segmentasi Keamanan

Jaringan akan dibagi menjadi beberapa zona:

```text
Management
     │
     ├── IT
     ├── Finance
     ├── HR
     └── Server

Guest
     │
     └── Internet
```

Guest tidak seharusnya memiliki akses langsung ke jaringan internal perusahaan.

## 3. Security Policy

Rancangan policy awal:

| Source     | Destination      | Akses |
| ---------- | ---------------- | ----- |
| Management | Internal Network | Allow |
| IT         | Server           | Allow |
| Finance    | Server           | Allow |
| HR         | Server           | Allow |
| Guest      | Internal Network | Deny  |
| Guest      | Internet         | Allow |

## 4. Security yang Akan Diimplementasikan

Pada tahap security, kita akan menerapkan:

* Extended ACL
* Pembatasan Inter-VLAN
* Guest Network Isolation
* SSH
* Port Security
* STP Security
* Shutdown unused ports
* Native VLAN Hardening
* Pembatasan Management Access

## 5. Pengujian Security

Setelah security policy diterapkan, pengujian akan dilakukan menggunakan:

```text
ping
tracert
```

Tujuannya untuk memastikan traffic yang diizinkan dapat berjalan dan traffic yang tidak diizinkan berhasil diblokir.

> **Status:** Security configuration belum selesai dan akan diperbarui setelah tahap implementasi ACL dan network hardening.
