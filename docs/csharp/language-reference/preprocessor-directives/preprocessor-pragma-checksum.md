---
title: '#pragma checksum (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 28a9ccfb9d36e648304a177294904ab1b7f18892
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45614508"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="224f2-102">#pragma checksum (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="224f2-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="224f2-103">Generuje sumy kontrolne dla plików źródłowych, aby pomóc w debugowaniu stron [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="224f2-103">Generates checksums for source files to aid with debugging [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="224f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="224f2-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a><span data-ttu-id="224f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="224f2-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="224f2-106">Nazwa pliku który wymaga monitorowania w celu zmiany lub aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="224f2-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="224f2-107">Globalnie unikatowy identyfikator (GUID) dla algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="224f2-107">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="224f2-108">Ciąg cyfr szesnastkowych reprezentujący liczbę bajtów sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="224f2-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="224f2-109">Musi być parzystą liczbą cyfr szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="224f2-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="224f2-110">Nieparzysta liczba cyfr powoduje ostrzeżenie kompilacji i dyrektywy są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="224f2-110">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="224f2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="224f2-111">Remarks</span></span>  
 <span data-ttu-id="224f2-112">Debuger programu Visual Studio używa sumy kontrolnej do sprawdzania, czy użyte zostało prawidłowe źródło.</span><span class="sxs-lookup"><span data-stu-id="224f2-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="224f2-113">Kompilator oblicza sumę kontrolną pliku źródłowego, a następnie przesyła dane wyjściowe do pliku bazy danych programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="224f2-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="224f2-114">Następnie debuger używa pliku PDB do porównania sumy kontrolnej obliczanej dla pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="224f2-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="224f2-115">To rozwiązanie nie działa w przypadku projektów [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)], ponieważ obliczana suma kontrolna jest przeznaczona dla wygenerowanego pliku źródłowego, a nie pliku aspx. </span><span class="sxs-lookup"><span data-stu-id="224f2-115">This solution does not work for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="224f2-116">Aby rozwiązać ten problem, dyrektywa `#pragma checksum` zapewnia obsługę sumy kontrolnej dla stron [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="224f2-116">To address this problem, `#pragma checksum` provides checksum support for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
 <span data-ttu-id="224f2-117">Po utworzeniu [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projekt w języku Visual C# wygenerowanym pliku źródłowym zawiera sumy kontrolnej pliku .aspx, z którego jest generowany źródła.</span><span class="sxs-lookup"><span data-stu-id="224f2-117">When you create an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="224f2-118">Następnie kompilator zapisuje te informacje w pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="224f2-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="224f2-119">Jeśli kompilator nie napotka w pliku dyrektywy `#pragma checksum`, oblicza jego sumę kontrolną i zapisuje jej wartość w pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="224f2-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="224f2-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="224f2-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="224f2-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="224f2-121">See Also</span></span>

- [<span data-ttu-id="224f2-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="224f2-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="224f2-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="224f2-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="224f2-124">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="224f2-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
