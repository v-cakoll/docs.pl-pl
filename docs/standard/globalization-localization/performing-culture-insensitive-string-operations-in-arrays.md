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
ms.openlocfilehash: b52ff8d72132c1076dfdece5e1ce47bbece37b81
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855998"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Wykonywanie niezależnych od kultury operacji na ciągach w tablicach

Przeciążenia metod i <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> są domyślnie wykonywane w celu sortowania z uwzględnieniem kultury, przy <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> użyciu właściwości. Wyniki wrażliwe na kulturę zwracane przez te metody mogą się różnić w zależności od różnic w kolejności sortowania. Aby wyeliminować zachowanie wrażliwe na kulturę, użyj jednego z przeciążeń tej metody, `comparer` która akceptuje parametr. `comparer` Parametr<xref:System.Collections.IComparer> określa implementację do użycia podczas porównywania elementów w tablicy. Dla parametru należy określić niestandardową klasę niezmiennej porównującej, <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>która używa. Przykład niestandardowej klasy niezmiennej porównującej znajduje się w podrozdziale "Using the SortedList Class" w temacie [wykonywanie operacji na ciągach, które nie uwzględniają kultury w temacie kolekcje](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) .

> [!NOTE]
> Przekazywanie **CultureInfo. InvariantCulture** do metody porównania wykonuje porównanie nieuwzględniające kulturę. Nie powoduje to jednak porównania w języku innym niż język, na przykład w przypadku ścieżek plików, kluczy rejestru i zmiennych środowiskowych. Żadna z tych funkcji nie wspiera podejmowania decyzji dotyczących zabezpieczeń w oparciu o wynik porównania. W przypadku niezgodności z językiem lub pomocy technicznej dla decyzji o zabezpieczeniach opartych na wynikach aplikacja powinna używać metody porównania, <xref:System.StringComparison> która akceptuje wartość. Aplikacja powinna następnie przejść <xref:System.StringComparison.Ordinal>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
