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
ms.openlocfilehash: 183078b1f7a3eb3530fea8af06dbb59055d7d25d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120796"
---
# <a name="performing-culture-insensitive-string-operations"></a>Wykonywanie operacji ciągów niewrażliwych na kulturę
Większość metod platformy .NET Framework, które wykonują operacje ciągu zależne od kultury domyślnie zapewniają <xref:System.Globalization.CultureInfo> przeciążenia metody, które umożliwiają jawnie określić kultury do użycia przez przekazywanie parametru. Te przeciążenia umożliwiają wyeliminowanie różnic kulturowych w mapowaniach przypadków i regułach sortowania oraz gwarantują wyniki niewrażliwe na kulturę.  
  
 W tej sekcji przedstawiono następujące tematy, aby zademonstrować, jak wykonywać operacje ciągów niewrażliwe na kulturę przy użyciu metod .NET Framework, które są domyślnie zależne od kultury.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wykonywanie niezależnych od kultury porównań ciągów](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 Opisuje sposób używania <xref:System.String.Compare%2A?displayProperty=nameWithType> <xref:System.String.CompareTo%2A?displayProperty=nameWithType> i metody do wykonywania nieczułych na kulturę porównań ciągów.  
  
 [Wykonywanie niezależnych od kultury zmian wielkości liter](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 Opisuje sposób używania <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, <xref:System.Char.ToLower%2A?displayProperty=nameWithType> i metody do wykonywania zmian wielkości liter niewrażliwe na kulturę.  
  
 [Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 Opisuje sposób używania <xref:System.Collections.CaseInsensitiveComparer> <xref:System.Collections.CaseInsensitiveHashCodeProvider> , <xref:System.Collections.SortedList>klasy <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> , i do wykonywania operacji niewrażliwych na kulturę w kolekcjach.  
  
 [Wykonywanie niezależnych od kultury operacji na ciągach w tablicach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 Opisuje sposób używania <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> i metod do wykonywania operacji niewrażliwych na kulturę w tablicach.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Operacje ciągów niewrażliwe na kulturę](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 W tym artykule opisano, dlaczego należy pamiętać o kulturze podczas wykonywania operacji na ciągach i zawiera wskazówki dotyczące wykonywania operacji wrażliwych na kulturę i podczas wykonywania operacji niewrażliwych na kulturę.

## <a name="see-also"></a>Zobacz też

- [Sortowanie tabel wagowych (dla .NET w systemach Windows)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Domyślna tabela elementów sortowania Unicode (dla .NET Core w systemach Linux i macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
