---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21cea76f31bdf2ac5fcf434ee759f874f917617b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653536"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="7c5c5-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c5c5-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="7c5c5-103">**- Refout** opcja określa ścieżkę pliku, w którym zestaw odwołania powinny być danymi wyjściowymi.</span><span class="sxs-lookup"><span data-stu-id="7c5c5-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="7c5c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c5c5-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="7c5c5-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7c5c5-105">Arguments</span></span>

 <span data-ttu-id="7c5c5-106">`filepath` Ścieżka i nazwa pliku zestawu odwołania.</span><span class="sxs-lookup"><span data-stu-id="7c5c5-106">`filepath` The path and filename of the reference assembly.</span></span> <span data-ttu-id="7c5c5-107">Ogólnie należy w podfolderze podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7c5c5-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="7c5c5-108">Zalecane Konwencji (używane przez program MSBuild) jest umieszczenie zestawu odwołania w "ref /" podfolderu względem podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7c5c5-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="7c5c5-109">Wszystkie foldery w `filepath` musi istnieć; kompilator nie je utworzyć.</span><span class="sxs-lookup"><span data-stu-id="7c5c5-109">All folders in `filepath` must exist; the compiler does not create them.</span></span> 

## <a name="remarks"></a><span data-ttu-id="7c5c5-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c5c5-110">Remarks</span></span>

<span data-ttu-id="7c5c5-111">Obsługa języka Visual Basic `-refout` przełącznika, począwszy od wersji 15 ustęp 3.</span><span class="sxs-lookup"><span data-stu-id="7c5c5-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="7c5c5-112">Zestawy referencyjne są tylko metadane zestawy, które zawierają metadanych, ale żaden kod implementacji.</span><span class="sxs-lookup"><span data-stu-id="7c5c5-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="7c5c5-113">Obejmują one informacje o wszystkim poza typy anonimowe typu i element członkowski.</span><span class="sxs-lookup"><span data-stu-id="7c5c5-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="7c5c5-114">Ich treści metody są zamieniane na jeden `throw null` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7c5c5-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="7c5c5-115">Przyczyna przy użyciu `throw null` treści metody (w przeciwieństwie do treści) jest tak, aby PEVerify można uruchomić i przekazywania (w związku z tym sprawdzanie poprawności kompletności metadanych).</span><span class="sxs-lookup"><span data-stu-id="7c5c5-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="7c5c5-116">Zestawy referencyjne obejmuje dane poziomu zestawu [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7c5c5-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="7c5c5-117">Ten atrybut można określić w źródle (następnie kompilator nie będzie trzeba go syntetyzowania).</span><span class="sxs-lookup"><span data-stu-id="7c5c5-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="7c5c5-118">Z powodu tego atrybutu środowisk uruchomieniowych odmówić załadować zestawów odwołań do wykonania (ale nadal może być załadowany w kontekstu reflection-only).</span><span class="sxs-lookup"><span data-stu-id="7c5c5-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="7c5c5-119">Narzędzia, które odzwierciedlać zestawów konieczne upewnij się, że są ładowane zestawów odwołań jako tylko do odbicia. w przeciwnym razie zwraca środowiska uruchomieniowego <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="7c5c5-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="7c5c5-120">`-refout` i [ `-refonly` ](refonly-compiler-option.md) wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="7c5c5-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c5c5-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c5c5-121">See Also</span></span>
<span data-ttu-id="7c5c5-122">[-refonly](refonly-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="7c5c5-122">[-refonly](refonly-compiler-option.md) </span></span>  
[<span data-ttu-id="7c5c5-123">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7c5c5-123">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="7c5c5-124">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="7c5c5-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)  

