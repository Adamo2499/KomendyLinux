# Pobieranie i uruchamianie obrazu Dockera

Sposób I: Wykorzystanie gotowego skryptu autorstwa [Talandar99](https://github.com/Talandar99)

```bash
    git clone https://github.com/Talandar99/shellfish.git # sklonowanie repozytorium
    ./run_docker_portainer.sh # uruchomienie skryptu
```

Sposób II: Manualna instalacja (na podstawie dokumentacji)

```bash
# Portainer to tylko przykładowy obraz
docker pull portainer # pobieranie obrazu
sudo docker volume create portainer data # utworzenie woluminu Portainer (żeby nie utracić danych)
sudo docker rum -d -p 8000:8000 -p 9000:9000 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -w portainer_data:/data_portainer/portainer-ce # uruchomienie kontenera Portainer
docker images # wyświetlenie informacji o dostępnepnych obrazach Dockera
```
