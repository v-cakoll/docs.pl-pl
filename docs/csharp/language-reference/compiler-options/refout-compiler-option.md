---
title: -refout (opcje kompilatora C#)
ms.date: 08/08/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fbae6f461304c37ba2ef10da16b5d520377bb225
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="f9b36-102">-refout (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="f9b36-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="f9b36-103">**- Refout** opcja określa ścieżkę pliku, w którym zestaw odwołania powinny być danymi wyjściowymi.</span><span class="sxs-lookup"><span data-stu-id="f9b36-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="f9b36-104">Przekłada się `metadataPeStream` w interfejsie API emisji.</span><span class="sxs-lookup"><span data-stu-id="f9b36-104">This translates to `metadataPeStream` in the Emit API.</span></span>

## <a name="syntax"></a><span data-ttu-id="f9b36-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9b36-105">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="f9b36-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f9b36-106">Arguments</span></span>

 <span data-ttu-id="f9b36-107">`filepath`Ścieżka zestawu odwołania.</span><span class="sxs-lookup"><span data-stu-id="f9b36-107">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="f9b36-108">Zazwyczaj powinien odpowiadać okresowi istnienia podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f9b36-108">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="f9b36-109">Zalecane Konwencji (używane przez program MSBuild) jest umieszczenie zestawu odwołania w "ref /" podfolderu względem podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f9b36-109">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9b36-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9b36-110">Remarks</span></span>

<span data-ttu-id="f9b36-111">Zestawy tylko metadane mieć ich treści metody zastąpione pojedynczy `throw null` body, ale dołączone wszystkie elementy członkowskie z wyjątkiem typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="f9b36-111">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="f9b36-112">Przyczyna przy użyciu `throw null` jest jednostki (w przeciwieństwie do treści), dzięki czemu PEVerify można uruchamiać i przekazywania (w związku z tym sprawdzanie poprawności kompletności metadanych).</span><span class="sxs-lookup"><span data-stu-id="f9b36-112">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="f9b36-113">Zestawy referencyjne obejmuje dane poziomu zestawu `ReferenceAssembly` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f9b36-113">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="f9b36-114">Ten atrybut można określić w źródle (następnie kompilator nie będzie trzeba go syntetyzowania).</span><span class="sxs-lookup"><span data-stu-id="f9b36-114">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="f9b36-115">Z powodu tego atrybutu środowisk uruchomieniowych będzie odmawiał załadowania zestawów odwołań do wykonania (ale nadal może być załadowany w trybie tylko do odbicia).</span><span class="sxs-lookup"><span data-stu-id="f9b36-115">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="f9b36-116">Narzędzia, które odzwierciedlać na potrzebę zestawów upewnij się, że są ładowane zestawów odwołań w trybie tylko do odbicia, w przeciwnym razie otrzymają komunikat o błędzie typeload ze środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f9b36-116">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="f9b36-117">Dodatkowe zestawy referencyjne usunąć metadanych (prywatne elementy członkowskie) z zestawów zawierających tylko metadane:</span><span class="sxs-lookup"><span data-stu-id="f9b36-117">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="f9b36-118">Zestaw odwołania ma tylko odwołania do potrzebne na powierzchni interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="f9b36-118">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="f9b36-119">Rzeczywiste zestawu może posiadać dodatkowe odwołania, powiązane z określonej implementacji.</span><span class="sxs-lookup"><span data-stu-id="f9b36-119">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="f9b36-120">Na przykład zestaw odwołania dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do wszystkich typów wymaganych do `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="f9b36-120">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="f9b36-121">Prywatne funkcji elementów członkowskich (metody, właściwości i zdarzenia) zostaną usunięte w przypadkach, gdy ich usunięcia ciemniejsza bez wpływu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f9b36-121">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="f9b36-122">Jeśli istnieją nie `InternalsVisibleTo` atrybuty, są takie same dla wewnętrznej funkcji elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="f9b36-122">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="f9b36-123">Jednak wszystkie typy (w tym typy prywatny ani zagnieżdżony) są przechowywane w zestawów odwołań.</span><span class="sxs-lookup"><span data-stu-id="f9b36-123">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="f9b36-124">Wszystkie atrybuty są zachowywane (nawet wewnętrzny z nich).</span><span class="sxs-lookup"><span data-stu-id="f9b36-124">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="f9b36-125">Wszystkie metody wirtualne są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="f9b36-125">All virtual methods are kept.</span></span> <span data-ttu-id="f9b36-126">Jawne implementacje interfejsu są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="f9b36-126">Explicit interface implementations are kept.</span></span> <span data-ttu-id="f9b36-127">Jawnie implementowane właściwości i zdarzenia są przechowywane, zgodnie z ich metod dostępu wirtualne (i w związku z tym są przechowywane).</span><span class="sxs-lookup"><span data-stu-id="f9b36-127">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="f9b36-128">Wszystkie pola struktury są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="f9b36-128">All fields of a struct are kept.</span></span> <span data-ttu-id="f9b36-129">(To jest kandydatem do post-C# — uściślenia 7.1)</span><span class="sxs-lookup"><span data-stu-id="f9b36-129">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="f9b36-130">`-refout` i [ `-refonly` ](refonly-compiler-option.md) wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="f9b36-130">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9b36-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9b36-131">See Also</span></span>
 [<span data-ttu-id="f9b36-132">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="f9b36-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="f9b36-133">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="f9b36-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
