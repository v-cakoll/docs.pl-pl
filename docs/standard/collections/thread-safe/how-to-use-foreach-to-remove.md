---
title: 'Porady: używanie ForEach do usuwanie elementów BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3337b3e6b181fd39e305e45f96b792d8051a81a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568927"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Porady: używanie ForEach do usuwanie elementów BlockingCollection
Oprócz pobieranie elementów z <xref:System.Collections.Concurrent.BlockingCollection%601> za pomocą <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody, można również użyć [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([dla każdego](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) w języku Visual Basic) aby usunąć elementy, dopóki nie zostanie Dodawanie zakończone i kolekcji jest pusty. Ta metoda jest wywoływana *mutacja wyliczenie* lub *wykorzystywanie wyliczenie* , ponieważ w odróżnieniu od typowych `foreach` (`For Each`) pętli, ten moduł wyliczający modyfikuje kolekcji źródłowej przez usunięcie elementy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób usunąć wszystkie elementy w <xref:System.Collections.Concurrent.BlockingCollection%601> za pomocą `foreach` (`For Each`) pętli.  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 W tym przykładzie użyto `foreach` pętli z <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> metoda odbierającą wątku, co powoduje, że każdy element, aby usunąć z kolekcji, ponieważ jest on wyliczone. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> Ogranicza maksymalną liczbę elementów znajdujących się w kolekcji w dowolnym momencie. Wyliczanie kolekcji w ten sposób blokuje wątku konsumenta, jeśli brak dostępnych elementów lub jeśli kolekcja jest pusta. W tym przykładzie blokuje nie ma znaczenia, ponieważ wątek producent dodaje elementy szybciej niż mogą być używane.  
  
 Nie ma żadnej gwarancji, że elementy są wyliczane w tej samej kolejności, w której są dodawane przez wątki producenta.  
  
 Aby wyliczyć kolekcji bez modyfikowania jej, wystarczy użyć `foreach` (`For Each`) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody. Jednak ważne jest zrozumienie, że tego rodzaju wyliczenie reprezentuje migawki kolekcji w określonym punkcie w czasie. Jeśli inne wątki dodawania lub usuwania elementów współbieżnie, podczas wykonywania pętli, pętla może reprezentuje rzeczywisty stan kolekcji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Programowanie równoległe](../../../../docs/standard/parallel-programming/index.md)
