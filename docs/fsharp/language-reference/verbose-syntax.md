---
title: Pełna składnia (F#)
description: 'Różnice między pełnego i uproszczonego składnię języka programowania w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: b0bed66b4a76c5ab11e6c9e7aaf695f864e74ca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563787"
---
# <a name="verbose-syntax"></a><span data-ttu-id="21fa0-103">Pełna składnia</span><span class="sxs-lookup"><span data-stu-id="21fa0-103">Verbose Syntax</span></span>

<span data-ttu-id="21fa0-104">Istnieją dwie formy składni dla wielu konstrukcje w języku F #: *Pełna składnia* i *lightweight — składnia*.</span><span class="sxs-lookup"><span data-stu-id="21fa0-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="21fa0-105">Pełna składnia nie jest używany jako często, ale ma tę zaletę, jest mniej wrażliwe na wcięcia.</span><span class="sxs-lookup"><span data-stu-id="21fa0-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="21fa0-106">Lightweight — składnia jest krótsza i używa wcięcia sygnalizują początek i koniec konstrukcje, zamiast dodatkowe słowa kluczowe, takich jak `begin`, `end`, `in`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="21fa0-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="21fa0-107">Domyślnie przyjmowana jest składnia lekkie składni.</span><span class="sxs-lookup"><span data-stu-id="21fa0-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="21fa0-108">W tym temacie opisano składnię konstrukcje F #, gdy lightweight — składnia nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="21fa0-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="21fa0-109">Pełna składnia jest zawsze włączony, dlatego nawet jeśli lightweight — składnia jest włączone, można nadal używać Pełna składnia dla niektórych konstrukcje.</span><span class="sxs-lookup"><span data-stu-id="21fa0-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="21fa0-110">Lightweight — składnia można wyłączyć za pomocą `#light "off"` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="21fa0-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>


## <a name="table-of-constructs"></a><span data-ttu-id="21fa0-111">Tabela konstrukcji</span><span class="sxs-lookup"><span data-stu-id="21fa0-111">Table of Constructs</span></span>
<span data-ttu-id="21fa0-112">W poniższej tabeli przedstawiono składnię nieskomplikowane i pełne konstrukcji języka F # w kontekstach, gdzie występuje różnica między dwoma formularzami.</span><span class="sxs-lookup"><span data-stu-id="21fa0-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="21fa0-113">W tej tabeli, kąt nawiasy (&lt;&gt;) należy ująć elementy składni dostarczone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="21fa0-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="21fa0-114">Zajrzyj do dokumentacji dla każdego konstrukcji języka Aby uzyskać szczegółowe informacje o składni używanej w ramach tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="21fa0-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>



<table>
<tr>
<th><span data-ttu-id="21fa0-115">Konstrukcji języka</span><span class="sxs-lookup"><span data-stu-id="21fa0-115">Language construct</span></span></th>
<th><span data-ttu-id="21fa0-116">Lightweight — Składnia</span><span class="sxs-lookup"><span data-stu-id="21fa0-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="21fa0-117">Pełna składnia</span><span class="sxs-lookup"><span data-stu-id="21fa0-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="21fa0-118">wyrażenia złożone</span><span class="sxs-lookup"><span data-stu-id="21fa0-118">compound expressions</span></span>
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


<span data-ttu-id="21fa0-119">zagnieżdżone `let` powiązania</span><span class="sxs-lookup"><span data-stu-id="21fa0-119">nested `let` bindings</span></span>

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
<span data-ttu-id="21fa0-120">blok kodu</span><span class="sxs-lookup"><span data-stu-id="21fa0-120">code block</span></span>
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
<tr><td><span data-ttu-id="21fa0-121">rekord</span><span class="sxs-lookup"><span data-stu-id="21fa0-121">record</span></span>
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
<tr><td><span data-ttu-id="21fa0-122">class</span><span class="sxs-lookup"><span data-stu-id="21fa0-122">class</span></span>
</td><td><span data-ttu-id="21fa0-123">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="21fa0-123">
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
<tr><td><span data-ttu-id="21fa0-124">— struktura</span><span class="sxs-lookup"><span data-stu-id="21fa0-124">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="21fa0-125">Unii rozłącznej</span><span class="sxs-lookup"><span data-stu-id="21fa0-125">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="21fa0-126">interface</span><span class="sxs-lookup"><span data-stu-id="21fa0-126">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="21fa0-127">wyrażenie obiektu</span><span class="sxs-lookup"><span data-stu-id="21fa0-127">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="21fa0-128">implementacja interfejsu</span><span class="sxs-lookup"><span data-stu-id="21fa0-128">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="21fa0-129">type — rozszerzenie</span><span class="sxs-lookup"><span data-stu-id="21fa0-129">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="21fa0-130">moduł</span><span class="sxs-lookup"><span data-stu-id="21fa0-130">module</span></span></td><td>

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



## <a name="see-also"></a><span data-ttu-id="21fa0-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21fa0-131">See Also</span></span>
[<span data-ttu-id="21fa0-132">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="21fa0-132">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="21fa0-133">Dyrektywy kompilatora</span><span class="sxs-lookup"><span data-stu-id="21fa0-133">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="21fa0-134">Wskazówki dotyczące formatowania kodu</span><span class="sxs-lookup"><span data-stu-id="21fa0-134">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
