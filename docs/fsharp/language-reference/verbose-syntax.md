---
title: "Pełna składnia (F#)"
description: "Różnice między pełnego i uproszczonego składnię języka programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0a6792b3-b312-4453-a025-21d9760eee5d
ms.openlocfilehash: 2cef359a879897825733a3186be97b38896f5953
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="verbose-syntax"></a><span data-ttu-id="6b6ee-104">Pełna składnia</span><span class="sxs-lookup"><span data-stu-id="6b6ee-104">Verbose Syntax</span></span>

<span data-ttu-id="6b6ee-105">Istnieją dwie formy składni dla wielu konstrukcje w języku F #: *Pełna składnia* i *lightweight — składnia*.</span><span class="sxs-lookup"><span data-stu-id="6b6ee-105">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="6b6ee-106">Pełna składnia nie jest używany jako często, ale ma tę zaletę, jest mniej wrażliwe na wcięcia.</span><span class="sxs-lookup"><span data-stu-id="6b6ee-106">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="6b6ee-107">Lightweight — składnia jest krótsza i używa wcięcia sygnalizują początek i koniec konstrukcje, zamiast dodatkowe słowa kluczowe, takich jak `begin`, `end`, `in`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="6b6ee-107">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="6b6ee-108">Domyślnie przyjmowana jest składnia lekkie składni.</span><span class="sxs-lookup"><span data-stu-id="6b6ee-108">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="6b6ee-109">W tym temacie opisano składnię konstrukcje F #, gdy lightweight — składnia nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="6b6ee-109">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="6b6ee-110">Pełna składnia jest zawsze włączony, dlatego nawet jeśli lightweight — składnia jest włączone, można nadal używać Pełna składnia dla niektórych konstrukcje.</span><span class="sxs-lookup"><span data-stu-id="6b6ee-110">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="6b6ee-111">Lightweight — składnia można wyłączyć za pomocą `#light "off"` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="6b6ee-111">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>


## <a name="table-of-constructs"></a><span data-ttu-id="6b6ee-112">Tabela konstrukcji</span><span class="sxs-lookup"><span data-stu-id="6b6ee-112">Table of Constructs</span></span>
<span data-ttu-id="6b6ee-113">W poniższej tabeli przedstawiono składnię nieskomplikowane i pełne konstrukcji języka F # w kontekstach, gdzie występuje różnica między dwoma formularzami.</span><span class="sxs-lookup"><span data-stu-id="6b6ee-113">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="6b6ee-114">W tej tabeli, kąt nawiasy (&lt;&gt;) należy ująć elementy składni dostarczone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6b6ee-114">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="6b6ee-115">Zajrzyj do dokumentacji dla każdego konstrukcji języka Aby uzyskać szczegółowe informacje o składni używanej w ramach tych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="6b6ee-115">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>



<table>
<tr>
<th><span data-ttu-id="6b6ee-116">Konstrukcji języka</span><span class="sxs-lookup"><span data-stu-id="6b6ee-116">Language construct</span></span></th>
<th><span data-ttu-id="6b6ee-117">Lightweight — Składnia</span><span class="sxs-lookup"><span data-stu-id="6b6ee-117">Lightweight syntax</span></span></th>
<th><span data-ttu-id="6b6ee-118">Pełna składnia</span><span class="sxs-lookup"><span data-stu-id="6b6ee-118">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="6b6ee-119">wyrażenia złożone</span><span class="sxs-lookup"><span data-stu-id="6b6ee-119">compound expressions</span></span>
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


<span data-ttu-id="6b6ee-120">zagnieżdżone `let` powiązania</span><span class="sxs-lookup"><span data-stu-id="6b6ee-120">nested `let` bindings</span></span>

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
<span data-ttu-id="6b6ee-121">blok kodu</span><span class="sxs-lookup"><span data-stu-id="6b6ee-121">code block</span></span>
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
<tr><td><span data-ttu-id="6b6ee-122">rekord</span><span class="sxs-lookup"><span data-stu-id="6b6ee-122">record</span></span>
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
<tr><td><span data-ttu-id="6b6ee-123">class</span><span class="sxs-lookup"><span data-stu-id="6b6ee-123">class</span></span>
</td><td><span data-ttu-id="6b6ee-124">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="6b6ee-124">
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
<tr><td><span data-ttu-id="6b6ee-125">— struktura</span><span class="sxs-lookup"><span data-stu-id="6b6ee-125">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="6b6ee-126">Unii rozłącznej</span><span class="sxs-lookup"><span data-stu-id="6b6ee-126">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="6b6ee-127">interface</span><span class="sxs-lookup"><span data-stu-id="6b6ee-127">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="6b6ee-128">wyrażenie obiektu</span><span class="sxs-lookup"><span data-stu-id="6b6ee-128">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="6b6ee-129">implementacja interfejsu</span><span class="sxs-lookup"><span data-stu-id="6b6ee-129">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="6b6ee-130">type — rozszerzenie</span><span class="sxs-lookup"><span data-stu-id="6b6ee-130">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="6b6ee-131">moduł</span><span class="sxs-lookup"><span data-stu-id="6b6ee-131">module</span></span></td><td>

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



## <a name="see-also"></a><span data-ttu-id="6b6ee-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b6ee-132">See Also</span></span>
[<span data-ttu-id="6b6ee-133">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="6b6ee-133">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="6b6ee-134">Dyrektywy kompilatora</span><span class="sxs-lookup"><span data-stu-id="6b6ee-134">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="6b6ee-135">Wskazówki dotyczące formatowania kodu</span><span class="sxs-lookup"><span data-stu-id="6b6ee-135">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
