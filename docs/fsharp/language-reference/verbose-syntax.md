---
title: Pełna składnia (F#)
description: 'Różnice między pełnego i uproszczonego składni języka F # języka programowania.'
ms.date: 05/16/2016
ms.openlocfilehash: b4f2354738da4692cb444e5e7dd9531d80d26664
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45647143"
---
# <a name="verbose-syntax"></a><span data-ttu-id="70ecf-103">Pełna składnia</span><span class="sxs-lookup"><span data-stu-id="70ecf-103">Verbose Syntax</span></span>

<span data-ttu-id="70ecf-104">Istnieją dwa rodzaje składni dla wielu konstrukcji w języku F #: *Pełna składnia* i *lightweight — składnia*.</span><span class="sxs-lookup"><span data-stu-id="70ecf-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="70ecf-105">Pełna składnia nie jest tak często używane, ale ma tę zaletę są mniej podatne na wcięcia.</span><span class="sxs-lookup"><span data-stu-id="70ecf-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="70ecf-106">Lightweight — składnia jest krótsza i używa wcięcia w celu sygnalizowania, że na początku i na końcu konstrukcji, zamiast dodatkowych słów kluczowych, takich jak `begin`, `end`, `in`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="70ecf-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="70ecf-107">Domyślnie przyjmowana jest składnia składni lekkiej.</span><span class="sxs-lookup"><span data-stu-id="70ecf-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="70ecf-108">W tym temacie opisano składnię konstrukcje F #, gdy lightweight — składnia nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="70ecf-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="70ecf-109">Pełna składnia jest zawsze włączone, dlatego nawet jeśli włączysz lightweight — składnia, nadal mogą używać Pełna składnia dla niektórych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="70ecf-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="70ecf-110">Lightweight — składnia można wyłączyć za pomocą `#light "off"` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="70ecf-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="70ecf-111">Tabela konstrukcji</span><span class="sxs-lookup"><span data-stu-id="70ecf-111">Table of Constructs</span></span>

<span data-ttu-id="70ecf-112">W poniższej tabeli przedstawiono składnię lekkie i szczegółowe informacje dotyczące konstrukcji języka F # w kontekstach w przypadku, gdy istnieje różnica między dwoma formularzami.</span><span class="sxs-lookup"><span data-stu-id="70ecf-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="70ecf-113">W tej tabeli, kąt nawiasy kwadratowe (&lt;&gt;) należy ująć elementy składni dostarczone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="70ecf-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="70ecf-114">Zapoznaj się z dokumentacją dla każdego konstrukcją języka pierwszej klasy, aby uzyskać szczegółowe informacje o składni używane w ramach te konstrukcje.</span><span class="sxs-lookup"><span data-stu-id="70ecf-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="70ecf-115">Konstrukcją języka pierwszej klasy</span><span class="sxs-lookup"><span data-stu-id="70ecf-115">Language construct</span></span></th>
<th><span data-ttu-id="70ecf-116">Lightweight — Składnia</span><span class="sxs-lookup"><span data-stu-id="70ecf-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="70ecf-117">Pełna składnia</span><span class="sxs-lookup"><span data-stu-id="70ecf-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="70ecf-118">wyrażenia złożone</span><span class="sxs-lookup"><span data-stu-id="70ecf-118">compound expressions</span></span>
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


<span data-ttu-id="70ecf-119">zagnieżdżone `let` powiązania</span><span class="sxs-lookup"><span data-stu-id="70ecf-119">nested `let` bindings</span></span>

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
<span data-ttu-id="70ecf-120">blok kodu</span><span class="sxs-lookup"><span data-stu-id="70ecf-120">code block</span></span>
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
<tr><td><span data-ttu-id="70ecf-121">Rekord</span><span class="sxs-lookup"><span data-stu-id="70ecf-121">record</span></span>
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
<tr><td><span data-ttu-id="70ecf-122">class</span><span class="sxs-lookup"><span data-stu-id="70ecf-122">class</span></span>
</td><td><span data-ttu-id="70ecf-123">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="70ecf-123">
```
type <class-name>(<params>) = ... ```

</span></span></td><td>

```
type <class-name>(<params>) =
    class
        ...
    end
```
</td>
</tr>
<tr><td><span data-ttu-id="70ecf-124">— struktura</span><span class="sxs-lookup"><span data-stu-id="70ecf-124">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="70ecf-125">złożenia dyskryminowanego</span><span class="sxs-lookup"><span data-stu-id="70ecf-125">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="70ecf-126">interface</span><span class="sxs-lookup"><span data-stu-id="70ecf-126">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="70ecf-127">wyrażenie obiektu</span><span class="sxs-lookup"><span data-stu-id="70ecf-127">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="70ecf-128">implementacja interfejsu</span><span class="sxs-lookup"><span data-stu-id="70ecf-128">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="70ecf-129">rozszerzenia typu</span><span class="sxs-lookup"><span data-stu-id="70ecf-129">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="70ecf-130">moduł</span><span class="sxs-lookup"><span data-stu-id="70ecf-130">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="70ecf-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70ecf-131">See also</span></span>

- [<span data-ttu-id="70ecf-132">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="70ecf-132">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="70ecf-133">Dyrektywy kompilatora</span><span class="sxs-lookup"><span data-stu-id="70ecf-133">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="70ecf-134">Wskazówki dotyczące formatowania kodu</span><span class="sxs-lookup"><span data-stu-id="70ecf-134">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
