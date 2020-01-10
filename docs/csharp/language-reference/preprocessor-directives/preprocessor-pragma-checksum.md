---
title: '#pragma — C# odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 1bbb404e1183daa5e68e512e7439b6ae52abd605
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712484"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="32f61-102">#pragma checksum (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="32f61-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="32f61-103">Generuje sumy kontrolne dla plików źródłowych, aby pomóc w debugowaniu stron ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="32f61-103">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32f61-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32f61-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="32f61-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32f61-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="32f61-106">Nazwa pliku, który wymaga monitorowania pod kątem zmian lub aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="32f61-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="32f61-107">Unikatowy identyfikator globalny (GUID) algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="32f61-107">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="32f61-108">Ciąg cyfr szesnastkowych reprezentujący liczbę bajtów sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="32f61-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="32f61-109">Musi być parzystą liczbą cyfr szesnastkowych.</span><span class="sxs-lookup"><span data-stu-id="32f61-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="32f61-110">Nieparzysta liczba cyfr skutkuje ostrzeżeniem w czasie kompilacji, a dyrektywa jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="32f61-110">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32f61-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32f61-111">Remarks</span></span>  
 <span data-ttu-id="32f61-112">Debuger programu Visual Studio używa sumy kontrolnej do sprawdzania, czy użyte zostało prawidłowe źródło.</span><span class="sxs-lookup"><span data-stu-id="32f61-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="32f61-113">Kompilator oblicza sumę kontrolną pliku źródłowego, a następnie przesyła dane wyjściowe do pliku bazy danych programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="32f61-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="32f61-114">Następnie debuger używa pliku PDB do porównania sumy kontrolnej obliczanej dla pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="32f61-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="32f61-115">To rozwiązanie nie działa w przypadku projektów ASP.NET, ponieważ obliczona suma kontrolna jest dla wygenerowanego pliku źródłowego, a nie pliku. aspx.</span><span class="sxs-lookup"><span data-stu-id="32f61-115">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="32f61-116">Aby rozwiązać ten problem, `#pragma checksum` zapewnia obsługę sum kontrolnych dla stron ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="32f61-116">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="32f61-117">Podczas tworzenia projektu ASP.NET w wizualizacji C#wygenerowany plik źródłowy zawiera sumę kontrolną dla pliku. aspx, z którego jest generowane źródło.</span><span class="sxs-lookup"><span data-stu-id="32f61-117">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="32f61-118">Następnie kompilator zapisuje te informacje w pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="32f61-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="32f61-119">Jeśli kompilator nie napotka w pliku dyrektywy `#pragma checksum`, oblicza jego sumę kontrolną i zapisuje jej wartość w pliku PDB.</span><span class="sxs-lookup"><span data-stu-id="32f61-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32f61-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="32f61-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="32f61-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32f61-121">See also</span></span>

- [<span data-ttu-id="32f61-122">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="32f61-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="32f61-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="32f61-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="32f61-124">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="32f61-124">C# Preprocessor Directives</span></span>](./index.md)
