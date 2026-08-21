# Connectivity Testing

## 1. Tujuan Pengujian

Pengujian dilakukan untuk memastikan konektivitas antar-VLAN berjalan melalui Core Multilayer Switch.

## 2. Metode Pengujian

Pengujian dilakukan menggunakan:

- ICMP Ping
- Pengujian komunikasi antar-VLAN
- Pengujian Internet Connectivty

## 3. Hasil Pengujian Antar VLAN

| Source | VLAN | Destination | VLAN | Hasil |
|---|---:|---|---:|---|
| PC0 | 10 | PC2 | 20 | PASS |
| PC0 | 10 | PC4 | 30 | PASS |
| PC0 | 10 | PC6 | 40 | PASS |
| PC0 | 10 | DNS Server | 50 | PASS |
| PC0 | 10 | PC8 | 60 | PASS |

## 4. Pengujian Internet Connectivity

Seluruh VLAN diuji untuk memastikan dapat mengakses jaringan eksternal melalui NAT/PAT pada Edge Router.

| Source VLAN | Destination | Hasil |
|---|---|---|
| VLAN 10 | 8.8.8.8 | PASS |
| VLAN 20 | 8.8.8.8 | PASS |
| VLAN 30 | 8.8.8.8 | PASS |
| VLAN 40 | 8.8.8.8 | PASS |
| VLAN 50 | 8.8.8.8 | PASS |
| VLAN 60 | 8.8.8.8 | PASS |

### Kesimpulan

Seluruh VLAN berhasil mencapai jaringan eksternal melalui Edge Router.

NAT/PAT berhasil menerjemahkan private IP address jaringan internal menuju IP interface WAN R1.

## 5. Security Testing — Guest Isolation

Pengujian dilakukan setelah penerapan Extended ACL `GUEST-ISOLATION` pada SVI VLAN 60.

### Before ACL

Sebelum ACL diterapkan, VLAN 60 dapat mengakses seluruh jaringan internal.

| Source | Destination | Result |
|---|---|---|
| VLAN 60 | VLAN 10 | PASS |
| VLAN 60 | VLAN 20 | PASS |
| VLAN 60 | VLAN 30 | PASS |
| VLAN 60 | VLAN 40 | PASS |
| VLAN 60 | VLAN 50 | PASS |
| VLAN 60 | Internet | PASS |

### After ACL

Setelah ACL diterapkan, akses Guest ke jaringan internal berhasil diblokir.

| Source | Destination | Result |
|---|---|---|
| VLAN 60 | VLAN 10 | DENY |
| VLAN 60 | VLAN 20 | DENY |
| VLAN 60 | VLAN 30 | DENY |
| VLAN 60 | VLAN 40 | DENY |
| VLAN 60 | VLAN 50 | DENY |
| VLAN 60 | Internet | PASS |

### Kesimpulan

ACL `GUEST-ISOLATION` berhasil menerapkan segmentasi jaringan untuk VLAN 60.

Guest tidak dapat mengakses jaringan internal perusahaan, tetapi tetap dapat mengakses jaringan eksternal melalui Internet.

**Security Policy: PASS ✅**

## 6. SSH Management Testing

Pengujian SSH dilakukan dari PC pada VLAN 10 Management.

| Device | Management IP | SSH | Result |
|---|---|---|---|
| CORE-SW | 10.10.10.1 | SSH v2 | PASS |
| ACCESS-SW1 | 10.10.10.2 | SSH v2 | PASS |
| ACCESS-SW2 | 10.10.10.3 | SSH v2 | PASS |
| ACCESS-SW3 | 10.10.10.4 | SSH v2 | PASS |

### Security Verification

- SSH version 2 enabled
- VTY hanya menerima SSH
- Local username digunakan untuk authentication
- Management dilakukan melalui VLAN 10
- SSH connectivity berhasil dari Management PC

## 7. Port Security Testing

Port Security diterapkan pada seluruh access port yang terhubung langsung ke PC.

### Konfigurasi Security

- Maximum MAC address: 1
- MAC address learning: Sticky
- Violation mode: Shutdown
- PortFast: Enabled
- Port Security: Enabled

### Verification

Seluruh access port yang terhubung ke PC menunjukkan status:

`Secure-up`

### Unauthorized Device Test

Pengujian dilakukan pada Access-SW1 Fa0/3 dengan mengganti PC asli menggunakan PC dengan MAC address berbeda.

Hasil pengujian:

- Port Security mendeteksi MAC address yang berbeda.
- Port masuk status `Secure-shutdown`.
- Security Violation Count meningkat menjadi `1`.
- Perangkat tidak dapat menggunakan port tersebut.

### Result

Port Security berhasil mencegah perangkat tidak terotorisasi menggunakan access port.

Status: **PASS**