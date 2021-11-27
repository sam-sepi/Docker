### elencare le reti    
docker network ls

### informazioni dettagliate sulla rete
docker network inspect *rete*

### mapping porte
docker run -p *porta host*:*porta container* *immagine*

### creare una rete
docker network create *nomerete*

### associare un contenitore alla rete
docker run --network *nomerete* *immagine*

