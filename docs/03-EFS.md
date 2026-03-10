# EFS – Sistema de Fitxers Compartit

## Descripció

Amazon EFS (Elastic File System) és un sistema de fitxers compartit que permet que múltiples instàncies EC2 accedeixin als mateixos arxius al mateix temps.

Aquest servei és necessari en arquitectures escalables amb múltiples servidors.

---

## Funció en WordPress

En aquest projecte, EFS s’utilitza per compartir les carpetes:

/var/www/html **dades del wordpress**

Aquesta carpeta conté:

- wp-admin
- wp-includes
- core de wordpress
- configuraciones
- themes
- plugins
- uploads

Gràcies a EFS, totes les instàncies EC2 utilitzen els mateixos fitxers.

---

## Avantatges

- Sistema de fitxers distribuït
- Escalabilitat automàtica
- Accés simultani des de diverses instàncies

---

## Passos per crear un EFS

- Possem el nom del sistema d'arxius i la VPC predeterminada
![Nou sistema d'arxius](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/efs02.png)

- Creem el grup de seguretat per permetre el tràfic NFS
![Grup de seguretat](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/efs03.png)

- Configuració en l'apartat de Xarxes , canviarem el grup de seguretat pel que hem creat anteriorment per el EC2 i EFS
![Configuració en xarxes](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/efs04.png)


## Muntar nostra EFS

1. Instal·larem el següent paquet **nfs-utils**

    ```bash
    sudo dnf install nfs-utils -y
    ```

2. Ja instal·lat el paquet anirem al nostre efs a buscar l'ordre de muntatge per nfs

    ![Ordre de muntatge](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/efs05.png)


3. Ara a la carpeta creada /mnt/efs montarem el efs

    ```bash
    sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport xxxxxxxxxx.us-east-1.amazonaws.com:/ /mnt/efs
    ```

    Y per comprovar que s'ha muntat correctament
    ```bash
    df -h
    ``` 

4. I perquè cada vegada que iniciem la instància no es tregui el muntatge afegim la línia següent a aquest fitxer **/etc/fstab**

    ```bash
    xxxxxxxx.us-east-1.amazonaws.com:/ /mnt/efs nfs4 nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport 0 0
    ```

5. I per sincronitzar els arxius que tenim al /var/www/html amb el punt de muntatge

    ```bash
    sudo rsync -av /var/www/html /mnt/efs/
    ```