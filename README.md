# Palio 2026 — Calcolo Punteggio

Web app in un **singolo file HTML** per il calcolo dei punteggi del **Palio 2026** (5 contrade: Andromeda, Bosco, Giardini, Lago, Sagittario). Funziona offline, senza installazione né backend.

## Uso
Apri `index.html` in un browser (anche con doppio click).

## Funzioni
- **Doppia classifica in tempo reale**: *Palio* (punti per posizione) e *Drappo* (punti × coefficiente della contrada).
- Inserimento per **posizione 1ª–5ª**, gare **divise per sport**.
- **Grafici a linee** cumulativi (Palio e Drappo) con colori delle contrade a gradiente, nomi a fine linea e cursore con i punti dopo ogni gara.
- **Modalità presentazione** a schermo intero per la proiezione (podio + classifica).
- **Salvataggio automatico** (localStorage) ed **Esporta/Importa** JSON e CSV.

> I dati sono salvati localmente nel browser di chi apre la pagina (nessuna sincronizzazione tra dispositivi). Usa *Esporta/Importa JSON* per backup o trasferimento.

## Grafica
Stile «broadcast sportivo»: fondo notte, numeri grandi, colori pieni delle contrade e linee oblique come le cinque aste del logo Gruppo Palio.
- **Oro = Palio, argento = Drappo** (classifiche, titoli, albo d'oro).
- La striscia «in testa» prende i colori della contrada che guida; il colore del testo (bianco o scuro) si sceglie da solo in base al contrasto.
- Su telefono la navigazione passa in una **barra a schede in basso**; le gare si inseriscono con una scheda per gara.
- Font di sistema (nessun webfont): condensed corsivo su iPhone/Mac (Avenir Next Condensed), con ripiego su Bahnschrift, Roboto Condensed e Arial Narrow.
- Colori e componenti sono definiti nel blocco `<style>` all'inizio di `index.html` (variabili `--gold`, `--silver`, `--ink-*`…); le icone sono SVG a tratto nella costante `ICONS`.

## Tecnologia
Vanilla HTML + CSS + JavaScript in un unico file. Unica dipendenza esterna: Firebase (sincronizzazione condivisa); senza rete l'app resta utilizzabile in locale.
