# Conectarea instanței OrderWorld la GitHub

Ținta este folderul existent:

```text
C:\Users\tigan\curseforge\minecraft\Instances\OrderWorld
```

Configurarea folosește GitHub Desktop. Modificările primite ulterior prin
**Pull origin** vor ajunge direct în această instanță.

## 1. Creează copia inițială a repository-ului

Închide Minecraft și CurseForge. Deschide GitHub Desktop și autentifică-te cu
contul `mrvoid-eop`.

În **File → Clone repository → URL**, folosește:

```text
https://github.com/mrvoid-eop/OrderWorld.git
```

Pentru **Local path**, alege un folder nou, gol, de exemplu:

```text
C:\Users\tigan\Documents\OrderWorld-Git-Setup
```

Apasă **Clone**. Acest folder este doar copia inițială pentru configurare.
Instanța existentă rămâne la calea ei. Git nu poate clona direct într-un folder
deja populat.

[Instrucțiunile GitHub pentru clonare](https://docs.github.com/en/desktop/adding-and-cloning-repositories/cloning-and-forking-repositories-from-github-desktop).

## 2. Atașează istoricul Git la instanța existentă

Închide GitHub Desktop după terminarea clonării, apoi deschide cele două
foldere în File Explorer. Activează afișarea elementelor ascunse, ca să vezi
folderul `.git` din copia clonată.

Înainte de copiere, verifică dacă instanța OrderWorld conține deja un fișier sau
folder `.git`. Dacă există, oprește acest pas: instanța are deja o configurare
Git care trebuie verificată. Nu o înlocui.

Din `OrderWorld-Git-Setup`, copiază în instanța OrderWorld:

- `.git` — folderul complet, inclusiv conținutul ascuns;
- `.gitignore`;
- `.gitattributes`;
- `README.md`;
- `LICENSE`;
- `docs` — folderul complet.

Acestea sunt fișierele inițiale ale repository-ului. Dacă între timp au apărut
și alte fișiere în copia clonată, verifică-le înainte de acest pas.
Nu înlocui fișiere existente când Windows întreabă despre un conflict:
oprește copierea și comunică numele fișierelor pentru comparare.

Nu muta modurile sau salvările. Copierea `.git` adaugă istoricul și conexiunea
la repository; regulile din `.gitignore` stabilesc ce fișiere locale vor fi
propuse pentru commit.

## 3. Deschide instanța în GitHub Desktop

Redeschide GitHub Desktop. Alege **File → Add local repository**, selectează
folderul instanței OrderWorld și apasă **Add repository**.

Verifică prin **Repository → Show in Explorer** că repository-ul selectat este
chiar în `curseforge\minecraft\Instances\OrderWorld`, nu în folderul de setup.
De acum folosește intrarea pentru instanța reală. Copia `OrderWorld-Git-Setup`
nu este folderul în care vei edita modpack-ul.

[Instrucțiunile GitHub pentru adăugarea unui repository local](https://docs.github.com/en/desktop/adding-and-cloning-repositories/adding-a-repository-from-your-local-computer-to-github-desktop).

## 4. Trimite fișierele modpack-ului

În fila **Changes**, verifică lista. Ar trebui să apară scripturile și
configurările din folderele acceptate de `.gitignore`. `mods/`, `saves/`,
`logs/` și `minecraftinstance.json` nu trebuie să apară.

Repository-ul este public: verifică și conținutul configurărilor care folosesc
servicii externe, ca să nu incluzi parole sau tokenuri. Debifează fișierele
care conțin astfel de date.

Scrie mesajul `Import OrderWorld modpack configuration`, apoi apasă
**Commit to main** și **Push origin**. După push, fișierele pot fi citite și
modificate prin conexiunea GitHub din ChatGPT.

Adaugă și inventarul modurilor. În PowerShell, rulează:

```powershell
Set-Location -LiteralPath 'C:\Users\tigan\curseforge\minecraft\Instances\OrderWorld'
Get-ChildItem -LiteralPath '.\mods' -Filter '*.jar' -File |
    Sort-Object Name |
    Select-Object -ExpandProperty Name |
    Set-Content -LiteralPath '.\mod-list.txt' -Encoding UTF8
```

Comanda creează sau actualizează `mod-list.txt` cu numele JAR-urilor, fără să
încarce JAR-urile. Fă commit și push pentru acest fișier. Comunică separat
versiunea Minecraft și versiunea Forge/NeoForge/Fabric afișate în CurseForge.

[Instrucțiunile GitHub pentru push](https://docs.github.com/en/desktop/making-changes-in-a-branch/pushing-changes-to-github-from-github-desktop).

## 5. Lucrul de zi cu zi

1. Închide Minecraft înainte de sincronizare.
2. Salvează prin commit modificările locale pe care vrei să le păstrezi.
3. Apasă **Fetch origin**, apoi **Pull origin** dacă există modificări noi.
4. Dacă apar conflicte, rezolvă-le înainte să continui; nu folosi force push
   sau discard changes ca să treci peste ele.
5. Folosește **Push origin** pentru a trimite commit-urile locale.
6. Pornește Minecraft și verifică schimbările în joc.

GitHub nu actualizează automat instanța cât timp joci. Salvările excluse din
Git trebuie păstrate prin backup-ul obișnuit al lumilor.
