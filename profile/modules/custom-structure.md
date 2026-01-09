# Custom Module Struktur

Alle Custom-Module **müssen** sich an diese Struktur halten. Diese Richtlinie gilt für **alle HTL Custom-Module** und ist verpflichtend.

---

## 📦 Basis `.info.yml`

Jedes Modul **muss** eine `.info.yml` besitzen und **muss** ein `version`-Feld enthalten, da dieses automatisch vom GitHub-Workflow gepflegt wird.

```yml
name: ""
type: module
description: ""
package: HTL
core_version_requirement: ^11
version: 0.0.1

dependencies:
  - drupal:media
```

- `dependencies` sind nur ein Beispiel

- `version` **niemals manuell erhöhen**

---

## 🛠 Modul erstellen (empfohlen)

Zum Erstellen neuer Module **muss** folgendes Plugin verwendet werden:

👉 [Drupal Generator - IntelliJ IDEs Plugin | Marketplace](https://plugins.jetbrains.com/plugin/26573-drupal-generator)

### Warum dieses Plugin?

- erzeugt **korrekte Dateinamen**

- erzeugt eine **genormte Drupal-Struktur**

- Drupal ist bei Modulnamen & Pfaden **sehr strikt**

- Root-Files können ausgewählt werden

- jede Datei enthält ein valides Grundgerüst

---

## 🧩 Modul Layout (Pflichtstruktur)

Die Ordnerstruktur **muss** sich grob an folgendem Layout orientieren.  
Der `src/`-Ordner ist **optional erweiterbar**, aber die Grundstruktur ist einzuhalten.

```
└── htl_typegrid_module/
    ├── htl_typegrid.info.yml
    ├── htl_typegrid.install
    ├── htl_typegrid.libraries.yml
    ├── htl_typegrid.links.menu.yml
    ├── htl_typegrid.module
    ├── htl_typegrid.routing.yml
    ├── htl_typegrid.services.yml
    ├── templates/
    │   └── block.html.twig
    ├── js/
    │   └── script.js
    ├── css/
    │   └── style.css
    ├── assets/
    │   └── dummy.png
    ├── src/
    │   ├── Service/
    │   ├── Model/
    │   ├── Helper/
    │   ├── Form/
    │   ├── Controller/
    │   ├── Commands/
    │   └── Plugin/
    │       └── Block/
    └── config/
        └── schema/
            └── htl_typegrid.schema.yml
```

---

## 🔁 GitHub Versioning & Releases (Pflicht)

Jedes Custom-Module-Repository **muss** den standardisierten GitHub Workflow verwenden.

### 📂 Ablageort

```text
.github/workflows/version-release.yml
```

➡️ Der Workflow ist **plug & play**  
➡️ **keine Anpassung pro Modul notwendig**  
➡️ funktioniert für **ein oder mehrere Module pro Repository**

---

## 🔖 Versionierung (Semantic Versioning)

Wir verwenden **SemVer**:

| Typ     | Ergebnis | Bedeutung        |
| ------- | -------- | ---------------- |
| upgrade | x.0.0    | Breaking Changes |
| release | 0.x.0    | Neue Features    |
| patch   | 0.0.x    | Bugfixes         |

---

## 🚀 Release auslösen

### Variante 1: Commit-Message (Standard)

Ein Release wird automatisch erstellt, wenn der Commit-Text enthält:

- `-upgrade`

- `-release`

- `-patch`

**Beispiele:**

```text
feat: neue Grid-API -release
fix: falsche Feldzuordnung -patch
refactor: interne Struktur geändert -upgrade
```

---

### Variante 2: Manuell (GitHub UI)

1. GitHub → **Actions**

2. Workflow **Version Update and Release** auswählen

3. **Run workflow**

4. Release-Typ auswählen

---

## ⚙️ Was macht der Workflow?

- liest bestehende Git-Tags

- berechnet die nächste Version

- aktualisiert **alle `*.info.yml` Dateien** im Repository

- erstellt automatisch:
  
  - Commit mit neuer Version
  
  - Annotated Git-Tag (`vX.Y.Z`)
  
  - GitHub Release

---

## ⚠️ Wichtige Regeln

- ❌ Version **niemals manuell ändern**

- ❌ keine eigenen Release-Tags setzen

- ✅ ein Repository = eine Version

- ✅ mehrere Module im Repo teilen sich **dieselbe Version**

---

## ✅ Zusammenfassung

- Einheitliche Modulstruktur

- Einheitliches Versioning

- Automatische Releases

- Keine manuelle Pflege nötig

➡️ Weniger Fehler  
➡️ Saubere Releases  
➡️ Nachvollziehbare Versionshistorie
