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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121989"
---
# <a name="memory--and-span-related-types"></a>Typy związane z pamięcią i zakresem

Począwszy od .NET Core 2.1, .NET zawiera szereg powiązanych ze sobą typów, które reprezentują ciągły, silnie typizany region dowolnej pamięci. Należą do nich:

- <xref:System.Span%601?displayProperty=nameWithType>, typ, który jest używany do uzyskiwania dostępu do ciągłego regionu pamięci. Wystąpienie <xref:System.Span%601> może być wspierane przez tablicę `T` <xref:System.String>typu , a , bufor przydzielony z [stackalloc](../../csharp/language-reference/operators/stackalloc.md)lub wskaźnik do pamięci niezarządzanej. Ponieważ musi być przydzielona na stosie, ma szereg ograniczeń. Na przykład pole w klasie nie <xref:System.Span%601>może być typu , ani zakres nie może być używany w operacjach asynchronicznych.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, niezmienną <xref:System.Span%601> wersję konstrukcji.

- <xref:System.Memory%601?displayProperty=nameWithType>, ciągły region pamięci, który jest przydzielany na zarządzanym stosie, a nie na stosie. Wystąpienie <xref:System.Memory%601> może być wspierane przez tablicę `T` <xref:System.String>typu lub . Ponieważ może być przechowywany na zarządzanym stercie, <xref:System.Memory%601> nie <xref:System.Span%601>ma żadnych ograniczeń .

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, niezmienną <xref:System.Memory%601> wersję konstrukcji.

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, który przydziela silnie typizowane bloki pamięci z puli pamięci do właściciela. <xref:System.Buffers.IMemoryOwner%601>można wypożyczyć z puli, <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> dzwoniąc i wypuszczono <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>je z powrotem do puli, dzwoniąc.

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, który reprezentuje właściciela bloku pamięci i kontroluje jego zarządzanie okresem istnienia.

- <xref:System.Buffers.MemoryManager%601>, abstrakcyjna klasa podstawowa, która może <xref:System.Memory%601> służyć <xref:System.Memory%601> do zastąpienia implementacji, dzięki czemu mogą być wspierane przez dodatkowe typy, takie jak bezpieczne dojścia. <xref:System.Buffers.MemoryManager%601>jest przeznaczony dla zaawansowanych scenariuszy.

- <xref:System.ArraySegment%601>, otoka dla określonej liczby elementów tablicy rozpoczynających się od określonego indeksu.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>, zbiór metod rozszerzenia do konwertowania ciągów, tablic i <xref:System.Memory%601> segmentów tablicy na bloki.

> [!NOTE]
> Dla wcześniejszych struktur <xref:System.Span%601> <xref:System.Memory%601> i są dostępne w [pakiecie System.Memory NuGet](https://www.nuget.org/packages/System.Memory/).

Aby uzyskać więcej <xref:System.Buffers?displayProperty=nameWithType> informacji, zobacz obszar nazw.

## <a name="working-with-memory-and-span"></a>Praca z pamięcią i zakresem

Ponieważ typy związane z pamięcią i zakresem są zwykle używane do przechowywania danych w potoku przetwarzania, ważne jest, aby deweloperzy postępowali zgodnie z zestawem najlepszych rozwiązań podczas korzystania z <xref:System.Span%601>typów <xref:System.Memory%601>i powiązanych. Te najlepsze rozwiązania są udokumentowane w [\<memory\<T> i Span T> wskazówki dotyczące użytkowania](memory-t-usage-guidelines.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
