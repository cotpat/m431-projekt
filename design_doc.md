# Konzept für ein Incremental-Spiel

## Grundidee
Konzept des Spiels ist eine KI-Singularität, die sich nach und nach durch die Systeme der Welt hackt, um sie sich einzuverleiben. Dadurch gewinnt die KI an Ressourcen. Diese Ressourcen werden aufgewendet, um das Tempo der Einverleibung zu steigern. Es gibt dabei diverse Zwischenetappen (im Fachjargon: *prestige layers*). Diese *prestige layer* bieten besondere Ressourcen, um die Einverleibung noch stärker zu beschleunigen. Diese werden aber erst nach einem Neustart zugänglich.

Die Einverleibung weiterer Systeme wird immer schwieriger. Das motiviert den Spieler dazu, das Spiel neu zu starten, damit er auf die Ressourcen der *prestige layer* zugreifen, die KI damit verbessern kann und somit weiter fortschreiten kann als in der letzten Runden.

## Core Gameplay


### Ressourcen, Erzeugung
Ressource | Quelle | Rate
--- | --- | ---
Tier 1 (Sentience) | passive Generierung durch gehackte Systeme | $\frac{1s^{-1}}{System}$
Tier 2 (Influence) | Generierung durch gehacktes Class C-Netz | $\frac{1}{Class\ C}$
Tier 3 (Malevolence) | Generierung durch gehacktes Class B-Netz | $\frac{1}{Class\ B}$
Tier 4 (Violence) | Generierung durch gehacktes Class A-Netz | $\frac{1}{Class\ A}$

### Systeme und Hacken
