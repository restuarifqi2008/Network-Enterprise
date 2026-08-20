# Desain Jaringan

## 1. Gambaran Project

**ARIFQI TECHNOLOGY Enterprise Network** adalah project simulasi infrastruktur jaringan perusahaan menggunakan Cisco Packet Tracer.

Project ini dibuat untuk menerapkan konsep Enterprise Network seperti VLAN, Layer 3 Switching, Inter-VLAN Routing, Network Services, Network Security, dan pengujian konektivitas.

## 2. Arsitektur Jaringan

Jaringan terdiri dari:

* 1 Edge Router
* 1 Core Multilayer Switch
* 3 Access Switch
* 10 PC Client
* 2 Server

### Alur Jaringan

```text
Internet
   │
Edge Router
   │
Core MLS
   │
   ├── Access Switch 1
   ├── Access Switch 2
   └── Access Switch 3
```

Core Multilayer Switch digunakan untuk melakukan Inter-VLAN Routing, sedangkan Edge Router nantinya digunakan untuk koneksi ke jaringan eksternal dan NAT.

## 3. Segmentasi Jaringan

Jaringan dibagi menjadi beberapa VLAN berdasarkan departemen dan fungsi:

| VLAN | Nama       | Fungsi                      |
| ---: | ---------- | --------------------------- |
|   10 | MANAGEMENT | Departemen Management       |
|   20 | IT         | Departemen IT               |
|   30 | FINANCE    | Departemen Finance          |
|   40 | HR         | Departemen HR               |
|   50 | SERVER     | Network Services dan Server |
|   60 | GUEST      | Pengguna Tamu               |

## 4. Tujuan Desain

Desain jaringan ini bertujuan untuk:

* Memisahkan setiap departemen menggunakan VLAN
* Mengurangi broadcast yang tidak diperlukan
* Memungkinkan komunikasi antar-VLAN
* Menyediakan routing terpusat menggunakan Core MLS
* Mengisolasi jaringan Guest dari jaringan internal
* Mempersiapkan jaringan untuk penerapan security policy
* Membuat infrastruktur yang mudah dikembangkan

## 5. Teknologi yang Digunakan

* Cisco Packet Tracer
* Cisco IOS
* VLAN
* 802.1Q Trunking
* Multilayer Switching
* Inter-VLAN Routing
* DHCP
* DNS
* NAT
* ACL
* STP
