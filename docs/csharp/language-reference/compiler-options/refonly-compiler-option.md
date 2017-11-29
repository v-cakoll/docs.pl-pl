---
title: -refonly (opcje kompilatora C#)
ms.date: 07/08/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4c745416bda56f5f1b1b4ab8267274d972a990d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="refonly-c-compiler-options"></a><span data-ttu-id="db098-102">/refonly (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="db098-102">/refonly (C# Compiler Options)</span></span>

<span data-ttu-id="db098-103">**/Refonly** opcja wskazuje, że zestaw odwołania powinny być danymi wyjściowymi zamiast zestawu implementacji, jako główny wynik.</span><span class="sxs-lookup"><span data-stu-id="db098-103">The **/refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="db098-104">`/refonly` Parametr dyskretnie wyłącza Generowanie plików PDB, jak zestawy odwołań nie może zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="db098-104">The `/refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="db098-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="db098-105">Syntax</span></span>

```console
/refonly
```

## <a name="remarks"></a><span data-ttu-id="db098-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db098-106">Remarks</span></span>

<span data-ttu-id="db098-107">Zestawy tylko metadane mieć ich treści metody zastąpione pojedynczy `throw null` body, ale dołączone wszystkie elementy członkowskie z wyjątkiem typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="db098-107">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="db098-108">Przyczyna przy użyciu `throw null` jest jednostki (w przeciwieństwie do treści), dzięki czemu PEVerify można uruchamiać i przekazywania (w związku z tym sprawdzanie poprawności kompletności metadanych).</span><span class="sxs-lookup"><span data-stu-id="db098-108">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="db098-109">Zestawy referencyjne obejmuje dane poziomu zestawu `ReferenceAssembly` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="db098-109">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="db098-110">Ten atrybut można określić w źródle (następnie kompilator nie będzie trzeba go syntetyzowania).</span><span class="sxs-lookup"><span data-stu-id="db098-110">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="db098-111">Z powodu tego atrybutu środowisk uruchomieniowych będzie odmawiał załadowania zestawów odwołań do wykonania (ale nadal może być załadowany w trybie tylko do odbicia).</span><span class="sxs-lookup"><span data-stu-id="db098-111">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="db098-112">Narzędzia, które odzwierciedlać na potrzebę zestawów upewnij się, że są ładowane zestawów odwołań w trybie tylko do odbicia, w przeciwnym razie otrzymają komunikat o błędzie typeload ze środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="db098-112">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="db098-113">Dodatkowe zestawy referencyjne usunąć metadanych (prywatne elementy członkowskie) z zestawów zawierających tylko metadane:</span><span class="sxs-lookup"><span data-stu-id="db098-113">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="db098-114">Zestaw odwołania ma tylko odwołania do potrzebne na powierzchni interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="db098-114">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="db098-115">Rzeczywiste zestawu może posiadać dodatkowe odwołania, powiązane z określonej implementacji.</span><span class="sxs-lookup"><span data-stu-id="db098-115">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="db098-116">Na przykład zestaw odwołania dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do wszystkich typów wymaganych do `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="db098-116">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="db098-117">Prywatne funkcji elementów członkowskich (metody, właściwości i zdarzenia) zostaną usunięte w przypadkach, gdy ich usunięcia ciemniejsza bez wpływu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="db098-117">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="db098-118">Jeśli istnieją nie `InternalsVisibleTo` atrybuty, są takie same dla wewnętrznej funkcji elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="db098-118">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="db098-119">Jednak wszystkie typy (w tym typy prywatny ani zagnieżdżony) są przechowywane w zestawów odwołań.</span><span class="sxs-lookup"><span data-stu-id="db098-119">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="db098-120">Wszystkie atrybuty są zachowywane (nawet wewnętrzny z nich).</span><span class="sxs-lookup"><span data-stu-id="db098-120">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="db098-121">Wszystkie metody wirtualne są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="db098-121">All virtual methods are kept.</span></span> <span data-ttu-id="db098-122">Jawne implementacje interfejsu są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="db098-122">Explicit interface implementations are kept.</span></span> <span data-ttu-id="db098-123">Jawnie implementowane właściwości i zdarzenia są przechowywane, zgodnie z ich metod dostępu wirtualne (i w związku z tym są przechowywane).</span><span class="sxs-lookup"><span data-stu-id="db098-123">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="db098-124">Wszystkie pola struktury są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="db098-124">All fields of a struct are kept.</span></span> <span data-ttu-id="db098-125">(To jest kandydatem do post-C# — uściślenia 7.1)</span><span class="sxs-lookup"><span data-stu-id="db098-125">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="db098-126">`/refonly` i [ `/refout` ](refout-compiler-option.md) wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="db098-126">The `/refonly` and [`/refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="db098-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db098-127">See also</span></span>
 [<span data-ttu-id="db098-128">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="db098-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="db098-129">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="db098-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
