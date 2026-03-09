# RDS – Base de Dades MySQL

## Descripció

Amazon RDS s’utilitza per gestionar la base de dades del sistema WordPress sense necessitat d’administrar manualment el servidor de base de dades.

Aquest servei permet tenir una base de dades gestionada, segura i amb funcionalitats de monitorització i còpies de seguretat.

---

## Configuració utilitzada

- Motor: MySQL
- Versió: 8.4.7
- Plantilla: Entorn de proves (Dev/Test)
- Tipus d’instància: db.t3.micro
- Disponibilitat: Single-AZ

---

## Seguretat

- Grup de seguretat: **SGmysql-wordpress**
- Port: **3306**

![SG](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/rds01.png)

---

## Funció dins de l’arquitectura

La base de dades emmagatzema tota la informació del lloc web:

- Usuaris
- Entrades del blog
- Pàgines
- Comentaris
- Configuració de WordPress

Les instàncies EC2 es connecten a la base de dades utilitzant **endpoint de RDS**

```mysql -h wordpress-base.xxxxxxx.us-east-1.rds.amazonaws.com -P 3306 -u admin -p```

---

## Avantatges d’utilitzar RDS

- Gestió automàtica del servidor
- Còpies de seguretat automàtiques
- Monitorització del rendiment
- Alta fiabilitat

---