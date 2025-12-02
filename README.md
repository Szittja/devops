# Hello DevOps Python

Ez egy egyszerű **Python + Flask** webalkalmazás, amely a DevOps
alaplépéseit mutatja be:

-   kódkészítés\
-   verziókövetés (trunk-based development)\
-   buildelés\
-   konténerizálás\
-   felhő deploy (Render.com -- CD)

Az alkalmazás egyetlen HTTP végpontot szolgál ki, amely egyszerű
szöveget ad vissza.

------------------------------------------------------------------------

# Alkalmazás futtatása lokálisan

## Követelmények

-   Python 3.10+
-   Git
-   (Opc.) Docker
-   (Opc.) Render.com account (free tier)

------------------------------------------------------------------------

## Virtuális környezet létrehozása

### Windows (PowerShell)

``` powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

### Linux / macOS

``` bash
python -m venv .venv
source .venv/bin/activate
```

------------------------------------------------------------------------

## Csomagok telepítése

``` bash
pip install -r requirements.txt
```

------------------------------------------------------------------------

## Alkalmazás indítása

``` bash
python app.py
```

Az alkalmazás elérhető:

**http://localhost:8080**


# Buildelés

A projekt tartalmaz build scripteket.

### Linux / macOS

``` bash
./build.sh
```

### Windows (PowerShell)

``` powershell
./build.ps1
```

A build: - létrehozza a `.venv` virtuális környezetet, - telepíti a
csomagokat a `requirements.txt` alapján.

Egy külső felhasználó is gond nélkül végig tudja csinálni.

# Git használata -- trunk-based development

A projekt trunk-based fejlesztési modellt követ.

-   **main** branch → trunk\
-   új funkciók → külön **feature branch**\
-   a változások külön commitokban jól követhetők\
-   merge → Pull Requesten keresztül

## Változások
- v1: Alap Hello World
- v2: Üzenet frissítve feature branch-ből