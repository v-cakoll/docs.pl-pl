---
title: Pełna składnia
description: Różnice między pełnego i uproszczonego składni w F# języka programowania.
ms.date: 05/16/2016
ms.openlocfilehash: c95965d7d9d18a0fca11663a474dbbc9375a9494
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641665"
---
# <a name="verbose-syntax"></a>Pełna składnia

Istnieją dwie formy składnia dla wielu konstrukcji w F# języka: *Pełna składnia* i *lightweight — składnia*. Pełna składnia nie jest tak często używane, ale ma tę zaletę są mniej podatne na wcięcia. Lightweight — składnia jest krótsza i używa wcięcia w celu sygnalizowania, że na początku i na końcu konstrukcji, zamiast dodatkowych słów kluczowych, takich jak `begin`, `end`, `in`i tak dalej. Domyślnie przyjmowana jest składnia składni lekkiej. W tym temacie opisano składnię F# konstrukcji, gdy lightweight — składnia nie jest włączone. Pełna składnia jest zawsze włączone, dlatego nawet jeśli włączysz lightweight — składnia, nadal mogą używać Pełna składnia dla niektórych konstrukcji. Lightweight — składnia można wyłączyć za pomocą `#light "off"` dyrektywy.

## <a name="table-of-constructs"></a>Tabela konstrukcji

W poniższej tabeli przedstawiono składnię uproszczona i pełne F# konstrukcji językowych w kontekstach w przypadku, gdy istnieje różnica między dwoma formularzami. W tej tabeli, kąt nawiasy kwadratowe (&lt;&gt;) należy ująć elementy składni dostarczone przez użytkownika. Zapoznaj się z dokumentacją dla każdego konstrukcją języka pierwszej klasy, aby uzyskać szczegółowe informacje o składni używane w ramach te konstrukcje.

<table>
<tr>
<th>Konstrukcją języka pierwszej klasy</th>
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

```fsharp
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>

zagnieżdżone `let` powiązania

</td><td>

```fsharp
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```fsharp
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

```fsharp
(
    <expression1>
    <expression2>
)
```

</td><td>

```fsharp
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

```fsharp
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

```fsharp
while <condition> do
    ...
```

</td><td>

```fsharp
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```fsharp
for var in start .. finish do
    ...
```

</td><td>

```fsharp
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```fsharp
do
    ...
```

</td><td>

```fsharp
do
    ...
in
```

</td>
</tr>
<tr><td>Rekord
</td><td>

```fsharp
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```fsharp
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

```fsharp
type <class-name>(<params>) =
    ...
```

</td><td>

```fsharp
type <class-name>(<params>) =
    class
        ...
    end
```

</td>
</tr>
<tr><td>— struktura</td><td>

```fsharp
[<StructAttribute>]
type <structure-name> =
    ...
```

</td><td>

```fsharp
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td>złożenia dyskryminowanego</td><td>

```fsharp
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```

</td><td>

```fsharp
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

```fsharp
type <interface-name> =
    ...
```

</td><td>

```fsharp
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td>wyrażenie obiektu</td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```fsharp
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

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>rozszerzenia typu</td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>moduł</td><td>

```fsharp
module <module-name> =
    ...
```

</td><td>

```fsharp
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Dyrektywy kompilatora](compiler-directives.md)
- [Wskazówki dotyczące formatowania kodu](code-formatting-guidelines.md)
