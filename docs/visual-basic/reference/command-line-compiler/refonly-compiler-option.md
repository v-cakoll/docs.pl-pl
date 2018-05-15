---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8f6c15084ac9b1a07aef8a0311edfcc4a93337c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="98eb8-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98eb8-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="98eb8-103">**- Refonly** opcja wskazuje, czy główny wynik kompilacji powinien być zestaw odwołania, zamiast zestawu implementacji.</span><span class="sxs-lookup"><span data-stu-id="98eb8-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="98eb8-104">`-refonly` Parametr dyskretnie wyłącza Generowanie plików PDB, jak zestawy odwołań nie może zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="98eb8-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="98eb8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="98eb8-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="98eb8-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="98eb8-106">Remarks</span></span>

<span data-ttu-id="98eb8-107">Obsługa języka Visual Basic `-refout` przełącznika, począwszy od wersji 15 ustęp 3.</span><span class="sxs-lookup"><span data-stu-id="98eb8-107">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="98eb8-108">Zestawy referencyjne są tylko metadane zestawy, które zawierają metadanych, ale żaden kod implementacji.</span><span class="sxs-lookup"><span data-stu-id="98eb8-108">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="98eb8-109">Obejmują one informacje o wszystkim poza typy anonimowe typu i element członkowski.</span><span class="sxs-lookup"><span data-stu-id="98eb8-109">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="98eb8-110">Przyczyna przy użyciu `throw null` jest jednostki (w przeciwieństwie do treści), dzięki czemu PEVerify można uruchamiać i przekazywania (w związku z tym sprawdzanie poprawności kompletności metadanych).</span><span class="sxs-lookup"><span data-stu-id="98eb8-110">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="98eb8-111">Zestawy referencyjne obejmuje dane poziomu zestawu [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="98eb8-111">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="98eb8-112">Ten atrybut można określić w źródle (następnie kompilator nie będzie trzeba go syntetyzowania).</span><span class="sxs-lookup"><span data-stu-id="98eb8-112">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="98eb8-113">Z powodu tego atrybutu środowisk uruchomieniowych będzie odmawiał załadowania zestawów odwołań do wykonania (ale nadal może być załadowany w kontekstu reflection-only).</span><span class="sxs-lookup"><span data-stu-id="98eb8-113">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="98eb8-114">Narzędzia, które odzwierciedlać zestawów konieczne upewnij się, że są ładowane zestawów odwołań jako tylko do odbicia. w przeciwnym razie zwraca środowiska uruchomieniowego <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="98eb8-114">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="98eb8-115">`-refonly` i [ `-refout` ](refout-compiler-option.md) wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="98eb8-115">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="98eb8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98eb8-116">See also</span></span>
<span data-ttu-id="98eb8-117">[-refout](refout-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="98eb8-117">[-refout](refout-compiler-option.md) </span></span>  
[<span data-ttu-id="98eb8-118">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="98eb8-118">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="98eb8-119">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="98eb8-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)   
