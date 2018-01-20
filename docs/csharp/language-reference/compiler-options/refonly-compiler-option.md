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
- refonly compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 25b0f6e024e194dff641fd5069755d0ea112a50b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="0e01f-102">-refonly (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="0e01f-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="0e01f-103">**- Refonly** opcja wskazuje, że zestaw odwołania powinny być danymi wyjściowymi zamiast zestawu implementacji, jako główny wynik.</span><span class="sxs-lookup"><span data-stu-id="0e01f-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="0e01f-104">`-refonly` Parametr dyskretnie wyłącza Generowanie plików PDB, jak zestawy odwołań nie może zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="0e01f-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e01f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e01f-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="0e01f-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e01f-106">Remarks</span></span>

<span data-ttu-id="0e01f-107">Zestawy tylko metadane mieć ich treści metody zastąpione pojedynczy `throw null` body, ale dołączone wszystkie elementy członkowskie z wyjątkiem typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="0e01f-107">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="0e01f-108">Przyczyna przy użyciu `throw null` jest jednostki (w przeciwieństwie do treści), dzięki czemu PEVerify można uruchamiać i przekazywania (w związku z tym sprawdzanie poprawności kompletności metadanych).</span><span class="sxs-lookup"><span data-stu-id="0e01f-108">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="0e01f-109">Zestawy referencyjne obejmuje dane poziomu zestawu `ReferenceAssembly` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0e01f-109">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="0e01f-110">Ten atrybut można określić w źródle (następnie kompilator nie będzie trzeba go syntetyzowania).</span><span class="sxs-lookup"><span data-stu-id="0e01f-110">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="0e01f-111">Z powodu tego atrybutu środowisk uruchomieniowych będzie odmawiał załadowania zestawów odwołań do wykonania (ale nadal może być załadowany w trybie tylko do odbicia).</span><span class="sxs-lookup"><span data-stu-id="0e01f-111">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="0e01f-112">Narzędzia, które odzwierciedlać na potrzebę zestawów upewnij się, że są ładowane zestawów odwołań w trybie tylko do odbicia, w przeciwnym razie otrzymają komunikat o błędzie typeload ze środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="0e01f-112">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="0e01f-113">Dodatkowe zestawy referencyjne usunąć metadanych (prywatne elementy członkowskie) z zestawów zawierających tylko metadane:</span><span class="sxs-lookup"><span data-stu-id="0e01f-113">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="0e01f-114">Zestaw odwołania ma tylko odwołania do potrzebne na powierzchni interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="0e01f-114">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="0e01f-115">Rzeczywiste zestawu może posiadać dodatkowe odwołania, powiązane z określonej implementacji.</span><span class="sxs-lookup"><span data-stu-id="0e01f-115">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="0e01f-116">Na przykład zestaw odwołania dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do wszystkich typów wymaganych do `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="0e01f-116">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="0e01f-117">Prywatne funkcji elementów członkowskich (metody, właściwości i zdarzenia) zostaną usunięte w przypadkach, gdy ich usunięcia ciemniejsza bez wpływu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0e01f-117">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="0e01f-118">Jeśli istnieją nie `InternalsVisibleTo` atrybuty, są takie same dla wewnętrznej funkcji elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="0e01f-118">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="0e01f-119">Jednak wszystkie typy (w tym typy prywatny ani zagnieżdżony) są przechowywane w zestawów odwołań.</span><span class="sxs-lookup"><span data-stu-id="0e01f-119">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="0e01f-120">Wszystkie atrybuty są zachowywane (nawet wewnętrzny z nich).</span><span class="sxs-lookup"><span data-stu-id="0e01f-120">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="0e01f-121">Wszystkie metody wirtualne są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="0e01f-121">All virtual methods are kept.</span></span> <span data-ttu-id="0e01f-122">Jawne implementacje interfejsu są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="0e01f-122">Explicit interface implementations are kept.</span></span> <span data-ttu-id="0e01f-123">Jawnie implementowane właściwości i zdarzenia są przechowywane, zgodnie z ich metod dostępu wirtualne (i w związku z tym są przechowywane).</span><span class="sxs-lookup"><span data-stu-id="0e01f-123">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="0e01f-124">Wszystkie pola struktury są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="0e01f-124">All fields of a struct are kept.</span></span> <span data-ttu-id="0e01f-125">(To jest kandydatem do post-C# — uściślenia 7.1)</span><span class="sxs-lookup"><span data-stu-id="0e01f-125">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="0e01f-126">`-refonly` i [ `-refout` ](refout-compiler-option.md) wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="0e01f-126">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e01f-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e01f-127">See also</span></span>
 [<span data-ttu-id="0e01f-128">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="0e01f-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="0e01f-129">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="0e01f-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
