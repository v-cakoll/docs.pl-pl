---
title: -jest opcja SET refonly (opcje kompilatora C#)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: 97245b50881d687572c1ae1df649651831822094
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662481"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="ef47a-102">-jest opcja SET refonly (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="ef47a-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="ef47a-103">**Jest opcja refonly -** opcja wskazuje, że zestaw odwołania powinny być danych wyjściowych zamiast zestawu implementacji jako główny wynik.</span><span class="sxs-lookup"><span data-stu-id="ef47a-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="ef47a-104">`-refonly` Parametr dyskretnie wyłącza podawania plików PDB, ponieważ zestawy odwołań nie można wykonać.</span><span class="sxs-lookup"><span data-stu-id="ef47a-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="ef47a-105">Ta opcja odnosi się do [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) właściwość MSBuild projektu.</span><span class="sxs-lookup"><span data-stu-id="ef47a-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef47a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef47a-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="ef47a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef47a-107">Remarks</span></span>

<span data-ttu-id="ef47a-108">Zestawy zawierające tylko metadane mieć ich treść metody zastąpione za pomocą jednego `throw null` treści, ale dołączone wszystkie elementy członkowskie z wyjątkiem typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="ef47a-108">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="ef47a-109">Przyczyna przy użyciu `throw null` treści (w przeciwieństwie do treści) jest tak, aby PEVerify można uruchomić i przekazać (dlatego sprawdzanie poprawności kompletność metadanych).</span><span class="sxs-lookup"><span data-stu-id="ef47a-109">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="ef47a-110">Zestawy referencyjne zawierają poziomie zestawu `ReferenceAssembly` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ef47a-110">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="ef47a-111">Ten atrybut może być określony w źródle (następnie kompilator nie będzie konieczne jej syntetyzowania).</span><span class="sxs-lookup"><span data-stu-id="ef47a-111">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="ef47a-112">Z powodu tego atrybutu środowisk wykonawczych będzie odmawiał załadowania zestawy referencyjne do wykonania (ale nadal może być załadowany w trybie tylko do odbicia).</span><span class="sxs-lookup"><span data-stu-id="ef47a-112">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="ef47a-113">Narzędzia, które odzwierciedlają na potrzeby zestawów, upewnij się, że są one ładowane odwołań do zestawów jako tylko do odbicia, w przeciwnym razie otrzymają błąd typeload ze środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="ef47a-113">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="ef47a-114">Dodatkowo zestawy odwołań metadanych (prywatne składowe) należy usunąć z zestawów zawierających tylko metadane:</span><span class="sxs-lookup"><span data-stu-id="ef47a-114">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="ef47a-115">Zestaw odwołania ma tylko odwołania do to, czego potrzebuje na powierzchni interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="ef47a-115">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="ef47a-116">Rzeczywistych zestaw może mieć dodatkowe informacje związane z określonych implementacji.</span><span class="sxs-lookup"><span data-stu-id="ef47a-116">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="ef47a-117">Na przykład odwołanie do zestawu dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do wszystkich typów wymaganych do `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="ef47a-117">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="ef47a-118">Prywatne funkcji elementów członkowskich (metody, właściwości i zdarzenia) są usuwane w przypadku, gdy ich usunięcia ciemniejsza nie ma wpływu na kompilację.</span><span class="sxs-lookup"><span data-stu-id="ef47a-118">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="ef47a-119">W przypadku nie <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutów, zrób to samo dla wewnętrznej funkcji elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="ef47a-119">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="ef47a-120">Jednak wszystkie typy (takie jak typy prywatny ani zagnieżdżony) są przechowywane w zestawach referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="ef47a-120">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="ef47a-121">Wszystkie atrybuty są utrzymywane (tymi nawet wewnętrznego).</span><span class="sxs-lookup"><span data-stu-id="ef47a-121">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="ef47a-122">Wszystkie metody wirtualne są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="ef47a-122">All virtual methods are kept.</span></span> <span data-ttu-id="ef47a-123">Jawne implementacje interfejsu są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="ef47a-123">Explicit interface implementations are kept.</span></span> <span data-ttu-id="ef47a-124">Jawnie implementowane właściwości i zdarzenia są zachowywane, zgodnie z ich metod dostępu wirtualne (i w związku z tym są przechowywane).</span><span class="sxs-lookup"><span data-stu-id="ef47a-124">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="ef47a-125">Wszystkie pola struktury są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="ef47a-125">All fields of a struct are kept.</span></span> <span data-ttu-id="ef47a-126">(To jest kandydatem do wpisu — C# — 7.1 refinement)</span><span class="sxs-lookup"><span data-stu-id="ef47a-126">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="ef47a-127">`-refonly` i [ `-refout` ](refout-compiler-option.md) opcje wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="ef47a-127">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef47a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef47a-128">See also</span></span>

- [<span data-ttu-id="ef47a-129">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="ef47a-129">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="ef47a-130">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ef47a-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
