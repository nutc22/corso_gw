# corso_gw

## setup

```shell
git clone https://github.com/matib12/corso_gw.git
chmod a+rw corso_gw
cd corso_gw

docker pull nutc22/gw-notebook:latest
docker run -it --rm --user $(id -u):$(id -g) --group-add users -v ${PWD}:/home/jovyan/work/ -p <PORT>:8888 -e GEN_CERT=yes nutc22/gw-notebook:latest
```
Ricordarsi di sostituire la porta da esporre al posto di `<PORT>`

Visitare il sito `https://<IP-ADDR>:<PORT`
e fidarsi del certificato auto firmato.

Inserire il token di sicurezza indicato nella shell per effettuare l'accesso

per terminare il processo `^C`



## modificare o clonare l'immagine

se si desidera ri-costruire l'immagine docker:

```shell
docker build . -t gw-notebook:<tag>
```

a questo punto si può creare il container:
```shell
docker run -it --user $(id -u):$(id -g) --group-add users -v ${PWD}:/home/jovyan/work/ -p <PORT>:8888 -e GEN_CERT=yes gw-notebook:<tag>
```
