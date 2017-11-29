---
title: "Wykonywanie niezależnych od kultury operacji na ciągach w tablicach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b4e040ed379cdbf43fbe8b2c4379fdd4dc781f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a><span data-ttu-id="62fd3-102">Wykonywanie niezależnych od kultury operacji na ciągach w tablicach</span><span class="sxs-lookup"><span data-stu-id="62fd3-102">Performing Culture-Insensitive String Operations in Arrays</span></span>
<span data-ttu-id="62fd3-103">Overloads z <xref:System.Array.Sort%2A?displayProperty=nameWithType> i <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody wykonanie zależne od kultury sortowania przy użyciu domyślnego <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="62fd3-103">Overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods perform culture-sensitive sorts by default using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="62fd3-104">Zależne od kultury wyników zwróconych w wyniku tych metod można różnią się zależnie od kultury z powodu różnic w kolejności sortowania.</span><span class="sxs-lookup"><span data-stu-id="62fd3-104">Culture-sensitive results returned by these methods can vary by culture due to differences in sort orders.</span></span> <span data-ttu-id="62fd3-105">Aby wyeliminować zachowanie zależne od kultury, użyj jednej z przeciążenia tej metody, która akceptuje `comparer` parametru.</span><span class="sxs-lookup"><span data-stu-id="62fd3-105">To eliminate culture-sensitive behavior, use one of the overloads of this method that accepts a `comparer` parameter.</span></span> <span data-ttu-id="62fd3-106">`comparer` Określa parametr <xref:System.Collections.IComparer> wdrożenia do użycia podczas porównywania elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="62fd3-106">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing elements in the array.</span></span> <span data-ttu-id="62fd3-107">W przypadku parametru określić klasy niestandardowej funkcji porównującej niezmienna, która używa <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="62fd3-107">For the parameter, specify a custom invariant comparer class that uses <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="62fd3-108">Przykład klasy niestandardowej funkcji porównującej niezmiennej znajduje się w podrzędnym "Przy użyciu klasy SortedList" tematu [wykonywanie niezależnych od kultury operacje na ciągach w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="62fd3-108">An example of a custom invariant comparer class is provided in the "Using the SortedList Class" subtopic of the [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) topic.</span></span>  
  
 <span data-ttu-id="62fd3-109">**Uwaga** przekazywanie **wartość CultureInfo.InvariantCulture** do porównania metody przeprowadzenia porównania niezależnych od kultury.</span><span class="sxs-lookup"><span data-stu-id="62fd3-109">**Note** Passing **CultureInfo.InvariantCulture** to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="62fd3-110">Jednak go nie powoduje-językowe porównania, na przykład ścieżki do plików, kluczy rejestru i zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="62fd3-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="62fd3-111">Nie obsługuje zabezpieczeń decyzje na podstawie wyniku porównania.</span><span class="sxs-lookup"><span data-stu-id="62fd3-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="62fd3-112">Dla porównania językowe lub obsługę decyzje na podstawie wyniku zabezpieczeń, aplikacja powinna używać metody porównania, która akceptuje <xref:System.StringComparison> wartość.</span><span class="sxs-lookup"><span data-stu-id="62fd3-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="62fd3-113">Następnie należy przekazać aplikacji <xref:System.StringComparison.Ordinal>.</span><span class="sxs-lookup"><span data-stu-id="62fd3-113">The application should then pass <xref:System.StringComparison.Ordinal>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62fd3-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62fd3-114">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="62fd3-115">Wykonywanie operacji na ciągach niezależnych od kultury</span><span class="sxs-lookup"><span data-stu-id="62fd3-115">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
