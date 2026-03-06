# EFS – Sistema de Fitxers Compartit

## Descripció

Amazon EFS (Elastic File System) és un sistema de fitxers compartit que permet que múltiples instàncies EC2 accedeixin als mateixos arxius al mateix temps.

Aquest servei és necessari en arquitectures escalables amb múltiples servidors.

---

## Funció en WordPress

En aquest projecte, EFS s’utilitza per compartir la carpeta:

/wp-content

Aquesta carpeta conté:

- Plugins
- Temes
- Imatges i arxius pujats pels usuaris

Gràcies a EFS, totes les instàncies EC2 utilitzen els mateixos fitxers.

---

## Avantatges

- Sistema de fitxers distribuït
- Escalabilitat automàtica
- Accés simultani des de diverses instàncies

---