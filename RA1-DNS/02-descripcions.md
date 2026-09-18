## Jerarquia del sistema DNS
El DNS és una base de dades distribuïda a diferents servidors.  
El sistema de noms segueix el que s'anomena una estructura jeràrquica en forma d'arbre invertit. Això vol dir que a la part superior trobem el nivell més baix, el **0** on comença tot. Aquest nivell és l'**arrel** i només hi ha 13 servidors arrel (replicats a tot el món) per temes tecnològics. Amb IPv4 no es poen construir paquets que permetin emmagatzemar IPs per més dominis. En canvi amb IPv6 es podrà superar aquesta limitació tècnica i segurament apareixeran més servidors arrel.  
Seguidament trobem el **TLD al nivell 1**.  
Al **nivell 2** es defineix el **domini**.  
Finalment **a partir del nivell 3** es defineixen els **subdominis**.

De moment habitualment no trobarem més de 5 nivells per temes de rendiment. El màxim que permet la ICANN però és de 127 nivells, comptant subdominis i arrel.

Quan tenim definit un domini, utilitzarem el terme FQDN (**F**ully **Q**ualified **D**omain **N**ame) per a referir-nos al mateix. D'aquesta forma queda identificat a la xarxa i podrem accedir si està ben definit al servidor i tenim connectivitat.

## Tipus de servidors
* **Servidor primari**: conté les zones (arxius de definició de dominis) a dintre seu
* **Servidor secundari**: conté una còpia de les zones facilitada pel servidor primari
* **Servidor cau**: no conté informació, s'utilitza per accelerar les cerques d'informació. La primera vegada que es realitza una consulta a un DNS la resposta es pot desar a un servidor cau, el que accelera l'accés a posteriors visites al mateix domini. Per gestionar la validesa de la informació es defineixen els següents valors:
* **TTL** o temps de vida màxim: validesa de la informació a la memòria cau. Quan finalitza aquest temps la consulta es torna a realitzar al servidor primari o secundari corresponent
* Temps d'actualització (**refresh**): temps que utilitza el servidor secundari per sol·licitar una renovació de la informació al servidor primari
* Temps de reintents (**retry**): temps que ha de transcórrer des de que es detecta que el servidor primari està "caigut" fins que es demana la informació a un altre servidor
* Temps de caducitat (**expire**): temps fins que s'esborra la informació de zona del servidor secundari en cas que no hi hagi connectivitat amb el primari o qui li pugui facilitar la informació de zona 

## Registre de recursos (RR)
Dintre de les zones es defineixen els recursos (equips accessibles per IP). Per deixar clar quin tipus d'informació s'està utilitzant, es defineixen diferents tipus de registres.

**Estructura dels recursos**

*FQDN TTL Tipus Classe RDATA*

* **FQDN** és el nom del domini (finalitza amb un . per indicar que està complet i no li falta cap paraula)
* **TTL** és un temps de "vida" mínim durant el qual la informació es pot mantenir en memòria cau
* **Tipus de registres**
  - *SOA* (Start Of Authority): on es defineix el domini
  - *NS* (Name Server): identificació del servidor de noms
  - *A* (Address): permet assignar l'adreça IP al domini
  - *CNAME* (Canonical Name): és un àlies, una altra forma d'identificar un recurs. Ajuda a entendre millor el contingut del fitxer de zona al no repetir IPs, cosa que pot fer pensar que es tracta d'un equip diferent i obliga a fixar-se més amb les IPs definides
  - *MX* (Mail eXchanger): indica el servidor de correu associat al domini definit
  - *PTR* (PoinTeR): permet definir resolució inversa, és dit, a partir d'una IP obtenir un domini. No sol utilitzar-se per no donar massa informació a possibles atacants
  - *HINFO*: informació sobre el maquinari. No sol utilitzar-se per no donar massa informació a possibles atacants
  - *SRV* (SeRVice): servei. Sol associar-se amb hosts i ports, per identificar el servei que es defineix (per exemple VoIP)
  - *TXT*: emmagatzema qualsevol tipus d'informació que es vol oferir públicament quan es consulti informació sobre un domini
  - *AAAA*: s'utilitza per definir adreces IPv6
* **Classe**: conté el valor IN i significa que s'utilitza per Internet
* **RDATA**: indica les dades que acompanyen cada tipus de recurs
   - A: una adreça IPv4
   - AAAA: una adreça IPv6
   - CNAME: un nom de domini alternatiu al principal
   - MX: indica la prioritat per accedir a un servidor (en 16 bits) acompanyat del nom de l'equip
   - NS: nom de l'equip que serà el servidor de noms
   - PTR: el nom de domini (in-addr.arpa)
   - SOA: es defineix amb el nom del domini, nom del servidor i adreça de correu d'un administrador (tot i que la sintaxi del correu és diferent al canviar @ per un .). Entre parèntesi trobarem: un número de sèrie, temps d'actualització, temps de reintent, temps de caducitat i temps mínim de vida (validesa de la informació emmagatzemada en memòria cau)

## Més informació
Agraïments a les següents webs:  
[Inicis DNS: /etc/hosts](https://thelinuxcode.com/etc-hosts-file-complete-guide-for-linux/ "Fitxer hosts")  
[Teoria sobre DNS](https://www.profesordeinformatica.com/servicios/dns "Ampliació de coneixements")  
[Limitació de servidors arrel](https://www.lifewire.com/dns-root-name-servers-3971336 "Ampliació de coneixements")   
[Nombre màxim de nivells de domini](https://www.byronvargas.com/web/cuantos-niveles-puede-tener-un-nombre-de-dominio-2/?expand_article=1 "Ampliació de coneixements")  
[Sobre els registres SRV](https://www.cloudflare.com/learning/dns/dns-records/dns-srv-record/ "Ampliació de coneixements")  
[Sobre els registres PTR](https://www.cloudflare.com/learning/dns/dns-records/dns-ptr-record/ "Ampliació sobre registres PTR")
