# konfigurasi mikroti
langkah " konfigurasi mikrotik
Login ke MikroTik:
1. Hubungkan komputer ke MikroTik dengan kabel LAN (biasanya ke Ether2).
2. Buka Winbox, klik Refresh, lalu pilih MAC Address perangkat MikroTik. 
3. Username: admin (kosongkan password), klik Connect.
4. Pilih Remove Configuration untuk memulai dari awal (opsional, tapi disarankan).
 
Konfigurasi Interface:
1. IP Address: Klik IP > Addresses, klik +, isi IP untuk interface LAN (misal 192.168.1.1/24 di Ether2), klik OK.
2. DHCP Client (untuk internet): Klik IP > DHCP Client, klik +, pilih interface WAN (misal ether1), pastikan Add Default Route dicentang, klik OK.
 
Konfigurasi Layanan Jaringan:
1. DNS: Klik IP > DNS, masukkan DNS ISP (misal Google DNS 8.8.8.8 atau DNS ISP), centang Allow Remote Requests, klik OK.
2. NAT (Masquerade): Klik IP > Firewall > tab NAT, klik +, pada Chain pilih srcnat, pada Out. Interface pilih interface WAN (ether1), ke tab Action, pilih masquerade, klik OK.
3. DHCP Server (untuk client): Klik IP > DHCP Server, klik DHCP Setup, ikuti wizard untuk mengatur IP Pool dan DNS untuk jaringan lokal Anda (di interface LAN, misal ether2).
 
Tes Koneksi:
Buka New Terminal di Winbox, ketik ping google.com atau ping 8.8.8.8 untuk memastikan internet sudah terhubung.
Pastikan di IP > Addresses interface LAN sudah mendapatkan IP, dan IP > Routes ada default route 0.0.0.0/0 dengan gateway dari ISP. 

Konfigurasi Tambahan (jika perlu):
Bridge: Untuk menggabungkan beberapa port LAN (misal Ether2, Ether3) menjadi satu jaringan, buat Bridge di Bridge, lalu tambahkan port-port tersebut di tab Ports. 
