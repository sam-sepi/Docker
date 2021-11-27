# Pulling di un'immagine dal docker hub
docker pull *immagine:versione*

# RUN dell'immagine
docker run *immagine*

# Pull e run dell'immagine non presente localmente
docker run *immagine*

# Pull di una versione mediante hash DIGEST
docker pull *immagine@digest*

# Ispezionare immagine per osservarne le caratteristiche
docker inspect *immagine*

# Elencare le immagini 
docker image ls
docker images

# Elencare ID immagini
docker images -q

# Rimuovere un'immagine
docker image rm *immagine ID*

