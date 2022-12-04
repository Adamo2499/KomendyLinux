# Tworzenie CA (wersja 2)

```bash
# utworzenie folderu do CA (zalecane, ale nie wymagace)
mkdir CA 
#skopiowanie pliku konfiguracyjnego do utworzonego folderu
copy /etc/ssh/openssh.cnf ~/CA 
# utworzenie folderów potrzebnych do CA
mkdir ./CA/misc ./CA/certs ./CA/private 
# utworzenie CA:
openssl ecparam -name prime256v1 -genkey -noout -out ca.key
openssl req -new -x509 -sha256 -key ca.key -out ca.crt
# utworzenie certyfikatu dla serwera:
openssl ecparam -name prime256v1 -genkey -noout -out server.key
openssl req -new -sha256 -key server.key -out server.csr
openssl x509 -req -in server.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out server.crt -days 1000 -sha256
# utworzenie certyfikatu dla klienta:
openssl ecparam -name prime256v1 -genkey -noout -out client.key
openssl req -new -sha256 -key client.key -out client.csr
openssl x509 -req -in client.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out client.crt -days 1000 -sha256
```

Po wygenerowaniu certyfukatu klienta:

1. załaduj certyfikat KLIENTA client.crt lub client.pem na komputer (przez WinSCP)
2. zainstaluj go (PPM na plik, wybierz opcję Zainstaluj certyfikat)
3. Ctrl+R → certmgr.msc
4. zobacz, czy certyfikat z Twoim podpisem jest gdziekolwiek na liście

## Przydatne linki

- [Linux Expert](https://linuxexpert.pl/posts/1947/openssl-tworzenie-nowego-certyfikatu/#Dokumentacja_w_sieci) (jest po polsku + dokładnie tłumaczy co robi dana komenda)
- [Arch Linux Wki](https://wiki.archlinux.org/title/OpenSSL) (chaptery 3.1-3.3 (w zależności od wymaganego algorytmu), 3.4,, 3.6, 3.8 )
- [Delicious Brains](https://deliciousbrains.com/ssl-certificate-authority-for-local-https-development/)