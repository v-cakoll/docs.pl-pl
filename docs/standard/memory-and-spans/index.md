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
ms.openlocfilehash: fbfd091c821f59febfc8c7a203334454e7b59c12
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666424"
---
# <a name="memory--and-span-related-types"></a>Typy związane z pamięcią i zakresem

Począwszy od platformy .NET Core 2,1, .NET zawiera wiele powiązanych typów, które reprezentują ciągły, silnie określony region wolnej pamięci. Należą do nich następujące elementy:

- <xref:System.Span%601?displayProperty=nameWithType>, typ, który jest używany w celu uzyskania dostępu do ciągłego regionu pamięci. Wystąpienie może być obsługiwane przez tablicę typu `T`, a <xref:System.String>, bufor alokowany z [stackalloc](../../csharp/language-reference/operators/stackalloc.md)lub wskaźnik do pamięci niezarządzanej. <xref:System.Span%601> Ponieważ musi być przypisana na stosie, ma wiele ograniczeń. Na przykład pole w klasie nie może być typu <xref:System.Span%601>, ani nie może być używane w operacjach asynchronicznych.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, niezmienna wersja <xref:System.Span%601> struktury.

- <xref:System.Memory%601?displayProperty=nameWithType>, ciągły region pamięci przydzielony na stercie zarządzanym, a nie na stosie. Wystąpienie może być obsługiwane przez tablicę typu `T` lub <xref:System.String>. <xref:System.Memory%601> Ponieważ może być przechowywana na stercie zarządzanym, <xref:System.Memory%601> nie ma żadnych <xref:System.Span%601>ograniczeń.

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, niezmienna wersja <xref:System.Memory%601> struktury.

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, która przydziela jednoznacznie wpisane bloki pamięci z puli pamięci do właściciela. <xref:System.Buffers.IMemoryOwner%601>wystąpienia mogą być wydzierżawione z puli, wywołując <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> i wywołując z powrotem do puli <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>przez wywołanie.

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, który reprezentuje właściciela bloku pamięci i kontroluje jego okres istnienia.

- <xref:System.Buffers.MemoryManager%601>abstrakcyjna klasa bazowa, która może służyć do zastępowania implementacji <xref:System.Memory%601> , która <xref:System.Memory%601> może być wykonywana przez dodatkowe typy, takie jak bezpieczne dojścia. <xref:System.Buffers.MemoryManager%601>jest przeznaczony dla zaawansowanych scenariuszy.

- <xref:System.ArraySegment%601>, otoka dla określonej liczby elementów tablicy, zaczynając od określonego indeksu.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>, kolekcja metod rozszerzających do przekonwertowania ciągów, tablic i segmentów <xref:System.Memory%601> tablicowych.

> [!NOTE]
> W przypadku wcześniejszych platform <xref:System.Span%601> i <xref:System.Memory%601> są dostępne w [pakiecie NuGet system. Memory](https://www.nuget.org/packages/System.Memory/).

Aby uzyskać więcej informacji, zobacz <xref:System.Buffers?displayProperty=nameWithType> przestrzeń nazw.

## <a name="working-with-memory-and-span"></a>Praca z pamięcią i zakresem

Ponieważ typy związane z pamięcią i zakresem są zwykle używane do przechowywania danych w potoku przetwarzania, ważne jest, aby deweloperzy przestrzegali zestawu najlepszych rozwiązań w przypadku używania <xref:System.Span%601>, <xref:System.Memory%601>i powiązanych typów. Te najlepsze rozwiązania opisano w temacie [pamięć\<t > i obejmują\<> Wskazówki dotyczące użycia](memory-t-usage-guidelines.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
