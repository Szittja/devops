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

------------------------------------------------------------------------

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

------------------------------------------------------------------------

# Git használata -- trunk-based development

A projekt trunk-based fejlesztési modellt követ.

-   **main** branch → trunk\
-   új funkciók → külön **feature branch**\
-   a változások külön commitokban jól követhetők\
-   merge → Pull Requesten keresztül

## Változások
- v1: Alap Hello World
- v2: Üzenet frissítve feature branch-ből

------------------------------------------------------------------------

## Docker

A projekt tartalmaz egy működő Dockerfile-t.

### Image build
```bash
docker build -t hello-devops-python:v1 .
```

Docker konténer indítása

``` bash
docker run -p 8080:8080 hello-devops-python:v1
```

Az alkalmazás elérhető:

http://localhost:8080

------------------------------------------------------------------------

#  Felhő Deploy (CD) -- Render.com

A projekt deploy-ja a **Render.com** free tier felhő szolgáltatásában
fut.

##  Használt szolgáltató

**Render.com -- Web Service (Docker runtime)**\
Ingyenes, automatikus deploy GitHub-ból a Dockerfile alapján.

------------------------------------------------------------------------

## Deploy lépések

1.  Lépj be: https://render.com\
2.  **New → Web Service**\
3.  Válaszd ki a GitHub repository-t:\
    Szittja/devops
4.  Beállítások:
    -   Runtime: **Docker**
    -   Branch: **main**
    -   Root Directory: `.`
    -   Dockerfile: automatikusan felismerve
5.  **Create Web Service**
6.  A Render automatikusan:
    -   klónozza a repo-t,
    -   buildeli a Docker image-et,
    -   futtatja a konténert.

------------------------------------------------------------------------

# Publikus URL

 **https://devops-xayh.onrender.com**

(A free tier idővel alvó módba teheti.)

------------------------------------------------------------------------

## Demo Feature Branch
Ez a branch azért készült, hogy látható legyen egy feature branch a repóban.


------------------------------------------------------------------------

# Projekt struktúrája

    devops/
     ├── app.py
     ├── requirements.txt
     ├── build.sh
     ├── build.ps1
     ├── Dockerfile
     ├── README.md
     └── .gitignore

------------------------------------------------------------------------

# Felhasznált technológiák

-   Python 3 + Flask
-   Git + GitHub
-   Trunk-based development
-   Docker
-   Render.com (CD -- Cloud Deploy)
-   VS Code