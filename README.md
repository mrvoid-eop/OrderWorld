# OrderWorld

Fișierele de dezvoltare ale modpack-ului Minecraft OrderWorld.

Repository: https://github.com/mrvoid-eop/OrderWorld

Instanța locală:

```text
C:\Users\tigan\curseforge\minecraft\Instances\OrderWorld
```

## Starea proiectului

Configurarea Git este pregătită. Fișierele modpack-ului nu au fost încă importate.
Versiunile Minecraft, loader-ului și modurilor vor fi confirmate după import;
nu sunt deduse din alte modpack-uri.

## Conectarea la calculator

Urmează [ghidul pentru Windows și GitHub Desktop](docs/WINDOWS_SETUP.md).
Ghidul păstrează instanța la calea existentă și permite sincronizarea directă
în acel folder după configurarea inițială.

ChatGPT poate modifica fișierele din repository. Modificările ajung în instanța
locală când folosești **Pull origin** în GitHub Desktop. Pentru a trimite
modificările locale, folosește **Commit** și **Push origin**.

## Fișiere urmărite

| Cale | Conținut |
| --- | --- |
| `config/`, `defaultconfigs/` | Configurări ale modurilor |
| `kubejs/`, `scripts/` | Scripturi, rețete și resurse personalizate |
| `datapacks/`, `resourcepacks/` | Pachete personalizate dezarhivate |
| `openloader/`, `global_packs/` | Resurse încărcate global, dacă aceste foldere există |
| `packmenu/`, `patchouli_books/` | Meniuri și cărți, dacă aceste foldere există |
| `manifest.json`, `modlist.html`, `mod-list.txt` | Manifest și inventar al modurilor |
| `docs/` | Documentația proiectului |

Folderele sunt acceptate de regulile Git, dar nu sunt create automat și nu
confirmă că modurile respective sunt instalate. Căile noi de la rădăcină
trebuie adăugate explicit în `.gitignore`.

Salvările, logurile, backup-urile, fișierele JAR, arhivele și metadatele locale
CurseForge nu sunt urmărite. Fișierele ignorate rămân pe calculator.

Repository-ul este public. Verifică fișierele de configurare înainte de commit:
regulile `.gitignore` nu pot detecta parole sau tokenuri scrise în configurări.

## Verificarea modificărilor

Păstrează Minecraft închis în timpul sincronizării. După o modificare a
scripturilor sau configurărilor, pornește instanța și verifică rezultatul în joc.
Un commit reușit nu confirmă compatibilitatea cu modurile instalate.
