---
title: 'Deklaracje importowania: open — Słowo kluczowe (F#)'
description: 'Dowiedz się więcej o deklaracje importowania F # oraz jak określić modułu lub przestrzeni nazw elementów, których można odwoływać się bez korzystania z w pełni kwalifikowaną nazwę.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: ddbc1086e2adbe8dae408f4d39fd5af888d7fd5e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="5d980-103">Deklaracje importowania: `open` — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="5d980-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
<span data-ttu-id="5d980-104">Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="5d980-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="5d980-105">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="5d980-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="5d980-106">*Deklaracja importu* Określa nazwę modułu lub przestrzeni nazw elementów, których można odwoływać się bez korzystania z w pełni kwalifikowaną nazwę.</span><span class="sxs-lookup"><span data-stu-id="5d980-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>


## <a name="syntax"></a><span data-ttu-id="5d980-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d980-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="5d980-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d980-108">Remarks</span></span>
<span data-ttu-id="5d980-109">Odwołanie do kodu przy użyciu w pełni kwalifikowana ścieżka przestrzeni nazw lub modułu zawsze można utworzyć kod, który jest trudna do zapisu, przeczytaj i konserwacji.</span><span class="sxs-lookup"><span data-stu-id="5d980-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="5d980-110">Zamiast tego można użyć `open` — słowo kluczowe dla często używane moduły i przestrzenie nazw, dzięki czemu w przypadku odwołania członkiem tego modułu lub przestrzeni nazw, można użyć Krótka forma nazwy zamiast w pełni kwalifikowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="5d980-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="5d980-111">To słowo kluczowe jest podobny do `using` — słowo kluczowe języka C# `using namespace` w programie Visual C++ i `Imports` w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5d980-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="5d980-112">Modułu lub przestrzeni nazw, pod warunkiem, musi być w tym samym projekcie lub przywoływanego projektu lub zestawu.</span><span class="sxs-lookup"><span data-stu-id="5d980-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="5d980-113">Jeśli nie jest dostępne, można dodać odwołania do projektu, lub użyj `-reference` polecenia`-`wiersz opcji (lub jego skrót `-r`).</span><span class="sxs-lookup"><span data-stu-id="5d980-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="5d980-114">Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="5d980-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="5d980-115">Deklaracja importu udostępnia nazwy w kodzie występującym w deklaracji, aż do końca otaczającej przestrzeni nazw, modułu lub pliku.</span><span class="sxs-lookup"><span data-stu-id="5d980-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="5d980-116">Korzystając z wielu deklaracji importu, powinna pojawić się w osobnych wierszach.</span><span class="sxs-lookup"><span data-stu-id="5d980-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="5d980-117">Poniższy kod przedstawia użycie `open` — słowo kluczowe w celu uproszczenia kodu.</span><span class="sxs-lookup"><span data-stu-id="5d980-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="5d980-118">Kompilator języka F # nie Emituj błędu lub ostrzeżenia, gdy niejednoznaczności występują po tej samej nazwie w więcej niż jeden Otwórz modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5d980-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="5d980-119">Gdy występują niejednoznaczności, F # daje preferencje więcej ostatnio otwartą modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5d980-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="5d980-120">Na przykład w poniższym kodzie `empty` oznacza `Seq.empty`, nawet jeśli `empty` znajduje się w obu `List` i `Seq` modułów.</span><span class="sxs-lookup"><span data-stu-id="5d980-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="5d980-121">Dlatego należy zachować ostrożność podczas takich jak otworzyć modułach ani przestrzeniach nazw `List` lub `Seq` zawierających elementy członkowskie, które mają identyczne nazwy; zamiast tego Rozważ użycie nazwy kwalifikowane.</span><span class="sxs-lookup"><span data-stu-id="5d980-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="5d980-122">Należy unikać każdej sytuacji, w której jest zależny od kolejność deklaracje importowania kodu.</span><span class="sxs-lookup"><span data-stu-id="5d980-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>


## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="5d980-123">Przestrzenie nazw, które są otwarte domyślnie</span><span class="sxs-lookup"><span data-stu-id="5d980-123">Namespaces That Are Open by Default</span></span>
<span data-ttu-id="5d980-124">Niektórych przestrzeni nazw są tak często używane w kodzie języka F #, że otwarciu niejawnie bez konieczności deklaracji jawny import.</span><span class="sxs-lookup"><span data-stu-id="5d980-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="5d980-125">W poniższej tabeli przedstawiono przestrzeni nazw, które są otwarte domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5d980-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="5d980-126">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="5d980-126">Namespace</span></span>|<span data-ttu-id="5d980-127">Opis</span><span class="sxs-lookup"><span data-stu-id="5d980-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="5d980-128">Zawiera podstawowe definicje typów F # dla wbudowanych typów, takie jak `int` i `float`.</span><span class="sxs-lookup"><span data-stu-id="5d980-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="5d980-129">Zawiera podstawowe operacje arytmetyczne, takie jak `+` i `*`.</span><span class="sxs-lookup"><span data-stu-id="5d980-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="5d980-130">Zawiera klasy modyfikować kolekcji, takie jak `List` i `Array`.</span><span class="sxs-lookup"><span data-stu-id="5d980-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="5d980-131">Zawiera typy do sterowania konstrukcje, takie jak obliczanie leniwe i asynchroniczne przepływy pracy.</span><span class="sxs-lookup"><span data-stu-id="5d980-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="5d980-132">Zawiera funkcje sformatowany we/wy, takich jak `printf` funkcji.</span><span class="sxs-lookup"><span data-stu-id="5d980-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="5d980-133">AutoOpen — atrybut</span><span class="sxs-lookup"><span data-stu-id="5d980-133">AutoOpen Attribute</span></span>
<span data-ttu-id="5d980-134">Możesz zastosować `AutoOpen` atrybutu do zestawu, jeśli chcesz automatycznie otworzyć przestrzeni nazw lub modułu, gdy odwołuje się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="5d980-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="5d980-135">Można także zastosować `AutoOpen` atrybutu modułu do automatycznego otwierania tego modułu po otwarciu nadrzędnego modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5d980-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="5d980-136">Aby uzyskać więcej informacji, zobacz [Core.autoopenattribute — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="5d980-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>


## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="5d980-137">RequireQualifiedAccess — atrybut</span><span class="sxs-lookup"><span data-stu-id="5d980-137">RequireQualifiedAccess Attribute</span></span>
<span data-ttu-id="5d980-138">Niektóre moduły, rekordy lub typy Unii mogą określać `RequireQualifiedAccess` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5d980-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="5d980-139">Podając odniesienie elementy tych modułów, rekordy lub Unii należy użyć kwalifikowanej nazwy niezależnie od tego, czy obejmują deklaracja importu.</span><span class="sxs-lookup"><span data-stu-id="5d980-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="5d980-140">Użycie tego atrybutu strategicznie dla typów, które definiują najczęściej używane nazwy, pomaga uniknąć konfliktów nazw i tym samym wprowadzić kod bardziej odporne na zmiany w bibliotekach.</span><span class="sxs-lookup"><span data-stu-id="5d980-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="5d980-141">Aby uzyskać więcej informacji, zobacz [Core.requirequalifiedaccessattribute — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="5d980-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>


## <a name="see-also"></a><span data-ttu-id="5d980-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d980-142">See Also</span></span>
[<span data-ttu-id="5d980-143"># Odwołanie — język</span><span class="sxs-lookup"><span data-stu-id="5d980-143"># Language Reference</span></span>](index.md)

[<span data-ttu-id="5d980-144">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="5d980-144">Namespaces</span></span>](namespaces.md)

[<span data-ttu-id="5d980-145">Moduły</span><span class="sxs-lookup"><span data-stu-id="5d980-145">Modules</span></span>](modules.md)

