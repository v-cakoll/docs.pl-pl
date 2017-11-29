---
title: "Wykonywanie niezależnych od kultury operacji na ciągach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e703e9adc531b7d1695d3e9bbed61a2c0f62ad31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="af80d-102">Wykonywanie niezależnych od kultury operacji na ciągach</span><span class="sxs-lookup"><span data-stu-id="af80d-102">Performing Culture-Insensitive String Operations</span></span>
<span data-ttu-id="af80d-103">Większości metod .NET Framework, które wykonują operacje na ciągach zależne od kultury domyślnie Podaj przeciążenia metody, dzięki którym można jawnie określić kultura używana przez przekazanie <xref:System.Globalization.CultureInfo> parametru.</span><span class="sxs-lookup"><span data-stu-id="af80d-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="af80d-104">Te przeciążenia pozwala wyeliminować kultury zmian w przypadku mapowania i sortowanie zasady i gwarantuje niezależnych od kultury.</span><span class="sxs-lookup"><span data-stu-id="af80d-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="af80d-105">Ta sekcja zawiera następujące tematy, aby pokazują, jak wykonać za pomocą metod .NET Framework, które są zależne od kultury operacje na ciągach niezależnych od kultury domyślnie.</span><span class="sxs-lookup"><span data-stu-id="af80d-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af80d-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="af80d-106">In This Section</span></span>  
 [<span data-ttu-id="af80d-107">Wykonywanie ciągu niezależnych od kultury porównań</span><span class="sxs-lookup"><span data-stu-id="af80d-107">Performing Culture-Insensitive String Comparisons</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="af80d-108">Informacje dotyczące używania <xref:System.String.Compare%2A?displayProperty=nameWithType> i <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody do porównywania ciągów niezależnych od kultury.</span><span class="sxs-lookup"><span data-stu-id="af80d-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="af80d-109">Wykonywanie niezależnych od kultury zmian wielkości liter</span><span class="sxs-lookup"><span data-stu-id="af80d-109">Performing Culture-Insensitive Case Changes</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="af80d-110">Informacje dotyczące używania <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, i <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metod do wykonania niezależnych od kultury zmian wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="af80d-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="af80d-111">Wykonywanie operacji na ciągach niezależnych od kultury w kolekcjach</span><span class="sxs-lookup"><span data-stu-id="af80d-111">Performing Culture-Insensitive String Operations in Collections</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="af80d-112">Informacje dotyczące używania <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> klasy <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> i <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> wykonywanie niezależnych od kultury operacji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="af80d-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="af80d-113">Wykonywanie operacji na ciągach niezależnych od kultury w tablicach</span><span class="sxs-lookup"><span data-stu-id="af80d-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="af80d-114">Informacje dotyczące używania <xref:System.Array.Sort%2A?displayProperty=nameWithType> i <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody służące do wykonywania operacji niezależnych od kultury w tablicach.</span><span class="sxs-lookup"><span data-stu-id="af80d-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="af80d-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="af80d-115">Related Sections</span></span>  
 [<span data-ttu-id="af80d-116">Operacje na ciągach niezależnych od kultury</span><span class="sxs-lookup"><span data-stu-id="af80d-116">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="af80d-117">W tym artykule opisano, dlaczego należy zwrócić uwagę kultury podczas wykonywania operacji na ciągach i zawiera wskazówki dotyczące przeprowadzania zależne od kultury operacji i przeprowadzania operacji niezależnych od kultury.</span><span class="sxs-lookup"><span data-stu-id="af80d-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>
