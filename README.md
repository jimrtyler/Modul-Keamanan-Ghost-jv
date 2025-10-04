# 👻 Modul Keamanan Ghost
**Piranti Pengerasan Keamanan Windows & Azure Adhedhasar PowerShell**

> **Pengerasan keamanan proaktif kanggo endpoint Windows lan lingkungan Azure.** Ghost nyediakake fungsi pengerasan adhedhasar PowerShell sing bisa mbantu ngurangi vektor serangan umum kanthi mateni layanan lan protokol sing ora perlu.

## ⚠️ Penafian Penting

**TESTING DIBUTUHAKE**: Tansah test Ghost ing lingkungan non-produksi dhisik. Mateni layanan bisa mengaruhi fungsi bisnis sing sah.

**ORA ANA JAMINAN**: Senajan Ghost ngarahake vektor serangan umum, ora ana piranti keamanan sing bisa nyegah kabeh serangan. Iki minangka salah sawijining komponen saka strategi keamanan komprehensif.

**DAMPAK OPERASIONAL**: Sawetara fungsi bisa mengaruhi fungsionalitas sistem. Deleng saben setelan kanthi teliti sadurunge deployment.

**PENILAIAN PROFESIONAL**: Kanggo lingkungan produksi, konsultasi karo profesional keamanan kanggo mesthekake setelan selaras karo kabutuhan organisasi sampeyan.

## 📊 Lanskap Keamanan

Kerusakan ransomware tekan **$57 milyar ing taun 2025**, kanthi riset nuduhake yen akeh serangan sukses ngeksploitasi layanan Windows dhasar lan konfigurasi sing salah. Vektor serangan umum kalebu:

- **90% insiden ransomware** nglibatake eksploitasi RDP
- **Kerentanan SMBv1** ngidini serangan kaya WannaCry lan NotPetya  
- **Makro dokumen** tetep dadi metode utama pengiriman malware
- **Serangan adhedhasar USB** terus ngarahake jaringan air-gapped
- **Penyalahgunaan PowerShell** wis mundhak banget ing taun-taun pungkasan

## 🛡️ Fungsi Keamanan Ghost

Ghost nyediakake **16 fungsi pengerasan Windows** plus **integrasi keamanan Azure**:

### Pengerasan Endpoint Windows

| Fungsi | Tujuan | Pertimbangan |
|----------|---------|----------------|
| `Set-RDP` | Ngatur akses Remote Desktop | Bisa mengaruhi administrasi jarak jauh |
| `Set-SMBv1` | Ngontrol protokol SMB lawas | Dibutuhake kanggo sistem lawas banget |
| `Set-AutoRun` | Ngontrol AutoPlay/AutoRun | Bisa mengaruhi kenyamanan pangguna |
| `Set-USBStorage` | Mbatesi piranti panyimpenan USB | Bisa mengaruhi panggunaan USB sing sah |
| `Set-Macros` | Ngontrol eksekusi makro Office | Bisa mengaruhi dokumen makro-diaktifake |
| `Set-PSRemoting` | Ngatur PowerShell remoting | Bisa mengaruhi manajemen jarak jauh |
| `Set-WinRM` | Ngontrol Windows Remote Management | Bisa mengaruhi administrasi jarak jauh |
| `Set-LLMNR` | Ngatur protokol resolusi jeneng | Biasane aman kanggo dipateni |
| `Set-NetBIOS` | Ngontrol NetBIOS ndhuwur TCP/IP | Bisa mengaruhi aplikasi lawas |
| `Set-AdminShares` | Ngatur administrative shares | Bisa mengaruhi akses file jarak jauh |
| `Set-Telemetry` | Ngontrol pangumpulan data | Bisa mengaruhi kemampuan diagnostik |
| `Set-GuestAccount` | Ngatur akun Guest | Biasane aman kanggo dipateni |
| `Set-ICMP` | Ngontrol respon ping | Bisa mengaruhi diagnostik jaringan |
| `Set-RemoteAssistance` | Ngatur Remote Assistance | Bisa mengaruhi operasi help desk |
| `Set-NetworkDiscovery` | Ngontrol network discovery | Bisa mengaruhi browsing jaringan |
| `Set-Firewall` | Ngatur Windows Firewall | Kritis kanggo keamanan jaringan |

### Keamanan Cloud Azure

| Fungsi | Tujuan | Syarat |
|----------|---------|--------------|
| `Set-AzureSecurityDefaults` | Ngaktifake keamanan dhasar Azure AD | Ijin Microsoft Graph |
| `Set-AzureConditionalAccess` | Ngonfigurasi kebijakan akses | Lisensi Azure AD P1/P2 |
| `Set-AzurePrivilegedUsers` | Audit akun istimewa | Ijin Global Admin |

### Opsi Deployment Enterprise

| Metode | Kasus Panggunaan | Syarat |
|--------|----------|--------------|
| **Eksekusi Langsung** | Testing, lingkungan cilik | Hak admin lokal |
| **Group Policy** | Lingkungan domain | Admin domain, manajemen GP |
| **Microsoft Intune** | Piranti sing dikelola cloud | Lisensi Intune, Graph API |

## 🚀 Wiwitan Cepet

### Penilaian Keamanan
```powershell
# Muat modul Ghost
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')

# Priksa postur keamanan saiki
Get-Ghost
```

### Pengerasan Dhasar (Test Dhisik)
```powershell
# Pengerasan esensial - test ing lingkungan lab dhisik
Set-Ghost -SMBv1 -AutoRun -Macros

# Tinjauan owah-owahan
Get-Ghost
```

### Deployment Enterprise
```powershell
# Deployment Group Policy (lingkungan domain)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Deployment Intune (piranti sing dikelola cloud)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Metode Instalasi

### Opsi 1: Download Langsung (Testing)
```powershell
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')
```

### Opsi 2: Instalasi Modul
```powershell
# Install saka PowerShell Gallery (nalika kasedhiya)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Opsi 3: Deployment Enterprise
```powershell
# Salin menyang lokasi jaringan kanggo deployment Group Policy
# Konfigurasi skrip PowerShell Intune kanggo deployment cloud
```

## 💼 Conto Kasus Panggunaan

### Bisnis Cilik
```powershell
# Perlindungan dhasar kanthi dampak minimal
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Lingkungan Kesehatan
```powershell
# Pengerasan fokus HIPAA
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Layanan Keuangan
```powershell
# Konfigurasi keamanan dhuwur
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Organisasi Cloud-First
```powershell
# Deployment sing dikelola Intune
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Rincian Fungsi

### Fungsi Pengerasan Inti

#### Layanan Jaringan
- **RDP**: Blokir akses remote desktop utawa randomisasi port
- **SMBv1**: Pateni protokol file sharing lawas
- **ICMP**: Nyegah respon ping kanggo reconnaissance
- **LLMNR/NetBIOS**: Blokir protokol resolusi jeneng lawas

#### Keamanan Aplikasi  
- **Makro**: Pateni eksekusi makro ing aplikasi Office
- **AutoRun**: Nyegah eksekusi otomatis saka media removable

#### Manajemen Jarak Jauh
- **PSRemoting**: Pateni sesi PowerShell jarak jauh
- **WinRM**: Mandegake Windows Remote Management
- **Remote Assistance**: Blokir koneksi remote assistance

#### Kontrol Akses
- **Admin Shares**: Pateni shares C$, ADMIN$
- **Guest Account**: Pateni akses akun Guest
- **USB Storage**: Mbatesi panggunaan piranti USB

### Integrasi Azure
```powershell
# Sambung menyang tenant Azure
Connect-AzureGhost -Interactive

# Aktifake default keamanan
Set-AzureSecurityDefaults -Enable

# Konfigurasi akses kondisional
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Audit pangguna istimewa
Set-AzurePrivilegedUsers -AuditOnly
```

### Integrasi Intune (Anyar ing v2)
```powershell
# Sambung menyang Intune
Connect-IntuneGhost -Interactive

# Deploy liwat kebijakan Intune
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Pertimbangan Penting

### Syarat Testing
- **Lingkungan Lab**: Test kabeh setelan ing lingkungan terisolasi dhisik
- **Deployment Bertahap**: Roll out kanthi bertahap kanggo identifikasi masalah
- **Rencana Rollback**: Pastikan sampeyan bisa mbalikake owah-owahan yen perlu
- **Dokumentasi**: Catat setelan apa sing bisa kanggo lingkungan sampeyan

### Dampak Potensial
- **Produktivitas Pangguna**: Sawetara setelan bisa mengaruhi alur kerja harian
- **Aplikasi Lawas**: Sistem lawas bisa mbutuhake protokol tartamtu
- **Akses Jarak Jauh**: Pertimbangake dampak ing administrasi jarak jauh sing sah
- **Proses Bisnis**: Verifikasi yen setelan ora ngrusak fungsi kritis

### Keterbatasan Keamanan
- **Defense in Depth**: Ghost minangka siji lapisan keamanan, dudu solusi lengkap
- **Manajemen Berkelanjutan**: Keamanan mbutuhake pemantauan lan update berkelanjutan
- **Pelatihan Pangguna**: Kontrol teknis kudu dipasangake karo kesadaran keamanan
- **Evolusi Ancaman**: Metode serangan anyar bisa ngliwati perlindungan saiki

## 🎯 Conto Skenario Serangan

Nalika Ghost ngarahake vektor serangan umum, pencegahan spesifik gumantung ing implementasi lan testing sing tepat:

### Serangan Gaya WannaCry
- **Mitigasi**: `Set-Ghost -SMBv1` mateni protokol sing rentan
- **Pertimbangan**: Pastiken ora ana sistem lawas sing mbutuhake SMBv1

### Ransomware Adhedhasar RDP
- **Mitigasi**: `Set-Ghost -RDP` blokir akses remote desktop
- **Pertimbangan**: Bisa mbutuhake metode akses jarak jauh alternatif

### Malware Adhedhasar Dokumen
- **Mitigasi**: `Set-Ghost -Macros` mateni eksekusi makro
- **Pertimbangan**: Bisa mengaruhi dokumen makro-diaktifake sing sah

### Ancaman Sing Digawa USB
- **Mitigasi**: `Set-Ghost -USBStorage -AutoRun` mbatesi fungsionalitas USB
- **Pertimbangan**: Bisa mengaruhi panggunaan piranti USB sing sah

## 🏢 Fitur Enterprise

### Dukungan Group Policy
```powershell
# Terapake setelan liwat registry Group Policy
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Setelan diterapake domain-wide sawise refresh GP
gpupdate /force
```

### Integrasi Microsoft Intune
```powershell
# Gawe kebijakan Intune kanggo setelan Ghost
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Kebijakan deploy menyang piranti sing dikelola kanthi otomatis
```

### Pelaporan Kepatuhan
```powershell
# Generate laporan penilaian keamanan
Get-Ghost | Export-Csv -Path "SecurityAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Laporan postur keamanan Azure
Get-AzureGhost | Out-File "AzureSecurityReport.txt"
```

## 📚 Praktik Terbaik

### Pra-Deployment
1. **Dokumentasikan Status Saiki**: Jalanake `Get-Ghost` sadurunge owah-owahan
2. **Test Kanthi Teliti**: Validasi ing lingkungan non-produksi
3. **Rencanakake Rollback**: Ngerti carane mbalikake saben setelan
4. **Tinjauan Stakeholder**: Pastiken unit bisnis nyetujoni owah-owahan

### Nalika Deployment
1. **Pendekatan Bertahap**: Deploy menyang grup pilot dhisik
2. **Monitor Dampak**: Deleng keluhan pangguna utawa masalah sistem
3. **Dokumentasikan Masalah**: Catat masalah apa wae kanggo referensi masa depan
4. **Komunikasikan Owah-owahan**: Informasikan pangguna babagan perbaikan keamanan

### Pasca-Deployment
1. **Penilaian Rutin**: Jalanake `Get-Ghost` kanthi berkala kanggo verifikasi setelan
2. **Update Dokumentasi**: Jaga konfigurasi keamanan tetep terkini
3. **Tinjau Efektivitas**: Monitor insiden keamanan
4. **Perbaikan Berkelanjutan**: Sesuaikan setelan adhedhasar lanskap ancaman

## 🔧 Pemecahan Masalah

### Masalah Umum
- **Error Ijin**: Pastiken sesi PowerShell elevated
- **Dependensi Layanan**: Sawetara layanan bisa duwe dependensi
- **Kompatibilitas Aplikasi**: Test karo aplikasi bisnis
- **Konektivitas Jaringan**: Verifikasi akses jarak jauh isih bisa

### Opsi Pemulihan
```powershell
# Aktifake maneh layanan spesifik yen perlu
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Babagan Penulis

**Jim Tyler** - Microsoft MVP kanggo PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10.000+ subscriber)
- **Newsletter**: [PowerShell.News](https://powershell.news) - Intelijen keamanan mingguan
- **Penulis**: "PowerShell for Systems Engineers"
- **Pengalaman**: Puluhan taun otomasi PowerShell lan keamanan Windows

## 📄 Lisensi & Penafian

### Lisensi MIT
Ghost diwenehake ing sangisore Lisensi MIT kanggo panggunaan, modifikasi, lan distribusi gratis.

### Penafian Keamanan
- **Tanpa Jaminan**: Ghost diwenehake "apa adanya" tanpa jaminan apa wae
- **Testing Dibutuhake**: Tansah test ing lingkungan non-produksi dhisik
- **Panduan Profesional**: Konsultasi karo profesional keamanan kanggo deployment produksi
- **Dampak Operasional**: Penulis ora tanggung jawab kanggo gangguan operasional apa wae
- **Keamanan Komprehensif**: Ghost minangka siji komponen saka strategi keamanan lengkap

### Dukungan
- **GitHub Issues**: [Laporake bug utawa request fitur](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentasi**: Gunakake `Get-Help <function> -Full` kanggo bantuan rinci
- **Komunitas**: Forum komunitas PowerShell lan keamanan

---

**🔒 Kuatake postur keamanan sampeyan karo Ghost - nanging tansah test dhisik.**

```powershell
# Wiwiti karo penilaian, dudu asumsi
Get-Ghost
```

**⭐ Beri bintang repository iki yen Ghost mbantu ningkatake postur keamanan sampeyan!**