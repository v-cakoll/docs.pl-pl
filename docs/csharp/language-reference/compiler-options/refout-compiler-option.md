---
title: -opcji refout (C# opcje kompilatora)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 97cbf540527d0449387b71bb1d97df95b6a4aba4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602503"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="73b40-102">-opcji refout (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="73b40-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="73b40-103">Opcja **-opcji refout** określa ścieżkę pliku, w którym zestaw odniesienia powinien być wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="73b40-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="73b40-104">Powoduje to przetłumaczenie na `metadataPeStream` w interfejsie API emisji.</span><span class="sxs-lookup"><span data-stu-id="73b40-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="73b40-105">Ta opcja odnosi się do właściwości Project [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="73b40-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="73b40-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="73b40-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="73b40-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="73b40-107">Arguments</span></span>

 <span data-ttu-id="73b40-108">`filepath`Ścieżka do zestawu referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="73b40-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="73b40-109">Zwykle powinna być zgodna z zestawem podstawowym.</span><span class="sxs-lookup"><span data-stu-id="73b40-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="73b40-110">Zalecaną konwencją (używaną przez program MSBuild) jest umieszczenie zestawu odwołania w podfolderze "ref/" względem podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="73b40-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="73b40-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73b40-111">Remarks</span></span>

<span data-ttu-id="73b40-112">Zestawy zawierające tylko metadane są zastępowane przez jedną `throw null` treść, ale obejmują wszystkie elementy członkowskie z wyjątkiem typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="73b40-112">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="73b40-113">Powodem używania `throw null` treści (w przeciwieństwie do braku treści) jest to, że PEVerify może działać i kończyć się powodzeniem (w związku z tym sprawdzanie kompletności metadanych).</span><span class="sxs-lookup"><span data-stu-id="73b40-113">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="73b40-114">Zestawy referencyjne zawierają atrybut na poziomie `ReferenceAssembly` zestawu.</span><span class="sxs-lookup"><span data-stu-id="73b40-114">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="73b40-115">Ten atrybut może być określony w źródle (a następnie kompilator nie będzie musiał przeprowadzić jego syntezy).</span><span class="sxs-lookup"><span data-stu-id="73b40-115">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="73b40-116">Ze względu na ten atrybut środowiska uruchomieniowe będą odrzucać ładowanie zestawów odwołań do wykonania (ale nadal mogą być ładowane w trybie tylko odbicie).</span><span class="sxs-lookup"><span data-stu-id="73b40-116">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="73b40-117">Narzędzia odzwierciedlające zestawy muszą mieć pewność, że ładują zestawy referencyjne jako tylko odbicie. w przeciwnym razie w środowisku uruchomieniowym wystąpi błąd typeload.</span><span class="sxs-lookup"><span data-stu-id="73b40-117">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="73b40-118">Zestawy referencyjne usuwają metadane (prywatne składowe) z zestawów samych metadanych:</span><span class="sxs-lookup"><span data-stu-id="73b40-118">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="73b40-119">Zestaw odniesienia zawiera odwołania do potrzebnych elementów interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="73b40-119">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="73b40-120">Rzeczywisty zestaw może zawierać dodatkowe odwołania dotyczące konkretnych implementacji.</span><span class="sxs-lookup"><span data-stu-id="73b40-120">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="73b40-121">Na przykład zestaw odwołania dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do żadnych typów wymaganych przez. `dynamic`</span><span class="sxs-lookup"><span data-stu-id="73b40-121">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="73b40-122">Prywatne funkcje — elementy członkowskie (metody, właściwości i zdarzenia) są usuwane w przypadkach, gdy ich usunięcie nie ma zauważalnego wpływu na kompilację.</span><span class="sxs-lookup"><span data-stu-id="73b40-122">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="73b40-123">Jeśli nie ma żadnych <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutów, wykonaj te same czynności w przypadku wewnętrznych funkcji.</span><span class="sxs-lookup"><span data-stu-id="73b40-123">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="73b40-124">Ale wszystkie typy (w tym typy prywatne lub zagnieżdżone) są przechowywane w zestawach referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="73b40-124">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="73b40-125">Wszystkie atrybuty są zachowywane (nawet wewnętrznie).</span><span class="sxs-lookup"><span data-stu-id="73b40-125">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="73b40-126">Wszystkie metody wirtualne są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="73b40-126">All virtual methods are kept.</span></span> <span data-ttu-id="73b40-127">Jawne implementacje interfejsu są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="73b40-127">Explicit interface implementations are kept.</span></span> <span data-ttu-id="73b40-128">Jawne zaimplementowane właściwości i zdarzenia są przechowywane, ponieważ ich metody dostępu są wirtualne (i dlatego są utrzymywane).</span><span class="sxs-lookup"><span data-stu-id="73b40-128">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="73b40-129">Wszystkie pola struktury są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="73b40-129">All fields of a struct are kept.</span></span> <span data-ttu-id="73b40-130">(Jest to kandydat dla uściślenia poC#--7,1)</span><span class="sxs-lookup"><span data-stu-id="73b40-130">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="73b40-131">Opcje `-refout` [i`-refonly`](refonly-compiler-option.md) wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="73b40-131">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="73b40-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73b40-132">See also</span></span>

- [<span data-ttu-id="73b40-133">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="73b40-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="73b40-134">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="73b40-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
