# 🌩️ WordPress Escalable a AWS

Projecte de Cloud Computing – Implantació d’un sistema escalable amb WordPress al núvol d’Amazon Web Services (AWS).

## 📌 Objectiu del Projecte

Implantar una arquitectura escalable horitzontalment a AWS utilitzant WordPress, garantint:

- Alta disponibilitat
- Balanceig de càrrega
- Escalabilitat automàtica
- Redundància de base de dades
- Sistema de còpies de seguretat
- Recuperació davant fallades

---

## 🏗️ Arquitectura del Sistema

(INSEREIX AQUÍ UN DIAGRAMA – pots fer-lo amb draw.io o Canva)

Components principals:

- EC2 (instàncies WordPress)
- RDS PostgreSQL (Master-Slave)
- EFS (fitxers compartits)
- ALB (Application Load Balancer)
- Auto Scaling Group
- AWS Backup

---

## 🔧 Serveis AWS Utilitzats

### 🖥️ EC2
Instàncies Linux amb WordPress instal·lat.

Configuració:
- Nombre d'instàncies: Wordpress-cloud
- AMI: ami-0f3caa1cf4417e51b
- Tipus d’instància: t3.micro
- Security Groups: sg-0a451d3aa98caeb88

---

### 🗄️ RDS – Mysql (Master-Slave)

Base de dades gestionada amb rèplica en lectura.

Configuració:
- Motor: MySQL
- Versión: 8.4.7
- Plantilla: Entorno de pruebas (Dev/Test)
- Disponibilidad: Implementación de una única instancia de base de datos (Single-AZ)
- Tipo de instancia: db.t4g.micro
- Storage: 20 GB

Avantatges:
- Alta disponibilitat
- Redundància
- Failover automàtic

---

### 📂 EFS (Elastic File System)

Sistema de fitxers compartit entre totes les instàncies EC2.

Funció:
- Compartir carpeta `/wp-content`
- Garantir consistència entre instàncies

---

### ⚖️ Application Load Balancer (ALB)

Distribueix el tràfic entre instàncies EC2.

Configuració:
- Target Group
- Health Checks
- Listener HTTP

---

### 📈 Auto Scaling Group

Permet crear o eliminar instàncies automàticament segons:

- CPU usage
- Nombre de peticions

Configuració:
- Min instances:
- Max instances:
- Scaling policies:

---

### 💾 AWS Backup

Sistema automàtic de còpies de seguretat per:
- RDS
- EFS

Configuració:
- Backup plan
- Retenció:

---

## 🔄 Escalabilitat Horitzontal

Quan la càrrega augmenta:

1. ALB detecta més tràfic
2. Auto Scaling crea noves instàncies EC2
3. Les noves instàncies es connecten a:
   - EFS
   - RDS
4. El sistema continua funcionant sense interrupció

---

## 🛡️ Alta Disponibilitat

- Múltiples instàncies EC2
- RDS amb rèplica
- Sistema distribuït en diferents AZ
- Balanceig de càrrega

---

## 🚨 Recuperació davant Fallades

Escenaris provats:

- Eliminació d’una instància EC2
- Aturada manual del Master RDS
- Eliminació d’arxius

Resultat:
El sistema continua funcionant correctament.

---

## 🎯 Resultats

✔ Escalabilitat funcional  
✔ Sistema redundant  
✔ WordPress accessible via ALB  
✔ Dades compartides correctament  
✔ Auto Scaling operatiu  

---

## 📚 Conclusions

Aquest projecte permet entendre com dissenyar arquitectures reals al núvol amb:

- Escalabilitat
- Alta disponibilitat
- Redundància
- Automatització