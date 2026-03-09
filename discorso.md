# Post-Quantum Cryptography — Discorso di laurea
**Olivieri Michele · UniBO 2024-25 · ~4'45"**

---

## ① Apertura

Buongiorno a tutti, mi presento: sono Michele Olivieri e oggi vi parlerò
della mia tesi sulla crittografia post-quantistica.

Come sappiamo, la sicurezza digitale moderna è fondata sulla crittografia
a chiave pubblica — la tecnologia che protegge le comunicazioni cifrate,
i pagamenti online, le firme digitali. La sua robustezza è garantita dalla
difficoltà di risolvere certi problemi matematici in tempi ragionevoli.

Ma cosa succederebbe se quella difficoltà venisse meno? È esattamente
questa la domanda che ha dato origine alla crittografia post-quantistica:
una branca della crittografia che sviluppa algoritmi sicuri non solo contro
i computer classici, ma anche contro i computer quantistici — che
minacciano di rendere quei problemi risolvibili in tempo polinomiale.

---

## ② Crittografia classica e perché è vulnerabile

Per capire in che modo, bisogna partire dai fondamenti.
Gli algoritmi oggi universalmente in uso — RSA e la crittografia su curve
ellittiche — si basano su due problemi: la fattorizzazione di grandi interi
e il logaritmo discreto. RSA sfrutta il fatto che moltiplicare due numeri
primi enormi è immediato, mentre trovare quei fattori a partire dal
prodotto è computazionalmente intrattabile. Su questa asimmetria si regge
gran parte dell'infrastruttura di sicurezza globale.

Quello che accomuna questi due problemi è una caratteristica matematica
sottostante: hanno una struttura algebrica periodica e regolare. Ed è
esattamente quella struttura che li rende vulnerabili al calcolo quantistico.

---

## ③ L'algoritmo di Shor

Già nel 1994 Shor dimostrò che un computer quantistico sufficientemente
potente potrebbe fattorizzare in tempo polinomiale, demolendo la
sicurezza di RSA. L'intuizione chiave è trasformare il problema: invece
di cercare i fattori di N direttamente, Shor riduce la fattorizzazione al
trovare il periodo della funzione f(x) = aˣ mod N.

Questa riduzione è matematica classica — non c'è nulla di quantistico.
Il vantaggio entra nel calcolo del periodo: su un computer classico,
trovarlo usando la DFT richiede ancora tempo esponenziale; con la
Quantum Fourier Transform diventa polinomiale. Grazie a sovrapposizione
e interferenza quantistica, le frequenze compatibili con la periodicità
vengono amplificate, le altre si cancellano, e il periodo emerge con alta
probabilità — rendendo l'intera fattorizzazione efficiente.

---

## ④ La risposta: crittografia post-quantistica

La risposta della comunità crittografica è costruire algoritmi fondati su
problemi matematici che non hanno quella struttura periodica.
La famiglia più promettente sono i reticoli algebrici: strutture geometriche 
n-dimensionali generate da combinazioni lineari a coefficienti interi di 
vettori base. Il problema fondamentale è Learning With Errors, ovvero 
recuperare un vettore segreto s da equazioni lineari deliberatamente 
perturbate da rumore casuale costruito come: b = A·s + e, è dimostrato che 
si riduce a problemi NP-hard.
È infatti proprio quel rumore a spezzare qualsiasi struttura periodica,
rendendo inefficace l'approccio di Shor.

È importante essere precisi: non esiste una dimostrazione formale che
questi problemi siano impossibili da risolvere per un computer quantistico.
Tuttavia la comunità scientifica li ritiene molto più solidi, perché si
riducono a problemi classificati NP-hard e non presentano la regolarità
algebrica che ha reso RSA e ECC vulnerabili. È per questo che esistono più 
famiglie di algoritmi: reticoli, codici correttori di errori, funzioni hash.

Il NIST ha coordinato un processo di standardizzazione globale avviato
nel 2016 e concluso nel 2024 con i primi standard ufficiali: ML-KEM per
lo scambio di chiavi basato su Learning With Errors; ML-DSA per le
firme digitali, anch'esso sui reticoli; SLH-DSA fondato esclusivamente
sull'unidirezionalità delle funzioni hash — una scelta conservativa per
diversificare il rischio nel caso in cui venissero scoperte vulnerabilità
nei reticoli.

---

## ⑤ Implementazioni industriali

Questa transizione non è più solo teorica. Signal, Apple, Google e
Cloudflare hanno già distribuito protocolli ibridi — classico più
post-quantistico in parallelo — su centinaia di milioni di dispositivi.
La motivazione comune è proteggersi fin da subito dal modello di
minaccia "harvest now, decrypt later": un attaccante che raccoglie
traffico cifrato oggi per decifrarlo in futuro con un computer quantistico.
L'approccio ibrido garantisce che la sicurezza complessiva non sia mai
inferiore a quella classica, anche nell'eventualità che i nuovi algoritmi
presentassero vulnerabilità impreviste.

---

## ⑥ Conclusione

La crittografia post-quantistica non è una risposta a una crisi già in
atto: è una risposta preventiva a una crisi prevedibile. La migrazione
dell'intera infrastruttura crittografica globale — dai certificati TLS
alle firme firmware, dai protocolli di messaggistica alle smartcard
bancarie — è un'operazione di scala e complessità senza precedenti,
che richiederà anni di lavoro coordinato tra industria, governi e
comunità accademica.

L'ottica con cui guardare questa tesi non è tanto tecnica quanto
metodologica: la sicurezza di un sistema crittografico non è mai una
garanzia permanente, ma il risultato di un processo continuo di
valutazione, aggiornamento e adattamento. Il passaggio dalla crittografia
classica a quella post-quantistica è, in questo senso, non un'eccezione
alla storia della crittografia — ma la sua continuazione naturale.

Grazie.