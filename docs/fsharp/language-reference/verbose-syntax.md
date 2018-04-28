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
# <a name="verbose-syntax"></a><span data-ttu-id="713e7-103">Pełna składnia</span><span class="sxs-lookup"><span data-stu-id="713e7-103">Verbose Syntax</span></span>

<span data-ttu-id="713e7-104">Istnieją dwie formy składni dla wielu konstrukcje w języku F #: *Pełna składnia* i *lightweight — składnia*.</span><span class="sxs-lookup"><span data-stu-id="713e7-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="713e7-105">Pełna składnia nie jest używany jako często, ale ma tę zaletę, jest mniej wrażliwe na wcięcia.</span><span class="sxs-lookup"><span data-stu-id="713e7-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="713e7-106">Lightweight — składnia jest krótsza i używa wcięcia sygnalizują początek i koniec konstrukcje, zamiast dodatkowe słowa kluczowe, takich jak `begin`, `end`, `in`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="713e7-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="713e7-107">Domyślnie przyjmowana jest składnia lekkie składni.</span><span class="sxs-lookup"><span data-stu-id="713e7-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="713e7-108">W tym temacie opisano składnię konstrukcje F #, gdy lightweight — składnia nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="713e7-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="713e7-109">Pełna składnia jest zawsze włączony, dlatego nawet jeśli lightweight — składnia jest włączone, można nadal używać Pełna składnia dla niektórych konstrukcje.</span><span class="sxs-lookup"><span data-stu-id="713e7-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="713e7-110">Lightweight — składnia można wyłączyć za pomocą `#light "off"` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="713e7-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>


## <a name="table-of-constructs"></a><span data-ttu-id="713e7-111">Tabela konstrukcji</span><span class="sxs-lookup"><span data-stu-id="713e7-111">Table of Constructs</span></span>
<span data-ttu-id="713e7-112">W poniższej tabeli przedstawiono składnię nieskomplikowane i pełne konstrukcji języka F # w kontekstach, gdzie występuje różnica między dwoma formularzami.</span><span class="sxs-lookup"><span data-stu-id="713e7-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="713e7-113">W tej tabeli, kąt nawiasy (&lt;&gt;) należy ująć elementy składni dostarczone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="713e7-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="713e7-114">Zajrzyj do dokumentacji dla każdego konstrukcji języka Aby uzyskać szczegółowe informacje o składni używanej w ramach tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="713e7-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>



<table>
<tr>
<th><span data-ttu-id="713e7-115">Konstrukcji języka</span><span class="sxs-lookup"><span data-stu-id="713e7-115">Language construct</span></span></th>
<th><span data-ttu-id="713e7-116">Lightweight — Składnia</span><span class="sxs-lookup"><span data-stu-id="713e7-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="713e7-117">Pełna składnia</span><span class="sxs-lookup"><span data-stu-id="713e7-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="713e7-118">wyrażenia złożone</span><span class="sxs-lookup"><span data-stu-id="713e7-118">compound expressions</span></span>
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


<span data-ttu-id="713e7-119">zagnieżdżone `let` powiązania</span><span class="sxs-lookup"><span data-stu-id="713e7-119">nested `let` bindings</span></span>

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
<span data-ttu-id="713e7-120">blok kodu</span><span class="sxs-lookup"><span data-stu-id="713e7-120">code block</span></span>
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
<tr><td><span data-ttu-id="713e7-121">rekord</span><span class="sxs-lookup"><span data-stu-id="713e7-121">record</span></span>
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
<tr><td><span data-ttu-id="713e7-122">class</span><span class="sxs-lookup"><span data-stu-id="713e7-122">class</span></span>
</td><td><span data-ttu-id="713e7-123">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="713e7-123">
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
<tr><td><span data-ttu-id="713e7-124">— struktura</span><span class="sxs-lookup"><span data-stu-id="713e7-124">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="713e7-125">Unii rozłącznej</span><span class="sxs-lookup"><span data-stu-id="713e7-125">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="713e7-126">interface</span><span class="sxs-lookup"><span data-stu-id="713e7-126">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="713e7-127">wyrażenie obiektu</span><span class="sxs-lookup"><span data-stu-id="713e7-127">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="713e7-128">implementacja interfejsu</span><span class="sxs-lookup"><span data-stu-id="713e7-128">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="713e7-129">type — rozszerzenie</span><span class="sxs-lookup"><span data-stu-id="713e7-129">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="713e7-130">moduł</span><span class="sxs-lookup"><span data-stu-id="713e7-130">module</span></span></td><td>

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



## <a name="see-also"></a><span data-ttu-id="713e7-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="713e7-131">See Also</span></span>
[<span data-ttu-id="713e7-132">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="713e7-132">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="713e7-133">Dyrektywy kompilatora</span><span class="sxs-lookup"><span data-stu-id="713e7-133">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="713e7-134">Wskazówki dotyczące formatowania kodu</span><span class="sxs-lookup"><span data-stu-id="713e7-134">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
