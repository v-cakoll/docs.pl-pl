---
title: -opcji refout (opcje kompilatora C#)
ms.date: 08/08/2017
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
ms.openlocfilehash: 34f7b62c0d9a14c52dde0ddd4ac0d5c29a3b5b75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662468"
---
# <a name="-refout-c-compiler-options"></a><span data-ttu-id="bb68e-102">-opcji refout (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="bb68e-102">-refout (C# Compiler Options)</span></span>

<span data-ttu-id="bb68e-103">**- Opcji refout** opcja określa ścieżkę pliku, gdzie zestaw odwołania powinny być danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="bb68e-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="bb68e-104">Przekłada się to `metadataPeStream` w interfejsie API emisji.</span><span class="sxs-lookup"><span data-stu-id="bb68e-104">This translates to `metadataPeStream` in the Emit API.</span></span> <span data-ttu-id="bb68e-105">Ta opcja odnosi się do [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) właściwość MSBuild projektu.</span><span class="sxs-lookup"><span data-stu-id="bb68e-105">This option corresponds to the [ProduceReferenceAssembly](/visualstudio/msbuild/common-msbuild-project-properties) project property of MSBuild.</span></span>

## <a name="syntax"></a><span data-ttu-id="bb68e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb68e-106">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="bb68e-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bb68e-107">Arguments</span></span>

 <span data-ttu-id="bb68e-108">`filepath` Ścieżka pliku dla zestawu odwołania.</span><span class="sxs-lookup"><span data-stu-id="bb68e-108">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="bb68e-109">Zazwyczaj powinien odpowiadać okresowi istnienia podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="bb68e-109">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="bb68e-110">Zalecane Konwencji (używane przez program MSBuild) jest umieszczenie zestawu odwołania w "ref /" podfolder względem podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="bb68e-110">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="bb68e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb68e-111">Remarks</span></span>

<span data-ttu-id="bb68e-112">Zestawy zawierające tylko metadane mieć ich treść metody zastąpione za pomocą jednego `throw null` treści, ale dołączone wszystkie elementy członkowskie z wyjątkiem typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="bb68e-112">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="bb68e-113">Przyczyna przy użyciu `throw null` treści (w przeciwieństwie do treści) jest tak, aby PEVerify można uruchomić i przekazać (dlatego sprawdzanie poprawności kompletność metadanych).</span><span class="sxs-lookup"><span data-stu-id="bb68e-113">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="bb68e-114">Zestawy referencyjne zawierają poziomie zestawu `ReferenceAssembly` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bb68e-114">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="bb68e-115">Ten atrybut może być określony w źródle (następnie kompilator nie będzie konieczne jej syntetyzowania).</span><span class="sxs-lookup"><span data-stu-id="bb68e-115">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="bb68e-116">Z powodu tego atrybutu środowisk wykonawczych będzie odmawiał załadowania zestawy referencyjne do wykonania (ale nadal może być załadowany w trybie tylko do odbicia).</span><span class="sxs-lookup"><span data-stu-id="bb68e-116">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="bb68e-117">Narzędzia, które odzwierciedlają na potrzeby zestawów, upewnij się, że są one ładowane odwołań do zestawów jako tylko do odbicia, w przeciwnym razie otrzymają błąd typeload ze środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="bb68e-117">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="bb68e-118">Dodatkowo zestawy odwołań metadanych (prywatne składowe) należy usunąć z zestawów zawierających tylko metadane:</span><span class="sxs-lookup"><span data-stu-id="bb68e-118">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="bb68e-119">Zestaw odwołania ma tylko odwołania do to, czego potrzebuje na powierzchni interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="bb68e-119">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="bb68e-120">Rzeczywistych zestaw może mieć dodatkowe informacje związane z określonych implementacji.</span><span class="sxs-lookup"><span data-stu-id="bb68e-120">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="bb68e-121">Na przykład odwołanie do zestawu dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do wszystkich typów wymaganych do `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="bb68e-121">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="bb68e-122">Prywatne funkcji elementów członkowskich (metody, właściwości i zdarzenia) są usuwane w przypadku, gdy ich usunięcia ciemniejsza nie ma wpływu na kompilację.</span><span class="sxs-lookup"><span data-stu-id="bb68e-122">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="bb68e-123">W przypadku nie <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutów, zrób to samo dla wewnętrznej funkcji elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="bb68e-123">If there are no <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="bb68e-124">Jednak wszystkie typy (takie jak typy prywatny ani zagnieżdżony) są przechowywane w zestawach referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="bb68e-124">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="bb68e-125">Wszystkie atrybuty są utrzymywane (tymi nawet wewnętrznego).</span><span class="sxs-lookup"><span data-stu-id="bb68e-125">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="bb68e-126">Wszystkie metody wirtualne są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="bb68e-126">All virtual methods are kept.</span></span> <span data-ttu-id="bb68e-127">Jawne implementacje interfejsu są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="bb68e-127">Explicit interface implementations are kept.</span></span> <span data-ttu-id="bb68e-128">Jawnie implementowane właściwości i zdarzenia są zachowywane, zgodnie z ich metod dostępu wirtualne (i w związku z tym są przechowywane).</span><span class="sxs-lookup"><span data-stu-id="bb68e-128">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="bb68e-129">Wszystkie pola struktury są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="bb68e-129">All fields of a struct are kept.</span></span> <span data-ttu-id="bb68e-130">(To jest kandydatem do wpisu — C# — 7.1 refinement)</span><span class="sxs-lookup"><span data-stu-id="bb68e-130">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="bb68e-131">`-refout` i [ `-refonly` ](refonly-compiler-option.md) opcje wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="bb68e-131">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb68e-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb68e-132">See also</span></span>

- [<span data-ttu-id="bb68e-133">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="bb68e-133">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="bb68e-134">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="bb68e-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
