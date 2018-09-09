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
ms.openlocfilehash: 22815b5ab993b36bc8bcb91f89f346cb6d812e19
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251696"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Wykonywanie niezależnych od kultury operacji na ciągach w tablicach
Przeciążenia <xref:System.Array.Sort%2A?displayProperty=nameWithType> i <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody wykonywania kultury sortowania przy użyciu domyślnego <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości. Wrażliwość na ustawienia kulturowe wyniki zwrócone przez te metody mogą się różnić kultury z powodu różnic w kolejności sortowania. Aby wyeliminować wrażliwość na ustawienia kulturowe zachowanie, użyj jednej z przeciążenia tej metody, która akceptuje `comparer` parametru. `comparer` Parametr określa <xref:System.Collections.IComparer> wdrożenia do użycia podczas porównywania elementów w tablicy. Dla parametru należy określić klasę niestandardowego modułu porównującego niezmiennej, która używa <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Przykład klasy niestandardowej funkcji porównującej niezmiennej znajduje się w podrzędnym "Przy użyciu klasy SortedList —" tematu [wykonywanie niezależnych od kultury operacje na ciągach w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) tematu.  
  
 **Uwaga** przekazywanie **CultureInfo.InvariantCulture** do porównania metoda wykonać porównanie niezależnych od kultury. Jednak nie spowoduje nielingwistyczne porównania, na przykład ścieżki do plików, kluczy rejestru i zmiennych środowiskowych. Żadna z nich nie jest obsługiwany decyzje dotyczące bezpieczeństwa, w oparciu o wyniki porównania. Dla porównania nielingwistyczne lub pomocy technicznej dla decyzji dotyczących zabezpieczeń opartych na wynik, aplikacja powinna użyć metody porównania, która akceptuje <xref:System.StringComparison> wartość. Aplikacja powinna następnie przekazać <xref:System.StringComparison.Ordinal>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
- <xref:System.Collections.IComparer>  
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
