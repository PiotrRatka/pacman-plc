# [EN] Pacman PLC (CoDeSys v2.3)

PL bellow.

A classic Pacman game implementation developed in CoDeSys v2.3 for a soft-PLC environment, written in Structured Text (ST) and featuring native Target Visu graphics.

## Architecture & Logic

- **Grid & Dot Matrix:** The 20x15 maze is built using two-dimensional arrays (`ARRAY[0..20, 0..15] OF BOOL`) inside the `MAPA` function block, storing wall locations and collectible dots separately.
- **Collision Detection:** The `OBLICZ_KOLIZJE` program cyclically evaluates adjacent cells in X and Y planes, preventing coordinate updates into wall boundaries.
- **Movement & Timing:** Coordinates `hoz` and `ver` are driven by bidirectional counters (`CTUD`) triggered by a 200 ms `TON` timer.
- **Input Handling:** WASD directional controls mapped to inputs `S1`–`S4` using bistable latches (`SR`).
- **HMI Visualization:** The `GRA` screen binds sprite positions directly to PLC coordinate variables and drives mouth-opening animations via an auxiliary timer.

## Repository Structure

- `POUs/` — source code of program blocks in Structured Text (`PLC_PRG`, `MAPA`, `OBLICZ_KOLIZJE`)
- `Global_Variables/` — global variable declarations, flags, and game coordinates
- `Visualizations/` — HMI screen definition (`GRA`) and visual property bindings
- `PACMAN.pro` — full CoDeSys v2.3 binary project file
- `.pacman_demo.gif` / `.game_preview.png` — gameplay demo animation and screenshot
- `PACMAN00000000s.ci` — CoDeSys compiler intermediate cache file

## How to Run

1. Open `PACMAN.pro` in CoDeSys v2.3[cite: 1].
2. Enable simulation via **Online** -> **Simulation Mode**.
3. Log in to the target (**Online** -> **Login** / `Alt + F8`) and start program execution (**Online** -> **Run** / `F5`).
4. Navigate to the **Visualizations** tab, open `GRA`, and control movement using the W, A, S, and D keys.

# Pacman PLC (CoDeSys v2.3)

Implementacja gry Pacman przygotowana w środowisku CoDeSys v2.3 na wirtualnym sterowniku PLC w języku Structured Text (ST) z wykorzystaniem wbudowanego modułu wizualizacji Target Visu.


## Opis działania

- **Siatka labiryntu i punkty:** Układ planszy o wymiarach 20x15 zrealizowany na dwuwymiarowych macierzach `ARRAY[0..20, 0..15] OF BOOL` w bloku funkcyjnym `MAPA` (oddzielne tablice dla geometrii ścian oraz punktów do zebrania).
- **Detekcja kolizji:** Program `OBLICZ_KOLIZJE` cyklicznie sprawdza stan sąsiednich komórek w osiach poziomej i pionowej, blokując ruch postaci po napotkaniu przeszkody.
- **Ruch i pozycjonowanie:** Współrzędne `hoz` i `ver` sterowane są licznikami rewersyjnymi `CTUD`, taktowanymi timerem cyklicznym `TON` (200 ms).
- **Sterowanie klawiaturą:** Obsługa wejść w układzie WASD (`S1`–`S4`) zrealizowana na przerzutnikach bistabilnych `SR`.
- **Wizualizacja:** Ekran `GRA` z dynamiczną zmianą położenia postaci na bazie aktualnych koordynatów oraz animacją kłapania ustami sterowaną osobnym timerem.

## Struktura plików

- `.pacman_demo.gif` / `.game_preview.png` — animacja demonstracyjna i zrzut ekranu rozgrywki
- `POUs/` — kod źródłowy bloków programowych w Structured Text (`PLC_PRG`, `MAPA`, `OBLICZ_KOLIZJE`)
- `Global_Variables/` — deklaracje zmiennych globalnych, współrzędnych i flag ruchu[cite: 1]
- `Visualizations/` — definicja ekranu HMI `GRA` wraz z przypisaniem zmiennych do obiektów graficznych[cite: 1]
- `PACMAN.pro` — kompletny, binarny plik projektu gotowy do otwarcia w środowisku CoDeSys v2.3[cite: 1]
- `PACMAN00000000s.ci` — plik tymczasowy kompilatora CoDeSys (zawiera dane kompilacji i cache symboli)

## Uruchomienie

1. Otwórz plik `PACMAN.pro` w programie CoDeSys v2.3[cite: 1].
2. Włącz tryb symulacji w menu górnym: **Online** -> **Simulation Mode**.
3. Połącz się ze sterownikiem (**Online** -> **Login** / `Alt + F8`), a następnie uruchom wykonywanie programu (**Online** -> **Run** / `F5`).
4. Przejdź do zakładki **Visualizations**, otwórz obiekt `GRA` i steruj ruchem postaci za pomocą klawiszy W, A, S, D.
