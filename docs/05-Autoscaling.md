# Auto Scaling

## Descripció

AWS Auto Scaling permet crear o eliminar instàncies EC2 automàticament segons la demanda del sistema.

Aquest mecanisme és la base de l’escalabilitat horitzontal.

---

## Plantilla de lanzamiento 
Abans de crear l'auto scaling haurem de crear una imatge de la nostra màquina original, que serà la nostra plantilla per a l'autoscaling.

- Seleccionem la imatge de la nostra màquina original
![Plantilla de lanzamiento]()

- Parell de claus la mateixa que la màquina original

- A opcions avançades activem el monitoratge detallat
![Opcions avançades]()  

- A la configuració de xarxa seleccionem la mateixa que la nostra instància original i també els mateixos grups de seguretat de la instància original.
![Configuració de xarxa]()

---

## Creació de grup de AutoScaling

- Seleccionem la plantilla de lanzamiento que hem creat anteriorment
![Seleccionem la plantilla de lanzamiento]()

- Xarxa : seleccionarem la subxarxa on esta la nostra màquina original
![Xarxa]()

- Configurar les opcions avançades 
    - Balancejador de càrrega : Associar amb un Load Balancer existent
    ![Balancejador de càrrega]()

    - Configuracio de escalabilitat i tamaño de grup
    ![Configuracio de escalabilitat i tamaño de grup]()

    - Politiques de manteniment de instancias
    ![Politiques de manteniment de instancias]()

Un cop creat les polítiques d'escalat , crearem les polítiques d'esclat dinàmic on especifiquem els paràmetres perquè s'escalin les instàncies.

---

## Comprovació

- Elimino una instància i al moment em fa una alerta
![Comprovació]()

- I es crea automàticament una nova instància
![Comprovació]()

## Funcionament

Quan la càrrega del sistema augmenta o quan s'elimina una instància:

- Auto Scaling crea noves instàncies EC2.

Quan la càrrega disminueix:

- Algunes instàncies s’eliminen per optimitzar els recursos.

Les noves instàncies es registren automàticament al Load Balancer.

---