# HowTo: PS4 PKG Extraction Tool (Apple Silicon)

## English
```text
PS4 PKG Extraction Tool (Apple Silicon)
```

The application is a terminal tool for extracting PS4 `.pkg` game packages to use with shadPS4.

### Requirements

- Apple computer with Apple Silicon CPU and macOS 14 or higher

The system should provide:

- Bash
- Ruby
- standard Unix tools such as `tar`, `awk`, `sed`, `mktemp`, `tail`

If Ruby is missing, the app tries to install it automatically on startup through a supported package manager such as Homebrew, apt, dnf, or pacman.

### Start on macOS

1. Place `ps4-pkg-extraction-tool` in any folder.
2. Open Terminal.
3. Change into the folder where the file is located:

```bash
cd /path/to/folder
```

4. Make the file executable if needed:

```bash
chmod +x "ps4-pkg-extraction-tool"
```

5. Start the application:

```bash
./ps4-pkg-extraction-tool
```

If macOS blocks the file through Gatekeeper, remove the quarantine attribute:

```bash
xattr -d com.apple.quarantine "ps4-pkg-extraction-tool"
```

Then start it again:

```bash
./ps4-pkg-extraction-tool
```

### Use the Menu

After startup, the app shows:

```text
What do you want to extract?
  1) Single PKG file
  2) Folder with multiple PKG files
```

#### Option 1: Extract a Single PKG File

Choose:

```text
1
```

The app then asks for the PKG file:

```text
Drop the PKG game package you wanna extract on this screen and press Enter:
```

You can either:

- paste the full path to the `.pkg` file
- drag and drop the `.pkg` file into the terminal

Then press Enter.

Example:

```text
~/Downloads/#ROMS/PS4/GAMES/PKG/Game.pkg
```

The app automatically creates an output folder:

```text
READY
```

This folder is created in the same folder as the selected PKG file.

The extracted result will be placed, for example, here:

```text
~/Downloads/#ROMS/PS4/GAMES/PKG/READY/CUSAxxxxx
```

#### Option 2: Extract a Folder with Multiple PKG Files

Choose:

```text
2
```

The app then asks for the folder:

```text
Drop the folder including the PKG game packages you wanna extract on this screen and press Enter:
```

You can either:

- paste the full path to the folder
- drag and drop the folder into the terminal

Then press Enter.

The app searches the selected folder for PKG files and extracts them into:

```text
READY
```

### Drag and Drop in Terminal

macOS Terminal automatically escapes special characters. A path like:

```text
~/Downloads/#ROMS/PS4/GAMES/PKG/Game.pkg
```

may appear like this after drag and drop:

```text
~/Downloads/\#ROMS/PS4/GAMES/PKG/Game.pkg
```

This is normal. The app automatically cleans these terminal escapes.

### Successful Output

A successful extraction looks similar to this:

```text
Processing PKG: "Game.pkg"
Title ID: CUSAxxxxx
PKG Size: ...
Extracting to: ".../READY/CUSAxxxxx"
Progress: 10 / 37 files
Progress: 20 / 37 files
Progress: 37 / 37 files
Extraction complete. Files extracted to: ".../READY/CUSAxxxxx"

Done!
```

### Troubleshooting

#### `Permission denied`

The file is not executable.

Fix:

```bash
chmod +x "ps4-pkg-extraction-tool"
```

#### macOS Blocks the Application

The error may look similar to:

```text
cannot be opened because it is from an unidentified developer
```

Fix:

```bash
xattr -d com.apple.quarantine "ps4-pkg-extraction-tool"
```

#### `Ruby is required`

This tool needs Ruby. The app tries to install Ruby automatically. If that fails, install Ruby manually.

macOS with Homebrew:

```bash
brew install ruby
```

Ubuntu/Debian:

```bash
sudo apt update
sudo apt install ruby
```

#### `Error: File not found`

Check:

- Does the PKG file really exist?
- Did you paste the complete path?
- Are there hidden characters at the beginning or end of the path?
- Did you choose a file when the app asked for a file, or a folder when it asked for a folder?

### Notes

- The app extracts its bundled helper files into a temporary folder on startup.
- This temporary folder is deleted automatically when the app exits.
- The extracted PKG contents remain in the `READY` folder.
- The original PKG file is not modified.

---

## Deutsch
```text
PS4 PKG Extraction Tool (Apple Silicon)
```

Die Anwendung ist ein Terminal-Tool zum Entpacken von PS4-`.pkg` Spiele Pakete.

### Voraussetzungen

- Apple computer mit Apple Silicon CPU und macOS 14 odr höher

Auf dem System sollte vorhanden sein:

- Bash
- Ruby
- Standard-Unix-Tools wie `tar`, `awk`, `sed`, `mktemp`, `tail`

Falls Ruby fehlt, versucht die Anwendung beim Start Ruby automatisch über einen unterstützten Paketmanager zu installieren, zum Beispiel Homebrew, apt, dnf oder pacman.

### Starten auf macOS

1. Lege die Datei `ps4-pkg-extraction-tool` in einen Ordner deiner Wahl.
2. Öffne Terminal.
3. Wechsle in den Ordner, in dem die Datei liegt:

```bash
cd /pfad/zum/ordner
```

4. Mache die Datei ausführbar, falls nötig:

```bash
chmod +x "ps4-pkg-extraction-tool"
```

5. Starte die Anwendung:

```bash
./ps4-pkg-extraction-tool
```

Falls macOS die Datei wegen Gatekeeper blockiert, entferne das Quarantine-Attribut:

```bash
xattr -d com.apple.quarantine "ps4-pkg-extraction-tool"
```

Danach erneut starten:

```bash
./ps4-pkg-extraction-tool
```

### Menü verwenden

Nach dem Start erscheint:

```text
What do you want to extract?
  1) Single PKG file
  2) Folder with multiple PKG files
```

#### Option 1: Einzelne PKG-Datei entpacken

Wähle:

```text
1
```

Danach fragt die Anwendung nach der PKG-Datei:

```text
Drop the PKG game package you wanna extract on this screen and press Enter:
```

Du kannst jetzt entweder:

- den vollständigen Pfad zur `.pkg`-Datei einfügen
- oder die `.pkg`-Datei per Drag & Drop ins Terminal ziehen

Dann Enter drücken.

Beispiel:

```text
~/Downloads/#ROMS/PS4/GAMES/PKG/Game.pkg
```

Die Anwendung erstellt automatisch einen Ordner:

```text
READY
```

Dieser Ordner wird im selben Ordner wie die PKG-Datei angelegt.

Das Ergebnis landet dann zum Beispiel hier:

```text
~/Downloads/#ROMS/PS4/GAMES/PKG/READY/CUSAxxxxx
```

#### Option 2: Ordner mit mehreren PKG-Dateien entpacken

Wähle:

```text
2
```

Danach fragt die Anwendung nach dem Ordner:

```text
Drop the folder including the PKG game packages you wanna extract on this screen and press Enter:
```

Du kannst jetzt entweder:

- den vollständigen Pfad zum Ordner einfügen
- oder den Ordner per Drag & Drop ins Terminal ziehen

Dann Enter drücken.

Die Anwendung sucht im angegebenen Ordner nach PKG-Dateien und entpackt sie in:

```text
READY
```

### Drag & Drop im Terminal

macOS Terminal escaped Sonderzeichen automatisch. Aus einem Pfad wie:

```text
~/Downloads/#ROMS/PS4/GAMES/PKG/Game.pkg
```

kann beim Drag & Drop zum Beispiel werden:

```text
~/Downloads/\#ROMS/PS4/GAMES/PKG/Game.pkg
```

Das ist normal. Die Anwendung bereinigt solche Terminal-Escapes automatisch.

### Erfolgreiche Ausgabe

Bei einer erfolgreichen Extraktion sieht die Ausgabe ungefähr so aus:

```text
Processing PKG: "Game.pkg"
Title ID: CUSAxxxxx
PKG Size: ...
Extracting to: ".../READY/CUSAxxxxx"
Progress: 10 / 37 files
Progress: 20 / 37 files
Progress: 37 / 37 files
Extraction complete. Files extracted to: ".../READY/CUSAxxxxx"

Done!
```

### Fehlerbehebung

#### `Permission denied`

Die Datei ist nicht ausführbar.

Lösung:

```bash
chmod +x "ps4-pkg-extraction-tool"
```

#### macOS blockiert die Anwendung

Fehler kann ungefähr so wirken:

```text
cannot be opened because it is from an unidentified developer
```

Lösung:

```bash
xattr -d com.apple.quarantine "ps4-pkg-extraction-tool"
```

#### `Ruby is required`

Diese Tool benötigt Ruby. Die App versucht Ruby automatisch zu installieren. Falls das nicht klappt, installiere Ruby manuell.

macOS mit Homebrew:

```bash
brew install ruby
```

Ubuntu/Debian:

```bash
sudo apt update
sudo apt install ruby
```

#### `Error: File not found`

Prüfe:

- Existiert die PKG-Datei wirklich?
- Wurde der komplette Pfad eingefügt?
- Enthält der Pfad am Anfang oder Ende unsichtbare Zeichen?
- Wurde eine Datei statt eines Ordners gewählt, oder umgekehrt?

### Hinweise

- Die App entpackt ihre eingebetteten Hilfsdateien beim Start in einen temporären Ordner.
- Dieser temporäre Ordner wird beim Beenden automatisch gelöscht.
- Die entpackten PKG-Inhalte bleiben natürlich im `READY`-Ordner erhalten.
- Die App verändert die originale PKG-Datei nicht.
