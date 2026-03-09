# Auto Scaling

## Descripció

AWS Auto Scaling permet crear o eliminar instàncies EC2 automàticament segons la demanda del sistema.

Aquest mecanisme és la base de l’escalabilitat horitzontal.

---

## Configuració utilitzada

- Nombre mínim d’instàncies: 1
- Nombre màxim d’instàncies: 3
- Mètrica utilitzada: CPU Utilization

---

## Funcionament

Quan la càrrega del sistema augmenta:

- Auto Scaling crea noves instàncies EC2.

Quan la càrrega disminueix:

- Algunes instàncies s’eliminen per optimitzar els recursos.

Les noves instàncies es registren automàticament al Load Balancer.

---