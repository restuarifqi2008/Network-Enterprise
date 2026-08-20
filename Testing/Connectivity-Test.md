# Connectivity Testing

## 1. Tujuan Pengujian

Pengujian dilakukan untuk memastikan konektivitas antar-VLAN berjalan melalui Core Multilayer Switch.

## 2. Metode Pengujian

Pengujian dilakukan menggunakan:

- ICMP Ping
- Pengujian komunikasi antar-VLAN

## 3. Hasil Pengujian

| Source | VLAN | Destination | VLAN | Hasil |
|---|---:|---|---:|---|
| PC0 | 10 | PC2 | 20 | PASS |
| PC0 | 10 | PC4 | 30 | PASS |
| PC0 | 10 | PC6 | 40 | PASS |
| PC0 | 10 | DNS Server | 50 | PASS |
| PC0 | 10 | PC8 | 60 | PASS |

## 4. Detail Pengujian

### VLAN 10 → VLAN 20

```text
Source      : PC0
IP Address  : 10.10.10.10
Destination : PC2
IP Address  : 10.10.20.10

Command:
ping 10.10.20.10

Result: PASS