# Pulling di un'immagine dal docker hub
docker pull *immagine:versione*

# esecuzione dell'immagine
docker run *immagine*

# esecuzione dell'immagine in background
docker run -d *immagine*

# Pull ed esecuzione dell'immagine non presente localmente
docker run *immagine*

# Pull di una versione mediante hash DIGEST
docker pull *immagine@digest*

# Ispezionare immagine per osservarne le caratteristiche
docker inspect *immagine*
docker inspect *immagine:versione*

# Elencare le immagini 
docker image ls
docker images

# Elencare ID immagini
docker images -q

# Rimuovere un'immagine
docker image rm *immagine ID*

# Elencare le operazioni svolte sull'immagine
docker history *immagine*

# eseguire temporaneamente un container
docker run *immagine sleep secondi*

# elencare i processi in corso
docker ps

# elencare i processi in corso o interrotti
docker ps -a

# assegnare un nome al contenitore in esecuzione
docker run --name=*nome* *immagine*

# interazione con un terminale del contenitore
docker run -it *immagine* *terminale* (es.: docker run -it ubuntu /bin/bash )

# uscire dal contenitore mantenendone l'esecuzione 
CTRL+P e CTRL+Q

# rientrare nel container
docker attach *ID contenitore*

# concludere l'esecuzione
docker stop *ID contenitore*

# elencare i processi attivi nel container
ps -elf
docker top *ID contenitore*

# statistiche del contenitore
docker stats *ID contenitore*


