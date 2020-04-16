---
title: Pełna składnia
description: Poznaj różnicę między składnią pełnej i lekkiej w języku programowania F#.
ms.date: 05/16/2016
ms.openlocfilehash: 722807695c56beb0d681b95a78ed8cb8c1df3ddf
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463905"
---
# <a name="verbose-syntax"></a>Pełna składnia

Istnieją dwie formy składni dostępne dla wielu konstrukcji w języku F#: *składnia pełnej* i *uproszczona składnia*. Składnia pełnej nie jest tak często używana, ale ma tę zaletę, że jest mniej wrażliwa na wcięcie. Uproszczona składnia jest krótsza i używa wcięci do sygnalizowania początku i końca `begin` `end`konstrukcji, a nie dodatkowych słów kluczowych, takich jak , `in`i tak dalej. Domyślną składnią jest uproszczona składnia. W tym temacie opisano składnię konstrukcji języka F#, gdy nie jest włączona składnia lightweight. Składnia pełnej jest zawsze włączona, więc nawet jeśli włączysz lekką składnię, nadal można użyć składni pełnej dla niektórych konstrukcji. Można wyłączyć uproszczoną składnię `#light "off"` przy użyciu dyrektywy.

## <a name="table-of-constructs"></a>Tabela konstrukcji

W poniższej tabeli przedstawiono składnię odciążania i pełnej dla konstrukcji języka F# w kontekstach, w których istnieje różnica między tymi dwoma formularzami. W tej tabeli nawiasy kątowe (&lt;&gt;) zawierają elementy składni dostarczane przez użytkownika. Zapoznaj się z dokumentacją dla każdej konstrukcji języka, aby uzyskać bardziej szczegółowe informacje na temat składni używanej w tych konstrukcjach.

<table>
<tr>
<th>Konstrukcja języka</th>
<th>Uproszczona składnia</th>
<th>Składnia pełnej</th>
</tr>
<tr>
<td>
wyrażenia złożone
</td>
<td>

```xml
<expression1 />
<expression2 />
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

```fsharp
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
<tr><td>rejestrowanie
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
<tr><td>dyskryminowany związek</td><td>

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
<tr><td>rozszerzenie typu</td><td>

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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka F#](index.md)
- [Dyrektywy kompilatora](compiler-directives.md)
- [Wskazówki dotyczące formatowania kodu](../style-guide/formatting.md)
