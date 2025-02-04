# Guida alla build per Linux

Questa è una guida alla compilazione di ShashChess.

Non necessita di una GUI, anche se la supporta, e funziona nel terminale.

### Passp 1:

Scarica o clona la repository, usando il comando seguente nel terminale (assicurati di usarlo in una cartella vuota):

```bash
git clone https://github.com/amchess/ShashChess.git
```

### Passo 2:

Dalla cartelle in cui hai clonato la repository, naviga fino alla cartella 'src', dove troverai il Makefile:

```bash
cd ShashChess/src/
```

### Passo 3:

Usa il comando 'make', specificando il 'target' che preferisci.

Se non sai cosa sia un target, usa il seguente comando per ottenere una spiegazione:

```bash
make help
```

Un target che funziona bene per casi generali è indicato nel seguente comando:

```bash
make profile-build
```

Questo comando lavorerà per un po', creando un eseguibile intitolato "shashchess".

### Passo 4:

Ora che hai l'eseguibile, puoi farlo partire con questo comando:

```bash
./shashchess
```

Se tutto è andato bene, dovresti vedere il nome del motore e i suoi autori.
