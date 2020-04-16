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
# <a name="verbose-syntax"></a><span data-ttu-id="02fb3-103">Pełna składnia</span><span class="sxs-lookup"><span data-stu-id="02fb3-103">Verbose Syntax</span></span>

<span data-ttu-id="02fb3-104">Istnieją dwie formy składni dostępne dla wielu konstrukcji w języku F#: *składnia pełnej* i *uproszczona składnia*.</span><span class="sxs-lookup"><span data-stu-id="02fb3-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="02fb3-105">Składnia pełnej nie jest tak często używana, ale ma tę zaletę, że jest mniej wrażliwa na wcięcie.</span><span class="sxs-lookup"><span data-stu-id="02fb3-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="02fb3-106">Uproszczona składnia jest krótsza i używa wcięci do sygnalizowania początku i końca `begin` `end`konstrukcji, a nie dodatkowych słów kluczowych, takich jak , `in`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="02fb3-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="02fb3-107">Domyślną składnią jest uproszczona składnia.</span><span class="sxs-lookup"><span data-stu-id="02fb3-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="02fb3-108">W tym temacie opisano składnię konstrukcji języka F#, gdy nie jest włączona składnia lightweight.</span><span class="sxs-lookup"><span data-stu-id="02fb3-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="02fb3-109">Składnia pełnej jest zawsze włączona, więc nawet jeśli włączysz lekką składnię, nadal można użyć składni pełnej dla niektórych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="02fb3-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="02fb3-110">Można wyłączyć uproszczoną składnię `#light "off"` przy użyciu dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="02fb3-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="02fb3-111">Tabela konstrukcji</span><span class="sxs-lookup"><span data-stu-id="02fb3-111">Table of Constructs</span></span>

<span data-ttu-id="02fb3-112">W poniższej tabeli przedstawiono składnię odciążania i pełnej dla konstrukcji języka F# w kontekstach, w których istnieje różnica między tymi dwoma formularzami.</span><span class="sxs-lookup"><span data-stu-id="02fb3-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="02fb3-113">W tej tabeli nawiasy kątowe (&lt;&gt;) zawierają elementy składni dostarczane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="02fb3-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="02fb3-114">Zapoznaj się z dokumentacją dla każdej konstrukcji języka, aby uzyskać bardziej szczegółowe informacje na temat składni używanej w tych konstrukcjach.</span><span class="sxs-lookup"><span data-stu-id="02fb3-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="02fb3-115">Konstrukcja języka</span><span class="sxs-lookup"><span data-stu-id="02fb3-115">Language construct</span></span></th>
<th><span data-ttu-id="02fb3-116">Uproszczona składnia</span><span class="sxs-lookup"><span data-stu-id="02fb3-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="02fb3-117">Składnia pełnej</span><span class="sxs-lookup"><span data-stu-id="02fb3-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="02fb3-118">wyrażenia złożone</span><span class="sxs-lookup"><span data-stu-id="02fb3-118">compound expressions</span></span>
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

<span data-ttu-id="02fb3-119">zagnieżdżone `let` powiązania</span><span class="sxs-lookup"><span data-stu-id="02fb3-119">nested `let` bindings</span></span>

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
<span data-ttu-id="02fb3-120">blok kodu</span><span class="sxs-lookup"><span data-stu-id="02fb3-120">code block</span></span>
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
<tr><td><span data-ttu-id="02fb3-121">rejestrowanie</span><span class="sxs-lookup"><span data-stu-id="02fb3-121">record</span></span>
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
<tr><td><span data-ttu-id="02fb3-122">class</span><span class="sxs-lookup"><span data-stu-id="02fb3-122">class</span></span>
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
<tr><td><span data-ttu-id="02fb3-123">— struktura</span><span class="sxs-lookup"><span data-stu-id="02fb3-123">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="02fb3-124">dyskryminowany związek</span><span class="sxs-lookup"><span data-stu-id="02fb3-124">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="02fb3-125">interface</span><span class="sxs-lookup"><span data-stu-id="02fb3-125">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="02fb3-126">wyrażenie obiektu</span><span class="sxs-lookup"><span data-stu-id="02fb3-126">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="02fb3-127">implementacja interfejsu</span><span class="sxs-lookup"><span data-stu-id="02fb3-127">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="02fb3-128">rozszerzenie typu</span><span class="sxs-lookup"><span data-stu-id="02fb3-128">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="02fb3-129">moduł</span><span class="sxs-lookup"><span data-stu-id="02fb3-129">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="02fb3-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02fb3-130">See also</span></span>

- [<span data-ttu-id="02fb3-131">Odwołanie do języka F#</span><span class="sxs-lookup"><span data-stu-id="02fb3-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="02fb3-132">Dyrektywy kompilatora</span><span class="sxs-lookup"><span data-stu-id="02fb3-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="02fb3-133">Wskazówki dotyczące formatowania kodu</span><span class="sxs-lookup"><span data-stu-id="02fb3-133">Code Formatting Guidelines</span></span>](../style-guide/formatting.md)
