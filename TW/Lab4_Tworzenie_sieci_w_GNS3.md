# Przygotowanie sieci w GNS3

## Przydatne linki

https://www.gns3.com/software/download -> GNS3
https://tfr.org/cisco-ios/7200/c7200-adventerprisek9-mz.124-24.T5.bin -> obraz Cisco IOS 7200
https://tfr.org/cisco-ios/36xx/3660/c3660-a3jk9s-mz.124-19.bin -> obraz Cisco IOS 3660
https://gns3.com/marketplace/appliances/ipterm -> ipterm

## Dodanie obrazu maszyny do GNS3
a) Routery Cisco 7200 i 3660
Edit -> Preferences -> IOS Routers -> New ->Wybieramy pobrany plik bin -> zgadzamy się na dekompresję obrazu -> Ustawienia pamięci bez zmian 
->  Zaznaczamy EtherSwitch (tylko w przypadku Cisco 3660) -> wybieramy odpowiednie interfejsy sieciowe -> Finish

b) ipterm

File -> Import appliances -> wskazujemy pobrany plik ipterm -> Apply -> OK

## Komendy w Cisco iOS (Router/ switch)

```
conf t (configure terminal) -> przejście do terminala konfiguracyjnego
interface nazwa_interfejsu nr_interfejsu
ip addr <adres IP> <maska>
no shutdown
ip route <adresy IP> -> ustawienie statycznej trasy routingu
ip default-gateway <adres bramy>

```
