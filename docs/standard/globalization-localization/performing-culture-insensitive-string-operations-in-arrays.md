---
title: Wykonywanie niezależnych od kultury operacji na ciągach w tablicach
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4d732d64eecff72403c455c14b68c3aec1b5407
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Wykonywanie niezależnych od kultury operacji na ciągach w tablicach
Overloads z <xref:System.Array.Sort%2A?displayProperty=nameWithType> i <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody wykonanie zależne od kultury sortowania przy użyciu domyślnego <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości. Zależne od kultury wyników zwróconych w wyniku tych metod można różnią się zależnie od kultury z powodu różnic w kolejności sortowania. Aby wyeliminować zachowanie zależne od kultury, użyj jednej z przeciążenia tej metody, która akceptuje `comparer` parametru. `comparer` Określa parametr <xref:System.Collections.IComparer> wdrożenia do użycia podczas porównywania elementów w tablicy. W przypadku parametru określić klasy niestandardowej funkcji porównującej niezmienna, która używa <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Przykład klasy niestandardowej funkcji porównującej niezmiennej znajduje się w podrzędnym "Przy użyciu klasy SortedList" tematu [wykonywanie niezależnych od kultury operacje na ciągach w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) tematu.  
  
 **Uwaga** przekazywanie **wartość CultureInfo.InvariantCulture** do porównania metody przeprowadzenia porównania niezależnych od kultury. Jednak go nie powoduje-językowe porównania, na przykład ścieżki do plików, kluczy rejestru i zmiennych środowiskowych. Nie obsługuje zabezpieczeń decyzje na podstawie wyniku porównania. Dla porównania językowe lub obsługę decyzje na podstawie wyniku zabezpieczeń, aplikacja powinna używać metody porównania, która akceptuje <xref:System.StringComparison> wartość. Następnie należy przekazać aplikacji <xref:System.StringComparison.Ordinal>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
