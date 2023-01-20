# Hacking Ético y Ciberseguridad

### Seguimiento del curso "Curso completo de Hacking Ético y Ciberseguridad" [curso de Udemy](https://www.udemy.com/course/curso-completo-de-hacking-etico-y-ciberseguridad/).

<br>

### Definicion del alcance del hacking etico

- Antes de realizar ninguna acción, discutir con el cliente las tareas
  que llevará a cabo el analista durante el Hacking Ético, así como los
  roles y responsabilidades de ambos

- Asegurar mediante contrato firmado que las acciones que se llevan
  a cabo son en representación del cliente

- Análisis de las políticas de la organización que definen el uso que
  los usuarios hacen de los sistemas y de la infraestructura

- Procedimiento en el caso de que se localice una intrusión por un
  tercero

<br>

# Recursos

- [Repositorio donde podéis encontrar cientos de reportes de auditorías reales de diferentes empresas del sector del Hacking Ético y de la Ciberseguridad que se han ido recopilando a lo largo del tiempo](https://github.com/juliocesarfort/public-pentesting-reports).

- [(Opcion #1) Plantillas que podéis utilizar para comenzar a elaborar vuestro propio informe de Hacking Ético o auditoría de seguridad](https://pentestreports.com/templates/).

- [(Opcion #2) Plantillas que podéis utilizar para comenzar a elaborar vuestro propio informe de Hacking Ético o auditoría de seguridad](https://github.com/hmaverickadams/TCM-Security-Sample-Pentest-Report).

<br>

# Dependencias

### 1) Maquina virtual: [VMware Workstation Player](https://customerconnect.vmware.com/en/downloads/details?downloadGroup=WKST-PLAYER-1700&productId=1377&rPId=97014).

### 2) Sistema operativo (So): [Kali Linux para MVware](https://www.kali.org/get-kali/#kali-virtual-machines).

<br>

### Como ejecutar el SO desde MVware

- Descomprimimos el 7zip que descargar la pagina de Kali Linux.
- Instalamos MVware.
- Ejecutamos la opcion "Open a virtual machine".
- Seleccinamos la imagen .vmx dentro de la carpeta de Kali Linux.
- Le damos click a la opcion que nos cargo, en este caso por defecto su nombre es "kali-linux-2022.4-vmware-amd64" y precionamos el boton "Play virtual machine"

<br>

Un error comun es que salga que la board no soporte maquinas virtuales antes de iniciar el SO, deben habilidar el SVM mode (Secure Virtual Machine/Virtualization mode in AMD BIOS) dentro de la configuracion de su Bios.

<br>

# Metodologias

Las metodologías nos facilitan la realización de un
conjunto de actividades en un orden determinado y
estableciendo una prioridad adecuada para intentar
garantizar el éxito y alcanzar un objetivo final

Metodologias principales:

- [OSSTMM (Open-Source Security Testing Methodology Manual)](https://www.isecom.org/OSSTMM.3.pdf)

- [The penetration testing execution standard](http://www.pentest-standard.org/index.php/Main_Page)

- ISSAF (Information Systems Security Assessment Framework)

- OTP (OWASP Testing Project)

<br>

# Recopilacion pasiva de información

- Recopilacion de informacion sobre un objetivo determinado sin que las actividades realizadas por el analista sea minimante detectadas por dicho objectivo.

- Dificil de ralizar y a menudo propociona resultado poco concluyentes

- La manera habitual de recolecion pasiva de informacion es mediante el acceso a la informacion almacenada en lugares publicos

- Raramente se utiliza de manera individual

  <br>

En teoria es buscar la contenido indexado publico, por ejm redes sociales, pagina web, google, youtube etc...
<br>
La idea es buscar estos recursos en lugares publicos sin necesidad de penetrar el objetivo, ya que el objetivo será penetrado posteriormente.

<br>

## Hacking con buscadores: Google Hacking (Google Dork)

- Para mostrar referencias de un dominio especifico, escrbimos el comando site, seguido de dos puntos y el dominio de referencia:  
  `site:udemy.com`

- Para un tipo de archivo especifico escrbimos el comando filetype, seguido de dos puntos y el tipo de archivo:  
  `site:udemy.com filetype:pdf`

- Para una busquedad exacta usamos comillas:  
  `"index of" / "chat/logs"`

- Para buscar copias de seguridad de MySQL (MySQL dump) escribimos:  
  `filetype:sql "MySQL dump"`

- Para buscar un palabra dentro de un contenido agregamos la palabra dentro de parentesis (password), si queremos buscar multiples palabras usamos el condicional OR (|) para separar entre palabras:  
  `filetype:sql "MySQL dump" (pass|password|pws|psd)`

- `link:url` - Muestra páginas que apuntan a la definida por dicha url. La cantidad (y calidad) de los enlaces a una página determina su relevancia para los buscadores. Nota: sólo presenta aquellas páginas con pagerank 5 o más.

- `cache:url` - Se mostrará la versión de la página definida por url que Google tiene en su memoria, es decir, la copia que hizo el robot de Google la última vez que pasó por dicha página.

- `info:url` - Google presentará información sobre la página web que corresponde con la url.

- `allintitle:términos` - Restringe los resultados a aquellos que contienen los términos en el título.  
  `site:gov filetype:pdf allintitle:restricted`

- `related:url` - Google mostrará páginas similares a la que especifica la url. Nota: Es difícil entender que tipo de relación tiene en cuenta Google para mostrar dichas páginas. Muchas veces carece de utilidad.

- `allinanchor:términos` - Google restringe las búsquedas a aquellas páginas apuntadas por enlaces donde el texto contiene los términos buscados.

- `inanchor:término` - Las búsquedas se restringen a aquellas apuntadas por enlaces donde el texto contiene el término especificado. A diferencia de allinanchor se puede combinar con la búsqueda habitual.

- `allintext:términos` - Se restringen las búsquedas a los resultados que contienen los términos en el texto de la página.

- `intext:término` - Restringe los resultados a aquellos textos que contienen término en el texto. A diferencia de allintext se puede combinar con la búsqueda habitual de términos.

- `allinurl:términos` - Sólo se presentan los resultados que contienen los términos buscados en la url.

- `inurl:término` - Los resultados se restringen a aquellos que contienen término en la url. A diferencia de allinurl se puede combinar con la búsqueda habitual de términos.

  <br>

## Operadores Booleanos Google Hacking

Google hace uso de los operadores booleanos para realizar búsquedas combinadas de varios términos. Esos operadores son una serie de símbolos que Google reconoce y modifican la búsqueda realizada:

- (" ") - Busca las palabras exactas.

- (- -) Excluye una palabra de la búsqueda. (Ej: gmail -hotmail, busca páginas en las que aparezca la palabra gmail y no aparezca la palabra hotmail)

- OR (ó |) - Busca páginas que contengan un término u otro.

- (+ -) Permite incluir palabras que Google por defecto no tiene en cuenta al ser muy comunes (en español: "de", "el", "la".....). También se usa para que Google distinga acentos, diéresis y la letra ñ, que normalmente son elementos que no distingue.

- (\* -) Comodín. Utilizado para sustituir una palabra. Suele combinarse con el operador de literalidad (" ").

  <br>

## Google Hacking Database EXPLOIT DATABASE

- [Site EXPLOIT DATABASE](https://www.exploit-db.com/google-hacking-database)

 <br>

# Shodan

Shodan nos ayuda a encontrar dispositivos conectados a internet, en este caso escanea una ip y busca que los servicios que se estan ejecutando en los puertos abiertos.

- [Pagina Shodan (Requiere crear una cuenta para utilizar)](https://www.shodan.io)

- [Repositorio GitHub con consultas en Shodan para multiples dospositivos como powerbanks/webcams ..etc.](https://github.com/jakejarvis/awesome-shodan-queries/)
