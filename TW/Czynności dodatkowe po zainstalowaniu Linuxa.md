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
    ssh-keygen -t rsa # wygenerowanie kluczy SSH na podstawie algorytmu RSA
    file ~/.ssh/id_rsa # sprawdzenie poprawności utworzenia klucza
    ssh-copy-id -i id_rsa remote-user@server-ip # skopiowanie kluczy na serwer
    ssh remote-user@server-ip # zalogowanie się poprzez SSH do serwera
```
