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
ms.openlocfilehash: 79ff899e2964ae2c1e90b7178616c612dddf6d86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287509"
---
# <a name="performing-culture-insensitive-string-operations"></a>Wykonywanie operacji na ciągach niewrażliwych na kulturę
Większość .NET Framework metod, które wykonują operacje na ciągach zależnych od kultury, domyślnie udostępnia przeciążenia metod, które umożliwiają jawne określenie kultury do użycia przez przekazanie <xref:System.Globalization.CultureInfo> parametru. Te przeciążenia pozwalają wyeliminować wahania kulturowe w odniesieniu do mapowań i reguł sortowania, a następnie zagwarantować wyniki niewrażliwe na kulturę.  
  
 Ta sekcja zawiera następujące tematy przedstawiające sposób wykonywania operacji na ciągach niewrażliwych na kulturę przy użyciu metod .NET Framework, które domyślnie są zależne od kultury.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wykonywanie niezależnych od kultury porównań ciągów](performing-culture-insensitive-string-comparisons.md)  
 Opisuje sposób użycia <xref:System.String.Compare%2A?displayProperty=nameWithType> <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metod i do wykonywania porównania ciągów niewrażliwych na kulturę.  
  
 [Wykonywanie niezależnych od kultury zmian wielkości liter](performing-culture-insensitive-case-changes.md)  
 Opisuje sposób używania <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType> metod,, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> i <xref:System.Char.ToLower%2A?displayProperty=nameWithType> do wykonywania zmian wielkości liter bez uwzględniania kultur.  
  
 [Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach](performing-culture-insensitive-string-operations-in-collections.md)  
 Opisuje sposób używania <xref:System.Collections.CaseInsensitiveComparer> , klasy, <xref:System.Collections.CaseInsensitiveHashCodeProvider> <xref:System.Collections.SortedList> <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> i <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> do wykonywania operacji niewrażliwych na kulturę w kolekcjach.  
  
 [Wykonywanie niezależnych od kultury operacji na ciągach w tablicach](performing-culture-insensitive-string-operations-in-arrays.md)  
 Opisuje sposób użycia <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metod i do wykonywania operacji niewrażliwych na kulturę w tablicach.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Operacje na ciągach nieuwzględniających kultur](culture-insensitive-string-operations.md)  
 W tym artykule opisano, dlaczego należy pamiętać o kulturze podczas wykonywania operacji na ciągach i przedstawiono wskazówki dotyczące sytuacji, w których należy wykonać operacje zależne od kultury i kiedy wykonywać operacje niewrażliwe na kulturę.

## <a name="see-also"></a>Zobacz także

- [Sortowanie tabel wag (dla platformy .NET w systemach Windows)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Domyślna tabela elementów sortowania Unicode (dla platformy .NET Core w systemie Linux i macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
