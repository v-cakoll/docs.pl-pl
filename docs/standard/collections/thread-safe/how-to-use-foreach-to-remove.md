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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711236"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Porady: używanie ForEach do usuwanie elementów BlockingCollection

Oprócz pobierania elementów z <xref:System.Collections.Concurrent.BlockingCollection%601> za <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> pomocą <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody i, można również użyć [foreach](../../../csharp/language-reference/keywords/foreach-in.md) [(For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) w języku Visual Basic), aby usunąć elementy, dopóki dodawanie nie zostanie zakończona, a kolekcja jest pusta. Jest to nazywane *mutowanie wyliczenia* lub *zużywa wyliczenie,* ponieważ w przeciwieństwie do typowej `foreach` (`For Each`) pętli, ten wyliczacz modyfikuje kolekcji źródłowej przez usunięcie elementów.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak <xref:System.Collections.Concurrent.BlockingCollection%601> usunąć `foreach` wszystkie`For Each`elementy w pętli () za pomocą ( ).

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

W tym `foreach` przykładzie używa <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> pętli z metodą w wątku zużywa, co powoduje, że każdy element, który ma zostać usunięty z kolekcji, jak jest wyliczany. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>ogranicza maksymalną liczbę elementów, które znajdują się w kolekcji w dowolnym momencie. Wyliczanie kolekcji w ten sposób blokuje wątek konsumenta, jeśli nie są dostępne żadne elementy lub jeśli kolekcja jest pusta. W tym przykładzie blokowanie nie jest problemem, ponieważ wątek producenta dodaje elementy szybciej niż mogą być używane.

Nie ma żadnej gwarancji, że elementy są wyliczane w tej samej kolejności, w jakiej są dodawane przez wątki producenta.

Aby wyliczyć kolekcję bez modyfikowania `foreach` `For Each`jej, <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> po prostu użyj ( ) bez metody. Jednak ważne jest, aby zrozumieć, że tego rodzaju wyliczenia reprezentuje migawkę kolekcji w określonym momencie w czasie. Jeśli inne wątki są dodawanie lub usuwanie elementów jednocześnie podczas wykonywania pętli, a następnie pętli może nie reprezentować rzeczywisty stan kolekcji.

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Programowanie równoległe](../../../../docs/standard/parallel-programming/index.md)
