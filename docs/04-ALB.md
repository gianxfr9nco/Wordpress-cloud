# Application Load Balancer (ALB)

## Descripció

L’Application Load Balancer distribueix el tràfic web entre diferents instàncies EC2.

Això permet millorar el rendiment del sistema i garantir alta disponibilitat.

---

## Configuració utilitzada

- Protocol: HTTP
- Port: 80
- Target Group: instàncies EC2
- Health Checks activats

---

## Funcionament

1. L’usuari accedeix a la pàgina web.
2. La petició arriba al Load Balancer.
3. El Load Balancer redirigeix la petició a una instància EC2 disponible.

Si una instància falla, el Load Balancer deixa d’enviar-li tràfic.

---
