# Tworzenie CA

```bash
openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:2048 > key1 # Generowanie klucza i zapisywnaie go w pliku key
openssl req -new -rsa256 -key key1 -out certificate1 # Generowanie prośby o podpis na bazie klucza w pliku key i zapisanie go w pliku certificate
openssl req -x509 -newkey rsa:4096 -days 810 -keyout key2 -out certificate2 # Generowanie klucza RSA wraz z własnoręczym podpisaniem certyfikatu i zapisanie klucza w pliku key i certyfikatu w pliku certificate 
openssl x509 -text -in certificate #  Sprawdzenie  zawartości pliku certificate
openssl x509 -req -in certificate1 -CA certificate2 -CAkey key2 -CAcreateserial -out podpisanyCertyfikat.crt -days 500 -sha256 # Podpisanie certyfikatu
```

Jeżeli wszystko poszło OK, to można wygererowany certyfikat ściągnąć poprzez WinSCP / polecenie SCP na Windowsa.
Po ściągnięciu można zainstalować certyfikat i póżniej sprawdzić poprawność zainstalowania używając certmgr.msc > Pośrednie urzędy certyfikacji > Certyfikaty i tam powinien być nasz certyfikat

## Przydatne linki

- [Linux Expert](https://linuxexpert.pl/posts/1947/openssl-tworzenie-nowego-certyfikatu/#Dokumentacja_w_sieci) (jest po polsku + dokładnie tłumaczy co robi dana komenda)
- [Arch Linux Wki](https://wiki.archlinux.org/title/OpenSSL) (chaptery 3.1-3.3 (w zależności od wymaganego algorytmu), 3.4,, 3.6, 3.8 )
- [Delicious Brains](https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/)