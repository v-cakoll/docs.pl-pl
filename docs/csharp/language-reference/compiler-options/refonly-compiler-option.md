---
title: -jest opcja SET refonly (opcje kompilatora C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: c15308d27b504f22b266e28f6db0caf837ae36c5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421214"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="33133-102">-jest opcja SET refonly (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="33133-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="33133-103">**Jest opcja refonly -** opcja wskazuje, że zestaw odwołania powinny być danych wyjściowych zamiast zestawu implementacji jako główny wynik.</span><span class="sxs-lookup"><span data-stu-id="33133-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="33133-104">`-refonly` Parametr dyskretnie wyłącza podawania plików PDB, ponieważ zestawy odwołań nie można wykonać.</span><span class="sxs-lookup"><span data-stu-id="33133-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="33133-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="33133-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="33133-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33133-106">Remarks</span></span>

<span data-ttu-id="33133-107">Zestawy zawierające tylko metadane mieć ich treść metody zastąpione za pomocą jednego `throw null` treści, ale dołączone wszystkie elementy członkowskie z wyjątkiem typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="33133-107">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="33133-108">Przyczyna przy użyciu `throw null` treści (w przeciwieństwie do treści) jest tak, aby PEVerify można uruchomić i przekazać (dlatego sprawdzanie poprawności kompletność metadanych).</span><span class="sxs-lookup"><span data-stu-id="33133-108">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="33133-109">Zestawy referencyjne zawierają poziomie zestawu `ReferenceAssembly` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="33133-109">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="33133-110">Ten atrybut może być określony w źródle (następnie kompilator nie będzie konieczne jej syntetyzowania).</span><span class="sxs-lookup"><span data-stu-id="33133-110">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="33133-111">Z powodu tego atrybutu środowisk wykonawczych będzie odmawiał załadowania zestawy referencyjne do wykonania (ale nadal może być załadowany w trybie tylko do odbicia).</span><span class="sxs-lookup"><span data-stu-id="33133-111">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="33133-112">Narzędzia, które odzwierciedlają na potrzeby zestawów, upewnij się, że są one ładowane odwołań do zestawów jako tylko do odbicia, w przeciwnym razie otrzymają błąd typeload ze środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="33133-112">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="33133-113">Dodatkowo zestawy odwołań metadanych (prywatne składowe) należy usunąć z zestawów zawierających tylko metadane:</span><span class="sxs-lookup"><span data-stu-id="33133-113">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="33133-114">Zestaw odwołania ma tylko odwołania do to, czego potrzebuje na powierzchni interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="33133-114">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="33133-115">Rzeczywistych zestaw może mieć dodatkowe informacje związane z określonych implementacji.</span><span class="sxs-lookup"><span data-stu-id="33133-115">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="33133-116">Na przykład odwołanie do zestawu dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do wszystkich typów wymaganych do `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="33133-116">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="33133-117">Prywatne funkcji elementów członkowskich (metody, właściwości i zdarzenia) są usuwane w przypadku, gdy ich usunięcia ciemniejsza nie ma wpływu na kompilację.</span><span class="sxs-lookup"><span data-stu-id="33133-117">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="33133-118">W przypadku nie `InternalsVisibleTo` atrybutów, zrób to samo dla wewnętrznej funkcji elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="33133-118">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="33133-119">Jednak wszystkie typy (takie jak typy prywatny ani zagnieżdżony) są przechowywane w zestawach referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="33133-119">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="33133-120">Wszystkie atrybuty są utrzymywane (tymi nawet wewnętrznego).</span><span class="sxs-lookup"><span data-stu-id="33133-120">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="33133-121">Wszystkie metody wirtualne są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="33133-121">All virtual methods are kept.</span></span> <span data-ttu-id="33133-122">Jawne implementacje interfejsu są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="33133-122">Explicit interface implementations are kept.</span></span> <span data-ttu-id="33133-123">Jawnie implementowane właściwości i zdarzenia są zachowywane, zgodnie z ich metod dostępu wirtualne (i w związku z tym są przechowywane).</span><span class="sxs-lookup"><span data-stu-id="33133-123">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="33133-124">Wszystkie pola struktury są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="33133-124">All fields of a struct are kept.</span></span> <span data-ttu-id="33133-125">(To jest kandydatem do wpisu — C# — 7.1 refinement)</span><span class="sxs-lookup"><span data-stu-id="33133-125">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="33133-126">`-refonly` i [ `-refout` ](refout-compiler-option.md) opcje wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="33133-126">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="33133-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33133-127">See also</span></span>

- [<span data-ttu-id="33133-128">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="33133-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="33133-129">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="33133-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
