# BDiSI - Laboratorium
## 11 X 2022
```sh
    1  passwd
    2  ls -l
    3  mkdir test_folder
    4  chmod 750 test_folder/
    5  getfacl test_folder/ # wyświetlenie uprawnień do danego pliku
    6  getfacl test_folder/ --omit-header ## wyświetlenie uprawnień do danego pliku z pominięciem metadanych
    7  rmdir test_folder/
    8  mkdir BDiSI
    9  cd BDiSI/
   10  mkdir Lab1
   11  cd Lab1/
   12  mkdir test_folder
   13  chmod 750 test_folder/ #zmiana upranień do folderu test_folder (tutaj user ma wszystkie uprawnienia, grupa do odczytu i przeglądania a inni nie mogą nic robić)
   14  group
   15  clear
   16  pwd
   17  chmod 730 test_folder/ #zmiana upranień do folderu test_folder (tutaj user ma wszystkie uprawnienia, grupa do zapisu i przeglądania a inni nie mogą nic robić)
   18  pwd
   19  clear
   20  pwd
   21  getfacl test_folder/
   22  setfacl -m user:wkoz:wx test_folder/ # nadanie uprawnień do zapisu i wykonania użytkownikowi wkoz w folderze test_folder
   23  getfacl test_folder/
   24  man setfack
   25  man setfal
   26  man setfacl # pomoc do polecenia setfacl
   27  man setfacl
   28  cd test_folder/
   29  pwd
   30  ls -l
   31  ls -l
   32  ls -la
   33  getfacl .
   34  touch /home/wkoz/Lab0/test
   35  touch /home/wkoz/Lab0/testFile
   36  touch /home/wkoz/Lab01/testFile  #utworzenie pustego pliku
   37  ls
   38  ls -l
   39  ls -l
   40  chmod g-w . # odebranie grupie upranień do zapisu w danym folderze
   41  chmod g+w . # nadanie grupie upranień do zapisu w danym folderze
   42  ls -l
   43  setfacl -d -m group:students:wx . # nadanie grupie students domyślnych uprawnień do zapisu i wykonania w aktualnym folderze
   44  getfacl katalog –-omit-header
   45  getfacl . –-omit-header
   46  mkdir ~/public
   47  setfacl g:students:wx 
   49  setfacl -m g:students:wx . # nadanie grupie students uprawnień do zapisu i wykonania w aktualnym folderze
   51  setfacl -m g:staff:rwx .
   52  clear
   53* touch /home/fbej/test_folder/testABie
```