# Podmorski svijet u Blenderu

3D vizualizacija podmorskog svijeta i olupine broda izrađena u **Blenderu**. Projekt je nastao pod snažnim utjecajem Pixarovog filma *U potrazi za Nemom*, s posebnim fokusom na kreiranje atmosfere kroz volumetrijsko osvjetljenje, ponašanje jata riba te vizualno pripovijedanje prijelaza s površine u mračne dubine. Zvučna komponenta je namjerno izostavljena kako bi se naglasila izoliranost podmorja.

> Seminarski rad — Fakultet primijenjene matematike i informatike, Sveučilište J. J. Strossmayera u Osijeku, 2026.
> Student: Tomislav Galošević

![status](https://img.shields.io/badge/status-completed-brightgreen) ![Blender](https://img.shields.io/badge/Blender-3D-orange) ![license](https://img.shields.io/badge/license-MIT-blue)

## Sadržaj

- [O projektu](#o-projektu)
- [Kako to izgleda](#kako-to-izgleda)
- [Korištene tehnike](#korištene-tehnike)
- [Struktura scene](#struktura-scene)
- [Preduvjeti](#preduvjeti)
- [Pokretanje](#pokretanje)
- [Renderiranje](#renderiranje)
- [Struktura repozitorija](#struktura-repozitorija)
- [Reference](#reference)
- [Napomena o korištenju AI alata](#napomena-o-korištenju-ai-alata)
- [Licenca](#licenca)

## O projektu

Cilj projekta bio je izraditi vizualno impresivno podvodno okruženje koje se oslanja isključivo na vizualne elemente i tišinu kako bi se dočarala dubina. Radnja prati kameru koja s površine zaranja na dno, gdje se otkriva stara olupina drvene galije, okružena dinamičnim morskim životom. 

Posebna je pažnja posvećena dinamici faune te postizanju fotorealistične podvodne magle kroz napredno sjenčanje (shading) i raspršivanje svjetlosti.

## Kako to izgleda

https://youtu.be/UhHKMCiD9HU

## Korištene tehnike

| Element | Pristup |
|---|---|
| **Površina i morsko dno** | `Ocean` modifikator (površina) te `Subdivision Surface` + `Displace` s proceduralnim teksturama (dno). |
| **Olupina broda** | Gotov 3D asset preuzet s interneta, skaliran, pozicioniran i dodatno teksturiran za efekt propadanja i podvodnog osvjetljenja. |
| **Morska fauna (ribe)** | Ručno modeliranje (box modeling) riba klauna i plavih tangova. Animacija jata ostvarena je kombinacijom `Particle Systems` i `Boids` fizike. |
| **Morski pas** | Ručno izmodeliran predator s dodanom skeletnom strukturom (`Rigging`). Animiran ručno pomoću ključnih sličica (`Keyframes`). |
| **Volumetrija i dubina** | Veliki granični okvir preko cijele scene s `Volume Scatter` i `Volume Absorption` materijalima (podvodna magla). |
| **Osvjetljenje** | Ambijentalno svjetlo koje slabo prodire s površine + diskretna usmjerena `Spotlights` svjetla za isticanje detalja. |
| **Ambijentalne čestice** | Dodatni `Particle` sustav za simulaciju morske prašine i planktona koji slobodno plutaju. |

## Struktura scene

Scena je podijeljena na nekoliko ključnih segmenata:

1. **Okoliš** — Površina mora s valovima i pješčano/muljevito dno.
2. **Središnji objekt** — Model olupine broda smješten u udubinu na dnu.
3. **Fauna** — Model morskog psa te sustavi čestica koji upravljaju jatima manjih riba.
4. **Atmosfera (Volumetrija)** — Objekt koji obavija cijelu scenu i definira gustoću vode te apsorpciju boja.
5. **Kamera** — Bézierova krivulja (`Follow Path`) kojom je animiran gladak prelet i zaron ronioca.

## Preduvjeti

- [Blender](https://www.blender.org/download/) 3.x ili noviji
- Solidan GPU i CPU radi izračuna volumetrije i većeg broja čestica.

## Pokretanje

```bash
git clone https://github.com/TvojGitHub/PodmorskiSvijet.git
cd PodmorskiSvijet
```

Otvori `.blend` datoteku direktno u Blenderu:

```bash
blender podmorski_svijet.blend
```

## Renderiranje

Proces iscrtavanja zahtijevao je optimizaciju parametara (broja uzoraka/samples, odbijanja svjetlosnih zraka) zbog složene volumetrije i velikog broja poligona (brod, ribe). 
- Za čišćenje slike od vizualnog šuma korišten je Blenderov **Denoiser**.
- Izlazni format je **MKV video sekvenca** sastavljena od kontinuiranih sličica.
- **Audio postavke:** Prilikom enkodiranja izričito je odabrana `No Audio` postavka.

## Struktura repozitorija

```
.
├── podmorski_svijet.blend # glavna Blender datoteka s projektom
├── SeaRender.mkv          # gotovi render output (60 okvira)
├── Seminar.docx           # seminarski rad i detaljna razrada projekta
└── README.md
```

## Reference

1. Blender Foundation. (2024). *Blender 3D Reference Manual*. Dostupno na: https://docs.blender.org/
2. Murdock, K. L. (2022). *Blender 3D Basics: A Complete Guide to Open Source 3D Creation*.
3. Gouni, S. i sur. (2020). *Osnove 3D modeliranja, volumetrije i animacije fluida*.
4. *U potrazi za Nemom* (Finding Nemo, Pixar Animation Studios, 2003.) - glavna vizualna inspiracija.

## Napomena o korištenju AI alata

Autor je koristio Gemini (Google) kao pomoć pri pisanju popratnog seminarskog rada. Generativna tehnologija korištena je za strukturiranje i stilsko oblikovanje teksta te akademsko opisivanje procesa 3D modeliranja, animacije i postavljanja osvjetljenja podmorskog svijeta i olupine broda u alatu Blender. Nijedan generirani sadržaj činjenične prirode ili vezan uz temu rada nije predstavljen kao izvorno autorovo djelo, već je AI alat poslužio isključivo kao jezična i strukturna podrška.
