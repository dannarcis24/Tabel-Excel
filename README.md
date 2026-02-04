# 🏆 Ranking System & Excel Exporter (C Implementation)

[![C Language](https://img.shields.io/badge/Language-C-00599C?style=flat&logo=c&logoColor=white)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Data Structures](https://img.shields.io/badge/Focus-Linked%20Lists-orange?style=flat)]()

**Ranking System** este o aplicație dezvoltată în limbajul C concepută pentru a gestiona baze de date cu participanți, a-i organiza în funcție de performanță și a genera un raport tabelar compatibil cu Excel (format `.xlt`).

## 🚀 Funcționalități Principală

* **Gestiune Dinamică**: Utilizatorul poate introduce un număr nelimitat de concurenți, memoria fiind gestionată dinamic pentru nume și prenume.
* **Organizare pe Niveluri (Clasament)**: Aplicația grupează automat concurenții care au același punctaj.
* **Ordonare Automată**: Sistemul inserează noii participanți direct în poziția corectă din punct de vedere al punctajului (ordine descrescătoare), utilizând liste înlănțuite imbricate.
* **Export Tabelar**: Generează un fișier de tip "tab-separated values" cu extensia `.xlt`, permițând vizualizarea ierarhică a locurilor ocupate (Locul 1, Locul 2 etc.) într-un format de tip coloane.
* **Validare Date**: Include verificări pentru integritatea numelor (fără spații, lungime minimă) și a punctajelor.



---

## 🏛️ Arhitectura Datelor

Aplicația se bazează pe o structură de date de tip **Listă de Liste**:

1. **Structura `concurent`**: Reține datele individuale (Nume, Prenume, Punctaj).
2. **Structura `clasament`**: O listă simplu înlănțuită ce grupează concurenții cu același punctaj.
3. **Structura `List` (BigList)**: O listă principală unde fiecare nod reprezintă un punctaj unic și conține o referință către lista de concurenți aferentă acelui scor.



---

## 🛠️ Structura Proiectului

* `main.c`: Coordonatorul aplicației; gestionează bucla de citire și funcția de export/afișare a tabelului final.
* `excellLib.h`: Header-ul care definește structurile de date și prototipurile funcțiilor pentru modularizare.
* `create.c`: Conține logica pentru citirea dinamică a șirurilor de caractere și validarea datelor de intrare.
* `functList.c`: Implementarea algoritmilor de inserare ordonată, gestionarea nodurilor de clasament și eliberarea memoriei.

---

## ⚙️ Instalare și Rulare

1. **Compilare**:
   Utilizați un compilator C (precum GCC) pentru a asambla modulele:
   ```bash
   gcc -o clasament main.c create.c functList.c -I clasment
   ```
2. **Executie:**
   ```bash
   ./clasment
   ```
   
---
## 🚀 Utilizare

Pentru a genera clasamentul, urmați acești pași în interfața consolei:

1. **Introducere Date**: Introduceți numărul total de concurenți.
2. **Completare Profil**: Pentru fiecare participant, completați datele solicitate (Nume, Prenume, Punctaj).
3. **Generare Raport**: La finalizarea introducerii datelor, programul va genera automat fișierul `tabelConcurenti.xlt` în directorul curent.

---

## 📂 Exemplu de Output (tabelConcurenti.xlt)

Fișierul generat utilizează delimitarea prin Tab, permițând deschiderea directă în Microsoft Excel sau în orice editor de text. Structura tabelului va arăta astfel:

| Numar | Locul 1 | | | Locul 2 | | |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | **Nume** | **Prenume** | **Punctaj** | **Nume** | **Prenume** | **Punctaj** |
| **1.** | Ionescu | Ana | 100 | Popescu | Dan | 95 |
| **2.** | Vasilescu | Ion | 100 | | | |
