# EFS – Sistema de Fitxers Compartit

## Descripció

Amazon EFS (Elastic File System) és un sistema de fitxers compartit que permet que múltiples instàncies EC2 accedeixin als mateixos arxius al mateix temps.

Aquest servei és necessari en arquitectures escalables amb múltiples servidors.

---

## Passos per crear un EFS

- Possem el nom del sistema d'arxius i la VPC predeterminada
![Nou sistema d'arxius](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/efs02.png)

- Creem el grup de seguretat per permetre el tràfic NFS
![Grup de seguretat](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/efs03.png)

- Configuració en l'apartat de Xarxes , canviarem el grup de seguretat pel que hem creat anteriorment per el EC2 i EFS
![Configuració en xarxes](/home/franco/wordpress-aws-cloud/docs/screenshots/efs04.png)

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

## Configuració

```bash
# 1. Instal·lar el client NFS
sudo yum install -y nfs-utils

# 2. Crear el punt de muntatge
sudo mkdir -p /mnt/efs

# 3. Conectar el EFS al punto de montaje
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport xxxxxxxxxx.us-east-1.amazonaws.com:/ /mnt/efs

# 4. Copiar los archivos de wordpress al efs
sudo rsync -av /var/www/html /mnt/efs/

# 5. Comprovació
df -h 

```

## Avantatges

- Sistema de fitxers distribuït
- Escalabilitat automàtica
- Accés simultani des de diverses instàncies

---