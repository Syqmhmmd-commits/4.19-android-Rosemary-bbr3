<div align="center">

# 🌩️ StormTerror Kernel Source

### Kernel 4.19 for Redmi Note 10S (rosemary) with BBRv3 backport

[![Kernel](https://img.shields.io/badge/Kernel-4.19.325-blue?style=for-the-badge)](https://www.kernel.org/)
[![BBRv3](https://img.shields.io/badge/TCP-BBRv3-orange?style=for-the-badge)](https://github.com/google/bbr)
[![Clang](https://img.shields.io/badge/Clang-24-purple?style=for-the-badge)](https://clang.llvm.org/)
[![License](https://img.shields.io/badge/License-GPL--2.0-red?style=for-the-badge)](./COPYING)

**Source code repository for StormTerror Kernel**

[Download Kernel](#-download) • [Build Guide](#-build-instructions) • [Source Origin](#-source-origin) • [Credits](#-credits)

</div>

---

## 📖 Overview

Repository ini berisi **source code kernel Linux 4.19** yang digunakan untuk membangun **StormTerror Kernel** — custom kernel untuk Redmi Note 10S (rosemary) dengan optimasi jaringan BBRv3.

Kernel ini adalah hasil **fork dan modifikasi** dari beberapa sumber upstream yang dikembangkan oleh komunitas. Source code ini disediakan **terbuka sesuai lisensi GPL-2.0** dan dapat digunakan, dimodifikasi, serta didistribusikan ulang dengan syarat mempertahankan lisensi dan credit yang sama.

## 📱 Supported Devices

| Device | Codename | Status |
|--------|----------|--------|
| Redmi Note 10S | `rosemary` | ✅ |
| Redmi Note 10S NFC | `rosemary` | ✅ |
| Redmi Note 10S (India) | `maltose` | ✅ |
| POCO M5s | `secret` | ✅ |

## ✨ Features

### 🌐 Network
- **BBRv3 TCP Congestion Control** — backport dari kernel upstream terbaru
  - Throughput lebih tinggi
  - Latency lebih rendah
  - Recovery packet loss lebih cepat

### ⚙️ Core
- **Kernel 4.19.325** — stable branch dengan CIP + ST patches
- **Neutron Clang 24** — toolchain modern untuk optimisasi lebih baik
- **LLVM_IAS=1** — integrated assembler, tanpa GNU as

### 🔧 Compatibility
- Android 12 — 16
- LineageOS 23.2 (Android 16)
- AnyKernel3 flashable
- Magisk / KernelSU friendly

## 📂 Source Origin

Source code ini **di-fork dan dimodifikasi** dari:

| Repository | Peran |
|------------|-------|
| [zesakain/4.19-android-bbr3](https://github.com/zesakain/4.19-android-bbr3) | **Sumber utama** — BBRv3 backport untuk rosemary |
| [xiaomi-mt6785-dev/android_kernel_xiaomi_mt6785](https://github.com/xiaomi-mt6785-dev/android_kernel_xiaomi_mt6785) | **Base kernel** — MT6785 platform |
| [LineageOS](https://github.com/LineageOS) | **Upstream kernel** — LineageOS 23.2 |

### 🔧 Modifikasi oleh StormTerror

- Set `EXTRAVERSION` ke `-StromTerror-perf`
- Build dengan **Neutron Clang 24**
- Kernel version: `4.19.325-StromTerror-perf`
- (WIP) Integrasi ReSukiSU untuk versi KSU
- Maintain dua versi: **non-KSU** dan **ReSukiSU**

## 🛠️ Build Instructions

### Requirements

| Tool | Version | Notes |
|------|---------|-------|
| **OS** | Ubuntu 22.04 / CachyOS | Build environment |
| **Clang** | Neutron Clang 24 | Toolchain utama |
| **GCC** | aarch64-linux-gnu-gcc | Cross-compiler (opsional) |
| **Storage** | ~20 GB | Source + build output |
| **RAM** | 8 GB+ | Rekomendasi 16 GB |

### Setup Toolchain

```bash
# Bikin folder toolchain
mkdir -p ~/toolchains && cd ~/toolchains

# Download Neutron Clang 24 (sesuaikan URL dengan versi terbaru)
git clone https://github.com/Neutron-Toolchains/clang-build-catalogue.git
# Download & extract Neutron Clang 24 ke ~/toolchains/neutron-clang

git clone https://github.com/Syqmhmmd-commits/4.19-android-Rosemary-bbr3.git
cd 4.19-android-Rosemary-bbr3


## 📜 License

Kernel Linux dilisensikan di bawah **GNU General Public License v2.0 (GPL-2.0)**.

Lihat file [COPYING](./COPYING) untuk teks lisensi lengkap.

### ⚠️ Kewajiban Distribusi Ulang

Jika kamu mendistribusikan ulang kernel ini (dalam bentuk binary atau source), kamu **WAJIB**:

1. ✅ Menyertakan **source code lengkap** (atau link ke source)
2. ✅ Mempertahankan **lisensi GPL-2.0**
3. ✅ Mencantumkan **credit ke upstream** (zesakain, LineageOS, xiaomi-mt6785-dev)
4. ✅ Menyatakan **modifikasi** yang kamu lakukan
5. ✅ Tidak menambahkan **restriksi tambahan** di atas GPL

## 🙏 Credits

Source code ini tidak akan ada tanpa kerja keras dari:

### Upstream Kernel
- **[Linux Kernel Community](https://www.kernel.org/)** — Kernel Linux 4.19
- **[LineageOS Team](https://github.com/LineageOS)** — Android kernel base
- **[CIP Project](https://www.cip-project.org/)** — Civil Infrastructure Platform patches
- **[ST Microelectronics](https://www.st.com/)** — ST patches

### Device-Specific
- **[zesakain](https://github.com/zesakain)** — BBRv3 backport untuk rosemary
- **[xiaomi-mt6785-dev](https://github.com/xiaomi-mt6785-dev)** — MT6785 kernel source
- **[LineageOS rosemary maintainers](https://github.com/LineageOS/android_device_xiaomi_rosemary)** — Device tree

### Toolchain & Tools
- **[Neutron Toolchains](https://github.com/Neutron-Toolchains)** — Neutron Clang 24
- **[LLVM Project](https://llvm.org/)** — Clang/LLD compiler
- **[osm0sis](https://github.com/osm0sis)** — AnyKernel3
- **[KernelSU / ReSukiSU](https://github.com/ReSukiSU)** — Root solution

### Special Thanks
- **Komunitas Redmi Note 10S** — Testing & feedback
- **Semua kontributor** — Yang udah bantu build & debug

## 🤝 Contributing

Kontribusi diterima dengan senang hati! Caranya:

1. **Fork** repo ini
2. **Bikin branch** baru (`git checkout -b feature/fitur-baru`)
3. **Commit** perubahan (`git commit -m "Add fitur baru"`)
4. **Push** ke branch (`git push origin feature/fitur-baru`)
5. **Buka Pull Request**

### Aturan Kontribusi
- Ikuti **coding style** kernel Linux
- Sertakan **deskripsi jelas** di commit message
- Test dulu sebelum submit PR
- Jangan hapus credit/attribution yang ada





