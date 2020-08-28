# Mallas Curriculares

Este repositorio alberga la plantilla de las malla de la carrera [Ingeniería Civil 
Informática](http://icinf.ulagos.cl/) de la [Universidad de Los Lagos](https://www.ulagos.cl/) 
en formato [HTML](https://html.com/) para su plataforma de gestión de contenido en
[Joomla!](https://www.joomla.org/) para los años
[2013](http://icinf.ulagos.cl/index.php/carrera/2013/malla-curricular-2013) y
[2020](http://icinf.ulagos.cl/index.php/carrera/2020/malla-curricular-2020).

## Descripción

La malla se compone de una tabla interactiva que muestra las *previaturas* y *continuidades* de 
las asignaturas al hacer click en sobre el curso.

Al hacer click en una asignatura se destacará en color rojo, sus *previaturas* en amarillo y sus
*continuidades* en verde.

## Dependencias

- [AniJS](https://anijs.github.io/)

## Edición

Para editar la plantilla se debe reconocer cuantos ramos/asignaturas tiene cada semestre por 
separado (en caso de tener una diferencia en la cantidad de ramos en un mismo año basta con 
extender una de las columnas de manera horizontal).

Cada asignatura tiene por defecto dos tags de anijs que limpian y marcan el contenido:
``` w
data-anijs="if:click,do:$removeClass Rojo Verde Amarillo,to:.Ramo; <--Limpia las selecciones
            if:click,do:$toggleClass Rojo,to:target; <--Marca el tag en rojo
```

Adicional a esto las *previaturas* se marcan talque:
```html
data-anijs="<--codigo generico-->;
            if:click,do:%toggleClass Amarillo,to:.prevAsignatura">
```

Similar a lo anterior para las *continuidades*:
```html
data-anijs="<--codigo generico-->;
            if:click,do:%toggleClass Verde,to:.contAsignatura;
            <--codigo generico-->">
```

> Ejemplo:
> ```html
> <td class="malla Ramo prevAnteproyectoDeTitulo prevPracticaProfesional contIntroduccionAlCalculo contIntroduccionALaFisica prevElectromagnetismo"
>     data-anijs="if:click,do:$removeClass Rojo Verde Amarillo,to:.Ramo;
>                 if:click,do:$toggleClass Rojo,to:target;
>                 if:click,do:$toggleClass Verde,to:.contFisicaNewtoniana;
>                 if:click,do:$toggleClass Amarillo,to:.prevFisicaNewtoniana">
>     Física Newtoniana
> </td>
> ```

Los estilos predefinidos para las tablas están en el tag `<style></style>` dado que
[Joomla!](https://www.joomla.org/) aplica y borra este tag al guardar cambios.

## Guardar cambios en Joomla!

Una vez logeado entraremos a la sección **Artículos** y buscamos como palabra clave *malla*, luego
seleccionamos la **Malla Curricular** que deseemos editar. Al final de la página en la sección de
edición de texto buscamos la pestaña **Code**, en esta pestaña borraremos y pegaremos el código
que hayamos editado de `template.html`.

> ¡¡¡No se debe guardar al salir si no haz realizado cambios, esto rompe el estilo css de la tabla!!!

Cualquier duda dejar un Issue.
