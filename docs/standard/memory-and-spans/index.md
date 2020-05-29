---
title: Pamięć i zakresy
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: c60c08d27c0e41228a15e8acdf01a9af28a23762
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201969"
---
# <a name="memory--and-span-related-types"></a>Typy związane z pamięcią i zakresem

Począwszy od platformy .NET Core 2,1, .NET zawiera wiele powiązanych typów, które reprezentują ciągły, silnie określony region dowolnej pamięci. Należą do nich:

- <xref:System.Span%601?displayProperty=nameWithType>, typ, który jest używany w celu uzyskania dostępu do ciągłego regionu pamięci. <xref:System.Span%601>Wystąpienie może być obsługiwane przez tablicę typu `T` , a <xref:System.String> , bufor alokowany z [stackalloc](../../csharp/language-reference/operators/stackalloc.md)lub wskaźnik do pamięci niezarządzanej. Ponieważ musi być przypisana na stosie, ma wiele ograniczeń. Na przykład pole w klasie nie może być typu <xref:System.Span%601> , ani nie może być używane w operacjach asynchronicznych.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, niezmienna wersja <xref:System.Span%601> struktury.

- <xref:System.Memory%601?displayProperty=nameWithType>, ciągły region pamięci przydzielony na stercie zarządzanym, a nie na stosie. <xref:System.Memory%601>Wystąpienie może być obsługiwane przez tablicę typu `T` lub <xref:System.String> . Ponieważ może być przechowywana na stercie zarządzanym, <xref:System.Memory%601> nie ma żadnych ograniczeń <xref:System.Span%601> .

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, niezmienna wersja <xref:System.Memory%601> struktury.

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, która przydziela jednoznacznie wpisane bloki pamięci z puli pamięci do właściciela. <xref:System.Buffers.IMemoryOwner%601>wystąpienia mogą być wydzierżawione z puli, wywołując i wywołując z <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> powrotem do puli przez wywołanie <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType> .

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, który reprezentuje właściciela bloku pamięci i kontroluje jego okres istnienia.

- <xref:System.Buffers.MemoryManager%601>abstrakcyjna klasa bazowa, która może służyć do zastępowania implementacji, <xref:System.Memory%601> która <xref:System.Memory%601> może być wykonywana przez dodatkowe typy, takie jak bezpieczne dojścia. <xref:System.Buffers.MemoryManager%601>jest przeznaczony dla zaawansowanych scenariuszy.

- <xref:System.ArraySegment%601>, otoka dla określonej liczby elementów tablicy, zaczynając od określonego indeksu.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>, kolekcja metod rozszerzających do przekonwertowania ciągów, tablic i segmentów tablicowych <xref:System.Memory%601> .

> [!NOTE]
> W przypadku wcześniejszych platform <xref:System.Span%601> i <xref:System.Memory%601> są dostępne w [pakiecie NuGet system. Memory](https://www.nuget.org/packages/System.Memory/).

Aby uzyskać więcej informacji, zobacz <xref:System.Buffers?displayProperty=nameWithType> przestrzeń nazw.

## <a name="working-with-memory-and-span"></a>Praca z pamięcią i zakresem

Ponieważ typy związane z pamięcią i zakresem są zwykle używane do przechowywania danych w potoku przetwarzania, ważne jest, aby deweloperzy przestrzegali zestawu najlepszych rozwiązań w przypadku używania <xref:System.Span%601> , <xref:System.Memory%601> i powiązanych typów. Te najlepsze rozwiązania zostały udokumentowane w temacie [pamięć \<T> i \<T> wskazówki dotyczące użycia](memory-t-usage-guidelines.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
