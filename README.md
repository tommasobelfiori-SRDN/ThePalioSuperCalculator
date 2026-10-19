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
Stile **«Minimal chiaro»** (proposta D scelta il 20 ottobre 2026), con tema chiaro e tema scuro: pulito e calmo, i dati sono i protagonisti e il colore delle contrade compare solo in pallini, barre ed etichette.
- **Oro = Palio, argento = Drappo** (selettore, etichette, titoli, albo d'oro).
- **Tema chiaro/scuro**: all'avvio segue il dispositivo, il pulsante luna/sole in alto cambia tema e la scelta resta salvata nel browser (`palioTheme`). I colori sono variabili CSS (`--bg`, `--card`, `--text`, `--gold`…) definite in `:root` e ridefinite in `:root[data-theme="dark"]`; i grafici si ridisegnano da soli al cambio.
- Tipografia sobria: Inter se presente, altrimenti il carattere di sistema; titoli a peso 500, numeri grandi in peso leggero (300).
- Classifica: elenco a sinistra con barra nel colore della contrada; a destra la scheda «In testa» (striscia coi colori della contrada in testa) e l'avanzamento con una tacca per gara. Il **banner dei vincitori** compare solo nella home.
- Su telefono la navigazione passa in una **barra a schede in basso**; le gare si inseriscono con una scheda per gara.
- Icone SVG a tratto nella costante `ICONS`; nessun webfont.

## Stato e dove si riprende (20 ottobre 2026)
- **Online** su www.paliomalaspina.com: ancora la grafica sobria scura (ultimo commit del sito pubblicato `39a6cc0`).
- **In lavorazione, non ancora pubblicato**: nuova grafica «Minimal chiaro» con tema chiaro e scuro (vedi «Grafica»), applicata a `index.html` partendo dalla proposta D del [file Figma](https://www.figma.com/design/9pXljb2kpZv3aHXL2bK0Mq). Le altre proposte (B, C, E) e la A (medievale) sono scartate.
- **Contenuto**: approvato. Mancano solo i testi delle contrade (motto e storia) da mettere in `STORIE`; non vanno inventati.
- **Da fare**: provare su iPhone/Safari reale, poi pubblicare dopo l'ok. La schermata Drappo e l'area admin non sono disegnate in Figma: seguono lo stesso stile.

## Pubblicazione
Il push su `main` pubblica subito il sito (GitHub Actions → Azure Static Web Apps). I dati live stanno in Firebase Realtime Database: il pubblico vede le classifiche solo quando l'admin preme «Pubblica classifiche ora» (con PIN di conferma). Per questo le prove vanno fatte come sotto, senza toccare il database vero.

## Provare senza toccare il database vero
Esiste una cartella locale **non versionata**, `.claude/prove/` (solo sul computer di chi sviluppa). `python3 .claude/prove/mk_test.py` crea una copia di `index.html` con un Firebase finto (`stub.js`) in `.claude/prove/t/`; servita su una porta locale si apre con `index.html?mode=revealed|wait|announce|admin|loading|local` (e `&n=<gare disputate>`). In modalità `admin` qualsiasi password entra e nessuna scrittura arriva al database. La pagina vera col database vero va aperta solo da visitatore (sola lettura).

## Tecnologia
Vanilla HTML + CSS + JavaScript in un unico file. Unica dipendenza esterna: Firebase (sincronizzazione condivisa); senza rete l'app resta utilizzabile in locale.
