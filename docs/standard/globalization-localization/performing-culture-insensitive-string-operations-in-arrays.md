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
ms.openlocfilehash: ba02333aaafbadc85e4d3c547659f4ce4d2740c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683010"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Wykonywanie niezależnych od kultury operacji na ciągach w tablicach
Przeciążenia <xref:System.Array.Sort%2A?displayProperty=nameWithType> i <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody wykonywania kultury sortowania przy użyciu domyślnego <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości. Wrażliwość na ustawienia kulturowe wyniki zwrócone przez te metody mogą się różnić kultury z powodu różnic w kolejności sortowania. Aby wyeliminować wrażliwość na ustawienia kulturowe zachowanie, użyj jednej z przeciążenia tej metody, która akceptuje `comparer` parametru. `comparer` Parametr określa <xref:System.Collections.IComparer> wdrożenia do użycia podczas porównywania elementów w tablicy. Dla parametru należy określić klasę niestandardowego modułu porównującego niezmiennej, która używa <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Przykład klasy niestandardowej funkcji porównującej niezmiennej znajduje się w podrzędnym "Przy użyciu klasy SortedList —" tematu [wykonywanie niezależnych od kultury operacje na ciągach w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) tematu.  
  
 **Uwaga** przekazywanie **CultureInfo.InvariantCulture** do porównania metoda wykonać porównanie niezależnych od kultury. Jednak nie spowoduje nielingwistyczne porównania, na przykład ścieżki do plików, kluczy rejestru i zmiennych środowiskowych. Żadna z nich nie jest obsługiwany decyzje dotyczące bezpieczeństwa, w oparciu o wyniki porównania. Dla porównania nielingwistyczne lub pomocy technicznej dla decyzji dotyczących zabezpieczeń opartych na wynik, aplikacja powinna użyć metody porównania, która akceptuje <xref:System.StringComparison> wartość. Aplikacja powinna następnie przekazać <xref:System.StringComparison.Ordinal>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
