# Palio 2026 — Calcolo Punteggio

Web app in un **singolo file HTML** per il calcolo dei punteggi del **Palio 2026** (5 contrade: Andromeda, Bosco, Giardini, Lago, Sagittario). Funziona offline, senza installazione né backend.

## Uso
Apri `index.html` in un browser (anche con doppio click).

## Funzioni
- **Doppia classifica in tempo reale**: *Palio* (punti per posizione) e *Drappo* (punti × coefficiente della contrada).
- Inserimento per **posizione 1ª–5ª**, gare **divise per sport**.
- **Grafici a linee** cumulativi (Palio e Drappo) con colori delle contrade a gradiente, nomi a fine linea e cursore con i punti dopo ogni gara.
- **Esplora le contrade**: una pagina per contrada con bacheca di Palii e Drappi, capitani edizione per edizione e risultati dell'edizione in corso (vedi sotto).
- **Modalità presentazione** a schermo intero per la proiezione (podio + classifica).
- **Salvataggio automatico** (localStorage) ed **Esporta/Importa** JSON e CSV.

> I dati sono salvati localmente nel browser di chi apre la pagina (nessuna sincronizzazione tra dispositivi). Usa *Esporta/Importa JSON* per backup o trasferimento.

## Esplora le contrade
La scheda *Contrade* mostra le cinque contrade; toccandone una si apre la sua pagina. Tutto ciò che compare è ricavato dall'albo già presente nel file (`ALBO`): anni di Palio e Drappo, serie di vittorie, doppiette, capitani. L'edizione in corso (posizione, punti, gare vinte) si vede solo quando le classifiche sono pubblicate.

I testi scritti a mano (un motto e la storia della contrada) si aggiungono nella costante `STORIE` di `index.html`: quando sono compilati compaiono da soli nella pagina della contrada, altrimenti non si vede nulla.

```js
giardini: {motto:'Una frase breve', storia:['Primo paragrafo.', 'Secondo paragrafo.']},
```

## Grafica
Stile sportivo sobrio: fondo notte, colori pieni delle contrade e linee oblique come le cinque aste del logo Gruppo Palio.
- **Oro = Palio, argento = Drappo** (classifiche, titoli, albo d'oro).
- Tipografia misurata: caratteri dritti (pesi 600–700), titoli fino a circa 2,2 rem, maiuscolo solo per le micro-etichette.
- La striscia «in testa» prende i colori della contrada che guida; il colore del testo (bianco o scuro) si sceglie da solo in base al contrasto.
- Il **banner dei vincitori** compare solo nella home (la prima scheda), non nelle altre pagine.
- Su telefono la navigazione passa in una **barra a schede in basso**; le gare si inseriscono con una scheda per gara.
- Font di sistema (nessun webfont): condensed su iPhone/Mac (Avenir Next Condensed), con ripiego su Bahnschrift, Roboto Condensed e Arial Narrow.
- Colori e componenti sono definiti nel blocco `<style>` all'inizio di `index.html` (variabili `--gold`, `--silver`, `--ink-*`…); le icone sono SVG a tratto nella costante `ICONS`.

## Tecnologia
Vanilla HTML + CSS + JavaScript in un unico file. Unica dipendenza esterna: Firebase (sincronizzazione condivisa); senza rete l'app resta utilizzabile in locale.
