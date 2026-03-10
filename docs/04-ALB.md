# Application Load Balancer (ALB)

## Descripció

L’Application Load Balancer distribueix el tràfic web entre diferents instàncies EC2.

Això permet millorar el rendiment del sistema i garantir alta disponibilitat.

---

## Grup de desti
Configuració:
- Tipus de destino : Instancias | Protocol : HTTP / Port : 80
![Tipus de destino](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/balancejadordec%C3%A0rregues/grupdedesti/loadbalancer01.png)

- Codigo de exito : 200,302
![codi d'èxit](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/balancejadordec%C3%A0rregues/grupdedesti/loadblancer02.png)

- Registrar destino : grupodedestino-wordpress **a nostra màquina original**
![Registrar destino](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/balancejadordec%C3%A0rregues/grupdedesti/loadbalncer03.png)

## Balancejador de càrregues
Un cop creat el grup de destinació , creem el balancejador de càrregues.

- Nom : balanceadordecarga-wordpress
![Nom](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/balancejadordec%C3%A0rregues/loadbalancer09.png)

- mapeig de xarxa : seleccionem els mapeigs del teu gust , en meu cas he seleccionat els mateixos que la instància EC2
![mapeig de xarxa](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/balancejadordec%C3%A0rregues/loadbalancer06.png)

- Grup de seguretat : els mateixos de la nostra instància
![grup de seguretat](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/loadbalncer07.png)

- Agent d'escolta i adreçament : HTTP / Port : 80 | Acció predeterminada : grupodedestino-wordpress
![Agent d'escolta i adreçament](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/balancejadordec%C3%A0rregues/loadbalancer08.png)

---

## Comprovació
Un cop creat si anem a l'apartat de **Mapa de Recursos** podem veure que el trànsit del port 80 és redirigeix ​​a la nostra màquina d'EC2.
![Comprovació](https://github.com/gianxfr9nco/Wordpress-cloud/blob/main/docs/screenshots/balancejadordec%C3%A0rregues/loadbalancer13.png)

---

## Funcionament

1. L’usuari accedeix a la pàgina web.
2. La petició arriba al Load Balancer.
3. El Load Balancer redirigeix la petició a una instància EC2 disponible.

Si una instància falla, el Load Balancer deixa d’enviar-li tràfic.

---
