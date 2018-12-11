---
title: Pamięć i zakresy
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 116c08872385406224972e34feaddfe44122355e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130915"
---
# <a name="memory--and-span-related-types"></a>Powiązana z pamięcią i zakresu typów

Począwszy od platformy .NET Core 2.1 .NET zawiera wiele powiązanych typów, które reprezentują ciągłe, silnie typizowane region dowolnego pamięci. Należą do nich następujące elementy:

- <xref:System.Span%601?displayProperty=nameWithType>, typ, który umożliwia dostęp do niego ciągły region pamięci. A <xref:System.Span%601> wystąpienia może być wspierany przez tablicę typu `T`, <xref:System.String>, bufor przydzielony za pomocą [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), lub wskaźnika do niezarządzanej pamięci. Ponieważ ma ona zostać przydzielone na stosie, ma kilku ograniczeniom. Na przykład pole w klasie nie może być typu <xref:System.Span%601>, ani zakresu można używać w operacji asynchronicznych.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithtype>, wersja niezmienne <xref:System.Span%601> struktury.

- <xref:System.Memory%601?displayProperty=nameWithType>, dla niego ciągły region pamięci przydzielonej na zarządzanym stosie, a nie na stosie. A <xref:System.Memory%601> wystąpienia może być wspierany przez tablicę typu `T` lub <xref:System.String>. Ponieważ mogą być przechowywane w zarządzanym stosie <xref:System.Memory%601> nie ma żadnego ograniczenia <xref:System.Span%601>.

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithtype>, wersja niezmienne <xref:System.Memory%601> struktury.

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, który przydziela silnie typizowane bloki pamięci w puli pamięci do elementu owner. <xref:System.Buffers.IMemoryOwner%601> wystąpienia, wypożyczone z puli, wywołując <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> i zwalnia z powrotem do puli, wywołując <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, który reprezentuje właściciela bloku pamięci i kontroluje jego Zarządzanie okresem istnienia. 

- <xref:System.Buffers.MemoryManager%601>, abstrakcyjna klasa bazowa, która może być używany do zastępowania wdrożenia <xref:System.Memory%601> tak, aby <xref:System.Memory%601> był zabezpieczony za pomocą dodatkowych typów, takich jak bezpieczne dojścia. <xref:System.Buffers.MemoryManager%601> jest przeznaczony dla zaawansowanych scenariuszy.

- <xref:System.ArraySegment%601>, otoki dla określonej liczby elementów tablicy, zaczynając od określonego indeksu.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>, Kolekcja metody rozszerzenia dla konwersji ciągów, tablic i segmentów tablicy do <xref:System.Memory%601> bloków.

> [!NOTE]
> Dla starszych środowisk <xref:System.Span%601> i <xref:System.Memory%601> są dostępne w [pakietu System.Memory NuGet](https://www.nuget.org/packages/System.Memory/).

Aby uzyskać więcej informacji, zobacz <xref:System.Buffers?displayProperty=nameWithType> przestrzeni nazw.

## <a name="working-with-memory-and-span"></a>Praca z pamięci i zakresu

Ponieważ typy powiązana z pamięcią i zakresu zwykle są używane do przechowywania danych w potoku przetwarzania, jest ważne, że deweloperzy postępuj zgodnie z zestaw najlepszych rozwiązań, korzystając z <xref:System.Span%601>, <xref:System.Memory%601>i typów pokrewnych. Następujące najlepsze rozwiązania są udokumentowane w artykule [pamięci\<T > i zakres\<T > wytyczne dotyczące użycia](memory-t-usage-guidelines.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>