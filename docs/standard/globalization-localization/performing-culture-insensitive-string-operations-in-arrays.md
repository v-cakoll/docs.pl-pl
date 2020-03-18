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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120806"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Wykonywanie niezależnych od kultury operacji na ciągach w tablicach

Przeciążenia <xref:System.Array.Sort%2A?displayProperty=nameWithType> i <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody wykonywania sortowania zależne <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> od kultury domyślnie przy użyciu właściwości. Wyniki zależne od kultury zwracane przez te metody mogą się różnić w zależności od kultury ze względu na różnice w kolejność sortowania. Aby wyeliminować zachowanie zależne od kultury, należy użyć jednego z `comparer` przeciążeń tej metody, która akceptuje parametr. Parametr `comparer` określa <xref:System.Collections.IComparer> implementację do użycia podczas porównywania elementów w tablicy. Dla parametru określ niestandardową klasę <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>niezmiennego porównywarki, która używa . Przykład niezmiennej klasy porównania znajduje się w podtemacie "Using the SortedList Class" w temacie [Performing Culture-Insensitive String Operations in Collections.](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)

> [!NOTE]
> Przekazywanie **CultureInfo.InvariantCulture** do metody porównania wykonuje porównanie niewrażliwe na kulturę. Jednak nie powoduje porównania nielingwistycznego, na przykład dla ścieżek plików, kluczy rejestru i zmiennych środowiskowych. Nie obsługuje również decyzji dotyczących zabezpieczeń na podstawie wyniku porównania. W przypadku porównania nielingwistycznego lub obsługi decyzji dotyczących zabezpieczeń opartych na <xref:System.StringComparison> wynikach aplikacja powinna używać metody porównywania, która akceptuje wartość. Aplikacja powinna następnie <xref:System.StringComparison.Ordinal>przejść .

## <a name="see-also"></a>Zobacz też

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
