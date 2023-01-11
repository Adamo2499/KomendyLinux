# Czynności dodatkowe po zainstalowaniu Linuxa

Dodawanie pakietów z dodatkami gościa (żeby korzystać z możliwości typu wspólny schowek)

```bash
    sudo add-apt-repository multiverse # dodanie repozytorium do listy
    sudo apt update # aktualizacja listy repozytoriów
    sudo apt install virtualbox-guest-utils virtualbox-guest-x11 # instalacja pakietów obrazów gościa
    sudo reboot #restart systemu
```

[Konfiguracja adresu IP - Pasja Informatyki](https://pasja-informatyki.pl/sieci-komputerowe/linux-ubuntu-server-konfiguracja-ip/)

```bash
sudo touch /etc/cloud/cloud-init.disabled # wyłączenie komunikatu początkowego
ip a # sprawdzenie konfiguracji sieciowej maszyny (jeżeli nie zadziała polecenie ifconfig -a); należy sprawdzić który interfejs sieciowy ma adres sieciowy z puli 192.168.*.*
sudo nano /etc/netplan/00-cloud-init.yaml # edycja pliku konfiguracyjnego z zapisanymi konfiguracjami sieciowymi interfejsów jako root w celu nadania statycznego adresu IP (podgląd poniżej)
netplan apply # zastosowanie zmian
```

Wygląd pliku 00-cloud-init.yaml z ustawionym statycznym adresem IP (odstępy lepiej wstawiać spacjami zamiast tabulatorów ponieważ plik jest bardzo wrażliwy na składnię)

```yaml
network:
    ethernets:
        enp0s3:
            dhcp4: true
        enp0s8:
            addresses:
            - 192.168.0.101/24 # statyczny adres IP wraz z skróconą maską
            # gateway: 192.168.0.1 # adres bramy
            nameservers: {} # adresy serwerów DNS
```

Dodanie nowego użytkownika

```bash
sudo useradd user # dodanie użytkownika user
```

Wygenerowanie i dodanie kluczy SSH:

```bash
    ip a # sprawdzenie adresu IP maszyny wirtualnej
    ssh-keygen -t rsa # wygenerowanie kluczy SSH na podstawie algorytmu RSA
    file ~/.ssh/id_rsa # sprawdzenie poprawności utworzenia klucza
    ssh-copy-id -i id_rsa remote-user@server-ip # skopiowanie kluczy na serwer
    ssh remote-user@server-ip # zalogowanie się poprzez SSH do serwera
```
Na komputerze fizycznym (hoście):
Na WinSCP zalogować się do swojej maszyny wirtualnej swoim logiem i hasłem.  
Jako, że plik jest ukryty, to należy włączyć pokazywanie ukrytych opcji:  
Options->Preferences->Panels->Show hidden files  
Ściągamy pliki id_ecdsa na nasz komputer.  
Rozłączamy się z WinSCP.  
Włączamy PuTTYgen  
Przy opcji "Load an existing private key file" wybieramy nasz plik id_rsa (wcześniej trzeba zamienić wybór z plików ppk na Wszystkie Pliki)  
Zapisujemy prywatny klucz klikając na Save Private Key i wskazując dowolną lokalizację (będzie miał on rozszerzenie .ppk)  
Przechodzimy do PuTTY -> SSH -> Auth  
W ostatniej opcji wybieramy zapisany wcześniej klucz ppk  
Wracamy do okna Session i w polu Host Name wpisujemy remote-user@remote-ip-address(gdzie remote user to nazwa usera na maszynie wirtualnej a remote-ip-address to adres IP maszyny wirtualnej
Wciskamy open i po chwili powinniśmy być zalogowani do maszyny wirtualnej bez podawania hasła
