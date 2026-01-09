# HTL Drupal – Entwicklung mit WSL2 (Windows)

Diese Anleitung beschreibt die **empfohlene Entwicklungsumgebung unter Windows**  
mit **WSL2 + Ubuntu**, Docker, Composer und Node.js.

Ziel ist eine **saubere Linux-basierte Dev-Umgebung**, die identisch zu Linux/macOS ist.

---

## 🎯 Ziele

- Linux-Umgebung unter Windows

- Keine Windows-PHP- oder Node-Installation nötig

- Docker läuft über WSL2

- Volle IDE-Integration (PhpStorm)

- Einheitlich für alle Schüler

---

## 🧱 Architektur-Überblick

```text
Windows
└── WSL2 (Ubuntu)
    ├── Docker + Docker Compose
    ├── Node.js + npm
    ├── Composer
    └── Projekt-Code
```

➡️ **Alle Dev-Tools laufen in Ubuntu**, nicht in Windows

---

## 1️⃣ WSL2 installieren

### Voraussetzungen

- Windows 10 (2004+) oder Windows 11

- Virtualisierung im BIOS aktiviert

---

### WSL2 + Ubuntu installieren

```powershell
wsl --install -d Ubuntu
```

Danach:

- PC neu starten

- Ubuntu starten

- Benutzername & Passwort setzen

Test:

```bash
lsb_release -a
```

---

## 2️⃣ Docker mit WSL2

### Docker Desktop installieren

🔗 [Docker Desktop: The #1 Containerization Tool for Developers | Docker](https://www.docker.com/products/docker-desktop/)

Während der Installation:

- ✅ **WSL2 Backend aktivieren**

- ✅ Ubuntu Distribution auswählen

Docker Desktop → Settings → Resources → WSL Integration

➡️ Ubuntu aktivieren

---

### Test in Ubuntu

```bash
docker --version
docker compose version
```

---

## 3️⃣ Projekt-Ordner (wichtig!)

⚠️ **Code IMMER im Linux-Dateisystem ablegen**

❌ Nicht:

```text
/mnt/c/Users/...
```

✅ Richtig:

```bash
mkdir -p ~/projects
cd ~/projects
```

➡️ Massive Performance-Vorteile

---

## 4️⃣ Node.js & npm (Ubuntu)

Wir verwenden **NodeSource**, nicht apt-default.

```bash
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt install -y nodejs
```

Test:

```bash
node -v
npm -v
```

---

## 5️⃣ Composer installieren

Composer wird **global in Ubuntu** installiert.

```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
sudo mv composer.phar /usr/local/bin/composer
composer --version
```

📚 Referenz (PhpStorm):  
[Composer dependency manager | PhpStorm Documentation](https://www.jetbrains.com/help/phpstorm/using-the-composer-dependency-manager.html)

---

## 6️⃣ PhpStorm + WSL2

### Empfohlenes Setup

- PhpStorm läuft auf **Windows**

- PHP / Composer / Node laufen in **WSL2**

### Projekt öffnen

1. PhpStorm → **Open**

2. Pfad wählen:

```text
\\wsl$\Ubuntu\home\<user>\projects\HTL-Website-Drupal
```

---

### PHP Interpreter (WSL)

- Settings → PHP → CLI Interpreter

- Add → **From WSL**

- Distribution: Ubuntu

- PHP aus Docker oder System auswählen

---

### Composer in PhpStorm

- Settings → PHP → Composer

- Path: `/usr/local/bin/composer`

- Interpreter: WSL PHP

---

## 7️⃣ Docker-Projekt starten

```bash
cd ~/projects/HTL-Website-Drupal
docker compose up -d --build
```

Danach:

- Drupal läuft

- MariaDB läuft

- PHP läuft

---

## ⚠️ Wichtige Regeln

- ❌ Kein Code unter `/mnt/c`

- ❌ Keine Windows-PHP-Installation

- ❌ Keine Windows-Node-Installation

- ✅ Alles in Ubuntu

- ✅ Docker über WSL2

---

## 📚 Referenzen

- PhpStorm & Composer:  
  [Composer dependency manager | PhpStorm Documentation](https://www.jetbrains.com/help/phpstorm/using-the-composer-dependency-manager.html)

- WSL2 PHP Development (ohne MariaDB):  
  [GitHub - enflow/wsl2-php-development: Documentation how to setup WSL2 for PHP development](https://github.com/enflow/wsl2-php-development)

---

## ✅ Zusammenfassung

- WSL2 = Pflicht unter Windows

- Ubuntu als Dev-System

- Docker + Node + Composer dort installieren

- PhpStorm nur als IDE

➡️ Gleiches Setup wie Linux/macOS  
➡️ Keine Sonderfälle  
➡️ Ideal für Schule# HTL Drupal – Entwicklung mit WSL2 (Windows)

Diese Anleitung beschreibt die **empfohlene Entwicklungsumgebung unter Windows**  
mit **WSL2 + Ubuntu**, Docker, Composer und Node.js.

Ziel ist eine **saubere Linux-basierte Dev-Umgebung**, die identisch zu Linux/macOS ist.

---

## 🎯 Ziele

- Linux-Umgebung unter Windows

- Keine Windows-PHP- oder Node-Installation nötig

- Docker läuft über WSL2

- Volle IDE-Integration (PhpStorm)

- Einheitlich für alle Schüler

---

## 🧱 Architektur-Überblick

```
Windows
└── WSL2 (Ubuntu)
    ├── Docker + Docker Compose
    ├── Node.js + npm
    ├── Composer
    ├── Projekt-Code
    │   └── /home/<user>/projects/
    │       └── HTL-Website-Drupal/
```

➡️ **Alle Dev-Tools laufen in Ubuntu**, nicht in Windows
➡️ **Die Projekte liegen im Linux-Home-Verzeichnis** (`/home/<user>/projects`)

### Projekt-Ordner anlegen (einmalig)

```
mkdir -p ~/projects
```

---

## 1️⃣ WSL2 installieren

### Voraussetzungen

- Windows 10 (2004+) oder Windows 11

- Virtualisierung im BIOS aktiviert

---

### WSL2 + Ubuntu installieren

```powershell
wsl --install -d Ubuntu
```

Danach:

- PC neu starten

- Ubuntu starten

- Benutzername & Passwort setzen

Test:

```bash
lsb_release -a
```

---

## 2️⃣ Docker mit WSL2

### Docker Desktop installieren

🔗 [Docker Desktop: The #1 Containerization Tool for Developers | Docker](https://www.docker.com/products/docker-desktop/)

Während der Installation:

- ✅ **WSL2 Backend aktivieren**

- ✅ Ubuntu Distribution auswählen

Docker Desktop → Settings → Resources → WSL Integration

➡️ Ubuntu aktivieren

---

### Test in Ubuntu

```bash
docker --version
docker compose version
```

---

## 3️⃣ Projekt-Ordner (wichtig!)

⚠️ **Code IMMER im Linux-Dateisystem ablegen**

❌ Nicht:

```text
/mnt/c/Users/...
```

✅ Richtig:

```bash
mkdir -p ~/projects
cd ~/projects
```

➡️ Massive Performance-Vorteile

---

## 4️⃣ Node.js & npm (Ubuntu)

Wir verwenden **NodeSource**, nicht apt-default.

```bash
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt install -y nodejs
```

Test:

```bash
node -v
npm -v
```

---

## 5️⃣ Composer installieren

Composer wird **global in Ubuntu** installiert.

```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
sudo mv composer.phar /usr/local/bin/composer
composer --version
```

📚 Referenz (PhpStorm):  
[Composer dependency manager | PhpStorm Documentation](https://www.jetbrains.com/help/phpstorm/using-the-composer-dependency-manager.html)

---

## 6️⃣ PhpStorm + WSL2

### Empfohlenes Setup

- PhpStorm läuft auf **Windows**

- PHP / Composer / Node laufen in **WSL2**

### Projekt öffnen

1. PhpStorm → **Open**

2. Pfad wählen:

```text
\\wsl$\Ubuntu\home\<user>\projects\HTL-Website-Drupal
```

---

### PHP Interpreter (WSL)

- Settings → PHP → CLI Interpreter

- Add → **From WSL**

- Distribution: Ubuntu

- PHP aus Docker oder System auswählen

---

### Composer in PhpStorm

- Settings → PHP → Composer

- Path: `/usr/local/bin/composer`

- Interpreter: WSL PHP

---

## 7️⃣ Docker-Projekt starten

```bash
cd ~/projects/HTL-Website-Drupal
docker compose up -d --build
```

Danach:

- Drupal läuft

- MariaDB läuft

- PHP läuft

---

## ⚠️ Wichtige Regeln

- ❌ Kein Code unter `/mnt/c`

- ❌ Keine Windows-PHP-Installation

- ❌ Keine Windows-Node-Installation

- ✅ Alles in Ubuntu (also immer **`docker exec -it drupal_php bash`** um zur umgebung zu kommen)

- ✅ Docker über WSL2 (nicht 100% so performant wie nativ, aber für einfachheit besser)

---

## 📚 Referenzen

- PhpStorm & Composer:  
  [Composer dependency manager | PhpStorm Documentation](https://www.jetbrains.com/help/phpstorm/using-the-composer-dependency-manager.html)

- WSL2 PHP Development (bis MariaDB installieren, alles danach nicht mehr, und von hier auch Node und composer nicht):  
  [GitHub - enflow/wsl2-php-development: Documentation how to setup WSL2 for PHP development](https://github.com/enflow/wsl2-php-development)

---

## ✅ Zusammenfassung

- WSL2 = Pflicht unter Windows (muss sowieso mit Docker Desktop)

- Ubuntu als Dev-System

- Docker + Node + Composer dort installieren

- PhpStorm nur als IDE

➡️ Gleiches Setup wie Linux/macOS  
➡️ Keine Sonderfälle  
➡️ Ideal für Schule
