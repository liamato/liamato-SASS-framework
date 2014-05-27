#liamato SASS framework - Manual

##Archivos
* [core/](#core)
 * [main.scss](#mainscss)
 * [\_maps.scss](#mapsscss)
 * [\_mixins.scss](#mixinsscss)
 * [\_variables.scss](#variablesscss)
 * [normalize/](#normalize)
      * [\_normalize.scss](#normalizescss)
      * [\_normalize-variables.scss](#_normalize-variablesscss)
* [css/](#css)
 * [main.css](#maincss)
 * [main.css.map](#maincssmap)
* [doc/](#doc)
 * [\_doc.scss](#docscss)
* [fonts/](#fonts)
 * [Socialico](#socialico)
      * FFF\_EULA\_lisence.pdf
      * socialico\_plus-webfont.eot
      * socialico\_plus-webfont.svg
      * socialico\_plus-webfont.ttf
      * socialico\_plus-webfont.woff
      * socialico-webfont.eot
      * socialico-webfont.svg
      * socialico-webfont.ttf
      * socialico-webfont.woff
* [lib/](#lib)
 * [\_glyphicons.scss](#glyphiconsscss)
 * [\_placeholders.scss](#placeholdersscss)
* [preview/](#preview)
 * [index.html](#indexhtml)
 * [\_structure.scss](#structurescss)
 * [preview.scss](#previewscss)
 * [preview.css](#previewcss)
 * [preview.css.map](#previewcssmap)
 * [config.rb - preview](#configrb-preview)
* [config.rb - main](#configrb-main)
* [man.md](#manmd)
* [readme.md](#readmemd)


##[core/](core)

En esta carpeta etasn todos los archivos basicos y necesarios del framework

###[main.scss](core/main.scss)
- - -

Este es el archivo donde estanincluidos todos los modulos del framework

Si no quieres alguno en tu `css` es tan facil como comentar la linea con `//` antes del `@import`


###[maps.scss](core/_maps.scss)
- - -
Este es un archivo en el que se configuran los colores, fuentes, tamaño de las mismas y donde ademas tambien estan definidos los colores corporativos de las pricipales redes sociales

Para obtener los datos de `maps.scss` utilizamos diferentes mixins, como por ejemplo:

__Para el tipo de fuente:__
```scss
@include font(default);
```

__Para las medidas de las fuentes:__
```scss
@include font-size(10, p);
```

__Para los colores de las redes sociales:__
```scss
@include social(fb);
```

Otra forma de obtener los datos es con:

```scss
map-get($colors, First)
```

###[variables.scss](core/_variables.scss)
- - -
En este archivo  definimos los breakpoints para las `@media` queries y algunas rutas.

__Tip:__ Es aconsejable poner los breakpoints en `em` para que no le afecte el zoom, aun que se pueden poner en `px`

Las variables de rutas sirven para para poner mas faclimente las imagenes

Si por ejemplo tenemos esto:

**_variables.scss_**

```scss
$img-dir: "../../img/";
```

Es tan sencillo como poner:

```scss
background: url(#{$img-dir}fondo.png);
```

###[mixins.scss](core/_mixins.scss)
- - -
En este archivo estan todos los mixins a utilizar del framework

Se utiliza `@include` y el nombre del mixin para incluirlo

**_font-size($fs, $mf)_**

Este mixn se utiliza para conseguir el font size en em

Utiliza 2 atributos:

* $fs: 
 * **Requerido**
 * Se le pone la medida en px pero solo el numero
 * Para `16px` tiene que ser `16`
* $mf:
 * **Opcional**
 * Se le pone la "key" del mapa `$font-size` de `_maps.scss`
 * Por ejemplo `default`
 
Y quedaria `@include font-size(16, default);`

**_font($fnt)_**

Este mixin se utiliza para conseguir algun tipo de letra definido en el mapa `$font-map` de `_maps.scss`

Utiliza 1 atributo:

* $fnt:
 * **Requerido**
 * Se pone la "key" del mapa `$font-map` de `_maps.scss`
 * Por ejemplo `code`

Y quedaria `@include font(code);`

**_social($social)_**

Este mixin se utiliza para obtener el color de letra con el color corporativo de las principales redes sociales

Utiliza 1 atributo:

* $social:
 * **Requerido**
 * Se pone la "key" de la red social deseada del mapa `$colors-social` de `_maps.scss`
 * Por ejemplo `tw`

Y quedaria `@include social(tw);`

**_media($m-feature1, $m-feature1-val, $m-type, $m-feature2, $m-feature2-val)_**

Este mixin se utiliza para crear `@media` queries

Utiliza 5 atributos:

* $m-fetaure1:
 * **Requerido**
 * Se pone la caracteristica en la cual es evaluada la pantalla
 * Por defecto es `min-width` 
 * Por ejemplo `min-width`
* $m-feature1-val:
 * **Requerido**
 * Se pone el valor de la caracteristica anterior
 * Por ejemplo `$bp1`
* $m-type:
 * **Opcional**
 * Se pone el tipo de media al que va dirigido
 * Por ejemplo `all`
* $m-feature2:
 * **Opcional**
 * Se pone la segunda caracteristica por la cual es evaluada la pantalla
 * Por defecto es `max-width`
 * Por ejemplo `max-width`
* $m-feature2-val:
 * **Opcional**
 * Se pone el valor de la caracteristica anterior
 * Por ejemplo `$bp2`

Las posibilidades de los atributos anteriores estan en [aqui](https://developer.mozilla.org/es/docs/CSS/Media_queries#Pseudo-BNF_(para_aquellos_a_quienes_les_gustan_esas_cosas&#41;)

Aunque los mas abituales son:

* $m-feature1 & $m-feature2
 * min-width
 * max-width
 * width
* $m-feature1-val & $m-feature2-val
 * Las variables `$br` definidas en `_variables.scss`
 * Aglguna medida tanto en `px` como en `em`

Y quedaria:

* `@include media("min-width", "$bp1", "all", "max-width", $bp2);` en formato largo
* `@include media("min-width", "$bp1", "all");` en formato medio
* `@include media("min-width", "$bp1");` en formato corto


**_vendor($prop, $val)_**

Este mixin se utiliza para poner los prefijos de navegadores a las propiedades _css_

Utiliza 2 atributos:

* $prop:
 * **Requerido**
 * Se pone la propiedad `css` deseada
 * Por ejemplo `border-radius`
* $val:
 * **Requerido**
 * Se pone el valor de la propiedad `css`
 * Por ejemplo `5px`

Y quedaria `@include vendor("border-radius", 5px);`

**_g-horitzontal($startColor, $endColor)_**

Este mixin se utiliza para crear fondos con degradados horizontales

Utiliza 2 atributos:

* $startColor:
 * **Opcional**
 * Se pone el color de comienzo del degradado
 * Por ejemplo `white`
* $endColor:
 * **Opcional**
 * Se pone el color de final del degradado
 * Por ejemplo `lightgrey`

Y quedaria `@include g-horizontal("white", "lightgrey");`

**_g-vertical($startColor, $endColor)_**

Este mixin se utiliza para crear fondos con degradados verticales

Utiliza 2 atributos:

* $startColor:
 * **Opcional**
 * Se pone el color de comienzo del degradado
 * Por ejemplo `white`
* $endColor:
 * **Opcional**
 * Se pone el color de final del degradado
 * Por ejemplo `lightgrey`

Y quedaria `@include g-vertical("white", "lightgrey");`

**_g-directional($startColor, $endColor, $deg)_**

Este mixin se utiliza para crear fondos con degradados horizontales

Utiliza 3 atributos:

* $startColor:
 * **Opcional**
 * Se pone el color de comienzo del degradado
 * Por ejemplo `white`
* $endColor:
 * **Opcional**
 * Se pone el color de final del degradado
 * Por ejemplo `lightgrey`
* $deg:
 * **Opcional**
 * Se pone el angulo del degrado
 * Por ejemplo `135deg`

Y quedaria `@include g-directional("white", "lightgrey", 135deg);`

**_b-radius($br-width)_**

Este mixin se utiliza para hacer los bordes redondeados

Utiliza 1 atributo:

* $br-width:
 * **Requerido**
 * Se pone quanto se debe redondear el borde
 * Por ejemplo `5px`

Y quedaria `@include b-radius(5px);`

**_t-shadow($ts-x, $ts-y, $ts-blur, $ts-color)_**

Este mixin se utiliza para poner sombras al texto

* $ts-x:
 * **Requerido**
 * Se pone la posicion en `x` de la sombra
 * Por ejemplo `3px`
* $ts-y:
 * **Requerido**
 * Se pone la posicion en `y` de la sombra
 * Por ejemplo `3px`
* $ts-blur:
 * **Opcional**
 * Se pone la cantidad de difuminado que queremos
 * Por ejemplo `1px`
* $ts-color:
 * **Opcional**
 * Se pone el color de la sombra
 * Por ejemplo `#000`
* $ts-inset
 * **Opcinal**
 * Se pone si se quiere que sea inset
 * Por ejemplo `inset`

Y quedaria `@include t-shadow(3px, 3px, 1px, #000, inset);`

**_b-shadow($bs-x, $bs-y, $bs-blur, $bs-color)_**

Este mixin se utiliza para poner sombras a los elementos

* $bs-x:
 * **Requerido**
 * Se pone la posicion en `x` de la sombra
 * Por ejemplo `3px`
* $bs-y:
 * **Requerido**
 * Se pone la posicion en `y` de la sombra
 * Por ejemplo `3px`
* $bs-blur:
 * **Opcional**
 * Se pone la cantidad de difuminado que queremos
 * Por ejemplo `1px`
* $bs-color:
 * **Opcional**
 * Se pone el color de la sombra
 * Por ejemplo `#000`
* $bs-inset
 * **Opcinal**
 * Se pone si se quiere que sea inset
 * Por ejemplo `inset`

Y quedaria `@include b-shadow(3px, 3px, 1px, #000, inset);`

**_transition($transi-targ, $transi-time, $transi)_**

Este mixin se utiliza para crear transiciones

* $transi-targ:
 * **Opcional**
 * Se pone la propiedad objetivo de la transicion
 * Por ejemplo `all`
* $transi-time:
 * **Opcional**
 * Se pone el tiempo de la transicion
 * Por ejemplo `2s`
* $transi:
 * **Opcional**
 * Se pone el tipo de transicion
 * Por ejemplo `erase`

Y quedaria `@include transition("all", 2s, "erase");`

**_transform($transf-arg)_**

Este mixin se utiliza para crear transformaciones

* $transf-arg:
 * **Requrido**
 * Se pone la propiedad como se transforma
 * Por ejemplo `rotate(10deg);`

Y quedaria `@include transform("rotate(10deg);");`

**_resize($direction)_**

Este mixin se utiliza para redimensionar un elemento

* $direction:
 * **Opcional**
 * Se pone la direccion hacia donde se redimensiona
 * Por ejemplo `both`

Y quedaria `@include resize("both");`

**_rotate($deg)_**

Este mixin se utiliza para rotar un elemento

* $deg:
 * **Requerido**
 * Se pone los grados en _deg_ de inclinacion
 * Por ejemplo `10deg`

Y quedaria `@include rotate(10deg);`

**_scale($ratio)_**

Este mixin se utiliza para escalar un elemento

* $ratio:
 * **Requerido**
 * Se pone el ratio en que se escala el elemento
 * Por ejemplo `1.1`

Y quedaria `@include scale(1.1);`

**_skew($x: 0, $y: 0)_**

Este mixin se utiliza para poner de forma oblicua un elemento

* $x:
 * **Opcional**
 * Se ponen los grados del eje `x`
 * Por ejemplo `20deg`
* $y:
 * **Opcional**
 * Se ponen los grados del eje `y`
 * Por ejemplo `20deg`

Y quedaria `@include skew(20deg, 20deg);`

**_translate($x, $y)_**

Este mixin se utiliza para mover un elemento

* $x:
 * **Opcional**
 * Se ponen los _px_ del eje `x`
 * Por ejemplo `20px`
* $y:
 * **Opcional**
 * Se ponen los _px_ del eje `y`
 * Por ejemplo `20px`

Y quedaria `@include translate(20px, 20px);`

**_translate3d($x: 0, $y: 0, $z: 0)_**

Este mixin se utiliza para mover un elemento en 3D

* $x:
 * **Opcional**
 * Se ponen los _px_ del eje `x`
 * Por ejemplo `20px
* $y:
 * **Opcional**
 * Se ponen los _px_ del eje `y`
 * Por ejemplo `20px`
* $z:
 * **Opcional**
 * Se ponen los _px_ del eje `z`
 * Por ejemplo `20px`

Y quedaria `@include translate(20px, 20px, 20px);`

**_box-sizing($box-size)_**

Este mixin se utiliza para que la medida del elemento se cuente hasta el borde, el padding o solo el contenido

* $box-size:
 * **Opcional**
 * Se pone la medida hasta donde se mide el elemeto
 * Por ejemplo:
   * `border-box` Hasta el borde (default)
   * `padding-box` Hasta el padding
   * `content-box` Solo el contenido


###[normalize/](core/normalize)

---
En esta carpeta esta una variacion del framework [normalize.css](http://necolas.github.io/normalize.css/) y las dependencias de la modificacion

####[normalize.scss](core/normalize/_normalize.scss)
- - -
Este es el archivo utilizado para aplicar los estilos definidos en `maps.scss` y normalizar algunas caracteristicas de css para el "cross browser compatibility"

####[normalize-variables.scss](core/normalize/_normalize-variables.scss)
- - -
En este archivo estan definidos los "default" de las variables utilizadas en `normalize.scss` y la configuracion para que estas cojan los datos des de `maps.scss`

##[css/](css)


En esta carpeta se compila el archivo `css` i el `css.map` tanto si se utiliza compas con el archivo `config.rb` como sass con el commando de [aqui](readme.md#Auto-procesamiento-a-css)

###[main.css](css/main.css)
- - -

Este es el archivo de estilos con todos los archivos `.scss` minificados en uno, el que se deve linkar en el _HTML_ con

```
    <link href="tu-ruta/liamato-SASS-framework/css/main.css" media="all" rel="stylesheet" type="text/css">
```

###[main.map.css](css/main.map.css)
- - -

Este archivo se genera solo y sirve para poder trabajar con `SASS` en las _devtools_ como se muesta [aqui](http://www.mozilla-hispano.org/editando-sass-y-less-con-herramientas-de-desarrollo/)

##[doc/](doc)

Esta carpeta es para poner todos los archivos `.scss` de la paguina

###[doc.scss](doc/_doc.scss)
- - -

En este archivo se deve poner todo el `scss` de la paguina

**Tip:** Pon el codigo repartido en archivos i importalos con `@import "archivo.scss";` para que te sea mas facil organizar-te

##[fonts/](fonts)

En esta carpeta estan todas las fuentes del framework

##[lib/](lib)

En esta carpeta estan los componentes opcionales del framework

###[glyphicons.scss](lib/_glyphicons.scss)
- - -

En este archivo estan los iconos de las redes sociales de `$colors-social` en forma de classe

Por ejemplo `.github`

Y tambien aulgunas otras classes como por ejemplo `.`pg-wraper`

Para ver todes la classes [aqui](index.html)

###[placeholders.scss](lib/_placeholders.scss)
- - -

En este archivo estan los plceholders

* %clearfix
* %vcenter

Para insertar un placeholder se utiliza `@extend %clearfix;`

##[preview/](preview)

En esta carpeta esta el preview de los estilos definidos en `_maps.scss` y `_variables.scss`

Para que recoja los edtilos de `_maps.scss` y `_variables.scss` se deve compilar el `css` del preview cada vez que se modifican los archivos `_maps.scss` y `_variables.scss`

####SASS
    $ cd tu_proyecto/liamato-SASS-framework/preview
    $ sass preview.scss:preview.css --sourcemap --watch
####Compass
En este caso devemos configurar el archivo ```config.rb``` de la carpeta principal (puede dar problemas)

    $ cd tu_proyecto/liamato-SASS-framework/preview
    $ compass watch

###[index.html](preview/index.html)
- - -

Este es el archivo que se ve al entrar a [preview/](preview)

###[\_structure.scss](preview/_structure.scss)
- - -

En este archivo estan los estilos y la estructura del preview

###[preview.scss](preview/preview.scss)
- - -

Gracias a este archivo se recojen los estilos de `_maps.scss`, `_variables.scss` y `_structure.scss` para formar el archivo `preview.css` y `preview.css.map`

###[preview.css](preview/preview.css)
- - -

El conjunto de estilos para el preview

###[preview.css.map](preview/preview.css.map)
- - -

Es el archivo que vincula el `css` con el `scss`

###[config.rb - preview](preview/config.rb)
- - -

Es la configuracion de _compass_ para compilar el `css` del preview

##[config.rb - main](config.rb)

Es la configuracion de _compass_ para compilar el `css`

##[man.md](man.md)

Este archivo

##[readme.md](readme.md)

Archivo readme de **liamato SASS framework**


##Licencia

[![Licencia Creative Commons](http://i.creativecommons.org/l/by-nd/4.0/88x31.png "Licencia Creative Commons")](http://creativecommons.org/licenses/by-nd/4.0/deed.es_ES)

liamato SASS framework por [liamto](https://github.com/liamato) se distribuye bajo una [Licencia Creative Commons Atribución-SinDerivar 4.0 Internacional](http://creativecommons.org/licenses/by-nd/4.0/deed.es_ES)
