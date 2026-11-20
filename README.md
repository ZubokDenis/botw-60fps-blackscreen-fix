# The Legend of Zelda: Breath of the Wild (BotW) — 60 FPS Weapon Menu Black Screen Fix

Патч для устранения чёрного мерцания (черного кадра) при открытии селектора оружия, щитов, луков и рун при игре в 60 FPS на Nintendo Switch через **FPSLocker**.

Fix for the 1-frame black screen flicker when opening weapon/shield/bow/rune quick-select menus at 60 FPS using **FPSLocker** on Nintendo Switch.

---

## 🎮 Описание проблемы / Problem Overview

### На русском:
При разблокировке фреймрейта до 60 FPS в The Legend of Zelda: Breath of the Wild на Switch с помощью FPSLocker, при каждом открытии селектора оружия (D-pad) экран на мгновение (~16мс / 1 кадр) моргает чёрным. 

**Причина:**  
В оригинальном патче FPSLocker для BotW присутствует хук, замедляющий скорость UI-анимаций (`game_speed` = 0.5 при 60 FPS). Из-за этого начальная фаза перехода фонового размытия (Gaussian blur) рассинхронизируется с рендером интерфейса, и в течение первого кадра выводится неинициализированный черный буфер. Данный патч убирает этот конфликт, сохраняя динамическую скорость физики игры (1x) и стабильные 60 FPS без черного мерцания.

---

### In English:
When unlocking the frame rate to 60 FPS in BotW on Nintendo Switch via FPSLocker, opening any D-pad quick-select menu (weapons, shields, bows, runes) causes the screen to flash black for a single frame (~16ms).

**Cause:**  
The stock FPSLocker patch scales the UI speed multiplier by `game_speed` (0.5 at 60 FPS). This causes the background blur blend transition to lag behind the UI activation, rendering an uninitialized black render-target on the very first frame. This fix removes the UI speed hook while preserving the dynamic game speed calculation, giving smooth 60 FPS gameplay without any menu flicker.

---

## 📦 Поддерживаемые версии / Supported Versions

* **Title ID:** `01007EF00011E000`
* **Update Title ID:** `01007EF00011E800`
* **Build ID:** `CD57B23FA4BBAD65` (Версия игры **v1.9.0** / `v1114112`)

---

## 🚀 Установка / Installation

1. Скачайте файл `CD57B23FA4BBAD65.yaml` из этого репозитория.
2. Скопируйте файл на microSD карту вашей Nintendo Switch по пути:
   ```
   sdmc:/SaltySD/plugins/FPSLocker/patches/01007EF00011E000/CD57B23FA4BBAD65.yaml
   ```
   *(согласитесь на замену существующего файла).*
3. **ВАЖНО / IMPORTANT:**  
   В этой же папке **удалите файл `CD57B23FA4BBAD65.bin`** (если он есть).  
   FPSLocker компилирует `.yaml` в `.bin`. Если не удалить старый `.bin`, консоль продолжит использовать старый кэшированный патч с мерцанием!
4. Запустите игру, откройте оверлей FPSLocker (Tesla Overlay) и выставьте 60 FPS.
5. Наслаждайтесь плавной игрой без черных вспышек при смене оружия!

---

## 🛠 Кредиты / Credits

* **masagrator** — автор [FPSLocker](https://github.com/masagrator/FPSLocker) и [SaltyNX](https://github.com/masagrator/SaltyNX).