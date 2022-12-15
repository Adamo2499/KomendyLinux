# BDiSI Lab 3 25 X 2022

## Linux
```sh
ssh-keygen -b 521 -t ecdsa #utworzenie pary kluczy w oparciu o krzywech eliptycznE o maksymalnej długości (maksymalną długość i rodzaj klucza podanego przez Waraksę ptrzeba sprawdzić w manie)
cd ~/.ssh/ # przejście do katalogu z kluczami prywatnym i publicznym (publiczny ma na końcu .pub)
ssh-copy-id -i id_ecdsa xxxx@pollux.umg.edu.pl # skopiowanie klucza na serwer
```
## Windows
Na WinSCP zalogować się do Polluxa swoim logiem i hasłem.  
Jako, że plik jest ukryty, to należy włączyć pokazywanie ukrytych opcji:  
Options->Preferences->Panels->Show hidden files  
Ściągamy pliki id_ecdsa na nasz komputer.  
Rozłączamy się z WinSCP.  
Włączamy PuTTYgen  
Przy opcji "Load an existing private key file" wybieramy nasz plik id_ecdsa (wcześniej trzeba zamienić wybór z plików ppk na Wszystkie Pliki)  
Zapisujemy prywatny klucz klikając na Save Private Key i wskazując dowolną lokalizację (będzie miał on rozszerzenie .ppk)  
Przechodzimy do PuTTY -> SSH -> Auth  
W ostatniej opcji wybieramy zapisany wcześniej klucz ppk  
Wracamy do okna Session i w polu Host Name wpisujemy xxxx@pollux.umg.edu.pl (gdzie xxxx to nasz login na Polluxa)  
Wciskamy open i po chwili powinniśmy być zalogowani do Polluxa bez podawania hasła