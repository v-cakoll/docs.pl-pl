---
title: Pełna składnia
description: Różnice między pełnego i uproszczonego składni w F# języka programowania.
ms.date: 05/16/2016
ms.openlocfilehash: c770f2843276619cb2878198a537dcfb9c054b6b
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613788"
---
# <a name="verbose-syntax"></a><span data-ttu-id="134da-103">Pełna składnia</span><span class="sxs-lookup"><span data-stu-id="134da-103">Verbose Syntax</span></span>

<span data-ttu-id="134da-104">Istnieją dwie formy składnia dla wielu konstrukcji w F# języka: *Pełna składnia* i *lightweight — składnia*.</span><span class="sxs-lookup"><span data-stu-id="134da-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="134da-105">Pełna składnia nie jest tak często używane, ale ma tę zaletę są mniej podatne na wcięcia.</span><span class="sxs-lookup"><span data-stu-id="134da-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="134da-106">Lightweight — składnia jest krótsza i używa wcięcia w celu sygnalizowania, że na początku i na końcu konstrukcji, zamiast dodatkowych słów kluczowych, takich jak `begin`, `end`, `in`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="134da-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="134da-107">Domyślnie przyjmowana jest składnia składni lekkiej.</span><span class="sxs-lookup"><span data-stu-id="134da-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="134da-108">W tym temacie opisano składnię F# konstrukcji, gdy lightweight — składnia nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="134da-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="134da-109">Pełna składnia jest zawsze włączone, dlatego nawet jeśli włączysz lightweight — składnia, nadal mogą używać Pełna składnia dla niektórych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="134da-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="134da-110">Lightweight — składnia można wyłączyć za pomocą `#light "off"` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="134da-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="134da-111">Tabela konstrukcji</span><span class="sxs-lookup"><span data-stu-id="134da-111">Table of Constructs</span></span>

<span data-ttu-id="134da-112">W poniższej tabeli przedstawiono składnię uproszczona i pełne F# konstrukcji językowych w kontekstach w przypadku, gdy istnieje różnica między dwoma formularzami.</span><span class="sxs-lookup"><span data-stu-id="134da-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="134da-113">W tej tabeli, kąt nawiasy kwadratowe (&lt;&gt;) należy ująć elementy składni dostarczone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="134da-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="134da-114">Zapoznaj się z dokumentacją dla każdego konstrukcją języka pierwszej klasy, aby uzyskać szczegółowe informacje o składni używane w ramach te konstrukcje.</span><span class="sxs-lookup"><span data-stu-id="134da-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="134da-115">Konstrukcją języka pierwszej klasy</span><span class="sxs-lookup"><span data-stu-id="134da-115">Language construct</span></span></th>
<th><span data-ttu-id="134da-116">Lightweight — Składnia</span><span class="sxs-lookup"><span data-stu-id="134da-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="134da-117">Pełna składnia</span><span class="sxs-lookup"><span data-stu-id="134da-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="134da-118">wyrażenia złożone</span><span class="sxs-lookup"><span data-stu-id="134da-118">compound expressions</span></span>
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

<span data-ttu-id="134da-119">zagnieżdżone `let` powiązania</span><span class="sxs-lookup"><span data-stu-id="134da-119">nested `let` bindings</span></span>

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
<span data-ttu-id="134da-120">blok kodu</span><span class="sxs-lookup"><span data-stu-id="134da-120">code block</span></span>
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
<tr><td><span data-ttu-id="134da-121">Rekord</span><span class="sxs-lookup"><span data-stu-id="134da-121">record</span></span>
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
<tr><td><span data-ttu-id="134da-122">class</span><span class="sxs-lookup"><span data-stu-id="134da-122">class</span></span>
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
<tr><td><span data-ttu-id="134da-123">— struktura</span><span class="sxs-lookup"><span data-stu-id="134da-123">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="134da-124">złożenia dyskryminowanego</span><span class="sxs-lookup"><span data-stu-id="134da-124">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="134da-125">interface</span><span class="sxs-lookup"><span data-stu-id="134da-125">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="134da-126">wyrażenie obiektu</span><span class="sxs-lookup"><span data-stu-id="134da-126">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="134da-127">implementacja interfejsu</span><span class="sxs-lookup"><span data-stu-id="134da-127">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="134da-128">rozszerzenia typu</span><span class="sxs-lookup"><span data-stu-id="134da-128">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="134da-129">moduł</span><span class="sxs-lookup"><span data-stu-id="134da-129">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="134da-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="134da-130">See also</span></span>

- [<span data-ttu-id="134da-131">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="134da-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="134da-132">Dyrektywy kompilatora</span><span class="sxs-lookup"><span data-stu-id="134da-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="134da-133">Wskazówki dotyczące formatowania kodu</span><span class="sxs-lookup"><span data-stu-id="134da-133">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)