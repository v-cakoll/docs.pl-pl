---
title: -refonly (C# opcje kompilatora)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: eb62f98c5d548fe3583d3422eb7b6020a82c296a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606483"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="28acb-102">-refonly (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="28acb-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="28acb-103">Opcja **-refonly** wskazuje, że zestaw odwołania powinien być wyjściem, a nie zestawem implementacji, jako podstawowy wynik.</span><span class="sxs-lookup"><span data-stu-id="28acb-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="28acb-104">`-refonly` Parametr dyskretnie wyłącza umieszczanie plików PDB, ponieważ nie można wykonać zestawów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="28acb-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span> <span data-ttu-id="28acb-105">Ta opcja odnosi się do właściwości Project [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="28acb-105">This option corresponds to the [ProduceOnlyReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="28acb-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="28acb-106">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="28acb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28acb-107">Remarks</span></span>

<span data-ttu-id="28acb-108">Zestawy zawierające tylko metadane są zastępowane przez jedną `throw null` treść, ale obejmują wszystkie elementy członkowskie z wyjątkiem typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="28acb-108">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="28acb-109">Powodem używania `throw null` treści (w przeciwieństwie do braku treści) jest to, że PEVerify może działać i kończyć się powodzeniem (w związku z tym sprawdzanie kompletności metadanych).</span><span class="sxs-lookup"><span data-stu-id="28acb-109">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="28acb-110">Zestawy referencyjne zawierają atrybut na poziomie `ReferenceAssembly` zestawu.</span><span class="sxs-lookup"><span data-stu-id="28acb-110">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="28acb-111">Ten atrybut może być określony w źródle (a następnie kompilator nie będzie musiał przeprowadzić jego syntezy).</span><span class="sxs-lookup"><span data-stu-id="28acb-111">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="28acb-112">Ze względu na ten atrybut środowiska uruchomieniowe będą odrzucać ładowanie zestawów odwołań do wykonania (ale nadal mogą być ładowane w trybie tylko odbicie).</span><span class="sxs-lookup"><span data-stu-id="28acb-112">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="28acb-113">Narzędzia odzwierciedlające zestawy muszą mieć pewność, że ładują zestawy referencyjne jako tylko odbicie. w przeciwnym razie w środowisku uruchomieniowym wystąpi błąd typeload.</span><span class="sxs-lookup"><span data-stu-id="28acb-113">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="28acb-114">Zestawy referencyjne usuwają metadane (prywatne składowe) z zestawów samych metadanych:</span><span class="sxs-lookup"><span data-stu-id="28acb-114">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="28acb-115">Zestaw odniesienia zawiera odwołania do potrzebnych elementów interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="28acb-115">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="28acb-116">Rzeczywisty zestaw może zawierać dodatkowe odwołania dotyczące konkretnych implementacji.</span><span class="sxs-lookup"><span data-stu-id="28acb-116">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="28acb-117">Na przykład zestaw odwołania dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do żadnych typów wymaganych przez. `dynamic`</span><span class="sxs-lookup"><span data-stu-id="28acb-117">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="28acb-118">Prywatne funkcje — elementy członkowskie (metody, właściwości i zdarzenia) są usuwane w przypadkach, gdy ich usunięcie nie ma zauważalnego wpływu na kompilację.</span><span class="sxs-lookup"><span data-stu-id="28acb-118">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="28acb-119">Jeśli nie ma żadnych <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutów, wykonaj te same czynności w przypadku wewnętrznych funkcji.</span><span class="sxs-lookup"><span data-stu-id="28acb-119">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="28acb-120">Ale wszystkie typy (w tym typy prywatne lub zagnieżdżone) są przechowywane w zestawach referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="28acb-120">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="28acb-121">Wszystkie atrybuty są zachowywane (nawet wewnętrznie).</span><span class="sxs-lookup"><span data-stu-id="28acb-121">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="28acb-122">Wszystkie metody wirtualne są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="28acb-122">All virtual methods are kept.</span></span> <span data-ttu-id="28acb-123">Jawne implementacje interfejsu są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="28acb-123">Explicit interface implementations are kept.</span></span> <span data-ttu-id="28acb-124">Jawne zaimplementowane właściwości i zdarzenia są przechowywane, ponieważ ich metody dostępu są wirtualne (i dlatego są utrzymywane).</span><span class="sxs-lookup"><span data-stu-id="28acb-124">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="28acb-125">Wszystkie pola struktury są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="28acb-125">All fields of a struct are kept.</span></span> <span data-ttu-id="28acb-126">(Jest to kandydat dla uściślenia poC#--7,1)</span><span class="sxs-lookup"><span data-stu-id="28acb-126">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="28acb-127">Opcje `-refonly` [i`-refout`](refout-compiler-option.md) wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="28acb-127">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="28acb-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28acb-128">See also</span></span>

- [<span data-ttu-id="28acb-129">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="28acb-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="28acb-130">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="28acb-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
