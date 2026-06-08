# Palio 2026 — Calcolo Punteggio

Web app in un **singolo file HTML** per il calcolo dei punteggi del **Palio 2026** (5 contrade: Andromeda, Bosco, Giardini, Lago, Sagittario). Funziona offline, senza installazione né backend.

## Uso
Apri `index.html` in un browser (anche con doppio click).

## Funzioni
- **Doppia classifica in tempo reale**: *Palio* (punti per posizione) e *Drappo* (punti × coefficiente della contrada).
- Inserimento per **posizione 1ª–5ª**, gare **divise per sport**.
- **Grafici a linee** cumulativi (Palio e Drappo) con colori delle contrade a gradiente.
- **Modalità presentazione** a schermo intero per la proiezione.
- **Salvataggio automatico** (localStorage) ed **Esporta/Importa** JSON e CSV.

> I dati sono salvati localmente nel browser di chi apre la pagina (nessuna sincronizzazione tra dispositivi). Usa *Esporta/Importa JSON* per backup o trasferimento.

## Tecnologia
Vanilla HTML + CSS + JavaScript in un unico file, nessuna dipendenza esterna.
