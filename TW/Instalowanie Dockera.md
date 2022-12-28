# Instalowanie Dockera w systemie Ubuntu Server

Przydatne linki:

[Link do instalacji Dockera na Ubuntu](https://docs.docker.com/engine/install/ubuntu/#install-docker-engine)

[Pobieranie obrazów repozytoriów](https://hub.docker.com)

[Dokumentacja Dockera](https://docs.docker.com)

Sposób I: Wykorzystanie gotowego skryptu autorstwa [Talandar99](https://github.com/Talandar99)

```bash
    git clone https://github.com/Talandar99/shellfish.git # sklonowanie repozytorium
    ./install_docker_ubuntu.sh # uruchomienie skryptu
    sudo reboot # restart serwera
```

Sposób II: Manualna instalacja (na podstawie dokumentacji)

```bash

# Przygotowanie pakietów
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
# Dodanie oficjalnego klucza GPG Dockera
    sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
# Ustawienie repozytorium
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
# Aktualizacja listy pakietów
sudo apt-get update
# Instalacja Docker Engine, containterd i Docker Compose
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
# Sprawdzenie poprawności instalacji Dockera
sudo docker run hello-world
```
