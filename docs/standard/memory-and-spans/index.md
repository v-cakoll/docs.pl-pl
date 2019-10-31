---
title: Pamięć i zakresy
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: b61b1dbbedf4658fe113986fbb4a792a2f574534
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121989"
---
# <a name="memory--and-span-related-types"></a>Typy związane z pamięcią i zakresem

Począwszy od platformy .NET Core 2,1, .NET zawiera wiele powiązanych typów, które reprezentują ciągły, silnie określony region wolnej pamięci. Należą do nich następujące elementy:

- <xref:System.Span%601?displayProperty=nameWithType>, typ, który jest używany w celu uzyskania dostępu do ciągłego regionu pamięci. Wystąpienie <xref:System.Span%601> może być obsługiwane przez tablicę typu `T`, <xref:System.String>, buforu przydzielonego za pomocą [stackalloc](../../csharp/language-reference/operators/stackalloc.md)lub wskaźnika do pamięci niezarządzanej. Ponieważ musi być przypisana na stosie, ma wiele ograniczeń. Na przykład pole w klasie nie może być typu <xref:System.Span%601>, ani nie może być używane w operacjach asynchronicznych.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, niezmienna wersja struktury <xref:System.Span%601>.

- <xref:System.Memory%601?displayProperty=nameWithType>, ciągły region pamięci przydzielony na stercie zarządzanym, a nie na stosie. Wystąpienie <xref:System.Memory%601> może być obsługiwane przez tablicę typu `T` lub <xref:System.String>. Ponieważ może być przechowywana na stercie zarządzanym, <xref:System.Memory%601> nie ma żadnych ograniczeń <xref:System.Span%601>.

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, niezmienna wersja struktury <xref:System.Memory%601>.

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, która przydziela jednoznacznie wpisane bloki pamięci z puli pamięci do właściciela. wystąpienia <xref:System.Buffers.IMemoryOwner%601> mogą być wydzierżawione z puli przez wywołanie <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> i zwolnienie z powrotem do puli przez wywołanie <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, który reprezentuje właściciela bloku pamięci i kontroluje jego okres istnienia.

- <xref:System.Buffers.MemoryManager%601>, abstrakcyjna klasa bazowa, która może służyć do zastępowania implementacji <xref:System.Memory%601>, tak aby <xref:System.Memory%601> mogą być obsługiwane przez dodatkowe typy, takie jak bezpieczne dojścia. <xref:System.Buffers.MemoryManager%601> jest przeznaczony dla zaawansowanych scenariuszy.

- <xref:System.ArraySegment%601>, otoka dla określonej liczby elementów tablicy, zaczynając od określonego indeksu.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>, kolekcja metod rozszerzających dla konwersji ciągów, tablic i segmentów tablicy do bloków <xref:System.Memory%601>.

> [!NOTE]
> W przypadku wcześniejszych platform <xref:System.Span%601> i <xref:System.Memory%601> są dostępne w [pakiecie NuGet system. Memory](https://www.nuget.org/packages/System.Memory/).

Aby uzyskać więcej informacji, zobacz Przestrzeń nazw <xref:System.Buffers?displayProperty=nameWithType>.

## <a name="working-with-memory-and-span"></a>Praca z pamięcią i zakresem

Ponieważ typy związane z pamięcią i zakresem są zwykle używane do przechowywania danych w potoku przetwarzania, ważne jest, aby deweloperzy przestrzegali zestawu najlepszych rozwiązań w przypadku używania <xref:System.Span%601>, <xref:System.Memory%601>i typów pokrewnych. Poniższe najlepsze rozwiązania zostały udokumentowane w [pamięci\<t > i obejmować\<t > wytycznych dotyczących użycia](memory-t-usage-guidelines.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
