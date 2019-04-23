---
title: 'Deklaracje importowania: Open — słowo kluczowe'
description: Dowiedz się więcej o F# zaimportować deklaracje i jak określić modułu lub przestrzeni nazw elementów, których możesz odwoływać się bez korzystania z w pełni kwalifikowanej nazwy.
ms.date: 04/04/2019
ms.openlocfilehash: ad64190c3243c57a185f3b864270fca80590f079
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59055004"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="ba1ea-103">Deklaracje importowania: `open` — Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="ba1ea-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="ba1ea-104">Łączy dokumentacja interfejsu API, w tym artykule spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="ba1ea-105">Dokumentacja interfejsu API w witrynie docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="ba1ea-106">*Deklaracja importu* określa modułu lub przestrzeni nazw elementów, których możesz odwoływać się bez korzystania z w pełni kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="ba1ea-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba1ea-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="ba1ea-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba1ea-108">Remarks</span></span>

<span data-ttu-id="ba1ea-109">Odwoływanie się do kodu przy użyciu w pełni kwalifikowana ścieżka przestrzeni nazw lub module każdym razem, gdy można tworzyć kod, który jest trudny do zapisu, odczytu i obsługa.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="ba1ea-110">Zamiast tego można użyć `open` — słowo kluczowe dla często używanych modułów i przestrzeni nazw, dzięki czemu Gdy odwołujesz się członkiem tego modułu lub przestrzeni nazw, a nie w pełni kwalifikowana nazwa, można użyć krótkiej formy o nazwie.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="ba1ea-111">This — słowo kluczowe jest podobny do `using` — słowo kluczowe w języku C# `using namespace` w programie Visual C++ i `Imports` w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="ba1ea-112">W tym samym projekcie lub w przywoływanego projektu lub zestawu, modułu lub przestrzeni nazw, pod warunkiem musi być.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="ba1ea-113">Jeśli nie jest dostępne, można dodać odwołania do projektu lub użyj `-reference` polecenia`-`opcji (lub jego skrót `-r`).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="ba1ea-114">Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="ba1ea-115">Deklaracja importu udostępnia nazwy w kodzie, który następuje po deklaracji, aż do końcowego otaczającej przestrzeni nazw, modułu lub pliku.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="ba1ea-116">Korzystając z wielu deklaracji importu, powinna zostać wyświetlona w osobnych wierszach.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="ba1ea-117">Poniższy kod przedstawia użycie `open` — słowo kluczowe w celu uproszczenia kodu.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="ba1ea-118">F# Kompilator nie generuje błąd lub ostrzeżenie przypadku niejednoznaczności wystąpienia sytuacji takiej samej nazwie w więcej niż jeden otwarty modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="ba1ea-119">Gdy występują niejasności, F# preferuje bardziej ostatnio otwieranych modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="ba1ea-120">Na przykład w poniższym kodzie `empty` oznacza `Seq.empty`, nawet jeśli `empty` znajduje się w obu `List` i `Seq` modułów.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="ba1ea-121">W związku z tym, należy zachować ostrożność podczas takich jak otwierania modułów i przestrzeni nazw `List` lub `Seq` zawierających elementy członkowskie, które mają identyczne nazwy; zamiast tego Rozważ użycie kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="ba1ea-122">Należy unikać każdej sytuacji, w której kod jest zależny od kolejności deklaracji importu.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="ba1ea-123">Przestrzenie nazw, które są domyślnie otwarty</span><span class="sxs-lookup"><span data-stu-id="ba1ea-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="ba1ea-124">Niektóre przestrzenie nazw, dlatego często są używane w F# kodu, że są one otwarte niejawnie bez konieczności deklaracji jawny import.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="ba1ea-125">W poniższej tabeli przedstawiono przestrzenie nazw, które są domyślnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="ba1ea-126">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ba1ea-126">Namespace</span></span>|<span data-ttu-id="ba1ea-127">Opis</span><span class="sxs-lookup"><span data-stu-id="ba1ea-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="ba1ea-128">Zawiera podstawowe F# wpisz definicje dla typów wbudowanych, taką jak `int` i `float`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="ba1ea-129">Zawiera podstawowe operacje arytmetyczne, takie jak `+` i `*`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="ba1ea-130">Zawiera klasy kolekcji niezmienialnej, takie jak `List` i `Array`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="ba1ea-131">Zawiera typy dla konstrukcji kontrolki, takie jak obliczanie z opóźnieniem i asynchroniczne przepływy pracy.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="ba1ea-132">Zawiera funkcje dla sformatowane we/wy, takich jak `printf` funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="ba1ea-133">AutoOpen — atrybut</span><span class="sxs-lookup"><span data-stu-id="ba1ea-133">AutoOpen Attribute</span></span>

<span data-ttu-id="ba1ea-134">Można zastosować `AutoOpen` atrybut do zestawu, jeśli chcesz automatycznie otworzyć przestrzeni nazw lub module, gdy odwołuje się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="ba1ea-135">Można również zastosować `AutoOpen` atrybutu modułu, aby automatycznie otworzyć ten moduł, po otwarciu moduł nadrzędny lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="ba1ea-136">Aby uzyskać więcej informacji, zobacz [Core.autoopenattribute — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="ba1ea-137">Requirequalifiedaccess — atrybut</span><span class="sxs-lookup"><span data-stu-id="ba1ea-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="ba1ea-138">Niektóre moduły, rekordów lub typy Unii mogą określać `RequireQualifiedAccess` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="ba1ea-139">Gdy odwołujesz się elementy te moduły, rekordów lub Unii, należy użyć kwalifikowanej nazwy, niezależnie od tego, czy obejmują deklaracji importu.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="ba1ea-140">Użycie tego atrybutu strategicznie dla typów, które definiują najczęściej używane nazwy, pomagają uniknąć konfliktów nazw, a tym samym wprowadzić kod bardziej odporne na zmiany w bibliotekach.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="ba1ea-141">Aby uzyskać więcej informacji, zobacz [Core.requirequalifiedaccessattribute — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba1ea-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba1ea-142">See also</span></span>

- [<span data-ttu-id="ba1ea-143">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="ba1ea-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="ba1ea-144">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="ba1ea-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="ba1ea-145">Moduły</span><span class="sxs-lookup"><span data-stu-id="ba1ea-145">Modules</span></span>](modules.md)
