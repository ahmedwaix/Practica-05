# **Pràctica 05**

**Instal·lació d'un servei web amb HTTPS**

**Autors:** Ahmed Belhadi

**Tutor projecte:** Rafa

**Data:** 11/05/2023

# **ÍNDEX**

[**Introducció 3**](#introducció)

[**Exercicis 4**](#exercicis)

[**Conclusions 19**](#conclusions)

[**Bibliografia 19**](#bibliografia)

# **Introducció**

En aquesta pràctica aprendrem instal·lar una instància EC2, configurar
els permisos de seguretat per als ports HTTP i HTTPS, crear un
sub-domini a DuckDNS, instal·lar Drupal i solucionar problemes
relacionats amb la configuració. També tocarem temes com l\'enllaç
simbòlic i el protocol HTTPS i com fer un atack sniffing...


![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/1.png)

# 

# **Exercicis**

1.  **Instal·lar una instància EC2 anomenada webSegura ubuntu server (però es pot triar la que vulgeu)**

2.  **Assignar el security group per a que permeti el trànsit de dades pels ports HTTP i HTTPS**

> Una vegada configurat el AWS Academy i activat, ens dirigim a la
> següent ruta, per tal d'instal·lar una instància EC2, amb una imatge
> **Ubuntu Server**:
>
> Premem sobre Lanzar instancia, per tal de crear una instància, i li
> afegim el nom de "**webSegura**".
>
> Seguidament com a S.O, elegim **Ubuntu**, de tipus **Ubuntu Server 22.04 TLS**, amb una arquitectura de 64 bits
>
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/2.png)
>
> El cos de la instància agafo en el meu cas la tipus **micro**, que
> conté 1 CPU amb 1GB de RAM, però hem de pensar que quan més gran sigui
> més consumeix el nostre crèdit. En quant a les claus, agafem una que
> ja teniem, que la utilitzarem per el nostre Putty, ha d'estar en
> format RSA, i amb extensió .pem
>
>![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/3.png)
>
> Configurem la xarxa, i creem un nou Security group, de manera que
> farem que permetí el tràfic tant per **SSH**, per **HTTP** com per
> **HTTP**, que el utilitzarem posteriorment
>
![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/4.png)
>
> En quant al emmagatzematge li fiquem 8GB, i I la nostre instància ja
> s'hauria creat correctament:
>
>![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/5.png)

3.  **Assignar-l\'hi una ip elàstica XX.XX.XX.XX**

> Ens anem a l'apartat de **Dirreccions IP elàstiques \> Assignar la dirrecció IP elàstica,** per tal d\'assignar-ne una:
>
>![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/6.png)
>
> Quan ens la genera, ara hem de asociar-la a una instància, i és allò
> que elegim la nostra instància:
>
![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/7.png)
>
> Tal com es veu s'ha associat correctament la ip elástica a la
> instància **webSegura:**
>
![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/8.png)
>
![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/9.png)

4.  **Crear un subdomini a duckdns amb el teu correu de l'itb el nom del teu domini ha de ser el teu nom rafaelcuestas.duckdns.org**

> Per crear el subdomini a duckdns, amb el nostre correu del itb, primer
> hem de iniciar sessió a
> duckdns: 
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/10.png) 

> Ara, en l'apartat de **dominis** quan
> accedim, hem de ficar **ahmedbelhadi,** que aquest sera el nostre subdomini: **http://ahmedbelhadi.duckdns.org/**
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/11.png)

> Tal com es veu, ens surt un missatge que el domini s'ha afegit al nostre compte:![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/12.png)

> Ens a generat una **IP** random que ell  a escollit:![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/13.png)

5.  **Instal·la el drupal seguint les instruccions https://comoinstalar.me/como-instalar-drupal-en-ubuntu-20-04-lts/**

> Primer, per instal·lar el drupal hem d'instal·lar, LAMP (linux,
> apache, mysql, php) i procedim a fer-ho executant la següent comanda:
>
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/14.png)![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/15.png)

> 
> Ara instal·lem MySQL, hi ho farem des de la terminal mitjançant wget partint que hem de reedireccionar l'enllaç on està el MySQL, en el navegador.
> 
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/16.png)

> Instal·lem altres paquets necessaris\...
>![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/17.png)

> Elegirem que el volem en format Server tal com està el nostre
> Ubuntu![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/18.png) 
> 
> Elegim la versió del mysql
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/19.png)
> 
> Per últim faltaria instal·lar el mysql-server en el nostre Ubuntui assignar-li una contrasenya a root, en mode encryptat
>
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/20.png)![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/21.png)
![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/22.png)![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/23.png)Habilitem el nostre mysql i veiem el estat ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/24.png)

> Ara si processem a instalar el drupal, mitançant wget per terminal:
![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/25.png)
>
> Creem una carpeta que es alla on el descomprimirem el paquet instal·lat amb el tar![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/26.png)
>
> Creem un link simbòlic anomenat drupal, appuntant al directori **drupal-10.0.9,** canviem el propietari, i com també els permisos ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/27.png)
>
> Activem aquells mòduls que no s'activen per defecte a apache
>
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/28.png)
>
> Ara afegirem a l'arxiu de configuració nou que creem aquest contingut
> que mostrem per imatge per tal que és pugui navegar per el navegador a
> partir del
> alias:![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/29.png)

> També hem de copia l'arxiu de
> configuració predeterminat a un nou arxiu de configuració:
>
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/30.png)


> Li donem permissos i tal com es veu amb
> el **ls** podem veure amb s'han aplicat els
> canvis:![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/31.png)


> Habilitar la configuración del drupal i
> reiniciar el servei d'Apache2, per veure si el estat està actiu i que
> tot funciona:
>
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/32.png)
>
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/33.png)
>
> Iniciem sessió en el nostre **mysql,** creem una base de dades, un nou
> usuari **drupal,** i li donem privilegis de manera que pugui manegar
> per la base de
> dades![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/34.png)![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/35.png)

> Tornem a reiniciar el servei d'Apache i tal com es veu, l'estat està actiu funcionant
> correctament:![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/36.png)

> Ens dirigim al navegador, per tal d\'instal·lar el drupal via web, i elegim l'idioma
> (**Español**)![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/37.png)

> Ara elegim el perfil d'instal·lació, en el nostre cas elegim el per defecte el
> **estàndard**![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/38.png)
>
> Connectem la base de dades amb les nostres creedencials:
>
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/39.png)
>
> Aquí podem veure com s'està instal·lant el
> drupal:![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/40.png)
>
> Al final de l'instal·lació ens mostra que s'ha instal·lat els arxiu de
> traduccions![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/41.png)


> Configurem la nostra pàgina posant el nom que ha de tenir (**Drupal Ahmed**), també hem de posar el nostre email per vincular de manera que s'envï la informació per
> allà![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/42.png)
>
> Fiquem el usuari i password que ha de tenir per accedir a la pàgina,
> fiquem un e-mail, i com a informació addient fiquem el país i la zona
> horària (**Madrid**)
>
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/43.png)
>
> Si accedim amb la ip elàstica al drupal podem veure que ens dona la
> benvinguda:
>
> ![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/44.png)

6.  **Redireccionar el nom del teu domini a la ip elàstica de la teva instància EC2 comprova la propagació del dns amb https://dnschecker.org/**

> Per reedireccionar el nom del domini a la ip elàstica, ens reedirigim
> al **duckdns,** allà fiquem la ip elàstica, actualitzem la **ip**,
> prement el botó taronja que es troba al
> costat![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/45.png)
>
> Ara si anem a
> **https://dnschecker.org/**, fiquem el nostre domini, veiem la IP elàstica al costat de cada país
> de servidor DNS, bàsicament s'ha propagat pel
> món![Texto Descripción generada
automáticamente](https://github.com/ahmedwaix/Practica-05/blob/main/imagenes/46.png)

7.  **Comprovar que la teva pàgina web està accessible a través del teu domini**

> Per comprovar que la pàgina web és accesible per el meu domini fiquem:
> [[https://ahmedbelhadi.duckdns.org/drupal/]{.underline}](https://ahmedbelhadi.duckdns.org/drupal/),
> i veiem ens a donat la benvinguda
>
> ![](./images/media/image16.png){width="6.267716535433071in"
> height="3.125in"}

8.  **Comprobar que es pot accedeir al CMS mitjançant HTTPs i que el certificat és vàlid**

> La certificació la fem mitjançant certbot, i és per allò que
> instal·lem els següent paquet **snapd (**dimoni**)**
>
> ![](./images/media/image10.png){width="6.267716535433071in"
> height="1.7222222222222223in"}
>
> Fem un enllaç simbòlic **certbot,** al directori /usr/bin que apunta a
> /snap/bin/certbotlace simbólico del certbot, permetent accedir al
> programa Certbot utilizat per la gestió de certificats SSL/TLS, a
> partit de /usr/bin/certbot.
>
> ![](./images/media/image7.png){width="6.267716535433071in"
> height="0.25in"}
>
> Ara, ja podriem executar el programa **certbot,** utilitzant el plugin
> d'Apache, i així configurant de manera automàtica el certificat
> SSL/TLS
>
> ![](./images/media/image31.png){width="6.270833333333333in"
> height="4.88239501312336in"}![](./images/media/image8.png){width="6.267716535433071in"
> height="1.8194444444444444in"}Tal com es veu si reiniciem la pàgina
> veiem que s'està utilitzant la certificació que acabem de crear
> mitjançant el certbot:
>
> ![](./images/media/image9.png){width="6.267716535433071in"
> height="1.8055555555555556in"}

9.  **Realitza un atac de sniffing per al wordpress d'un company accedint a la part privada del gestor de continguts demostrant que quan s'accedeix mitjançant http es pot capturar l'user i el password i si es fa accedint amb https no se és vulnerable a aquest atac.**

> Video d'atac sniffing per wordpress accedint a la part privada del
> gestor de continguts per HTTP:
> [[https://youtu.be/n7SrVYy8X5A]{.underline}](https://youtu.be/n7SrVYy8X5A)
>
> *Wireshark pot capturar tot el trànsit de xarxa, les sol·licituds i
> respostes d'HTTP, tal com es veu en el video el nom d'usuari i el
> password són capturats , representant un risc a la seguretat, ja que
> qualsevol persona que estigui capturant el trànsit de xarxa podrà
> veure i després utilitzar aquestes credencials per accedir al lloc.*
>
> Video d'atac sniffing per wordpress accedint a la part privada del
> gestor de continguts per HTTPS:
> [[https://youtu.be/0IsH9kMb2Wo]{.underline}](https://youtu.be/0IsH9kMb2Wo)
>
> *Wireshark no pot capturar directament el contingut del trànsit
> xifrat, ja que HTTPS utilitza xifratge SSL/TLS per protegir les
> comunicacions entre el navegador i el servidor, de manera que el
> trànsit xifrat no es pot llegir ni interpretar sense la clau de
> xifratge adequat. En el vídeo és veu que pot capturar el trànsit, però
> les dades estan xifrades i no son llegibles, de manera que qualsevol
> persona no podra visualitzar ni obtenir les credencials d\'accés al
> lloc.*

# **Conclusions**

En general, vaig gaudir molt i també he après molt configurant i
administrant Drupal (sistema de gestió de continguts multipropósit).

# **Bibliografia**

-   [[https://comoinstalar.me/como-instalar-drupal-en-ubuntu-20-04-lts/]{.underline}](https://comoinstalar.me/como-instalar-drupal-en-ubuntu-20-04-lts/)

-   [[https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-20-04-es]{.underline}](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-20-04-es)

-   [[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04-es]{.underline}](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04-es)
