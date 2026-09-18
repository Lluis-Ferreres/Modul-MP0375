## Què és el DNS
El sistema de noms de domini (**D**omain **N**ame **S**ystem o **DNS**) s'utilitza per facilitar la utilització per part dels éssers humans dels recursos presents a Internet.

En concret el DNS ens permet generar una base de dades on relacionarem les IPs dels equips on es troba la informació compartida en xarxa amb noms que facilitaran recordar com accedir-hi.

En un principi s'utilitzaven mètodes més arcaics i que es mantenen a dia d'avui per si no és necessària la presència d'un servidor, però que són extremadament lents i difícils de mantenir quan la xarxa d'equips interconnectats comença a augmentar.  
El mètode consisteix a generar un fitxer de text on es relaciona la IP amb l'identificador de l'equip al que es vol accedir.  
Els problemes que això presenta:
* Actualització a cada equip on es desitja utilitzar-ho
* Possibles inconsistències entre diferents equips per contenir informacions errònies

Aquest mètode ens pot resultar útil a nivell local, per implementar petites proves, facilitar-nos l'accés a diferents equips que només necessitem nosaltres o protegir-nos d'accedir a màquines remotes sense adonar-nos. Existeix tant a sistemes Unix-GNU/Linux com Microsoft.

* /etc/hosts --> conté la informació comentada, una IP associada a un nom
* C:\Windows\System32\drivers\etc\hosts --> el mateix però a sistemes Microsoft

Tota la configuració del DNS es pot configurar mitjançant la correcta configuració del servidor DHCP.

## Definicions
**Domini**: és el nom que representa una unió d'equips relacionats d'alguna forma. Quan es defineix un domini és per relacionar i localitzar amb més facilitat informacions que pertànyen a una determinada organització o contingut. D'aquesta manera tots els equips que contenen informació i estan relacionats resulten més senzills de localitzar i organitzar. Un domini té una estructura dintre de la base de dades que permetrà establir la seva ubicació. Tot seguit passem a descriure-ho.

* **TLD**: **T**op **L**evel **D**omain s'anomenen dominis de primer nivell. Dintre de l'estructura de noms de domini, ens permet reorganitzar la informació per organitzacions comercials, militars, governs, per finalitats, ubicacions geogràfiques, continguts culturals, etc. Dintre d'aquests TLD trobem alguns com els següents: *.com, .cat, .gov, .it, .io, .es, .net, .edu, .org*, etc.

* **domini**: el domini es forma amb el nom identificador més un TLD. Amb aquesta informació s'intenta aconseguir una combinació que resulti senzilla de recordar per part dels usuaris, el que també forma part de les activitats de negoci de les empreses quan volen exposar els seus productes i volen donar-se a conèixer. Exemples: *google.cat, amazon.es, incibe.es*, etc.

* **subdomini**: indica dintre del domini (o més bé hauria d'indicar) dintre del domini el tipus de finalitat del lloc on ens anem a connectar. Exemples: *www.google.com (web per accedir al motor de cerca de l'empresa Google), www.incibe.es (web per accedir a la pàgina sobre informació pels ciutadans sobre ciberseguretat a Espanya), ftp.rediris.com (accés per intercanvi de fitxers amb la xarxa acadèmica o d'investigació rediris)*, etc.

**Zona**: es tracta d'un fitxer on es defineixen les característiques del domini així com també la relació entre IP i nom dels equips dintre del domini.
