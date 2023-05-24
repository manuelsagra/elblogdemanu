---
title: "Test"
description: "Esto es una prueba"
date: 2023-03-01T13:33:42+01:00
draft: true
---
## Elementos básicos

Este es un párrafo con **negritas** y también _cursivas_. E incluso, un "_Título de juego_". También puedo poner [un enlace](https://google.es/) y otro [con un título](https://google.es/ "Jajaja, no leas esto"). Voy a ~~tachar un texto~~.

### Emojis

Unos cuantos de [la lista](https://gist.github.com/rxaviers/7360908):

:joy: :smile: :confused: :cry: :yum: :+1:

### Otros elementos

Este es otro párrafo y luego viene un blockquote múltiple.

> Dorothy followed her through **many** of the beautiful rooms in her castle.
>
> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

Una tabla:

| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |
| Another   | Tasasa        | asasde      |

Otra tabla:

| Syntax | Description | Test Text |
| --- | --- | --- |
| Header | Title | Here's this |
| Paragraph | Text | And more |
| Another | Tasasa | asasde |

### Imágenes y vídeos

{{< yt UcuBdh3YU4o >}}

{{< tw manuelsagra 1630304735080087552 >}}

#### Listas

Ordenada:

1. First item
2. Second item
3. Third item
4. Fourth item

---

Desordenada:

* First item
* Second item
* Third item
* Fourth item

Tareas:

- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

##### Código y movidas

Si pulsas las teclas <kbd>Control</kbd> y <kbd>Alt</kbd> esto es <mark>importante porque sí</mark>. Luego en la consola teclea `bash` y saldrá algo así:

{{< highlight html >}}
<section id="main">
  <div>
   <h1 id="title">{{ .Title }}</h1>
    {{ range .Pages }}
        {{ .Render "summary"}}
    {{ end }}
  </div>
</section>
{{< /highlight >}}

```html
<html>
    <head>
        <title>Hola</title>
    </head>
</html>
```

Y otro bloque sin identación con formato[^1]:

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

Y shell[^bignote]:

```bash
$ chmod a+x First.sh
$ ./First.sh
```

Y C:

```bash
#include <stdio.h>
int main() {
   int year;
   printf("Enter a year: ");
   scanf("%d", &year);

   // leap year if perfectly divisible by 400
   if (year % 400 == 0) {
      printf("%d is a leap year.", year);
   }
   // not a leap year if divisible by 100
   // but not divisible by 400
   else if (year % 100 == 0) {
      printf("%d is not a leap year.", year);
   }
   // leap year if not divisible by 100
   // but divisible by 4
   else if (year % 4 == 0) {
      printf("%d is a leap year.", year);
   }
   // all other years are not leap years
   else {
      printf("%d is not a leap year.", year);
   }

   return 0;
}
```

###### Cabecera de sexto orden

Lista de definición:

First Term
: This is the definition of the first term.

Second Term
: This is one definition of the second term.
: This is another definition of the second term.

Y otro párrafo. Después vienen las notas a pié de página:


[^1]: This is the first footnote.

[^bignote]: Here's one with multiple paragraphs and code.

    Indent paragraphs to include them in the footnote.

    `{ my code }`

    Add as many paragraphs as you like.