# Szyfrowanie poczty z wykorzystaniem kluczy  

## Wygererowanie klucza (na Polluxie)

``` bash
gpg --gen-key # wygenerowanie kluczy publicznego (pubring.gpg) i prywatnego (secring.gpg) oraz innych potrzebnych danych
gpg --export -a -o ~/.gpgkey.txt  # wyeksportowanie klucza prywatnego do pliku tekstowego
```

- Ściągamy plik .gpgkey.txt oraz secring.gpg na Windowsa (poprzez WinSCP / polecenie scp)  

## Wgranie klucza publicznego na serwer

- Wyszukujemy w Internecie "openpgp public key server"
- Korzystamy z poniższych serwerów:

  - [keys.openpgp.org](https://keys.openpgp.org/)
  - [Hockeypuck OpenPGP keyserver](https://keyserver.ubuntu.com/)

### Wgranie klucza publicznego na serwer Hockeypucka

- Wciskamy opcję Submit Key
- Kopiujemy zawartość .gpgkey.txt i wlejamy ją do podanego okienka
- Wpisujemy nasz adres email i sprawdzamy, czy udało się nas znaleźć

### Wgranie klucza publicznego na serwer keys.openpgp org

- Wciskamy opcję Upload
- Klikamy opcję Upload file
- Wyszukujemy iwybieramy zapisany plik .gpgkey.txt
- Klikamy Send Verification Email
- W Thunderbirdzie klikamy na link w wiadomości, aby potwierdzić nasz klucz publiczny
  
## Dodanie klucza prywatnego do Thunderbirda

- Wchodzimy do ustawień Thunderbirda -> Ustawienia kont -> Szyfrowanie "end to end"
- Wybieramy opcję "Dodaj klucz"
- Wybieramy opcję "Importuj istniejący klucz OpenPGP"
- Wciskamy "Wybierz plik to zaimportowania" i wybieramy plik secring.gpg i klikamy "Kontynuuj"
- Wprowadzamy hasło, które wprowadziliśmy podczas tworzenia klucza
- Klikamy "Kontynuuj" i w oknie "Konfiguracja kont" i wybieramy nasz nowo zainportowany klucz

## Uzyskanie klucza publicznego kolegi / koleżanki

- Jeżeli chcielibyśmy uzyskać czyiś klucz publiczny to wykonujemy następujące czynności:
  - Wyszukujemy adres email poszukiwanej osoby
  - Jeżeli bierzemy klucz z Hockeypicka:
    - Klikamy na Hash / pub
    - Kopiujemy całość
    - Przechodzimy do Menadżera kluczy
    - Wybieramy Edycja -> Importuj klucze ze schowka
  - Jeżeli bierzemy klucz z keys.openpgp.org:
    - Klikamy w link i pobieramy plik .asc
    - Przechodzimy do Menadżera kluczy
    - Wybieramy Plik -> Importuj klucze publiczne z pliku
    - Wybieramy nasz plik .asc i wciskamy Open
  - Dalej tak samo dla obu przypadków:
    - Zaznaczamy opcję Zaakceptowany (niezweryfikowany)

## Potwierdzenie wiarygodności klucza

- Po odebraniu wiadmości klikamy w OpenPGP (prawy górny róg) -> Wyświetl klucz osoby podpisującej
- Wybieramy opcję Tak, zweryfikowano osobiście, że to właściwy odcisk klucza -> OK

## Unieważnienie klucza prywatnego

- Przechodzimy do ustawień Thunderbirda -> Ustawienia kont -> Szyfrowanie "end to end"
- Zmieniany rodzaj klucza na Żaden
- Wybieramy obecny klucz (będzie informacja o tym, kiedy wygaśnie) i klikamy Więcej -> Unieważnij klucz -> Unieważnij klucz