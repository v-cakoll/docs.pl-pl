---
title: Pełna składnia (F#)
description: 'Różnice między pełnego i uproszczonego składnię języka programowania w języku F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: fd040a66a789bc6717fd14e6a9f28274c9e3542b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="verbose-syntax"></a>Pełna składnia

Istnieją dwie formy składni dla wielu konstrukcje w języku F #: *Pełna składnia* i *lightweight — składnia*. Pełna składnia nie jest używany jako często, ale ma tę zaletę, jest mniej wrażliwe na wcięcia. Lightweight — składnia jest krótsza i używa wcięcia sygnalizują początek i koniec konstrukcje, zamiast dodatkowe słowa kluczowe, takich jak `begin`, `end`, `in`i tak dalej. Domyślnie przyjmowana jest składnia lekkie składni. W tym temacie opisano składnię konstrukcje F #, gdy lightweight — składnia nie jest włączone. Pełna składnia jest zawsze włączony, dlatego nawet jeśli lightweight — składnia jest włączone, można nadal używać Pełna składnia dla niektórych konstrukcje. Lightweight — składnia można wyłączyć za pomocą `#light "off"` dyrektywy.


## <a name="table-of-constructs"></a>Tabela konstrukcji
W poniższej tabeli przedstawiono składnię nieskomplikowane i pełne konstrukcji języka F # w kontekstach, gdzie występuje różnica między dwoma formularzami. W tej tabeli, kąt nawiasy (&lt;&gt;) należy ująć elementy składni dostarczone przez użytkownika. Zajrzyj do dokumentacji dla każdego konstrukcji języka Aby uzyskać szczegółowe informacje o składni używanej w ramach tych konstrukcji.



<table>
<tr>
<th>Konstrukcji języka</th>
<th>Lightweight — Składnia</th>
<th>Pełna składnia</th>
</tr>
<tr>
<td>
wyrażenia złożone
</td>
<td>

```xml
<expression1>
<expression2>
```
</td><td>

```
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>


zagnieżdżone `let` powiązania

</td><td>
```
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
blok kodu
</td><td>

```
(
    <expression1>
    <expression2>
)
```

</td><td>

```
begin
    <expression1>;
    <expression2>;
end
```
</td>
</tr>
<tr><td>
`for...do`
</td><td>

```
for counter = start to finish do
    ...
```

</td><td>

```
for counter = start to finish do
    ...
done
```

</td>
</tr>
<tr><td>
`while...do`
</td><td>

```
while <condition> do
    ...
```

</td><td>

```
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```
for var in start .. finish do
    ...
```

</td><td>

```
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```
do
    ...
```

</td><td>

```
do
    ...
in
```

</td>
</tr>
<tr><td>rekord
</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>class
</td><td>
```
type <class-name>(<params>) = ... ```

</td><td>

```
type <class-name>(<params>) =
    class
        ...
    end
```
</td>
</tr>
<tr><td>— struktura</td><td>

```
[<StructAttribute>]
type <structure-name> =
    ...
```
</td><td>

```
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td>Unii rozłącznej</td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```
</td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    with
        <value-or-member-definitions>
    end    
```

</td>
</tr>
<tr><td>interface</td><td>

```
type <interface-name> =
    ...
```
</td><td>

```
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td>wyrażenie obiektu</td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td>implementacja interfejsu</td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>type — rozszerzenie</td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>moduł</td><td>

```
module <module-name> =
    ...
```

</td><td>

```
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>



## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Dyrektywy kompilatora](compiler-directives.md)

[Wskazówki dotyczące formatowania kodu](code-formatting-guidelines.md)
