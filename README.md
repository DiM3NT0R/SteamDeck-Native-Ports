# Steam Deck Native Ports

[English](#ports) · [Русский](#по-русски)

Standalone native Linux/Vulkan ports built for Steam Deck (OLED/LCD, Zen 2 + RDNA 2, SteamOS). No mega-launchers, no emulators, no Proton or Flatpak overhead. Each game lives in its own repository with a self-contained release archive.

> [!NOTE]
> None of these repositories contain copyrighted game assets, ROMs, dumps, console keys, or proprietary vendor DLLs. Supply your own legally dumped game files.

## Ports

| Game | Base | Performance (OLED, 15W TDP) |
| :--- | :--- | :--- |
| [**The Legend of Zelda: Breath of the Wild**](https://github.com/DiM3NT0R/BOTW-SavageWind-SteamDeck) *(v1.9.0 + DLC)* | Switch (`SavageWindRecomp`) | 60–90 FPS (60–83 open world at native `1280×800`, 90 in shrines/menus) |
| [**EA SPORTS UFC 4**](https://github.com/DiM3NT0R/UFC4-Native-Plus) *(v28.00)* | PS4 (`UFC4-Native-Plus`) | Locked 60 FPS (`deck-576p`, zero stutters) |
| [**EA SPORTS UFC 3**](https://github.com/DiM3NT0R/UFC3-Native-SteamDeck) | PS4 (`SacredFire/bbport` + Vulkan) | 60 FPS native Linux/SteamOS |

## Repositories

* **The Legend of Zelda: Breath of the Wild** — https://github.com/DiM3NT0R/BOTW-SavageWind-SteamDeck ([Releases](https://github.com/DiM3NT0R/BOTW-SavageWind-SteamDeck/releases))
* **EA SPORTS UFC 4** — https://github.com/DiM3NT0R/UFC4-Native-Plus ([Releases](https://github.com/DiM3NT0R/UFC4-Native-Plus/releases))
* **EA SPORTS UFC 3** — https://github.com/DiM3NT0R/UFC3-Native-SteamDeck ([Releases](https://github.com/DiM3NT0R/UFC3-Native-SteamDeck/releases))

## Build & optimization notes

* **BOTW:** Compiled with `clang -O3 -march=znver2`, ThinLTO, and PGO; 2-way `gcopy` and `SETC_TAB`, in-place `cbuf k==1`, AVX2 texture hashing (`-17.7%` CPU `exec`, up to `83.5 FPS` on the Great Plateau vs `77.2` on the stock AppImage). Ships native Linux **FSR 4.1.2 Lite (`FSR4L-i8`)** + AMD CAS via `dlopen` (toggle in-game with `View + Menu`).
* **UFC 4:** Zero-lag frame pacing (`BB_VBLANK_HZ=60`, `Immediate`), Steam Deck `evdev` `FF_RUMBLE` vibration forwarding, Russian default (`BB_LANGUAGE=8`), one-click Steam shortcut.
* **UFC 3:** Native Linux Vulkan port (`shadPS4`-derived renderer) with Steam Deck display and controller tuning.

## Principles

* **One game, one archive.** No bloated multi-game launchers.
* **Native SteamOS binaries.** Linked directly against SteamOS host libraries (`ldd` clean, no Flatpak or Proton overhead).
* **Measured on hardware.** Every optimization is profiled on a Steam Deck OLED at 15W TDP and visually verified for zero artifacts.

## Credits

Core recompilation, upscaling bridges, and compatibility layers belong to their upstream authors:

* [Revivedx/SavageWindRecomp](https://github.com/Revivedx/SavageWindRecomp) — BOTW static recompilation
* [auz466/fsr4up-vk](https://github.com/auz466/fsr4up-vk) — native Linux Vulkan FSR 4.1.2 bridge
* [abdullah-tech7/UFC4-Native-Plus](https://github.com/abdullah-tech7/UFC4-Native-Plus) and shadPS4 / bbport contributors

---

## По-русски

Каталог автономных нативных Linux/Vulkan-портов, собранных под **Steam Deck (OLED/LCD, Zen 2 + RDNA 2, SteamOS)**. Без комбайнов-лаунчеров, эмуляторов, Proton и Flatpak. Каждая игра лежит в отдельном репозитории со своим автономным релизом.

> [!NOTE]
> Репозитории не содержат файлов игр, ROM-ов, дампов, ключей консолей или проприетарных DLL. Игровые файлы нужно подложить со своей копии.

### Порты

| Игра | База | Производительность (OLED, 15W TDP) |
| :--- | :--- | :--- |
| [**The Legend of Zelda: Breath of the Wild**](https://github.com/DiM3NT0R/BOTW-SavageWind-SteamDeck) *(v1.9.0 + DLC)* | Switch (`SavageWindRecomp`) | 60–90 FPS (60–83 в открытом мире в нативе `1280×800`, 90 в храмах и меню) |
| [**EA SPORTS UFC 4**](https://github.com/DiM3NT0R/UFC4-Native-Plus) *(v28.00)* | PS4 (`UFC4-Native-Plus`) | Лок 60 FPS (`deck-576p`, без статтеров) |
| [**EA SPORTS UFC 3**](https://github.com/DiM3NT0R/UFC3-Native-SteamDeck) | PS4 (`SacredFire/bbport` + Vulkan) | 60 FPS нативно на Linux/SteamOS |

### Репозитории

* **The Legend of Zelda: Breath of the Wild** — https://github.com/DiM3NT0R/BOTW-SavageWind-SteamDeck ([Релизы](https://github.com/DiM3NT0R/BOTW-SavageWind-SteamDeck/releases))
* **EA SPORTS UFC 4** — https://github.com/DiM3NT0R/UFC4-Native-Plus ([Релизы](https://github.com/DiM3NT0R/UFC4-Native-Plus/releases))
* **EA SPORTS UFC 3** — https://github.com/DiM3NT0R/UFC3-Native-SteamDeck ([Релизы](https://github.com/DiM3NT0R/UFC3-Native-SteamDeck/releases))

### Сборка и оптимизации

* **BOTW:** Собрано с `clang -O3 -march=znver2`, ThinLTO и PGO; 2-way `gcopy` и `SETC_TAB`, in-place `cbuf k==1`, AVX2-хеширование текстур (`-17.7%` к CPU `exec`, до `83.5 FPS` на Великом Плато против `77.2` на стоковом AppImage). Встроен нативный Linux **FSR 4.1.2 Lite (`FSR4L-i8`)** + AMD CAS через `dlopen` (переключается в игре по `View + Menu`).
* **UFC 4:** Фреймпейсинг без инпут-лага (`BB_VBLANK_HZ=60`, `Immediate`), проброс вибрации Steam Deck через `evdev` (`FF_RUMBLE`), русский язык по умолчанию (`BB_LANGUAGE=8`), добавление ярлыка в Steam в один клик.
* **UFC 3:** Нативный Linux/Vulkan-порт (рендерер на базе `shadPS4`), настроенный под экран и управление Steam Deck.

### Принципы

* **Одна игра — один архив.** Никаких тяжёлых все-в-одном лаунчеров.
* **Нативные бинарники под SteamOS.** Линковка напрямую к системным библиотекам SteamOS (`ldd` чистый, без прослоек Proton и Flatpak).
* **Замеры на реальном железе.** Каждая оптимизация профилируется на Steam Deck OLED при 15W TDP и проверяется визуально на отсутствие артефактов.

### Апстрим-проекты

Основа рекомпиляции, апскейлинга и слоёв совместимости принадлежит оригинальным авторам:

* [Revivedx/SavageWindRecomp](https://github.com/Revivedx/SavageWindRecomp) — статическая рекомпиляция BOTW
* [auz466/fsr4up-vk](https://github.com/auz466/fsr4up-vk) — нативный Linux Vulkan-мост для FSR 4.1.2
* [abdullah-tech7/UFC4-Native-Plus](https://github.com/abdullah-tech7/UFC4-Native-Plus) и контрибьюторы shadPS4 / bbport
