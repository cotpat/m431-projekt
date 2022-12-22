# Konzept für ein Incremental-Spiel

## Grundidee
Konzept des Spiels ist eine KI-Singularität, die sich nach und nach durch die Systeme der Welt hackt, um sie sich einzuverleiben. Dadurch gewinnt die KI an Ressourcen. Diese Ressourcen werden aufgewendet, um das Tempo der Einverleibung zu steigern. Es gibt dabei diverse Zwischenetappen (im Fachjargon: *prestige layers*). Diese *prestige layer* bieten besondere Ressourcen, um die Einverleibung noch stärker zu beschleunigen. Diese werden aber erst nach einem Neustart zugänglich.

Die Einverleibung weiterer Systeme wird immer schwieriger. Das motiviert den Spieler dazu, das Spiel neu zu starten, damit er auf die Ressourcen der *prestige layer* zugreifen, die KI damit verbessern kann und somit weiter fortschreiten kann als in der letzten Runden.

## Core Gameplay
### Ressourcen, Erzeugung
Ressource | Quelle | Rate
--- | --- | ---
Tier 1 (`Sentience`) | passive Generierung durch gehackte Systeme | $\frac{1s^{-1}}{System}$
Tier 2 (`Influence`) | Generierung durch gehacktes Class C-Netz | $\frac{1}{Class\ C}$
Tier 3 (`Malevolence`) | Generierung durch gehacktes Class B-Netz | $\frac{1}{Class\ B}$
Tier 4 (`Violence`) | Generierung durch gehacktes Class A-Netz | $\frac{1}{Class\ A}$

### Systeme und Hacken
Die Hauptaktion des Spiels, welche automatisch vor sich geht, ist das Hacken von Systemen bzw. von Hosts eines Netzwerks. Das Spiel startet mit einem einzigen gehackten System. Ziel ist das Hacken von allen Systeme, die im classful network-System abgebildet werden können:

Class | Anzahl Netzwerke | nutzbare Hosts pro Netzwerk | Total Nutzbare in Class
--- | --- | --- | ---
Class A | $2^7 = 128$ | $2^24 - 2 = 16'777'214$ | 2'147'483'392
Class B | $2^14 = 16'384$ | $2^16 - 2 = 65'534$ | 1'073'709'056
Class C | $2^21 = 2'097'152$ | $2^8 - 2 = 254$ | 532'676'608

Dies geschieht analog zu einem Kampf in einem RPG, aber vereinfacht. Systeme besitzen eine Ressource `health`, "Security" genannt, welche durch den Wert `attack` der KI ("Exploits") in der Rate $attack*s^{-1}$. `health` des ersten Systems ist `10`.
Ist `health` eines Systems bei 0 angekommen, geschieht folgendes:
  - Das System wird übernommen und generiert fortan die Ressource `sentience`
  - Das nächste System wird automatisch in Angriff genommen
    - Gibt es noch ungehackte Hosts im selben Class A/B/C-Netzwerk, wird dieses zum Ziel
    - War das gehackte System das letzte eines gegebenen Netzwerks und gibt es noch ungehackte Netzwerke derselben Klasse, folgt ein System in einem neuen Netzwerk derselben Klasse und es wird eine Ressourcenpunkt gemäss Ressourcentabelle vergeben
    - Stehen nach Abschluss des Systems keine Netzwerke derselben Klasse mehr zur Verfügung, folgt ein Netzwerk der nächsthöheren Klasse
  - `health` des nächsten Systems wird mit `1.1` potenziert. Die Progression von `health` folgt also der Formel $health = 10^{1+\frac{x-1}{10}}$, wobei `x` die Anzahl gehackter Systeme ist und zu Beginn des Spiels `x = 1` gilt.
