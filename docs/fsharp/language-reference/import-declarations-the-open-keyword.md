---
title: 'Deklaracje importowania: open — Słowo kluczowe (F#)'
description: 'Dowiedz się więcej o deklaracje importowania F # oraz jak określić modułu lub przestrzeni nazw elementów, których można odwoływać się bez korzystania z w pełni kwalifikowaną nazwę.'
ms.date: 05/16/2016
ms.openlocfilehash: 29f09297993b347464f1572ac9ca24902c786f4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="0fe37-103">Deklaracje importowania: `open` — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="0fe37-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
<span data-ttu-id="0fe37-104">Interfejs API łącza odwołań w tym artykule spowoduje przejście do MSDN.</span><span class="sxs-lookup"><span data-stu-id="0fe37-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="0fe37-105">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="0fe37-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="0fe37-106">*Deklaracja importu* Określa nazwę modułu lub przestrzeni nazw elementów, których można odwoływać się bez korzystania z w pełni kwalifikowaną nazwę.</span><span class="sxs-lookup"><span data-stu-id="0fe37-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>


## <a name="syntax"></a><span data-ttu-id="0fe37-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fe37-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="0fe37-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0fe37-108">Remarks</span></span>
<span data-ttu-id="0fe37-109">Odwołanie do kodu przy użyciu w pełni kwalifikowana ścieżka przestrzeni nazw lub modułu zawsze można utworzyć kod, który jest trudna do zapisu, przeczytaj i konserwacji.</span><span class="sxs-lookup"><span data-stu-id="0fe37-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="0fe37-110">Zamiast tego można użyć `open` — słowo kluczowe dla często używane moduły i przestrzenie nazw, dzięki czemu w przypadku odwołania członkiem tego modułu lub przestrzeni nazw, można użyć Krótka forma nazwy zamiast w pełni kwalifikowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="0fe37-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="0fe37-111">To słowo kluczowe jest podobny do `using` — słowo kluczowe języka C# `using namespace` w programie Visual C++ i `Imports` w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0fe37-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="0fe37-112">Modułu lub przestrzeni nazw, pod warunkiem, musi być w tym samym projekcie lub przywoływanego projektu lub zestawu.</span><span class="sxs-lookup"><span data-stu-id="0fe37-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="0fe37-113">Jeśli nie jest dostępne, można dodać odwołania do projektu, lub użyj `-reference` polecenia`-`wiersz opcji (lub jego skrót `-r`).</span><span class="sxs-lookup"><span data-stu-id="0fe37-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="0fe37-114">Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="0fe37-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="0fe37-115">Deklaracja importu udostępnia nazwy w kodzie występującym w deklaracji, aż do końca otaczającej przestrzeni nazw, modułu lub pliku.</span><span class="sxs-lookup"><span data-stu-id="0fe37-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="0fe37-116">Korzystając z wielu deklaracji importu, powinna pojawić się w osobnych wierszach.</span><span class="sxs-lookup"><span data-stu-id="0fe37-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="0fe37-117">Poniższy kod przedstawia użycie `open` — słowo kluczowe w celu uproszczenia kodu.</span><span class="sxs-lookup"><span data-stu-id="0fe37-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="0fe37-118">Kompilator języka F # nie Emituj błędu lub ostrzeżenia, gdy niejednoznaczności występują po tej samej nazwie w więcej niż jeden Otwórz modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0fe37-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="0fe37-119">Gdy występują niejednoznaczności, F # daje preferencje więcej ostatnio otwartą modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0fe37-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="0fe37-120">Na przykład w poniższym kodzie `empty` oznacza `Seq.empty`, nawet jeśli `empty` znajduje się w obu `List` i `Seq` modułów.</span><span class="sxs-lookup"><span data-stu-id="0fe37-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="0fe37-121">Dlatego należy zachować ostrożność podczas takich jak otworzyć modułach ani przestrzeniach nazw `List` lub `Seq` zawierających elementy członkowskie, które mają identyczne nazwy; zamiast tego Rozważ użycie nazwy kwalifikowane.</span><span class="sxs-lookup"><span data-stu-id="0fe37-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="0fe37-122">Należy unikać każdej sytuacji, w której jest zależny od kolejność deklaracje importowania kodu.</span><span class="sxs-lookup"><span data-stu-id="0fe37-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>


## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="0fe37-123">Przestrzenie nazw, które są otwarte domyślnie</span><span class="sxs-lookup"><span data-stu-id="0fe37-123">Namespaces That Are Open by Default</span></span>
<span data-ttu-id="0fe37-124">Niektórych przestrzeni nazw są tak często używane w kodzie języka F #, że otwarciu niejawnie bez konieczności deklaracji jawny import.</span><span class="sxs-lookup"><span data-stu-id="0fe37-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="0fe37-125">W poniższej tabeli przedstawiono przestrzeni nazw, które są otwarte domyślnie.</span><span class="sxs-lookup"><span data-stu-id="0fe37-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="0fe37-126">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="0fe37-126">Namespace</span></span>|<span data-ttu-id="0fe37-127">Opis</span><span class="sxs-lookup"><span data-stu-id="0fe37-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="0fe37-128">Zawiera podstawowe definicje typów F # dla wbudowanych typów, takie jak `int` i `float`.</span><span class="sxs-lookup"><span data-stu-id="0fe37-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="0fe37-129">Zawiera podstawowe operacje arytmetyczne, takie jak `+` i `*`.</span><span class="sxs-lookup"><span data-stu-id="0fe37-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="0fe37-130">Zawiera klasy modyfikować kolekcji, takie jak `List` i `Array`.</span><span class="sxs-lookup"><span data-stu-id="0fe37-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="0fe37-131">Zawiera typy do sterowania konstrukcje, takie jak obliczanie leniwe i asynchroniczne przepływy pracy.</span><span class="sxs-lookup"><span data-stu-id="0fe37-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="0fe37-132">Zawiera funkcje sformatowany we/wy, takich jak `printf` funkcji.</span><span class="sxs-lookup"><span data-stu-id="0fe37-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="0fe37-133">AutoOpen — atrybut</span><span class="sxs-lookup"><span data-stu-id="0fe37-133">AutoOpen Attribute</span></span>
<span data-ttu-id="0fe37-134">Możesz zastosować `AutoOpen` atrybutu do zestawu, jeśli chcesz automatycznie otworzyć przestrzeni nazw lub modułu, gdy odwołuje się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="0fe37-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="0fe37-135">Można także zastosować `AutoOpen` atrybutu modułu do automatycznego otwierania tego modułu po otwarciu nadrzędnego modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0fe37-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="0fe37-136">Aby uzyskać więcej informacji, zobacz [Core.autoopenattribute — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="0fe37-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>


## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="0fe37-137">RequireQualifiedAccess — atrybut</span><span class="sxs-lookup"><span data-stu-id="0fe37-137">RequireQualifiedAccess Attribute</span></span>
<span data-ttu-id="0fe37-138">Niektóre moduły, rekordy lub typy Unii mogą określać `RequireQualifiedAccess` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0fe37-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="0fe37-139">Podając odniesienie elementy tych modułów, rekordy lub Unii należy użyć kwalifikowanej nazwy niezależnie od tego, czy obejmują deklaracja importu.</span><span class="sxs-lookup"><span data-stu-id="0fe37-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="0fe37-140">Użycie tego atrybutu strategicznie dla typów, które definiują najczęściej używane nazwy, pomaga uniknąć konfliktów nazw i tym samym wprowadzić kod bardziej odporne na zmiany w bibliotekach.</span><span class="sxs-lookup"><span data-stu-id="0fe37-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="0fe37-141">Aby uzyskać więcej informacji, zobacz [Core.requirequalifiedaccessattribute — klasa](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="0fe37-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>


## <a name="see-also"></a><span data-ttu-id="0fe37-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fe37-142">See Also</span></span>
[<span data-ttu-id="0fe37-143"># Odwołanie — język</span><span class="sxs-lookup"><span data-stu-id="0fe37-143"># Language Reference</span></span>](index.md)

[<span data-ttu-id="0fe37-144">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="0fe37-144">Namespaces</span></span>](namespaces.md)

[<span data-ttu-id="0fe37-145">Moduły</span><span class="sxs-lookup"><span data-stu-id="0fe37-145">Modules</span></span>](modules.md)

