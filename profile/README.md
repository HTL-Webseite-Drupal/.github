# HTL Website – Drupal Rebuild

Schulisches Ingenieursprojekt zur **Neuentwicklung der HTL-Website mit Drupal**.  
Ziel ist eine **moderne, wartbare und langfristig weiterentwickelbare Website**, die sauber zwischen Schülergenerationen übergeben werden kann.

---

## 🎯 Projektziele

- Eigenes **Drupal Theme** (HTL Design)

- Eigene **Custom Module**

- Klare Standards für Struktur & Code

- Saubere Übergabe an nachfolgende Jahrgänge

- Reproduzierbare Entwicklungsumgebung

---

## 🧱 Technologie-Stack

- **Drupal 11**

- **PHP** (Docker Image)

- **MariaDB**

- **Docker & Docker Compose**

- GitHub für Versionierung & Releases

- Trello für Projektmanagement

---

## 🐳 Infrastruktur

Die komplette Entwicklung erfolgt **lokal mit Docker**.

### Ziele der Infrastruktur

- Einheitliche Dev-Umgebung für alle

- Kein "funktioniert nur bei mir" Problem

- Sehr schneller Einstieg für neue Schüler

- Kein lokales PHP / MySQL Setup nötig

---

## 🔧 Voraussetzungen

Es wird **nur Docker benötigt**.

Optional:

- Docker Compose v2 Plugin (meist bereits enthalten)

---

## 📥 Docker Installation

### 🪟 Windows

1. **Docker Desktop installieren**:  
   [Docker Desktop: The #1 Containerization Tool for Developers | Docker](https://www.docker.com/products/docker-desktop/)

2. Während der Installation:
   
   - **WSL2 aktivieren**
   
   - Neustart durchführen

3. Nach Installation prüfen:

```powershell
docker --version
docker compose version
```

4. Optional auch eine `Ubuntu WSL2` isntallation

🔗 [Ubuntu WSL2](optional/wsl-ubuntu.md) `optional/wsl-ubuntu.md`

--- 

### 🍎 macOS

1. **Docker Desktop für macOS installieren**:  
   [Docker Desktop: The #1 Containerization Tool for Developers | Docker](https://www.docker.com/products/docker-desktop/)

2. App starten und Berechtigungen erlauben

3. Terminal prüfen:

```bash
docker --version
docker compose version
```

---

### 🐧 Linux (Ubuntu / Debian)

```bash
sudo apt update
sudo apt install -y docker.io docker-compose-plugin
sudo systemctl enable docker --now
sudo usermod -aG docker $USER
```

➡️ Danach **abmelden & neu anmelden**

Test:

```bash
docker --version
docker compose version
```

---

## 🗺️ Roadmap & Projektorganisation

Für die Projektplanung verwenden wir **Trello**.

🔗 **Trello Board (Iteration 1 – erste Gruppe)**  
[Trello](https://trello.com/b/IzHLAasT/hauptboard)

- Backlog

- Aufgaben nach Iterationen

- Zuständigkeiten

---

## 🚪 Einstieg ins Projekt

Alle **technischen Details**, Setups und Regeln befinden sich im Ordner:

```text
docs/
```

➡️ **Dort beginnen**, bevor Code geschrieben wird

---

## 🧩 Module

### 📦 Benötigte Contrib-Module

Liste der benötigten Drupal-Module:

🔗 [Module](modules/contrib.md) `modules/contrib.md`

---

### 🛠 Eigene Custom Module

Für eigene Module gibt es eine klare Strukturvorgabe:

🔗 [Modul-Strultur](modules/custom-structure.md)  `modules/custom-structure.md`

Dort enthalten:

- Modul-Struktur

- `.info.yml` Vorgaben

- Versioning & Releases

---

## 📌 Wichtige Prinzipien

- Einheitliche Struktur > individuelle Lösungen

- Dokumentation ist **Pflicht**

- Versionierung läuft **automatisch**

- Infrastruktur nicht selbst umbauen

---

## ✅ Zusammenfassung

- Klare Projektvision

- Einheitliche Technik

- Saubere Übergabe möglich

- Ideal für langfristige Schulprojekte

➡️ Nachhaltig  
➡️ Wartbar  
➡️ Erweiterbar
