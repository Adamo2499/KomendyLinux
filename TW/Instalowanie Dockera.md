# Instalowanie Dockera w systemie Ubuntu Server

Przydatne linki:

[Link do instalacji Dockera na Ubuntu](https://docs.docker.com/engine/install/ubuntu/)

[Pobieranie obrazów repozytoriów](https://hub.docker.com)

[Dokumentacja Dockera](https://docs.docker.com)

```bash
    sudo apt update && sudo apt upgrade # aktualizacja pakietów oraz sytemów
    sudo apt install apt-transport-https ca-certificates curl gnupg system-properties-common # zainstalowanie pakietów wymaganych do poprawnego działania Dockera
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt -key add #import klucza GPG repozytorium Dockera
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" # dodanie repozytorium APT Docker do listy (jeżeli jeszcze nie ma)
    sudo apt update # aktualizacja listy repozytoriów
    sudo apt install docker-ce docker-ce-cli containerd.io # instalacja Dockera (głównego pakietu, terminala i demona)
    sudo systemctl status docker # weryfikacja statusu Dockera (start uruchamia a stop zatrzymuje)
    sudo usermod -aG docker $USER && sudo reboot # uruchomienie Dockera przez użytkownika niebędącego rootem (dopisanie użytkownika do grupy docker i restart serwera)
```