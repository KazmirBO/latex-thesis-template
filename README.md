# 🎓 Szablon LaTeX dla Prac Dyplomowych

Uniwersalny szablon LaTeX do formatowania polskich prac dyplomowych (licencjackich i magisterskich) z automatycznym formatowaniem, wieloma stylami numeracji stron i zgodnym z wymaganiami akademickimi układem.

![LaTeX](https://img.shields.io/badge/LaTeX-008080?style=flat&logo=latex&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Version](https://img.shields.io/badge/Version-2.2-blue.svg)

## 🚀 Szybki start

### 1. 🔧 Przygotowanie środowiska

> **Uwaga:** Szablon przetestowany z **LuaLaTeX** i **Biber** na systemie GNU/Linux dystrybucji Gentoo. Uruchamiany na Windows, ale działanie nie jest w 100% gwarantowane. Inne kompilatory nie były testowane.

**Linux (Ubuntu/Debian):**
```bash
sudo apt-get install texlive-full biber
```

**Windows:**
- [MiKTeX](https://miktex.org/) - zalecane dla użytkowników Windows
- [TeX Live](https://www.tug.org/texlive/) - alternatywa wieloplatformowa

### 2. 📁 Struktura plików

```
twoja-praca/
├── 📄 Szablon.sty          # Pakiet stylu (skopiuj z tego katalogu)
├── 📄 Szablon.tex          # Główny plik (skopiuj i dostosuj)
├── 📄 references.bib       # Bibliografia (skopiuj i wypełnij)
├── 📁 img/                 # Katalog na obrazy
│   └── 🖼️ logo.png        # Logo uczelni
└── 📁 chapters/           # Katalog na rozdziały (opcjonalny)
    ├── 📄 01-wstep.tex
    ├── 📄 02-przegląd.tex
    └── ...
```

### 3. ⚙️ Dostosowanie szablonu

#### Edytuj zmienne w pliku `Szablon.tex`:

```latex
% Ścieżka do logo uczelni (opcjonalne)
\newcommand{\logoPath}{./img/logo.png}

% Dane uczelni
\newcommand{\universityName}{Nazwa Twojej Uczelni}
\newcommand{\fieldOfStudy}{Kierunek studiów}
\newcommand{\studyMode}{Tryb studiów (stacjonarny/niestacjonarny)}
\newcommand{\studyLevel}{Poziom studiów (I/II stopnia)}

% Tytuły pracy
\newcommand{\thesisTitlePL}{Tytuł pracy magisterskiej w języku polskim}
\newcommand{\thesisTitleEN}{Title of the Master's Thesis in English}

% Dane autora i promotora
\newcommand{\student}{Imię i Nazwisko}
\newcommand{\albumNumber}{Numer albumu}
\newcommand{\supervisor}{Tytuł naukowy Imię Nazwisko promotora}

% Stopka dokumentu
\newcommand{\titlePageFooter}{Lublin \the\year}

% Wybór stylu numeracji (odkomentuj wybraną opcję):
% \renewcommand{\setupPageStyle}{\setupPageStyleBottomOuter}    % Domyślny: dół, zewnętrzna-wewnętrzna
% \renewcommand{\setupPageStyle}{\setupPageStyleBottomCenter}   % Dół, środek
% \renewcommand{\setupPageStyle}{\setupPageStyleTopOuter}       % Góra, zewnętrzna-wewnętrzna
% \renewcommand{\setupPageStyle}{\setupPageStyleTopCenter}      % Góra, środek
```

### 4. 🔨 Kompilacja

> **Zalecane:** Szablon został zaprojektowany i przetestowany z `lualatex` i `biber`. Inne kompilatory nie były testowane i mogą powodować problemy.

**Standardowa kompilacja:**
```bash
lualatex Szablon.tex
biber Szablon
lualatex Szablon.tex
lualatex Szablon.tex
```

**Z latexmk (automatyzacja):**
```bash
latexmk -lualatex -biber Szablon.tex
```

## ✨ Funkcje szablonu

<details>
<summary><strong>📐 Automatyczne formatowanie</strong></summary>

- ✅ **Układ dwustronny** z odpowiednimi marginesami
- ✅ **Odstęp 1,5 linii** zgodny z wymaganiami akademickimi  
- ✅ **Czcionka Times New Roman** (12pt)
- ✅ **Automatyczna numeracja** stron i rozdziałów
- ✅ **Wybór stylu numeracji stron** (4 opcje: dół/góra, środek/zewnętrzny)

</details>

<details>
<summary><strong>📋 Strona tytułowa</strong></summary>

- ✅ Automatyczne generowanie na podstawie zmiennych
- ✅ Walidacja wymaganych pól
- ✅ Wsparcie dla logo uczelni (opcjonalne)

</details>

<details>
<summary><strong>📝 Oświadczenia prawne</strong></summary>

- ✅ Oświadczenie promotora
- ✅ Oświadczenie autora o samodzielności
- ✅ Zgodne z polskimi wymogami prawnymi

</details>

<details>
<summary><strong>📖 Bibliografia</strong></summary>

- ✅ Format **BibTeX** z silnikiem **Biber**
- ✅ Polski format dat dostępu
- ✅ Wsparcie dla DOI i URL
- ✅ Automatyczne formatowanie

</details>

<details>
<summary><strong>🎨 Typografia</strong></summary>

- ✅ Pakiet **microtype** dla lepszej jakości składu
- ✅ Eliminacja problemów z `overfull hbox`
- ✅ Profesjonalne formatowanie tabel
- ✅ Hiperłącza PDF

</details>

## 📝 Pisanie treści

### 📑 Struktura rozdziałów

```latex
\chapter{Nazwa rozdziału}
\section{Nazwa sekcji}
\subsection{Nazwa podsekcji}
```

Możliwość dodania rozdziałów bez numeracji, ale dostępnych w spisie treści:

```latex
\chapter*{Nazwa rozdziału}
\addcontentsline{toc}{chapter}{Nazwa rozdziału}
\section*{Nazwa sekcji}
\addcontentsline{toc}{section}{Nazwa sekcji}
\subsection*{Nazwa podsekcji}
\addcontentsline{toc}{subsection}{Nazwa podsekcji}
```

oraz bez widoczności w spisie:

```latex
\chapter*{Rozdział}
\section*{Nazwa sekcji}
\subsection*{Nazwa podsekcji}
```

### 📚 Cytowania

```latex
% W tekście
Według badań \cite{kowalski2024}...

% Bibliografia na końcu
\printbibliography[title=Bibliografia]
```

### 🖼️ Obrazy

```latex
\begin{figure}[ht]
    \centering
    \includegraphics[width=0.8\textwidth]{img/wykres.png}
    \caption{Opis wykresu\\Źródło: źródło}
    \label{fig:wykres}
\end{figure}
```

### 📊 Tabele

```latex
\begin{table}[ht]
    \centering
    \caption{Opis tabeli}
    \begin{tabular}{lcc}
        \toprule
        Kolumna 1 & Kolumna 2 & Kolumna 3 \\
        \midrule
        Dane 1 & Dane 2 & Dane 3 \\
        \bottomrule
    \end{tabular}

    Źródło: źródło
    \label{tab:tabela}
\end{table}
```

## 🎨 Dostosowywanie wyglądu

### 📄 Styl numeracji stron

Szablon oferuje 4 style numeracji stron. Aby zmienić styl, odkomentuj wybraną linię w pliku `Szablon.tex`:

```latex
% Styl 1: Numeracja na dole, zewnętrzna-wewnętrzna (książkowy) - DOMYŚLNY
\renewcommand{\setupPageStyle}{\setupPageStyleBottomOuter}

% Styl 2: Numeracja na dole, wyśrodkowana
\renewcommand{\setupPageStyle}{\setupPageStyleBottomCenter}

% Styl 3: Numeracja na górze, zewnętrzna-wewnętrzna
\renewcommand{\setupPageStyle}{\setupPageStyleTopOuter}

% Styl 4: Numeracja na górze, wyśrodkowana
\renewcommand{\setupPageStyle}{\setupPageStyleTopCenter}
```

**Opis stylów:**

- **Zewnętrzna-wewnętrzna** - numery na zewnętrznych krawędziach stron (jak w książkach)
- **Wyśrodkowana** - numery zawsze na środku strony
- **Dół/Góra** - pozycja numerów na stronie

## 🚨 Rozwiązywanie problemów

### ❌ Błędy kompilacji

```bash
# Wyczyść pliki tymczasowe
rm *.aux *.bbl *.bcf *.blg *.fdb_latexmk *.fls *.log *.out *.run.xml *.synctex.gz *.toc

# Kompiluj ponownie
lualatex Szablon.tex
biber Szablon
lualatex Szablon.tex
```

### 🔤 Problemy z polskimi znakami

- Używaj kodowania **UTF-8**
- Upewnij się, że masz zainstalowany pakiet `babel[polish]`
- Sprawdź ustawienia edytora tekstu

### 📚 Problemy z bibliografią

- Sprawdź składnię pliku `.bib`
- Upewnij się, że używasz `biber` (nie `bibtex`)
- Cytuj tylko te źródła, które są w pliku `.bib`

## 🖥️ Wymagania systemowe

### 📋 Minimalne wymagania LaTeX

- **TeX Live 2020** lub nowszy
- **LuaLaTeX** (zalecany, przetestowany)
- **Biber** do bibliografii

### 📦 Zalecane pakiety

```
babel, fontenc, csquotes, amsmath, amssymb, mathptmx,
newtxtext, newtxmath, geometry, setspace, fancyhdr,
etoolbox, graphicx, caption, booktabs, cellspace,
tocloft, hyperref, lastpage, biblatex, microtype
```

## 📄 Licencja

Ten szablon jest udostępniony na licencji **MIT**. Możesz go swobodnie używać, modyfikować i dystrybuować.

## 👨‍💻 Autor

**Sebastian Kolanowski**  
📅 Wersja: 2.2 (styczeń 2026)

## 🆘 Wsparcie

W przypadku problemów:

1. 📖 Sprawdź sekcję "[Rozwiązywanie problemów](#-rozwiązywanie-problemów)"
2. ⚡ Upewnij się, że masz aktualną wersję LaTeX
3. 🔍 Sprawdź logi kompilacji w poszukiwaniu błędów

---

<div align="center">

**🎓 Powodzenia z pisaniem pracy dyplomowej!**

[![GitHub](https://img.shields.io/badge/GitHub-000000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/KazmirBO/latex-thesis-template)

</div>
