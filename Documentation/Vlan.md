# Konfigurasi VLAN

## 1. Pembagian VLAN

VLAN digunakan untuk memisahkan jaringan berdasarkan departemen dan fungsi.

| VLAN | Nama       | Fungsi                      |
| ---: | ---------- | --------------------------- |
|   10 | MANAGEMENT | Management                  |
|   20 | IT         | Departemen IT               |
|   30 | FINANCE    | Departemen Finance          |
|   40 | HR         | Departemen HR               |
|   50 | SERVER     | Server dan Network Services |
|   60 | GUEST      | Pengguna Tamu               |

## 2. Topologi VLAN

```text
                    Core MLS
                       │
          ┌────────────┼────────────┐
          │            │            │
         SW1          SW2          SW3
          │            │            │
       VLAN 10/20    VLAN 30/40    VLAN 60
```

## 3. Konfigurasi Trunk

Koneksi antara Core MLS dan Access Switch menggunakan trunk 802.1Q.

VLAN yang diizinkan melewati trunk:

```text
10,20,30,40,50,60
```

Koneksi trunk:

```text
Core MLS Fa0/2 → Access SW1 Fa0/1
Core MLS Fa0/3 → Access SW2 Fa0/1
Core MLS Fa0/4 → Access SW3 Fa0/1
```

## 4. Pembagian Access Port

### Access SW1

```text
Fa0/2 → VLAN 10
Fa0/3 → VLAN 10
Fa0/4 → VLAN 20
Fa0/5 → VLAN 20
```

### Access SW2

```text
Fa0/2 → VLAN 30
Fa0/3 → VLAN 30
Fa0/4 → VLAN 40
Fa0/5 → VLAN 40
```

### Access SW3

```text
Fa0/2 → VLAN 60
Fa0/3 → VLAN 60
```

### Server

DNS Server dan Web Server terhubung langsung ke Core MLS menggunakan access port pada VLAN 50.

## 5. Verifikasi

Konfigurasi VLAN dan trunk diverifikasi menggunakan:

```text
show vlan brief
show interfaces trunk
```

Hasil verifikasi menunjukkan bahwa VLAN dan trunk telah berjalan sesuai desain.
