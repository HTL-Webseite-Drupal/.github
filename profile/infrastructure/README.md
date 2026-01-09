# Infrastruktur (Docker – empfohlene Version)

## 🎯 Ziele

- Einheitliche lokale Entwicklungsumgebung

- Reproduzierbare Setups auf allen Rechnern

- Sehr einfacher Einstieg für neue Schüler

- Keine manuelle Drupal-Bastelei nötig

---

## 📦 Grundidee

- **Docker Compose** als zentrales Tool

- Ein PHP-Container speziell für Drupal

- MariaDB als Datenbank

- Volumes für Module & Themes

- Möglichst wenig manuelle Schritte nach `docker compose up`

---

## 📁 Empfohlene Projektstruktur

```
HTL-Website-Drupal/
├── docker-compose.yml
├── php-config/
│   ├── Dockerfile
│   └── php.ini
├── themes/
│   ├── contrib/
│   └── custom/
├── custom-modules/                # Nur custom module, installierte in docker umgebung
│   ├── custom_module_1/
│   └── custom_module_2/
```

**Wichtig:**

- Das eigentliche Drupal - Verzeichnis, ist nicht in lokalen files, sondern in der docker-umgebung, für performance.

- `custom-modules` und `themes/custom` werden **eingebunden**, nicht kopiert

---

## 🐳 Docker Compose – empfohlene Services

**Services:**

- `php` (Drupal + PHP)

- `mariadb` (Datenbank)

- optional: `adminer` oder `phpmyadmin`

Container-Namen sind **fix**, damit Doku & Setup überall gleich sind.

---

## 🧠 Environment-Variablen (`.env`)

```
DRUPAL_DB_NAME=drupal_htlDRUPAL_DB_USER=rootDRUPAL_DB_PASSWORD=rootDRUPAL_DB_HOST=mariadb
```

➡️ Keine Credentials im Code

---

## 🚀 Start der Umgebung

```
docker compose up -d --build
```

Danach läuft:

- Drupal

- PHP

- MariaDB

---

## ⚙️ Drupal Erstinstallation (einmalig)

### 1️⃣ In den PHP-Container wechseln

```
docker exec -it drupal_php bash
```

---

### 2️⃣ Translations-Verzeichnis vorbereiten

```
mkdir -p sites/default/files/translationschmod -R 777 sites/default/files
```

---

### 3️⃣ Settings-Datei anlegen

```
cp sites/default/default.settings.php sites/default/settings.phpchmod 777 sites/default/settings.php
```

---

## 🗄️ Drupal Installationsdaten

### Datenbank

- **Database Name:** `drupal_htl`

- **Username:** `root`

- **Password:** `root`

### Verbindung

- **Driver:** `mysql`

- **Host:** `mariadb`

- **Port:** `3306`

➡️ Rest auf **Standard** lassen

---

## 🔧 PHP Konfiguration

PHP wird über ein eigenes Image gebaut.

### Vorteile

- Einheitliche PHP-Version

- Drupal-optimierte Defaults

- OPcache aktiv

- Fehler sichtbar (DEV-Modus)

Beispielwerte (php.ini):

- `memory_limit = 512M`

- `upload_max_filesize = 64M`

- `display_errors = On`

---

## 🧩 Custom-Module & Themes

- Custom-Module liegen in `custom-modules/`

- Custom-Themes liegen in `themes/custom/`

- Werden per Volume direkt in Drupal eingebunden

➡️ Kein Kopieren ins Container-FS nötig

---

## ✅ Vorteile dieser Infrastruktur

- Gleiche Umgebung für alle

- Kein "bei mir geht’s" Problem

- Schnell auf neuen Rechnern

- Ideal für Unterricht & Teamarbeit

---

## ⚠️ Regeln

- ❌ Keine Drupal-Dateien direkt im Container ändern

- ❌ Keine Passwörter hardcoden

- ✅ Alles über Volumes & Git

---

## 🧠 Empfehlung

Diese Struktur ist **Pflicht** für alle HTL Drupal-Projekte.

Erweiterungen (z. B. Redis, Solr, Xdebug) sind später möglich,
aber **nicht Teil des Basis-Setups**.
