---
title: -jest opcja SET refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: 047b8b148e616c8ad94f55844f8bc4063a9e5cd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528930"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="15fa9-102">-jest opcja SET refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15fa9-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="15fa9-103">**Jest opcja refonly -** opcja wskazuje, że główny wynik kompilacji należy zamiast zestawu implementacji zestawu odwołania.</span><span class="sxs-lookup"><span data-stu-id="15fa9-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="15fa9-104">`-refonly` Parametr dyskretnie wyłącza podawania plików PDB, ponieważ zestawy odwołań nie można wykonać.</span><span class="sxs-lookup"><span data-stu-id="15fa9-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="15fa9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="15fa9-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="15fa9-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15fa9-106">Remarks</span></span>

<span data-ttu-id="15fa9-107">Obsługa języka Visual Basic `-refout` przełącznika, począwszy od wersji 15.3.</span><span class="sxs-lookup"><span data-stu-id="15fa9-107">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="15fa9-108">Zestawy referencyjne są tylko metadane zestawów, które zawierają metadane, ale bez kodu realizacji.</span><span class="sxs-lookup"><span data-stu-id="15fa9-108">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="15fa9-109">Obejmują one informacje typów i elementów członkowskich dla wszystkim, z wyjątkiem typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="15fa9-109">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="15fa9-110">Przyczyna przy użyciu `throw null` treści (w przeciwieństwie do treści) jest tak, aby PEVerify można uruchomić i przekazać (dlatego sprawdzanie poprawności kompletność metadanych).</span><span class="sxs-lookup"><span data-stu-id="15fa9-110">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="15fa9-111">Zestawy referencyjne zawierają poziomie zestawu [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="15fa9-111">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="15fa9-112">Ten atrybut może być określony w źródle (następnie kompilator nie będzie konieczne jej syntetyzowania).</span><span class="sxs-lookup"><span data-stu-id="15fa9-112">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="15fa9-113">Z powodu tego atrybutu środowisk wykonawczych będzie odmawiał załadowania zestawy referencyjne do wykonania (ale nadal może być załadowany w kontekstu reflection-only).</span><span class="sxs-lookup"><span data-stu-id="15fa9-113">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="15fa9-114">Narzędzia, które odzwierciedlają zestawów, należy upewnić się, że są one ładowane odwołań do zestawów jako tylko do odbicia. w przeciwnym wypadku środowisko wykonawcze zgłasza <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="15fa9-114">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="15fa9-115">`-refonly` i [ `-refout` ](refout-compiler-option.md) opcje wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="15fa9-115">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="15fa9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15fa9-116">See also</span></span>
- [<span data-ttu-id="15fa9-117">-refout</span><span class="sxs-lookup"><span data-stu-id="15fa9-117">-refout</span></span>](refout-compiler-option.md)
- [<span data-ttu-id="15fa9-118">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15fa9-118">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="15fa9-119">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="15fa9-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
