# Auto Scaling

## Descripció

AWS Auto Scaling permet crear o eliminar instàncies EC2 automàticament segons la demanda del sistema.

Aquest mecanisme és la base de l’escalabilitat horitzontal.

---

## Plantilla de lanzamiento 
Abans de crear l'auto scaling haurem de crear una imatge de la nostra màquina original, que serà la nostra plantilla per a l'autoscaling.

- Seleccionem la imatge de la nostra màquina original
![Plantilla de lanzamiento](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/autoscaling/auto01.png)

- Parell de claus la mateixa que la màquina original

- A opcions avançades activem el monitoratge detallat
![Opcions avançades](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/autoscaling/auto03.png)  

- A la configuració de xarxa seleccionem la mateixa que la nostra instància original i també els mateixos grups de seguretat de la instància original.
![Configuració de xarxa](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/autoscaling/auto02.png)

---

## Creació de grup de AutoScaling

- Seleccionem la plantilla de lanzamiento que hem creat anteriorment
![Seleccionem la plantilla de lanzamiento](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/autoscaling/auto04.png)

- Xarxa : seleccionarem la subxarxa on esta la nostra màquina original
![Xarxa](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/autoscaling/auto05.png)

- Configurar les opcions avançades 
    - Balancejador de càrrega : Associar amb un Load Balancer existent
    ![Balancejador de càrrega](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/autoscaling/auto06.png)

    - Configuracio de escalabilitat i tamaño de grup
    ![Configuracio de escalabilitat i tamaño de grup](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/autoscaling/auto07.png)

    - Politiques de manteniment de instancias
    ![Politiques de manteniment de instancias](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/autoscaling/auto08.png)

Un cop creat les polítiques d'escalat , crearem les polítiques d'esclat dinàmic on especifiquem els paràmetres perquè s'escalin les instàncies.

- Politiques d'esclat dinàmic
![Politiques d'esclat dinàmic](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/autoscaling/auto09.png)

- Parametres de escalabilitat
![Parametres de escalabilitat](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/autoscaling/auto10.png)
---

## Comprovació

- Elimino una instància i al moment em fa una alerta
![Comprovació](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/autoscaling/auto11.png)

- I es crea automàticament una nova instància
![Comprovació](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/autoscaling/auto12.png)

## Funcionament

Quan la càrrega del sistema augmenta o quan s'elimina una instància:

- Auto Scaling crea noves instàncies EC2.

Quan la càrrega disminueix:

- Algunes instàncies s’eliminen per optimitzar els recursos.

Les noves instàncies es registren automàticament al Load Balancer.

---