<a href="https://www.haskell.org">
  <img src="http://fieldstrength.org/images/haskell-logo.svg" alt="Haskell" align="right"  width="120" />
</a>

# Haskell sin mitos

Haskell es recursivo y, por tanto, es ineficiente. Haskell es complicado. Haskell es un lenguaje de programación académico y no está listo para producción. ¿Te suena familiar? Estos son algunos de los mitos menos estrafalarios que acompañan a Haskell.

En esta charla repasaremos algunas de las ideas equivocadas con más resonancia. No sólo descubriremos la verdad detrás de estos mitos, sino que también discutiremos las ventajas y los retos de trabajar con Haskell.

## Datos de la charla

Tema presentado el 26 de octubre de 2016, en [Quito Lambda](https://www.meetup.com/es/Quito-Lambda-Meetup/events/234492889/). La presentación está inspirada en la charla "Haskell is Not For Production and Other Tales" de [Katie Oats](http://www.codemiller.com/talks/).

Revisa la presentación completa [aquí](https://github.com/flandrade/haskell-sin-mitos/blob/master/slides/haskell-sin-mitos.pdf).

## Mitos 

- Haskell es académico. 
- Haskell no es utilizado en la industria. 
- Haskell es difícil. 
  - Haskell es difícil de contratar. 
  - Elitismo.
  - Documentación. 
- Haskell no está listo para producción.
- Haskell es la solución a todos los problemas. 

## Temas
- ¿Por qué Haskell?
- El legado de Haskell. 

## ¿Por qué Haskell?

### Razonar sobre el código.
- Tipificado estáticamente:

```haskell 
userExist :: Int -> Int -> Bool
userExist userId groupId = … 
```

```haskell 
newtype UserId = UserId  Int
newtype GroupId = GroupId  Int

userExist :: UserId -> GroupId -> Bool
userExist userId groupId = … 
```

### Pureza
- Evitar errores:  

En JavaScript podemos crear funciones que no cubren todos los casos:

```js
function foo (num) {
  if (num>10) {
    return “JavaScript no es tan malo”
  } 
}
``` 

Esto provocará un error para un caso no cubierto:

```js
console.log(foo(1).toUpperCase())
``` 

- Seguridad:

En Haskell tenemos el tipo `Maybe`: 

```haskell
data Maybe = Just a | Nothing
```

Para el ejemplo anterior:

```haskell
foo :: Integer -> Maybe String
foo num = 
  if num > 10 
    then “Haskell es seguro”
    else Nothing
```

```haskell 
bar num = 
  case foo num of 
    Just texto -> 
       String.toUpper texto 
    Nothing -> “Ouch”
```

Se debe cubrir todos los casos: 

```haskell 
bar num = 
  case foo num of 
    Just texto -> 
       String.toUpper texto 
```

Error:

```
Pattern match(es) are non-exhaustive
In a case alternative: Patterns not matched: Nothing
```

## Licencia 

MIT
