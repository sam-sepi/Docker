# FROM 
permette di specificare un’immagine di base (base image) da cui partire per derivare la nostra immagine personalizzata

FROM <nome_immagine>
FROM <nome_immagine>:<tag>
FROM <nome_immagine>@<hash

# ENV 
imposta variabili di ambiente valide per tutto il contesto di esecuzione di un Dockerfile

ENV <chiave>=<valore>

Per recuperare il valore della variabile d’ambiente all’interno del Dockerfile, basta riferirci ad essa anteponendo il carattere $ alla chiave stessa (per esempio: $FTP_HOME

# RUN 
possiamo istruire l’engine Docker affinché esegua dei comandi all’interno dell’immagine che andremo a generare. Per intenderci, se abbiamo indicato (tramite l’istruzione FROM) di voler utilizzare Debian come immagine base, possiamo utilizzare l’istruzione RUN per installare un pacchetto tramite il classico comando apt-get

L’istruzione RUN è disponibile in due modalità: shell ed exec. La prima modalità esegue il comando sfruttando le facility della shell del sistema operativo (espansione di variabili, I/O redirection e così via); l’altra modalità utilizza le sole primitive del sistema operativo.

RUN <comando> <parametro1> ... <parametroN>

RUN ["<comando>", "<parametro1>", ... , "<parametroN>"]

Il comando RUN fa sì che si generi un nuovo layer che porti con sé le modifiche derivate dal comando stesso. Ne deriva che ogni volta che l’engine incontra questa istruzione lungo il suo percorso, esso creerà un nuovo layer, per cui è caldamente consigliato far collassare più comandi correlati all’interno di una singola istruzione RUN.

# COPY
permette di spostare file e directory dal build context (il path sul nostro computer locale dove si trova il Dockerfile) all’interno del filesystem dell’immagine creata. 

COPY <src> <dest>

# Entrypoint
permette di eseguire un comando all’interno del container non appena questo si è avviato. Si differenzia dall’istruzione RUN in quanto, gli effetti dell’istruzione si avranno sul container stesso piuttosto che sull’immagine che l’ha generato. 

Utilizzando questa istruzione, l’ultima parte del comando **docker run** non sarà più un comando ma un parametro da passare al comando espresso nell’ENTRYPOINT. Proviamo a fare un po’ di chiarezza: abbiamo visto nella lezione precedente che se nel terminale scriviamo 

docker run -it ubuntu /bin/bash

una volta che il container otteniamo una shell verso l’interno del container. A questo punto però supponiamo di avere questo Dockerfile:

FROM ubuntu:precise
ENTRYPOINT ["ls"]

Supponiamo che l’immagine derivante da questo Dockerfile si chiami htmlit (vedremo nella lezione successiva come crearla). Il comando docker run htmlit ci restituirà il risultato del comando ls lanciato all’interno del container. Per quanto detto precedentemente, se aggiungessimo qualcosa dopo il nome dell’immagine da eseguire, questi saranno considerati come dei parametri al comando ls.

# CMD
come l’istruzione ENTRYPOINT ha effetto sul container e non modifica l’immagine, né aggiunge layer a questa, come avviene con l’istruzione RUN.


CMD <comando> <parametro_1> ... <parametro_n>

CMD ["<comando>", "<parametro_1>", ..., "<parametro_n>"]

Se non esiste un’istruzione ENTRYPOINT all’interno del Dockerfile in esame, l’utilizzo dell’istruzione CMD farà in modo che all’avvio del container venga eseguito il comando indicato. Questo è esattamente lo stesso comportamento dell’istruzione ENTRYPOINT, ma in questo caso possiamo sovrascrivere questo comando specificandone uno diverso nel momento in cui eseguiamo il comando docker run da terminale.

