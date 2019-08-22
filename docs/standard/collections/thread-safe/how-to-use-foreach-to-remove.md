---
title: 'Instrukcje: Używanie metody ForEach do usuwania elementów z kolekcji BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10fa77f6948a10959db5f79c37692eba67d47ecd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666540"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Instrukcje: Używanie metody ForEach do usuwania elementów z kolekcji BlockingCollection

Oprócz przejmowania <xref:System.Collections.Concurrent.BlockingCollection%601> elementów z przy <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> użyciu metody i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> można również użyć instrukcji [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([for each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) w Visual Basic) do usuwania elementów do momentu ukończenia dodawania, a kolekcja jest pusta. Jest to nazywane *mutacją wyliczenia* lub zużywaniem, ponieważ, w przeciwieństwie do typowej`For Each` `foreach` pętli (), ten moduł wyliczający modyfikuje kolekcję źródłową, usuwając elementy.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak usunąć wszystkie elementy w a <xref:System.Collections.Concurrent.BlockingCollection%601> za `foreach` pomocą pętli (`For Each`).

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

W tym przykładzie zastosowano `foreach` pętlę <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> z metodą w wątku zużywania, która powoduje, że każdy element zostanie usunięty z kolekcji w miarę ich wyliczania. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>ogranicza maksymalną liczbę elementów, które znajdują się w kolekcji w dowolnym momencie. Wyliczenie kolekcji w ten sposób blokuje wątek odbiorcy, jeśli żadne elementy nie są dostępne lub jeśli kolekcja jest pusta. W tym przykładzie blokowanie nie jest problemem, ponieważ wątek produkcyjny dodaje elementy szybciej niż można ich użyć.

Nie ma gwarancji, że elementy są wyliczane w tej samej kolejności, w jakiej są dodawane przez wątki producentów.

Aby wyliczyć kolekcję bez modyfikacji, użyj `foreach` tylko (`For Each`) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody. Jednak ważne jest, aby zrozumieć, że ten rodzaj wyliczenia reprezentuje migawkę kolekcji w określonym momencie. Jeśli inne wątki dodają lub usuwają elementy współbieżnie podczas wykonywania pętli, pętla może nie reprezentować rzeczywistego stanu kolekcji.

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Programowanie równoległe](../../../../docs/standard/parallel-programming/index.md)
