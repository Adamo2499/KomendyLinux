# Instalowanie Dockera w systemie Ubuntu Server

[Link do instalacji Dockera na Ubuntu](https://docs.docker.com/engine/install/ubuntu/)

```bash
    sudo apt update && sudo apt upgrade # aktualizacja pakietów oraz sytemów
    sudo apt install apt-transport-https ca-certificates curl gnupg syste-properties-common # zainstalowanie pakietów wymaganych do poprawnego działania Dockera
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt -key add #import klucza GPG repozytorium Dockera
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -)
```