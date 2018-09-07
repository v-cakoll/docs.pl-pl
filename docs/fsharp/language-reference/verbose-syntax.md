---
title: Pełna składnia (F#)
description: 'Różnice między pełnego i uproszczonego składni języka F # języka programowania.'
ms.date: 05/16/2016
ms.openlocfilehash: b4f2354738da4692cb444e5e7dd9531d80d26664
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44063121"
---
# <a name="verbose-syntax"></a>Pełna składnia

Istnieją dwa rodzaje składni dla wielu konstrukcji w języku F #: *Pełna składnia* i *lightweight — składnia*. Pełna składnia nie jest tak często używane, ale ma tę zaletę są mniej podatne na wcięcia. Lightweight — składnia jest krótsza i używa wcięcia w celu sygnalizowania, że na początku i na końcu konstrukcji, zamiast dodatkowych słów kluczowych, takich jak `begin`, `end`, `in`i tak dalej. Domyślnie przyjmowana jest składnia składni lekkiej. W tym temacie opisano składnię konstrukcje F #, gdy lightweight — składnia nie jest włączone. Pełna składnia jest zawsze włączone, dlatego nawet jeśli włączysz lightweight — składnia, nadal mogą używać Pełna składnia dla niektórych konstrukcji. Lightweight — składnia można wyłączyć za pomocą `#light "off"` dyrektywy.

## <a name="table-of-constructs"></a>Tabela konstrukcji

W poniższej tabeli przedstawiono składnię lekkie i szczegółowe informacje dotyczące konstrukcji języka F # w kontekstach w przypadku, gdy istnieje różnica między dwoma formularzami. W tej tabeli, kąt nawiasy kwadratowe (&lt;&gt;) należy ująć elementy składni dostarczone przez użytkownika. Zapoznaj się z dokumentacją dla każdego konstrukcją języka pierwszej klasy, aby uzyskać szczegółowe informacje o składni używane w ramach te konstrukcje.

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
<tr><td>Rekord
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
<tr><td>złożenia dyskryminowanego</td><td>

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
<tr><td>rozszerzenia typu</td><td>

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

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Dyrektywy kompilatora](compiler-directives.md)
- [Wskazówki dotyczące formatowania kodu](code-formatting-guidelines.md)
