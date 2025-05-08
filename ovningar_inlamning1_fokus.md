# Förberedande övningar inför Inlämning 1

Dessa övningar tränar exakt de moment du kommer behöva i inlämningen. Skriv varje övning i en funktion och testa att anropa den. Skriv en commit efter varje steg.

---

## 1. Läs in ett namn från användaren

```powershell
$namn = Read-Host "Ange ett namn"
Write-Host "Du angav: $namn"
```

Git commit: `"Läsa in namn från användaren"`

---

## 2. Skapa en mapp med användarens namn

```powershell
$namn = "TestPerson"
$stig = "./$namn"

if (-Not (Test-Path $stig)) {
    New-Item -ItemType Directory -Path $stig
} else {
    Write-Host "Mappen finns redan."
}
```

Git commit: `"Skapa mapp med användarens namn"`

---

## 3. Skapa undermappar i den mappen

```powershell
$undermappar = @("Dokumentation", "Data", "Loggar")

foreach ($mapp in $undermappar) {
    $fullStig = Join-Path -Path $stig -ChildPath $mapp
    New-Item -ItemType Directory -Path $fullStig
}
```

Git commit: `"Skapa undermappar"`

---

## 4. Skapa en loggfil med dagens datum i namnet

```powershell
$datum = Get-Date -Format "yyyy-MM-dd"
$loggfil = Join-Path -Path $stig -ChildPath "Loggar/logg_$datum.txt"

Add-Content -Path $loggfil -Value "Logg skapad: $datum"
```

Git commit: `"Skapa loggfil med datum"`

---

## 5. Kombinera allt i en körbar `.ps1`-fil och lägg till kommentarer

```powershell
# Denna fil skapar en mappstruktur och en loggfil baserat på användarnamn
Import-Module ./verktyg.psm1
Starta-Verktyg  # ← din huvudfunktion
```

Git commit: `"Första körbara run.ps1 med struktur"`

---

Du är nu redo att bygga inlämningen!
