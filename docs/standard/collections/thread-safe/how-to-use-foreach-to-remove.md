---
title: 'Porady: używanie ForEach do usuwanie elementów BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
ms.openlocfilehash: f9a858dea74be63634f887c4204aefa8ac338ad0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711236"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Porady: używanie ForEach do usuwanie elementów BlockingCollection

Oprócz pobierania elementów z <xref:System.Collections.Concurrent.BlockingCollection%601> przy użyciu metody <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A>, można również użyć instrukcji [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([dla każdej](../../../visual-basic/language-reference/statements/for-each-next-statement.md) w Visual Basic) do usuwania elementów do momentu ukończenia dodawania, a kolekcja jest pusta. Jest to nazywane *mutacją wyliczenia* lub *zużywaniem wyliczenia* , ponieważ w przeciwieństwie do typowej pętli `foreach` (`For Each`) ten moduł wyliczający modyfikuje kolekcję źródłową, usuwając elementy.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak usunąć wszystkie elementy w <xref:System.Collections.Concurrent.BlockingCollection%601> przy użyciu pętli `foreach` (`For Each`).

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

W tym przykładzie jest stosowana pętla `foreach` z metodą <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> w wątku zużywania, która powoduje, że każdy element zostanie usunięty z kolekcji w miarę ich wyliczania. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> ogranicza maksymalną liczbę elementów, które znajdują się w kolekcji w dowolnym momencie. Wyliczenie kolekcji w ten sposób blokuje wątek odbiorcy, jeśli żadne elementy nie są dostępne lub jeśli kolekcja jest pusta. W tym przykładzie blokowanie nie jest problemem, ponieważ wątek produkcyjny dodaje elementy szybciej niż można ich użyć.

Nie ma gwarancji, że elementy są wyliczane w tej samej kolejności, w jakiej są dodawane przez wątki producentów.

Aby wyliczyć kolekcję bez modyfikacji, po prostu Użyj `foreach` (`For Each`) bez metody <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A>. Jednak ważne jest, aby zrozumieć, że ten rodzaj wyliczenia reprezentuje migawkę kolekcji w określonym momencie. Jeśli inne wątki dodają lub usuwają elementy współbieżnie podczas wykonywania pętli, pętla może nie reprezentować rzeczywistego stanu kolekcji.

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Programowanie równoległe](../../../../docs/standard/parallel-programming/index.md)
