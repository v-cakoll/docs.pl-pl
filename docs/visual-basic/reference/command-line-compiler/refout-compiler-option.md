---
title: -opcji refout (Visual Basic)
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
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999471"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="5c227-102">-opcji refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c227-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="5c227-103">**- Opcji refout** opcja określa ścieżkę pliku, gdzie zestaw odwołania powinny być danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5c227-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="5c227-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c227-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="5c227-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5c227-105">Arguments</span></span>

 <span data-ttu-id="5c227-106">`filepath` Ścieżka i nazwa pliku zestawu odwołania.</span><span class="sxs-lookup"><span data-stu-id="5c227-106">`filepath` The path and filename of the reference assembly.</span></span> <span data-ttu-id="5c227-107">Ogólnie należy się w podfolderze podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5c227-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="5c227-108">Zalecane Konwencji (używane przez program MSBuild) jest umieszczenie zestawu odwołania w "ref /" podfolder względem podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5c227-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="5c227-109">Wszystkie foldery w `filepath` musi istnieć; kompilator nie tworzy je.</span><span class="sxs-lookup"><span data-stu-id="5c227-109">All folders in `filepath` must exist; the compiler does not create them.</span></span> 

## <a name="remarks"></a><span data-ttu-id="5c227-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c227-110">Remarks</span></span>

<span data-ttu-id="5c227-111">Obsługa języka Visual Basic `-refout` przełącznika, począwszy od wersji 15.3.</span><span class="sxs-lookup"><span data-stu-id="5c227-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="5c227-112">Zestawy referencyjne są tylko metadane zestawów, które zawierają metadane, ale bez kodu realizacji.</span><span class="sxs-lookup"><span data-stu-id="5c227-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="5c227-113">Obejmują one informacje typów i elementów członkowskich dla wszystkim, z wyjątkiem typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="5c227-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="5c227-114">Ich treść metody są zastępowane za pomocą jednego `throw null` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5c227-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="5c227-115">Przyczyna przy użyciu `throw null` treści metod (w przeciwieństwie do treści) jest tak, aby PEVerify można uruchomić i przekazać (dlatego sprawdzanie poprawności kompletność metadanych).</span><span class="sxs-lookup"><span data-stu-id="5c227-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="5c227-116">Zestawy referencyjne zawierają poziomie zestawu [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5c227-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="5c227-117">Ten atrybut może być określony w źródle (następnie kompilator nie będzie konieczne jej syntetyzowania).</span><span class="sxs-lookup"><span data-stu-id="5c227-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="5c227-118">Z powodu tego atrybutu środowisk wykonawczych odmawiał załadowania zestawy referencyjne do wykonania (ale nadal może być załadowany w kontekstu reflection-only).</span><span class="sxs-lookup"><span data-stu-id="5c227-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="5c227-119">Narzędzia, które odzwierciedlają zestawów, należy upewnić się, że są one ładowane odwołań do zestawów jako tylko do odbicia. w przeciwnym wypadku środowisko wykonawcze zgłasza <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="5c227-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="5c227-120">`-refout` i [ `-refonly` ](refonly-compiler-option.md) opcje wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="5c227-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c227-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c227-121">See Also</span></span>
<span data-ttu-id="5c227-122">[-jest opcja refonly](refonly-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="5c227-122">[-refonly](refonly-compiler-option.md) </span></span>  
[<span data-ttu-id="5c227-123">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c227-123">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="5c227-124">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="5c227-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)  

