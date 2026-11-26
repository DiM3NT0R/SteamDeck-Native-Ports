# Steam Deck Native Ports

A curated index of **native Linux ports** specifically optimized for **Steam Deck (OLED & LCD — Zen 2 / RDNA 2 / SteamOS)** — no bloated all-in-one launchers, no emulators, no game files included. Each game lives in its own standalone repository with a self-contained release archive.

> **Legal / No Game Files:** None of these repositories contain copyrighted game assets, ROMs, dumps, console keys, or proprietary vendor DLLs. You must supply your own legally dumped game files.

---

## Games

| Game | Origin | Steam Deck Performance | Key Optimizations | Repository & Release |
|---|---|---|---|---|
| **The Legend of Zelda: Breath of the Wild** *(v1.9.0 + DLC)* | Switch (`SavageWindRecomp`) | **60–90 FPS** (`60–83 FPS` open world at pure native `1280×800`, **90 FPS** shrines & menus) | `clang -O3 -march=znver2` + ThinLTO + PGO, 2-way `gcopy` & `SETC_TAB`, in-place `cbuf k==1`, AVX2 texture hashing, native Linux **FSR 4.1.2 Lite (`FSR4L-i8`)** + AMD CAS via `dlopen` | [`BOTW-SavageWind-SteamDeck`](https://github.com/DiM3NT0R/BOTW-SavageWind-SteamDeck) |
| **EA SPORTS UFC 4** *(v28.00)* | PS4 (`UFC4-Native-Plus`) | **Locked 60 FPS** (`deck-576p`, zero stutters) | Zero-lag frame pacing (`BB_VBLANK_HZ=60`, `Immediate`), Steam Deck evdev `FF_RUMBLE` vibration forwarding, Russian default (`BB_LANGUAGE=8`), one-click Steam shortcut | [`UFC4-Native-Plus`](https://github.com/DiM3NT0R/UFC4-Native-Plus/releases/tag/ufc4-v28.00-steamdeck-60fps) |
| **EA SPORTS UFC 3** | PS4 (`SacredFire/bbport` + Vulkan) | **60 FPS** native Linux/SteamOS | Native Linux Vulkan port (`shadPS4`-derived renderer), Steam Deck controller & display tuning | [`UFC3-Native-SteamDeck`](https://github.com/DiM3NT0R/UFC-3-PS4-PORT-LINUX-WINDOWS) |

---

## Philosophy

- **One game = one standalone download.** No multi-game mega-launchers.
- **Native SteamOS binaries.** Linked directly against SteamOS host libraries (`ldd` clean, no flatpak/Proton overhead).
- **Real measurements.** Every optimization is profiled on actual Steam Deck OLED hardware at 15W TDP with visual verification (zero artifacts).

---

## По-русски

Лёгкий каталог **нативных Linux-портов**, оптимизированных специально под **Steam Deck (OLED / LCD, Zen 2 + RDNA 2, SteamOS)** — без комбайнов-лаунчеров и эмуляторов. Каждая игра живёт в отдельном репозитории со своим автономным релизом.

> **Важно:** репозитории не содержат файлов игр, дампов, ключей консолей или проприетарных DLL. Игровые файлы пользователь подкладывает со своей копии.

### Коротко о результатах (15W TDP, Steam Deck OLED)
- **Zelda: Breath of the Wild** ([`BOTW-SavageWind-SteamDeck`](https://github.com/DiM3NT0R/BOTW-SavageWind-SteamDeck)): обычно **60–90 FPS** в чистом нативе `1280×800` (`60–83 FPS` в открытом мире в зависимости от сцены и движения, до `83.5 FPS` на Великом Плато против `77.2` на стоковом AppImage, и `90 FPS` в храмах/меню), `-17.7%` CPU `exec`, плюс нативная поддержка **FSR 4.1.2 Lite + AMD CAS** на Linux (переключается в меню игры `View + Menu`).
- **EA SPORTS UFC 4** ([`UFC4-Native-Plus`](https://github.com/DiM3NT0R/UFC4-Native-Plus/releases/tag/ufc4-v28.00-steamdeck-60fps)): стабильные **60 FPS**, исправлен инпут-лаг и вибрация Steam Deck, русский язык.
- **EA SPORTS UFC 3** ([`UFC3-Native-SteamDeck`](https://github.com/DiM3NT0R/UFC-3-PS4-PORT-LINUX-WINDOWS)): нативный Linux/Vulkan порт с оптимизацией под Steam Deck.

---

## Credits & Upstream Projects

All credit for the core recompilation and compatibility layers belongs to their original authors:
- [Revivedx/SavageWindRecomp](https://github.com/Revivedx/SavageWindRecomp) (BOTW static recompilation)
- [auz466/fsr4up-vk](https://github.com/auz466/fsr4up-vk) (native Linux Vulkan FSR 4.1.2 bridge)
- [abdullah-tech7/UFC4-Native-Plus](https://github.com/abdullah-tech7/UFC4-Native-Plus) & shadPS4 / bbport contributors
