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