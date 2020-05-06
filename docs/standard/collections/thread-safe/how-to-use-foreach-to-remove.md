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
ms.openlocfilehash: 1255fcda89396ea8ff9abf6cf111e6dd9ea5a87d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82861014"
---
# <a name="use-foreach-to-remove-items-in-a-blockingcollection"></a>Usuwanie elementów z BlockingCollection za pomocą instrukcji foreach

Oprócz <xref:System.Collections.Concurrent.BlockingCollection%601> przejmowania elementów z przy użyciu metody <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> można również użyć instrukcji [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([for each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) w Visual Basic) z elementem <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> do usuwania elementów do momentu ukończenia dodawania, a kolekcja jest pusta. Jest to nazywane *mutacją wyliczenia* lub *zużywaniem* , ponieważ, w przeciwieństwie do `foreach` typowej`For Each`pętli (), ten moduł wyliczający modyfikuje kolekcję źródłową, usuwając elementy.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak usunąć wszystkie elementy w a <xref:System.Collections.Concurrent.BlockingCollection%601> za pomocą pętli `foreach` (`For Each`).

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

W tym przykładzie zastosowano `foreach` pętlę <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> z metodą w wątku zużywania, która powoduje, że każdy element zostanie usunięty z kolekcji w miarę ich wyliczania. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>ogranicza maksymalną liczbę elementów, które znajdują się w kolekcji w dowolnym momencie. Wyliczenie kolekcji w ten sposób blokuje wątek odbiorcy, jeśli żadne elementy nie są dostępne lub jeśli kolekcja jest pusta. W tym przykładzie blokowanie nie jest problemem, ponieważ wątek produkcyjny dodaje elementy szybciej niż można ich użyć.

<xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> Zwraca wartość a `IEnumerable<T>`, więc kolejność nie może być gwarantowana. Jednak wewnętrznie a <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> jest używany jako typ kolekcji bazowej, która spowoduje dekolejkowanie obiektów po pierwszej kolejności (FIFO). Jeśli <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> są wykonywane współbieżne wywołania, zostaną one konkurencyjne. W drugim nie można zaobserwować jednego z użytych elementów (usuniętych z kolejki) w jednym wyliczeniu.

Aby wyliczyć kolekcję bez modyfikacji, użyj `foreach` tylko (`For Each`) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody. Jednak ważne jest, aby zrozumieć, że ten rodzaj wyliczenia reprezentuje migawkę kolekcji w określonym momencie. Jeśli inne wątki dodają lub usuwają elementy współbieżnie podczas wykonywania pętli, pętla może nie reprezentować rzeczywistego stanu kolekcji.

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Programowanie równoległe](../../../../docs/standard/parallel-programming/index.md)
