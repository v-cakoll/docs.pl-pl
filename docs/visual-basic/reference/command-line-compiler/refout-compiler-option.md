---
title: -opcji refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582871"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="57316-102">-opcji refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57316-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="57316-103">Opcja **-opcji refout** określa ścieżkę pliku, w którym zestaw odniesienia powinien być wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="57316-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="57316-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57316-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="57316-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="57316-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="57316-106">Ścieżka i nazwa pliku zestawu odwołania.</span><span class="sxs-lookup"><span data-stu-id="57316-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="57316-107">Zwykle powinien znajdować się w podfolderze podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="57316-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="57316-108">Zalecaną konwencją (używaną przez program MSBuild) jest umieszczenie zestawu odwołania w podfolderze "ref/" względem podstawowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="57316-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="57316-109">Wszystkie foldery w `filepath` muszą istnieć; Kompilator nie tworzy ich.</span><span class="sxs-lookup"><span data-stu-id="57316-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="57316-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57316-110">Remarks</span></span>

<span data-ttu-id="57316-111">Visual Basic obsługuje przełącznik `-refout`, zaczynając od wersji 15,3.</span><span class="sxs-lookup"><span data-stu-id="57316-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="57316-112">Zestawy referencyjne są zestawami zawierającymi tylko metadane, które zawierają metadane, ale nie mają kodu implementacji.</span><span class="sxs-lookup"><span data-stu-id="57316-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="57316-113">Zawierają one informacje o typie i elemencie członkowskim dla wszystkiego, z wyjątkiem typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="57316-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="57316-114">Ich treści metod są zastępowane pojedynczą instrukcją `throw null`.</span><span class="sxs-lookup"><span data-stu-id="57316-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="57316-115">Przyczyną użycia `throw null` metod treści (w przeciwieństwie do braku treści) jest to, że PEVerify może być uruchomiona i zakończyła się powodzeniem (w związku z tym sprawdzanie kompletności metadanych).</span><span class="sxs-lookup"><span data-stu-id="57316-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="57316-116">Zestawy referencyjne zawierają atrybut [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="57316-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="57316-117">Ten atrybut może być określony w źródle (a następnie kompilator nie będzie musiał przeprowadzić jego syntezy).</span><span class="sxs-lookup"><span data-stu-id="57316-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="57316-118">Ze względu na ten atrybut środowiska uruchomieniowe odmawiają załadowania zestawów referencyjnych na potrzeby wykonywania (ale nadal mogą być ładowane w kontekście "tylko odbicie").</span><span class="sxs-lookup"><span data-stu-id="57316-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="57316-119">Narzędzia odzwierciedlające zestawy muszą mieć pewność, że ładują zestawy referencyjne jako odbicie. w przeciwnym razie środowisko uruchomieniowe zgłosi <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="57316-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="57316-120">Opcje `-refout` i [`-refonly`](refonly-compiler-option.md) wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="57316-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="57316-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57316-121">See also</span></span>

- [<span data-ttu-id="57316-122">-refonly</span><span class="sxs-lookup"><span data-stu-id="57316-122">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="57316-123">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57316-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="57316-124">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="57316-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
