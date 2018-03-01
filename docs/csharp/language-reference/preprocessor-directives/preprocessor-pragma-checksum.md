---
title: "#Suma kontrolna pragma (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0604a559be25c300fcdc6041975306b465fc595f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="8a35e-102">#pragma checksum (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8a35e-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="8a35e-103">Generuje sumy kontrolne dla plików źródłowych pomóc w debugowaniu [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] stron.</span><span class="sxs-lookup"><span data-stu-id="8a35e-103">Generates checksums for source files to aid with debugging [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a35e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a35e-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a35e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a35e-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="8a35e-106">Nazwa pliku, który wymaga monitorowania na zmiany lub aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="8a35e-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="8a35e-107">Globalnie unikatowy identyfikator (GUID) dla pliku.</span><span class="sxs-lookup"><span data-stu-id="8a35e-107">The Globally Unique Identifier (GUID) for the file.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="8a35e-108">Ciąg reprezentujący liczbę bajtów sumy kontrolnej cyfr szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="8a35e-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="8a35e-109">Musi być parzysta liczba cyfr szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="8a35e-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="8a35e-110">Nieparzysta liczba cyfr powoduje ostrzeżenie kompilacji i dyrektywy są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="8a35e-110">An odd number of digits results in a compile-time warning, and the directive are  ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a35e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a35e-111">Remarks</span></span>  
 <span data-ttu-id="8a35e-112">Debuger programu Visual Studio korzysta z sumy kontrolnej, upewnij się, że zawsze znajdzie prawo źródła.</span><span class="sxs-lookup"><span data-stu-id="8a35e-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="8a35e-113">Kompilator oblicza sumę kontrolną pliku źródłowego, a następnie emituje dane wyjściowe do pliku programu (PDB) bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8a35e-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="8a35e-114">Debuger używa pliku PDB Aby porównać sumę kontrolną, która oblicza dla pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="8a35e-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="8a35e-115">To rozwiązanie nie działa w przypadku [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projektów, ponieważ jest obliczana sumy kontrolnej wygenerowanym pliku źródłowym, a nie plik .aspx.</span><span class="sxs-lookup"><span data-stu-id="8a35e-115">This solution does not work for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="8a35e-116">Aby rozwiązać ten problem, `#pragma checksum` zapewnia obsługę sumy kontrolnej [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] stron.</span><span class="sxs-lookup"><span data-stu-id="8a35e-116">To address this problem, `#pragma checksum` provides checksum support for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
 <span data-ttu-id="8a35e-117">Po utworzeniu [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projektu w [!INCLUDE[csprcs](~/includes/csprcs-md.md)], wygenerowanym pliku źródłowym zawiera sumę kontrolną dla plików .aspx, z którego jest generowany źródła.</span><span class="sxs-lookup"><span data-stu-id="8a35e-117">When you create an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] project in [!INCLUDE[csprcs](~/includes/csprcs-md.md)], the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="8a35e-118">Kompilator następnie zapisuje te informacje w pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="8a35e-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="8a35e-119">Jeśli nie wystąpi kompilator `#pragma checksum` dyrektywy w pliku, jego oblicza sumę kontrolną i zapisuje wartość w pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="8a35e-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a35e-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a35e-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a35e-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a35e-121">See Also</span></span>  
 [<span data-ttu-id="8a35e-122">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="8a35e-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8a35e-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8a35e-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8a35e-124">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="8a35e-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
