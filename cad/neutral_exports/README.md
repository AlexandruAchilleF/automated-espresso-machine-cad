# Formate Neutre CAD / Neutral CAD Exports

Acest director conține exporturile în formate neutre ale ansamblului 3D și ale componentelor principale ale espressorului automat, optimizate pentru interoperabilitate multi-platformă (SolidWorks, Autodesk Inventor, PTC Creo, Siemens NX, CATIA, Fusion 360, FreeCAD) și fluxuri de fabricație aditivă / printare 3D.

---

## Fișiere disponibile / Programate pentru export

| Fișier | Format | Standard / Protocol | Domeniu de utilizare principal |
| :--- | :--- | :--- | :--- |
| **`espressor_ansamblu_complet.step`** | STEP (`.step` / `.stp`) | ISO 10303-214 / AP242 | Schimb de geometrie solidă B-Rep cu păstrarea culorilor și ierarhiei de ansamblu |
| **`espressor_ansamblu_complet.iges`** | IGES (`.iges` / `.igs`) | US PRO / ANSI | Compatibilitate cu pachete CAD/CAM legacy |
| **`espressor_ansamblu_complet.stl`** | STL (`.stl`) | Triangulated Mesh (Tessellated) | Printare 3D (Slicere: PrusaSlicer, Bambu Studio, Cura) și randare în motoare externe (Blender, KeyShot) |
| **`grup_extractie_58mm.step`** | STEP (`.step`) | ISO 10303-214 | Subansamblu critic grup de extracție pentru simulări termice (CFD / FEA) |
| **`ansamblu_portafiltru.stl`** | STL (`.stl`) | Mesh de înaltă rezoluție | Prototipare rapidă prin sinterizare laser (SLS) sau SLA |

---

## Procedură de export din Autodesk AutoCAD

Dacă doriți să re-generați formatele neutre direct din fișierul nativ [`cad/native/Ansamblu_Total.dwg`](../native/Ansamblu_Total.dwg):

### 1. Export STEP (`.step` / `.stp`)
1. Deschideți modelul în AutoCAD 3D.
2. În linia de comandă tastați `EXPORT` sau folosiți comanda dedicată `STEPEXT`.
3. Selectați corpurile solide 3D (`3D Solids`) dorite.
4. Setați protocolul la **STEP AP214** (pentru conservarea structurii de culori și straturi).
5. Salvați fișierul în acest director.

### 2. Export STL (`.stl`) pentru Printare 3D
1. Tastați comanda `STLOUT`.
2. Selectați corpul 3D solid (un singur solid per operațiune sau combinați cu `UNION`).
3. Confirmați crearea fișierului binar (`Binary STL file: Yes`).
4. Selectați rezoluția / deviația de fațetare (controlată prin variabila de sistem `FACETRES = 5` sau `8` pentru curburi perfect netede).

### 3. Export ACIS SAT (`.sat`)
1. Tastați comanda `ACISOUT`.
2. Selectați solidele dorite și exportați în format SAT pentru compatibilitate directă de nucleu geometric ACIS.
