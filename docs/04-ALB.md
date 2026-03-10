# Application Load Balancer (ALB)

## Descripció

L’Application Load Balancer distribueix el tràfic web entre diferents instàncies EC2.

Això permet millorar el rendiment del sistema i garantir alta disponibilitat.

---

## Grup de desti
Configuració:
- Tipus de destino : Instancias | Protocol : HTTP / Port : 80

- Codigo de exito : 200,302

- Registrar destino : grupodedestino-wordpress **a nostra màquina original**

## Balancejador de càrregues
Un cop creat el grup de destinació , creem el balancejador de càrregues.

- Nom : balanceadordecarga-wordpress

- mapeig de xarxa : seleccionem els mapeigs del teu gust

- Grup de seguretat : els mateixos de la nostra instància

- Agent d'escolta i adreçament : HTTP / Port : 80 | Acció predeterminada : grupodedestino-wordpress

---

## Comprovació


---

## Funcionament

1. L’usuari accedeix a la pàgina web.
2. La petició arriba al Load Balancer.
3. El Load Balancer redirigeix la petició a una instància EC2 disponible.

Si una instància falla, el Load Balancer deixa d’enviar-li tràfic.

---
