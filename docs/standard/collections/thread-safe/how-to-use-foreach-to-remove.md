---
title: Usuwanie elementów z BlockingCollection za pomocą instrukcji foreach
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
ms.openlocfilehash: 46638d2cd8078fefebc0eacc4b8f7798ffe178ff
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288904"
---
# <a name="use-foreach-to-remove-items-in-a-blockingcollection"></a>Usuwanie elementów z BlockingCollection za pomocą instrukcji foreach

Oprócz przejmowania elementów z przy <xref:System.Collections.Concurrent.BlockingCollection%601> użyciu <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody i można również użyć instrukcji [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([for each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) w Visual Basic) z elementem <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> do usuwania elementów do momentu ukończenia dodawania, a kolekcja jest pusta. Jest to nazywane *mutacją wyliczenia* lub *zużywaniem* , ponieważ, w przeciwieństwie do typowej `foreach` `For Each` pętli (), ten moduł wyliczający modyfikuje kolekcję źródłową, usuwając elementy.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak usunąć wszystkie elementy w a <xref:System.Collections.Concurrent.BlockingCollection%601> za pomocą `foreach` `For Each` pętli ().

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

W tym przykładzie zastosowano `foreach` pętlę z <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> metodą w wątku zużywania, która powoduje, że każdy element zostanie usunięty z kolekcji w miarę ich wyliczania. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>ogranicza maksymalną liczbę elementów, które znajdują się w kolekcji w dowolnym momencie. Wyliczenie kolekcji w ten sposób blokuje wątek odbiorcy, jeśli żadne elementy nie są dostępne lub jeśli kolekcja jest pusta. W tym przykładzie blokowanie nie jest problemem, ponieważ wątek produkcyjny dodaje elementy szybciej niż można ich użyć.

<xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType>Zwraca wartość a `IEnumerable<T>` , więc kolejność nie może być gwarantowana. Jednak wewnętrznie a <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> jest używany jako typ kolekcji bazowej, która spowoduje dekolejkowanie obiektów po pierwszej kolejności (FIFO). Jeśli są wykonywane współbieżne wywołania <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> , zostaną one konkurencyjne. W drugim nie można zaobserwować jednego z użytych elementów (usuniętych z kolejki) w jednym wyliczeniu.

Aby wyliczyć kolekcję bez modyfikacji, użyj tylko `foreach` ( `For Each` ) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody. Jednak ważne jest, aby zrozumieć, że ten rodzaj wyliczenia reprezentuje migawkę kolekcji w określonym momencie. Jeśli inne wątki dodają lub usuwają elementy współbieżnie podczas wykonywania pętli, pętla może nie reprezentować rzeczywistego stanu kolekcji.

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Programowanie równoległe](../../parallel-programming/index.md)
