<div align="center">

# MacOS EFI · MSI GF75 Thin 10UC

### OpenCore 1.0 · macOS Sonoma 14.5 · Platinum Edition

[![OpenCore](https://img.shields.io/badge/OpenCore-1.0-6C5CE7?style=for-the-badge&logo=apple&logoColor=white)](https://github.com/acidanthera/OpenCorePkg)
[![macOS](https://img.shields.io/badge/macOS-Sonoma%2014.5-000000?style=for-the-badge&logo=apple&logoColor=white)](https://www.apple.com/macos/sonoma/)
[![Laptop](https://img.shields.io/badge/MSI-GF75%20Thin%2010UC-FF6B00?style=for-the-badge&logo=msi&logoColor=white)](https://www.msi.com/)
[![License](https://img.shields.io/badge/License-MIT-2ECC71?style=for-the-badge)](LICENSE)
[![Release](https://img.shields.io/github/v/release/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC?style=for-the-badge&label=Download&color=E74C3C&logo=github)](https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC/releases/latest)

**Готовый EFI-загрузчик Hackintosh для MSI GF75 Thin 10UC-048XRU**  
*Intel Comet Lake · UHD 630 · RTX 3050 · AX201 Wi-Fi 6*

[Скачать релиз](https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC/releases/latest) · [Руководство OpenCore](https://dortania.github.io/OpenCore-Install-Guide/) · [Сообщить о проблеме](https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC/issues)

</div>

---

## Обзор

| | |
|---|---|
| **Последний релиз** | [**v1.0.0 — Releases**](https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC/releases/latest) |
| **Архив** | `MacOS-EFI-MSI-GF75-Thin-10UC-v1.0.0.zip` |
| **Загрузчик** | OpenCore 1.0 |
| **macOS** | Sonoma 14.5 (совместимо с 14.x) |
| **Тема OpenCore** | Acidanthera GoldenGate |

> Полный образ раздела с EFI, recovery и вспомогательными файлами — в ZIP-архиве релиза.  
> Для установки на ESP достаточно скопировать папку `EFI` из архива на EFI-раздел диска.

---

## Конфигурация

| Компонент | Характеристики |
|-----------|----------------|
| **Модель** | MSI GF75 Thin 10UC-048XRU 17.3" (RTX 3050) |
| **Процессор** | Intel® Core™ i5-10500H @ 2.50 GHz |
| **Память** | 16 GB DDR4 3200 MHz (8+8) |
| **Диск** | M.2 PCIe SSD Kingston OM8PCP3512F 512 GB |
| **iGPU** | Intel UHD Graphics 630 |
| **dGPU** | NVIDIA GeForce RTX 3050 4 GB *(не используется в macOS)* |
| **Ethernet** | Realtek RTL8168H |
| **Дисплей** | IPS FHD 1920×1080 (17.3") @ 144 Hz |
| **Аудио** | Realtek ALC233 |
| **Wi-Fi** | Intel® Wi-Fi 6 AX201 |
| **Bluetooth** | Intel AX201 |

---

## Настройки BIOS

| Параметр | Значение |
|----------|----------|
| Скрытые настройки | `Ctrl Right` + `Shift Right` + `Alt Left` + `F2` |
| Secure Boot | **Выключить** → `Security` |
| CFG Lock | **Выключить** → `Advanced → Power & Performance → CPU → CPU Lock Configuration` |
| Fast Boot | **Выключить** → `Boot` |
| Режим загрузки | **UEFI без CSM** → `Boot` |

---

## Совместимость

### Работает

| Категория | Статус |
|-----------|--------|
| QE/CI графика iGPU Intel UHD 630 (10-е поколение) | ✅ |
| Управление питанием процессора | ✅ |
| Перезагрузка, сон и выключение | ✅ |
| Аудио Realtek ALC233 | ✅ |
| Трекпад с мультитач-жестами | ✅ |
| Состояние батареи | ✅ |
| Bluetooth | ✅ |
| Все USB-порты | ✅ |
| Функциональные клавиши | ✅ |
| Регулировка яркости | ✅ |
| Bluetooth-гарнитура и микрофон | ✅ |
| Wi-Fi (Intel AX201) | ✅ |
| Видео/аудио через HDMI | ✅ |
| iMessage | ✅ |
| FaceTime | ✅ |

### Не работает

| Функция | Статус |
|---------|--------|
| AirDrop | ❌ |

---

## Структура репозитория

```
├── BOOT/                  # Загрузчик BOOTx64.efi
├── OC/
│   ├── ACPI/              # SSDT-таблицы
│   ├── Drivers/           # OpenCore-драйверы
│   ├── Kexts/             # Кернел-расширения
│   ├── Resources/         # Тема OpenCore (GoldenGate)
│   ├── Tools/             # Утилиты OpenCore
│   └── config.plist       # Основной конфиг
├── LICENSE
└── README.md
```

---

## ACPI (SSDT)

| Файл | Назначение |
|------|------------|
| `SSDT-EC.aml` | Виртуальный EC |
| `SSDT-EC-USBX-LAPTOP.aml` | EC + USB power для ноутбука |
| `SSDT-HPET.aml` | Исправление HPET |
| `SSDT-IGPU.aml` | Настройка Intel iGPU |
| `SSDT-PLUG.aml` | Управление питанием CPU |
| `SSDT-PNLF.aml` | Яркость дисплея |
| `SSDT-USBX.aml` | USB power properties |
| `SSDT-XOSI.aml` | Патч _OSI → XOSI |

---

## Kexts

| Kext | Назначение |
|------|------------|
| Lilu | Патч-инжектор (базовый) |
| VirtualSMC | Эмуляция SMC |
| SMCProcessor | Температура процессора |
| SMCBatteryManager | Состояние батареи |
| WhateverGreen | Графика Intel iGPU |
| AppleALC | Аудио Realtek ALC233 |
| RealtekRTL8111 | Ethernet RTL8168H |
| AirportItlwm | Wi-Fi Intel AX201 |
| IntelBluetoothFirmware | Bluetooth firmware |
| IntelBluetoothInjector | Bluetooth injector |
| IntelBTPatcher | Bluetooth patcher |
| VoodooI2C + VoodooI2CHID | Трекпад I2C |
| VoodooPS2Controller | Клавиатура PS/2 |
| BrightnessKeys | Клавиши яркости |
| CPUFriend + CPUFriendDataProvider | Управление питанием |
| ECEnabler | Embedded Controller |
| NVMeFix | NVMe SSD |
| RestrictEvents | Ограничение событий |
| USBMap | Карта USB-портов |
| AAAMouSSE | Патч SSE |
| EmeraldSDHC | SD-карта |
| HoRNDIS | USB tethering |

---

## Установка

### Быстрый старт

1. Скачайте [**последний релиз**](https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC/releases/latest)
2. Распакуйте ZIP-архив
3. Смонтируйте EFI-раздел (через [MountEFI](https://github.com/corpnewt/MountEFI) или `diskutil mount` в macOS)
4. Скопируйте папку `EFI` из архива на EFI-раздел
5. Настройте BIOS по таблице выше
6. Перезагрузитесь и выберите macOS в OpenCore

### Сборка из репозитория

```bash
git clone https://github.com/smartmaster35rus-dev/MacOS-EFI-MSI-GF75-Thin-10UC.git
# Скопируйте BOOT и OC в EFI/ на ESP-разделе:
#   EFI/BOOT/  ← BOOT/
#   EFI/OC/    ← OC/
```

> Перед использованием сгенерируйте уникальные **SMBIOS**, **Serial Number** и **ROM** для iMessage/FaceTime.  
> Руководство: [Dortania — Post-Install](https://dortania.github.io/OpenCore-Post-Install/)

---

## OpenCore Drivers

| Драйвер | Назначение |
|---------|------------|
| OpenRuntime.efi | Runtime services |
| OpenCanopy.efi | Графический интерфейс загрузки |
| HfsPlusLegacy.efi | Поддержка HFS+ |
| AudioDxe.efi | Звук в OpenCore |
| Ps2KeyboardDxe.efi | PS/2 клавиатура |
| ResetNvramEntry.efi | Сброс NVRAM |

---

## Важно

- **RTX 3050** не поддерживается в macOS — используется только Intel UHD 630
- Для iMessage/FaceTime необходимы **уникальные** SMBIOS-данные
- Рекомендуется отключить дискретную видеокарту в BIOS (если доступно)
- Перед обновлением macOS проверяйте совместимость kexts

---

## Поддержка

- Сайт: [smartmaster35rus.ru](https://smartmaster35rus.ru)
- Telegram: [@SmartMaster35Rus](https://t.me/SmartMaster35Rus)

---

<div align="center">

**© 2026 [smartmaster35rus-dev](https://github.com/smartmaster35rus-dev)**

*Сделано с ♥ для сообщества Hackintosh*

</div>
