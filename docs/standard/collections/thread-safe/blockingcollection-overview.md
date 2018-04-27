---
title: BlockingCollection — Przegląd
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BlockingCollection, overview
ms.assetid: 987ea3d7-0ad5-4238-8b64-331ce4eb3f0b
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 74303f07134401193d07d3b5d584c9498f023d90
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="blockingcollection-overview"></a>BlockingCollection — Przegląd
<xref:System.Collections.Concurrent.BlockingCollection%601> to klasa wątkowo kolekcji, która zapewnia następujące funkcje:  
  
-   Implementacja wzorca producent — konsument.  
  
-   Współbieżne Dodawanie i pobieranie elementów z wielu wątków.  
  
-   Opcjonalne maksymalnej pojemności.  
  
-   W przypadku operacji wstawiania i usuwania, które zablokować, jeśli kolekcja jest pusta lub pełnego.  
  
-   Wstawianie i usuwanie "try" operacje nie należy blokować lub który zablokować maksymalnie w określonym przedziale czasu.  
  
-   Hermetyzuje wszystkie typ kolekcji implementujący <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
-   Anulowanie z tokenami anulowania.  
  
-   Dwa rodzaje wyliczenie z `foreach` (`For Each` w języku Visual Basic):  
  
    1.  Wyliczenie tylko do odczytu.  
  
    2.  Wyliczenie, które powoduje usunięcie elementów, ponieważ są one wyliczone.  
  
## <a name="bounding-and-blocking-support"></a>Obsługa blokujących i ograniczających  
 <xref:System.Collections.Concurrent.BlockingCollection%601> obsługuje blokujących i ograniczających. Ograniczenia oznacza, że można ustawić maksymalną pojemność kolekcji. Ograniczenia jest ważne w niektórych scenariuszach, ponieważ pozwala kontrolować maksymalny rozmiar kolekcji w pamięci, i uniemożliwia tworzenie wątków przenoszenie zbyt daleko wcześniejsze odbierającą wątków.  
  
 Wiele wątków lub zadań można dodać elementy do kolekcji jednocześnie, a jeśli kolekcji osiągnie określony maksymalną pojemność, Tworzenie wątków zablokuje do momentu usunięcia elementu. Wielu klientów może jednocześnie usunąć elementy, a jeśli kolekcja jest pusta, odbierającą wątków zablokuje dopóki producent dodaje element. Tworzenie wątków można wywołać <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> aby wskazać, że ma więcej elementów zostaną dodane. Monitor konsumentów <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> właściwość, aby dowiedzieć się, gdy kolekcja jest pusta i ma więcej elementów zostanie dodany. W poniższym przykładzie przedstawiono prosty kolekcji BlockingCollection o ograniczonej pojemności 100. Zadanie producent dodaje elementów do kolekcji, tak długo, jak niektóre zewnętrznych warunek jest spełniony, a następnie wywołuje <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>. Zadanie konsumenta trwa elementów do <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> właściwość ma wartość true.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Pełny przykład, zobacz [porady: Dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="timed-blocking-operations"></a>Upłynął, blokowanie operacji  
 W upłynął blokuje <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operacji w kolekcjach ograniczonych, metoda próbuje dodać lub podjąć element. Jeśli element jest dostępny jest umieszczona w zmiennej, która została przekazana przez odwołanie, a metoda zwraca wartość true. Metoda zwraca wartość false, jeśli żaden element jest pobierany po upływie określonego limitu czasu. Wątek jest bezpłatna inne przydatne pracy przed podjęciem ponownej próby można uzyskać dostępu do kolekcji. Na przykład czasu blokowanie dostępu, zobacz drugi przykład w [porady: Dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="cancelling-add-and-take-operations"></a>Anulowanie Dodaj i podejmij działania  
 Dodaj i zazwyczaj wykonywane są operacje podejmuje w pętli. Możesz anulować pętlę przez przekazywanie <xref:System.Threading.CancellationToken> do <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> lub <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody, a następnie zaznaczając wartość tokenu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwości w każdej iteracji. Jeśli ma wartość true, będzie ona wówczas od użytkownika odpowiada żądanie anulowania przez wyczyszczenie wszystkich zasobów i wyjścia z pętli. W poniższym przykładzie przedstawiono przeciążenia <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> pobierającej anulowania tokenu i kod używający go:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 Na przykład sposobu obsługi anulowania Zobacz drugi przykład w [porady: Dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="specifying-the-collection-type"></a>Określanie typu kolekcji  
 Po utworzeniu <xref:System.Collections.Concurrent.BlockingCollection%601>, można określić nie tylko ograniczonej pojemności, ale również typem kolekcji do użycia. Na przykład można określić <xref:System.Collections.Concurrent.ConcurrentQueue%601> dla pierwszego w pierwszy limit zachowanie (FIFO) lub <xref:System.Collections.Concurrent.ConcurrentStack%601> ostatniego pierwszy LIFO zachowania. Można użyć dowolnej klasy kolekcji, który implementuje <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> interfejsu. Domyślny typ kolekcji dla <xref:System.Collections.Concurrent.BlockingCollection%601> jest <xref:System.Collections.Concurrent.ConcurrentQueue%601>. W poniższym przykładzie przedstawiono sposób tworzenia <xref:System.Collections.Concurrent.BlockingCollection%601> ciągów, które ma pojemność 1000 i używa <xref:System.Collections.Concurrent.ConcurrentBag%601>:  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Aby uzyskać więcej informacji, zobacz [porady: Dodawanie ograniczenia i funkcji blokowania w kolekcji](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md).  
  
## <a name="ienumerable-support"></a>Obsługa interfejsu IEnumerable  
 <xref:System.Collections.Concurrent.BlockingCollection%601> udostępnia <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metodę, która umożliwia klientom korzystać `foreach` (`For Each` w języku Visual Basic) na usuwanie elementów do czasu ukończenia kolekcji, co oznacza, że jest pusty i ma więcej elementów zostanie dodany. Aby uzyskać więcej informacji, zobacz [porady: użycie ForEach do usuwanie elementów blockingcollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).  
  
## <a name="using-many-blockingcollections-as-one"></a>Przy użyciu wielu BlockingCollections wśród  
 W scenariuszach, w których klient musi jednocześnie pobieranie elementów z wielu kolekcji, można utworzyć tablic <xref:System.Collections.Concurrent.BlockingCollection%601> i użyj metody statyczne, takiego jak <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> którego dodawanie do lub wykonać z dowolnego z kolekcji w programie Tablica. Jeśli blokuje jednej kolekcji, metoda natychmiast próbuje innego dopóki nie zostanie znaleziony taki, który można wykonać operacji. Aby uzyskać więcej informacji, zobacz [porady: Użycie tablic blokowanie kolekcji w potoku](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Kolekcje i struktury danych](../../../../docs/standard/collections/index.md)  
 [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
