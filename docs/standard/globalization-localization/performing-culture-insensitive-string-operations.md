---
title: Wykonywanie niezależnych od kultury operacji na ciągach
ms.date: 08/22/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 748b4170e9e4c0df048c542d06bcb64a56ccf677
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254649"
---
# <a name="performing-culture-insensitive-string-operations"></a>Wykonywanie operacji na ciągach niezależnych od kultury
Większość metod .NET Framework, które wykonują operacje na ciągach wrażliwych na kulturę domyślnie zapewniają przeciążenia metody, które pozwalają na określenie jawnie kultura używana przez przekazanie <xref:System.Globalization.CultureInfo> parametru. Te przeciążone funkcje umożliwiają wyeliminować różnice kulturowe w przypadku mapowania i sortowanie reguł i zagwarantować wyników niezależnych od kultury.  
  
 Ta sekcja zawiera następujące tematy w celu zademonstrowania sposobu wykonywania za pomocą metod .NET Framework, które są zależne od kultury operacje na ciągach niezależnych od kultury domyślnie.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wykonywanie niezależnych od kultury porównań ciągów](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 Opisuje sposób używania <xref:System.String.Compare%2A?displayProperty=nameWithType> i <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody umożliwiają przeprowadzanie niezależnych od kultury porównań ciągów.  
  
 [Wykonywanie niezależnych od kultury zmian wielkości liter](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 Opisuje sposób używania <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, i <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody umożliwiają przeprowadzanie niezależnych od kultury zmian wielkości liter.  
  
 [Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 Opisuje sposób używania <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> klasy <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> i <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> do wykonywania operacji niezależnych od kultury w kolekcji.  
  
 [Wykonywanie niezależnych od kultury operacji na ciągach w tablicach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 Opisuje sposób używania <xref:System.Array.Sort%2A?displayProperty=nameWithType> i <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody umożliwiają przeprowadzanie operacji niezależnych od kultury w tablicach.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Niezależne od kultury operacje na ciągach](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 W tym artykule opisano, dlaczego należy pamiętać o kultury podczas wykonywania operacji na ciągi znaków i zawiera wskazówki dotyczące przeprowadzania operacji wrażliwych na kulturę i przeprowadzania operacji niezależnych od kultury.

## <a name="see-also"></a>Zobacz także

- [Tabele wagi sortowania](https://www.microsoft.com/en-us/download/details.aspx?id=10921)
