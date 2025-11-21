# 📌 README.md

# **Daemons Exploiter --- Portfolio**

Questo progetto è un portfolio interattivo con stile minimal, animazioni
ispirate ad Apple, una modalità Dark e una modalità "Hacker" nascosta
attivabile tramite una parola segreta.\
Il sito combina estetica pulita, animazioni fluide ed elementi
cyberpunk.

------------------------------------------------------------------------

## 📁 **Struttura del progetto**

Il progetto è composto da:

-   **HTML principale** → layout, sezioni, canvas, overlay, terminale
-   **CSS interno** → stile, animazioni, temi
-   **JavaScript interno** → effetti interattivi, modalità hacker,
    typing effect, effetto Matrix, fade-in Apple

Non utilizza file esterni a parte un'importazione Google Fonts.

------------------------------------------------------------------------

# ⚙️ **Funzionalità nel dettaglio**

Di seguito una spiegazione completa di tutte le funzioni e degli effetti
presenti nel file.

------------------------------------------------------------------------

# 🎨 **Sezione Grafica e Stili**

## 1️⃣ Hero con effetto di digitazione

Elemento: `<p id="typing"></p>`

Il testo viene scritto lettera per lettera tramite:

``` js
const tagline = "Cybersecurity • Automation • Web Engineering";
let i = 0;
setInterval(() => {
  document.getElementById("typing").textContent = tagline.slice(0, i);
  i = i < tagline.length ? i + 1 : 0;
}, 120);
```

✔ Simula un terminale o una macchina da scrivere\
✔ Riparte automaticamente quando finisce

------------------------------------------------------------------------

## 2️⃣ Sezioni "Apple Fade" con animazione on-scroll

Elementi: `.apple-fade`

Utilizza **IntersectionObserver** per mostrare le sezioni quando entrano
nel viewport.

``` js
const observer = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) entry.target.classList.add("visible");
  });
}, { threshold: 0.15 });
```

✔ Effetto elegante e fluido\
✔ Stile Apple-style moderno\
✔ Ottimizzato con IntersectionObserver

------------------------------------------------------------------------

## 3️⃣ Modalità Dark (tasto **D**)

Premendo **D** si attiva/disattiva la dark mode:

``` js
document.addEventListener("keydown", (e) => {
  if (e.key.toLowerCase() === "d") document.body.classList.toggle("dark");
});
```

✔ Semplice e immediata\
✔ Cambia sfondo, testo, card e nav\
✔ Non interferisce con la modalità hacker

------------------------------------------------------------------------

# 🔐 **Modalità Hacker (Easter Egg)**

La parte più avanzata del progetto.\
Si attiva digitando la parola:

    hacker

### 🔸 Rilevamento parola segreta

``` js
let buffer = "";
const secret = "hacker";

document.addEventListener("keydown", (e) => {
    buffer += e.key.toLowerCase();
    if (buffer.endsWith(secret)) {
        activateHackerMode();
        buffer = "";
    }
    if (buffer.length > 10) buffer = "";
});
```

✔ Non richiede input box\
✔ Invisibile all'utente\
✔ Utilizza un "buffer circolare"

------------------------------------------------------------------------

# 🟩 Effetti della modalità Hacker

Quando la modalità si attiva, succedono diverse trasformazioni:

------------------------------------------------------------------------

## 1️⃣ Tema grafico hacker / cyberpunk

Classe: `.hacker`

Modifica:

-   colori (verde neon + nero)
-   ombre, bordi, glow
-   sfondo animato con flickering CRT
-   terminale visibile
-   abilita il canvas Matrix

------------------------------------------------------------------------

## 2️⃣ Terminale animato

Elemento: `<div class="terminal">`

Le linee compaiono in sequenza:

``` js
const lines = [ ... ];
setInterval(()=>{ ... },1500);
```

✔ Riproduce un boot-sequence da film\
✔ Solo nella modalità hacker\
✔ Avanza automaticamente

------------------------------------------------------------------------

## 3️⃣ Effetto Matrix sullo sfondo

Elemento: `<canvas id="matrixCanvas">`

Funzione principale:

-   genera caratteri 0/1 in caduta
-   con effetto pioggia verticale
-   si aggiorna ogni 50ms

``` js
function drawMatrix(){ ... }
setInterval(drawMatrix, 50);
```

✔ Attivo solo in modalità hacker\
✔ Usa canvas 2D\
✔ Dynamically resizable

------------------------------------------------------------------------

## 4️⃣ Effetto di "scansione" con allarme breach

Elementi:

-   `<div id="scanOverlay">`
-   `<div id="breachMsg">SYSTEM BREACH DETECTED</div>`

Funzione:

``` js
function terminalScan(){
    ...
}
```

Crea un effetto:

-   overlay verde che scende
-   testo lampeggiante "BREACH"
-   transizione automatica

✔ Cybersecurity vibes\
✔ Introduce la modalità hacker in modo cinematografico

------------------------------------------------------------------------

# 🧠 **Funzioni JavaScript principali**

  Funzione                 Scopo
  ------------------------ --------------------------------------------
  `activateHackerMode()`   Attiva la modalità hacker e l'effetto scan
  `terminalScan()`         Mostra overlay + messaggio breach
  `drawMatrix()`           Effetto a pioggia di 0/1 stile Matrix
  Typing effect            Scrive il testo nella hero automaticamente
  IntersectionObserver     Fa comparire sezioni in stile Apple
  Key listener (D)         Attiva/disattiva dark mode
  Key listener (secret)    Riconosce la parola "hacker"

------------------------------------------------------------------------

# ✔️ **Punti forti del progetto**

-   Design professionale, pulito e moderno\
-   Animazioni fluide senza librerie esterne\
-   Easter egg hacker ben realizzato e coinvolgente\
-   Modalità Dark immediata\
-   Effetti grafici avanzati (Matrix, scanning, terminal)\
-   Totalmente responsive\
-   Solo HTML/CSS/JS---nessuna dipendenza aggiuntiva
