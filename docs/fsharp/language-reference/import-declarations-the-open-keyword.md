---
title: 'Deklaracje importowania: open — Słowo kluczowe'
description: Dowiedz się więcej o deklaracjach importu języka F# i o tym, jak określają one moduł lub obszar nazw, do których można odwoływać się bez użycia w pełni kwalifikowanej nazwy.
ms.date: 04/04/2019
ms.openlocfilehash: 0baef27c7dc3181b9da0defb1c793fec04269c09
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021534"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="285b7-103">Deklaracje importu: słowo `open` kluczowe</span><span class="sxs-lookup"><span data-stu-id="285b7-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="285b7-104">Łącza odwołania interfejsu API w tym artykule spowoduje, że przejdziesz do usługi MSDN.</span><span class="sxs-lookup"><span data-stu-id="285b7-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="285b7-105">Odwołanie docs.microsoft.com interfejsu API nie jest kompletne.</span><span class="sxs-lookup"><span data-stu-id="285b7-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="285b7-106">*Deklaracja importu* określa moduł lub obszar nazw, do których elementów można odwoływać się bez użycia w pełni kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="285b7-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="285b7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="285b7-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="285b7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="285b7-108">Remarks</span></span>

<span data-ttu-id="285b7-109">Odwoływanie się do kodu przy użyciu w pełni kwalifikowanego obszaru nazw lub ścieżki modułu za każdym razem można utworzyć kod, który jest trudny do zapisania, odczytu i utrzymania.</span><span class="sxs-lookup"><span data-stu-id="285b7-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="285b7-110">Zamiast tego można użyć `open` słowa kluczowego dla często używanych modułów i obszarów nazw, dzięki czemu podczas odwoływania się do członka tego modułu lub obszaru nazw można użyć krótkiej formy nazwy zamiast w pełni kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="285b7-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="285b7-111">To słowo kluczowe `using` jest podobne do `using namespace` słowa kluczowego w `Imports` języku C#, w języku Visual C++ i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="285b7-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="285b7-112">Dostarczony moduł lub obszar nazw musi znajdować się w tym samym projekcie lub w projekcie lub zestawie, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="285b7-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="285b7-113">Jeśli tak nie jest, można dodać odwołanie do `-reference` projektu lub użyć opcji wiersza polecenia `-r`(lub jego skrótu).</span><span class="sxs-lookup"><span data-stu-id="285b7-113">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="285b7-114">Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="285b7-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="285b7-115">Deklaracja importu udostępnia nazwy w kodzie następującym po deklaracji, aż do końca otaczającego obszaru nazw, modułu lub pliku.</span><span class="sxs-lookup"><span data-stu-id="285b7-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="285b7-116">W przypadku używania wielu deklaracji importu powinny one być wyświetlane w oddzielnych wierszach.</span><span class="sxs-lookup"><span data-stu-id="285b7-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="285b7-117">Poniższy kod przedstawia użycie `open` słowa kluczowego w celu uproszczenia kodu.</span><span class="sxs-lookup"><span data-stu-id="285b7-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="285b7-118">Kompilator Języka F# nie emituje błędu ani ostrzeżenia, gdy wystąpią niejasności, gdy ta sama nazwa występuje w więcej niż jednym otwartym module lub obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="285b7-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="285b7-119">Gdy wystąpią niejasności, F# daje pierwszeństwo nowo otwarty moduł lub obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="285b7-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="285b7-120">Na przykład w poniższym `empty` `Seq.empty`kodzie `empty` oznacza , nawet `List` `Seq` jeśli znajduje się w modułach i modułach.</span><span class="sxs-lookup"><span data-stu-id="285b7-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="285b7-121">W związku z tym należy zachować ostrożność podczas `List` `Seq` otwierania modułów lub obszarów nazw, takich jak lub które zawierają elementy członkowskie, które mają identyczne nazwy; zamiast tego należy rozważyć użycie kwalifikowanych nazw.</span><span class="sxs-lookup"><span data-stu-id="285b7-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="285b7-122">Należy unikać sytuacji, w której kod jest zależny od kolejności deklaracji importowych.</span><span class="sxs-lookup"><span data-stu-id="285b7-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="285b7-123">Obszary nazw, które są domyślnie otwarte</span><span class="sxs-lookup"><span data-stu-id="285b7-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="285b7-124">Niektóre przestrzenie nazw są tak często używane w kodzie Języka F#, że są otwierane niejawnie bez konieczności jawnej deklaracji importu.</span><span class="sxs-lookup"><span data-stu-id="285b7-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="285b7-125">W poniższej tabeli przedstawiono obszary nazw, które są domyślnie otwarte.</span><span class="sxs-lookup"><span data-stu-id="285b7-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="285b7-126">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="285b7-126">Namespace</span></span>|<span data-ttu-id="285b7-127">Opis</span><span class="sxs-lookup"><span data-stu-id="285b7-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="285b7-128">Zawiera podstawowe definicje typów F# dla `int` typów `float`wbudowanych, takich jak i .</span><span class="sxs-lookup"><span data-stu-id="285b7-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="285b7-129">Zawiera podstawowe operacje arytmetyczne, takie jak `+` i `*`.</span><span class="sxs-lookup"><span data-stu-id="285b7-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="285b7-130">Zawiera niezmienne klasy kolekcji, takie jak `List` i `Array`.</span><span class="sxs-lookup"><span data-stu-id="285b7-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="285b7-131">Zawiera typy dla konstrukcji kontroli, takich jak ocena z opóźnieniem i przepływów pracy asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="285b7-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="285b7-132">Zawiera funkcje sformatowanego we/wy, takie jak `printf` funkcja.</span><span class="sxs-lookup"><span data-stu-id="285b7-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="285b7-133">Atrybut AutoOpen</span><span class="sxs-lookup"><span data-stu-id="285b7-133">AutoOpen Attribute</span></span>

<span data-ttu-id="285b7-134">Można zastosować `AutoOpen` atrybut do zestawu, jeśli chcesz automatycznie otworzyć obszar nazw lub moduł, gdy zbliża się do zestawu.</span><span class="sxs-lookup"><span data-stu-id="285b7-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="285b7-135">Można również zastosować `AutoOpen` atrybut do modułu, aby automatycznie otworzyć ten moduł po otwarciu modułu nadrzędnego lub obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="285b7-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="285b7-136">Aby uzyskać więcej informacji, zobacz [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="285b7-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="285b7-137">Atrybut Wymagaj wykwalifikowanegoAkcesji</span><span class="sxs-lookup"><span data-stu-id="285b7-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="285b7-138">Niektóre moduły, rekordy lub typy `RequireQualifiedAccess` unii mogą określać atrybut.</span><span class="sxs-lookup"><span data-stu-id="285b7-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="285b7-139">Podczas odwoływania się do elementów tych modułów, rekordów lub związków należy użyć nazwy kwalifikowanej, niezależnie od tego, czy jest do nich deklaracja importu.</span><span class="sxs-lookup"><span data-stu-id="285b7-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="285b7-140">Jeśli używasz tego atrybutu strategicznie na typy, które definiują powszechnie używane nazwy, można uniknąć kolizji nazw i tym samym uczynić kod bardziej odporne na zmiany w bibliotekach.</span><span class="sxs-lookup"><span data-stu-id="285b7-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="285b7-141">Aby uzyskać więcej informacji, zobacz [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="285b7-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="285b7-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="285b7-142">See also</span></span>

- [<span data-ttu-id="285b7-143">Odwołanie do języka F#</span><span class="sxs-lookup"><span data-stu-id="285b7-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="285b7-144">Namespaces</span><span class="sxs-lookup"><span data-stu-id="285b7-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="285b7-145">Moduły</span><span class="sxs-lookup"><span data-stu-id="285b7-145">Modules</span></span>](modules.md)
