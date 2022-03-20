# Corona analyser

## Popis projektu
Cílem úlohy je vytvořit shellový skript pro analýzu záznamů osob s prokázanou nákazou koronavirem způsobujícím onemocnění COVID-19 na území České republiky. Skript bude filtrovat záznamy a poskytovat základní statistiky podle zadání uživatele.

## Detailní specifikace
Skript filtruje záznamy osob s prokázanou nákazou koronavirem způsobujícím onemocnění COVID-19. Pokud je skriptu zadán také příkaz, nad filtrovanými záznamy daný příkaz provede. Pokud skript nedostane ani filtr ani příkaz, opisuje záznamy na standardní výstup.

### Syntax spuštění
```
./corona [-h] [FILTERS] [COMMAND] [LOG [LOG2 [...]]
```
<strong>-h</strong> - vypíše nápovědu s krátkým popisem každého příkazu a přepínače<br>

<strong>FILTERS</strong> může být kombinace následujících (každý maximálně jednou):
  <ul>
    <li><code>-a DATETIME</code> - after: jsou uvažovány pouze záznamy PO tomto datu (včetně tohoto data). <code>DATETIME</code> je formátu <code>YYYY-MM-DD</code>.</li>
    <li><code>-b DATETIME</code> - before: jsou uvažovány pouze záznamy PŘED tímto datem (včetně tohoto data)</li>
    <li><code>-g GENDER</code> - jsou uvažovány pouze záznamy nakažených osob daného pohlaví. <code>GENDER</code> může být <code>M</code> (muži)
    nebo <code>Z</code> (ženy)</li>
    <li><code>-s [WIDTH]</code> - u příkazů <code>gender</code>, <code>age</code>, <code>daily</code>, <code>monthly</code>, <code>yearly</code>, <code>countries</code>, <code>districts</code> a <code>regions</code> vypisuje data ne číselně, ale graficky v podobě histogramů. Nepovinný parametr <code>WIDTH</code> nastavuje šířku histogramů, tedy délku nejdelšího řádku, na <code>WIDTH</code>. Tedy, <code>WIDTH</code> musí být kladné celé číslo. Pokud není parametr <code>WIDTH</code> uveden, řídí se šířky řádků požadavky uvedenými níže.</li>
  </ul>

<strong>COMMAND</strong> může být jeden z:
  <ul>
    <li><code>infected</code> - spočítá počet nakažených</li>
    <li><code>merge</code> - sloučí několik souborů se záznamy do jednoho, zachovávající původní pořadí (hlavička bude ve výstupu jen jednou)</li>
    <li><code>gender</code> - vypíše počet nakažených pro jednotlivá pohlav.</li>
    <li><code>age</code> - vypíše statistiku počtu nakažených osob dle věku</li>
    <li><code>daily</code> - vypíše statistiku nakažených osob pro jednotlivé dny</li>
    <li><code>monthly</code> - vypíše statistiku nakažených osob pro jednotlivé měsíce</li>
    <li><code>yearly</code> - vypíše statistiku nakažených osob pro jednotlivé roky</li>
    <li><code>countries</code> - vypíše statistiku nakažených osob pro jednotlivé země nákazy (bez ČR, tj. kódu <code>CZ</code>)</li>
    <li><code>districts</code> - vypíše statistiku nakažených osob pro jednotlivé okresy</li>
    <li><code>regions</code> - vypíše statistiku nakažených osob pro jednotlivé kraje</li>
  </ul>
