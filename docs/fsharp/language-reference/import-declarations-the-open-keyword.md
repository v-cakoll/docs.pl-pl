---
title: 'Deklaracje importowania: słowo kluczowe open'
description: Dowiedz F# się więcej na temat deklaracji importu i sposobu określania modułu lub przestrzeni nazw, których elementy można odwołać bez używania w pełni kwalifikowanej nazwy.
ms.date: 04/04/2019
ms.openlocfilehash: 816bac551692c3397290f64c6267ee22e4ce90fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630578"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="2b3df-103">Deklaracje importowania: słowo kluczowe `open`</span><span class="sxs-lookup"><span data-stu-id="2b3df-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="2b3df-104">Linki do odwołań do interfejsów API w tym artykule przeprowadzą Cię do subskrypcji MSDN.</span><span class="sxs-lookup"><span data-stu-id="2b3df-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="2b3df-105">Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="2b3df-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="2b3df-106">*Deklaracja importu* określa moduł lub przestrzeń nazw, których elementy można odwoływać bez używania w pełni kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2b3df-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b3df-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b3df-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="2b3df-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b3df-108">Remarks</span></span>

<span data-ttu-id="2b3df-109">Odwoływanie się do kodu przy użyciu w pełni kwalifikowanej przestrzeni nazw lub ścieżki modułu za każdym razem, gdy program może utworzyć kod, który jest trudno pisać, czytać i konserwować.</span><span class="sxs-lookup"><span data-stu-id="2b3df-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="2b3df-110">Zamiast tego można użyć `open` słowa kluczowego dla często używanych modułów i przestrzeni nazw, aby podczas odwoływania się do elementu członkowskiego tego modułu lub przestrzeni nazw można użyć krótkiej formy nazwy zamiast w pełni kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2b3df-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="2b3df-111">To słowo kluczowe jest podobne do `using` słowa kluczowego `using namespace` C#w, C++w wizualizacji i `Imports` w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2b3df-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="2b3df-112">Dostarczony moduł lub przestrzeń nazw muszą znajdować się w tym samym projekcie lub w przywoływanym projekcie lub zestawie.</span><span class="sxs-lookup"><span data-stu-id="2b3df-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="2b3df-113">Jeśli tak nie jest, można dodać odwołanie do projektu lub użyć `-reference` opcji wiersza polecenia`-` `-r`(lub jego skrótu).</span><span class="sxs-lookup"><span data-stu-id="2b3df-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="2b3df-114">Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="2b3df-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="2b3df-115">Deklaracja importu udostępnia nazwy dostępne w kodzie, który następuje po deklaracji, do końca otaczającej przestrzeni nazw, modułu lub pliku.</span><span class="sxs-lookup"><span data-stu-id="2b3df-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="2b3df-116">Jeśli używasz wielu deklaracji importu, powinny one pojawiać się w osobnych wierszach.</span><span class="sxs-lookup"><span data-stu-id="2b3df-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="2b3df-117">Poniższy kod ilustruje użycie `open` słowa kluczowego w celu uproszczenia kodu.</span><span class="sxs-lookup"><span data-stu-id="2b3df-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="2b3df-118">F# Kompilator nie emituje błędu lub ostrzeżenia, gdy niejasności wystąpi, gdy ta sama nazwa występuje w więcej niż jednym otwartym module lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2b3df-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="2b3df-119">Gdy wystąpi niejasności, F# zapewnia preferencję dla ostatnio otwartego modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2b3df-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="2b3df-120">Na przykład, w poniższym kodzie, `empty` oznacza `Seq.empty`, `empty` chociaż znajduje się zarówno `List` w module, jak i `Seq` .</span><span class="sxs-lookup"><span data-stu-id="2b3df-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="2b3df-121">W związku z tym należy zachować ostrożność podczas otwierania modułów lub `List` przestrzeni `Seq` nazw, takich jak lub zawierających składowe o identycznych nazwach. zamiast tego należy rozważyć użycie kwalifikowanych nazw.</span><span class="sxs-lookup"><span data-stu-id="2b3df-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="2b3df-122">Należy unikać każdej sytuacji, w której kod jest zależny od kolejności deklaracji importu.</span><span class="sxs-lookup"><span data-stu-id="2b3df-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="2b3df-123">Obszary nazw, które są domyślnie otwarte</span><span class="sxs-lookup"><span data-stu-id="2b3df-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="2b3df-124">Niektóre przestrzenie nazw są często używane F# w kodzie, który są otwierane niejawnie bez potrzeby jawnej deklaracji importu.</span><span class="sxs-lookup"><span data-stu-id="2b3df-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="2b3df-125">W poniższej tabeli przedstawiono obszary nazw, które są domyślnie otwarte.</span><span class="sxs-lookup"><span data-stu-id="2b3df-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="2b3df-126">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="2b3df-126">Namespace</span></span>|<span data-ttu-id="2b3df-127">Opis</span><span class="sxs-lookup"><span data-stu-id="2b3df-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="2b3df-128">Zawiera podstawowe F# definicje typów dla typów wbudowanych, takich jak `int` i. `float`</span><span class="sxs-lookup"><span data-stu-id="2b3df-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="2b3df-129">Zawiera podstawowe operacje arytmetyczne, `+` takie `*`jak i.</span><span class="sxs-lookup"><span data-stu-id="2b3df-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="2b3df-130">Zawiera niezmienne klasy kolekcji, `List` takie `Array`jak i.</span><span class="sxs-lookup"><span data-stu-id="2b3df-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="2b3df-131">Zawiera typy dla konstrukcji kontroli, takich jak Ocena z opóźnieniem i asynchroniczne przepływy pracy.</span><span class="sxs-lookup"><span data-stu-id="2b3df-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="2b3df-132">Zawiera funkcje dla sformatowanych operacji we/wy `printf` , takich jak funkcja.</span><span class="sxs-lookup"><span data-stu-id="2b3df-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="2b3df-133">AutoOpen — atrybut</span><span class="sxs-lookup"><span data-stu-id="2b3df-133">AutoOpen Attribute</span></span>

<span data-ttu-id="2b3df-134">Można zastosować `AutoOpen` atrybut do zestawu, jeśli chcesz automatycznie otworzyć przestrzeń nazw lub moduł, gdy odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="2b3df-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="2b3df-135">Można również zastosować `AutoOpen` atrybut do modułu, aby automatycznie otworzyć ten moduł po otwarciu modułu nadrzędnego lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2b3df-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="2b3df-136">Aby uzyskać więcej informacji, zobacz [Klasa Core.](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)AutoOpenAttribute.</span><span class="sxs-lookup"><span data-stu-id="2b3df-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="2b3df-137">RequireQualifiedAccess — atrybut</span><span class="sxs-lookup"><span data-stu-id="2b3df-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="2b3df-138">Niektóre moduły, rekordy lub typy Unii mogą określać `RequireQualifiedAccess` atrybut.</span><span class="sxs-lookup"><span data-stu-id="2b3df-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="2b3df-139">Gdy odwołujesz się do elementów tych modułów, rekordów lub Unii, musisz użyć kwalifikowanej nazwy bez względu na to, czy dołączysz deklarację importu.</span><span class="sxs-lookup"><span data-stu-id="2b3df-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="2b3df-140">Jeśli ten atrybut jest używany strategicznie dla typów, które definiują często używane nazwy, można uniknąć kolizji nazw, a tym samym zwiększyć odporność kodu na zmiany w bibliotekach.</span><span class="sxs-lookup"><span data-stu-id="2b3df-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="2b3df-141">Aby uzyskać więcej informacji, zobacz [Klasa Core. RequireQualifiedAccessAttribute —](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="2b3df-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b3df-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b3df-142">See also</span></span>

- [<span data-ttu-id="2b3df-143">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="2b3df-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="2b3df-144">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="2b3df-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="2b3df-145">Moduły</span><span class="sxs-lookup"><span data-stu-id="2b3df-145">Modules</span></span>](modules.md)
