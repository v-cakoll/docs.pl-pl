---
title: BlockingCollection — Przegląd
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BlockingCollection, overview
ms.assetid: 987ea3d7-0ad5-4238-8b64-331ce4eb3f0b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 257435516b38d0e4389b7feceba68371bcc8f90e
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519919"
---
# <a name="blockingcollection-overview"></a>BlockingCollection — Przegląd
<xref:System.Collections.Concurrent.BlockingCollection%601> jest klasą wątkowo kolekcji, która oferuje następujące funkcje:  
  
-   Implementacja wzorca producent — konsument.  
  
-   Równocześnie Dodawanie i pobieranie elementów z wielu wątków.  
  
-   Opcjonalne maksymalnej pojemności.  
  
-   Operacje wstawiania i usuwania, które zablokować, jeśli kolekcja jest pusta lub pełne.  
  
-   Wstawiania i usuwania "try" operacje nie należy blokować lub Blokuj, aż w wybranym okresie.  
  
-   Hermetyzuje dowolny typ kolekcji, który implementuje <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
-   Unieważnieniu przy użyciu tokenów anulowania.  
  
-   Dwa rodzaje wyliczenie z `foreach` (`For Each` w języku Visual Basic):  
  
    1.  Wyliczenie tylko do odczytu.  
  
    2.  Wyliczenie, które usuwa elementy, jak wyliczane są.  
  
## <a name="bounding-and-blocking-support"></a>Blokujących i ograniczających pomocy technicznej  
 <xref:System.Collections.Concurrent.BlockingCollection%601> obsługuje blokujących i ograniczających. Blokujących oznacza, że można ustawić maksymalną pojemność kolekcji. Blokujących jest ważne w niektórych scenariuszach, ponieważ pozwala na sterowanie maksymalny rozmiar kolekcji w pamięci i uniemożliwia tworzenie wątków przeniesienie zbyt daleko wcześniej konsumencki wątków.  
  
 Wiele wątków lub zadań można dodawać elementy do kolekcji jednocześnie, a jeśli kolekcja osiągnie określoną maksymalną pojemność, Tworzenie wątków zablokuje do momentu usunięcia elementu. Wielu odbiorców jednocześnie usunąć elementy, a jeśli kolekcja staje się puste, wątki konsumencki spowoduje zablokowanie aż producent dodaje element. Tworzenie wątku można wywołać <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> do wskazania, zostaną dodane nie więcej elementów. Monitor konsumentów <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> właściwości, aby dowiedzieć się, gdy kolekcja jest pusta i nie więcej elementy zostaną dodane. Poniższy przykład pokazuje prosty BlockingCollection z ograniczoną pojemność 100. Zadanie producentów dodaje elementy do kolekcji, tak długo, jak niektóre zewnętrznych warunek jest spełniony, a następnie wywołuje <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>. Zadanie konsumenta trwa elementów do momentu <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> właściwość ma wartość true.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Aby uzyskać kompletny przykład, zobacz [porady: Dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="timed-blocking-operations"></a>Upłynął limit czasu operacji blokowania  
 W upłynął limit czasu blokowania <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operacji na kolekcjach ograniczonych, metoda próbuje dodać lub wykonać element. Jeśli element jest dostępny jest umieszczany w zmiennej, która została przekazana przez odwołanie, a metoda zwraca wartość true. Jeśli żaden element nie jest pobierany po upływie limitu czasu określonego metoda zwraca wartość false. Ten wątek jest następnie robić innych przydatnych działań przed podjęciem ponownej próby uzyskać dostęp do kolekcji. Na przykład blokowanie dostępu przez czasu Zobacz drugi przykład w [porady: Dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="cancelling-add-and-take-operations"></a>Anulowania Dodawanie i pobieranie operacji  
 Dodaj i wykonaj operacje są zazwyczaj wykonywane w pętli. Możesz anulować pętli, przekazując <xref:System.Threading.CancellationToken> do <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> lub <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody, a następnie zaznaczając wartość tokenu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość w każdej iteracji. Jeśli ma wartość true, to do Ciebie odpowiedzi na żądanie anulowania czyszczenia zasobów i wyjścia z pętli. W poniższym przykładzie pokazano przeciążenia <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> przyjmującej anulowania tokenu i kod, używa ona:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 Na przykład jak dodać obsługę anulowania, zobacz drugi przykład w [porady: Dodawanie i pobieranie elementów osobno z kolekcji BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="specifying-the-collection-type"></a>Określanie typu kolekcji  
 Po utworzeniu <xref:System.Collections.Concurrent.BlockingCollection%601>, można określić nie tylko ograniczoną pojemność, ale również typ kolekcji do użycia. Na przykład można określić <xref:System.Collections.Concurrent.ConcurrentQueue%601> dla pierwszego w pierwszym się zachowanie (FIFO) lub <xref:System.Collections.Concurrent.ConcurrentStack%601> ostatniego zachowania pierwszy LIFO (). Można użyć dowolnej klasy kolekcji, który implementuje <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> interfejsu. Domyślny typ kolekcji dla <xref:System.Collections.Concurrent.BlockingCollection%601> jest <xref:System.Collections.Concurrent.ConcurrentQueue%601>. Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Collections.Concurrent.BlockingCollection%601> ciągów, które ma pojemność wynoszącą 1000 i używa <xref:System.Collections.Concurrent.ConcurrentBag%601>:  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Aby uzyskać więcej informacji, zobacz [porady: Dodawanie blokujących i ograniczających do kolekcji funkcji blokowania](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md).  
  
## <a name="ienumerable-support"></a>Obsługa interfejsu IEnumerable  
 <xref:System.Collections.Concurrent.BlockingCollection%601> udostępnia <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metodę, która umożliwia klientom korzystać `foreach` (`For Each` w języku Visual Basic) do momentu ukończenia kolekcji, należy usunąć elementy, co oznacza, że jest pusta i nie więcej elementy zostaną dodane. Aby uzyskać więcej informacji, zobacz [porady: użycie ForEach do usuwanie elementów blockingcollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).  
  
## <a name="using-many-blockingcollections-as-one"></a>Za pomocą wielu BlockingCollections jako jeden  
 W przypadku scenariuszy, w którym konsument musi podjąć równocześnie elementów z wieloma kolekcjami można utworzyć tablice o <xref:System.Collections.Concurrent.BlockingCollection%601> i użyj metod statycznych, takich jak <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> który dodawanie do lub wykonać z dowolnego z kolekcji w Tablica. Jeśli blokuje jedną kolekcję metody natychmiast próbuje innego aż znajdzie taki, który można wykonać operacji. Aby uzyskać więcej informacji, zobacz [porady: Użycie tablic blokowanie kolekcji w potoku](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [Kolekcje i struktury danych](../../../../docs/standard/collections/index.md)  
- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
