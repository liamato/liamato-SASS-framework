#liamato SASS framework

**_liamato SASS framework_** ha estado diseñado con el proposito de **crear una base** para los estilos de proyectos.

**Sin estilos predefinidos** ni classes muy generales, **no pretende ser un framework de diseño** sino un framework de ayuda para diseñar más ágilmente.

###Organización

```
    css/
        main.css
        main.css.map
    
    core/
        normalize/
            _normalize.scss
            _normalize-variables.scss
        _maps.scss
        _mixins.scss
        _variables.scss
        main.scss
    
    doc/
        _doc.scss
    
    fonts/
        socialico/
            FFF_EULA_lisence.pdf
            socialico_plus-webfont.eot
            socialico_plus-webfont.svg
            socialico_plus-webfont.ttf
            socialico_plus-webfont.woff
            socialico-webfont.eot
            socialico-webfont.svg
            socialico-webfont.ttf
            socialico-webfont.woff
    
    lib/
        _glyphicons.scss
        _placeholders.scss
        
    preview/
        index.html
        preview.scss
        preview.css
        preview.css.map
        _structure.scss
        config.rb
    
    config.rb
```

###Auto procesamiento a css
####SASS
    $ cd tu_proyecto/liamato-SASS-framework
    $ sass core/main.scss:css/main.css --sourcemap --watch
####Compass
En este caso devemos configurar el archivo ```config.rb``` de la carpeta principal (puede dar problemas)

    $ cd tu_proyecto/liamato-SASS-framework
    $ compass watch
    
###Manual
[Explicacion](man.md) de todos los mixins, variables, maps, classes, etc...

###Configuración

####core/[_maps.scss](core/maps.scss)
Definimos los colores principales de la pagina, las fuentes y los tamaños de estas.

Ademas tambien estan definidos los colores de las principales redes sociales.



####core/[_variables.scss](core/_variables.scss)
Definimos los breakpoints para las ```@media``` querys y las rutas para las imagenes que vamos a utilizar en el css.


####[doc/](doc/)
En esta carpeta devemos ponet todos los archivos sass/scss

####[_doc.scss](doc/_doc.scss)
Este archivo es en el que se deve poner todo el sass especifico para estructurar y formar la paguina
Es aconsejable que pongas en diferentes archivos el codigo y que los importes con ```@import``` en el documento _doc.scss al igual que si le quieres añadir algun otro framework

###Licencia
<a rel="license" href="http://creativecommons.org/licenses/by-nd/4.0/deed.es_ES"><img alt="Licencia Creative Commons" style="border-width:0" src="http://i.creativecommons.org/l/by-nd/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Text" property="dct:title" rel="dct:type">liamato SASS framework</span> por <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/liamato/" property="cc:attributionName" rel="cc:attributionURL">liamato</a> se distribuye bajo una <a rel="license" href="http://creativecommons.org/licenses/by-nd/4.0/deed.es_ES">Licencia Creative Commons Atribución-SinDerivar 4.0 Internacional</a>.<br />


Inspirado en [Wakkos SASS framework](https://github.com/Wakkos/Wakkos-CSS-Framework)