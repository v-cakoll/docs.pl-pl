---
title: Wykonywanie niezależnych od kultury operacji na ciągach w tablicach
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
ms.openlocfilehash: 051ee77ae5d6552e26e0216d58734d90188475f9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120806"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Wykonywanie niezależnych od kultury operacji na ciągach w tablicach

Przeciążenia metod <xref:System.Array.Sort%2A?displayProperty=nameWithType> i <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> wykonują domyślnie sortowanie zależne od kultury przy użyciu właściwości <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>. Wyniki wrażliwe na kulturę zwracane przez te metody mogą się różnić w zależności od różnic w kolejności sortowania. Aby wyeliminować zachowanie wrażliwe na kulturę, użyj jednego z przeciążeń tej metody, która akceptuje parametr `comparer`. `comparer` parametr określa implementację <xref:System.Collections.IComparer> do użycia podczas porównywania elementów w tablicy. Dla parametru należy określić niestandardową klasę niezmiennej porównującej, która używa <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Przykład niestandardowej klasy niezmiennej porównującej znajduje się w podrozdziale "Using the SortedList Class" w temacie [wykonywanie operacji na ciągach, które nie uwzględniają kultury w temacie kolekcje](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) .

> [!NOTE]
> Przekazywanie **CultureInfo. InvariantCulture** do metody porównania wykonuje porównanie nieuwzględniające kulturę. Nie powoduje to jednak porównania w języku innym niż język, na przykład w przypadku ścieżek plików, kluczy rejestru i zmiennych środowiskowych. Żadna z tych funkcji nie wspiera podejmowania decyzji dotyczących zabezpieczeń w oparciu o wynik porównania. W przypadku niezgodności z językiem lub pomocy technicznej dla decyzji o zabezpieczeniach opartych na wynikach aplikacja powinna używać metody porównania, która akceptuje wartość <xref:System.StringComparison>. Aplikacja powinna następnie przekazać <xref:System.StringComparison.Ordinal>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
