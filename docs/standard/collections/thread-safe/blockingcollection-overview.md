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
ms.openlocfilehash: fb01d29c723962e28d8ec4afc984cb4d6c48f9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711327"
---
# <a name="blockingcollection-overview"></a>BlockingCollection — Przegląd
<xref:System.Collections.Concurrent.BlockingCollection%601>jest klasą kolekcji bezpieczne dla wątków, która zapewnia następujące funkcje:  
  
- Wdrożenie wzorca producent-konsument.  
  
- Jednoczesne dodawanie i przyjmowanie elementów z wielu wątków.  
  
- Opcjonalna maksymalna pojemność.  
  
- Operacje wstawiania i usuwania, które blokują, gdy zbieranie jest puste lub pełne.  
  
- Wstawianie i usuwanie operacji "try", które nie blokują lub które blokują do określonego czasu.  
  
- Hermetyzuje dowolny typ kolekcji, który implementuje<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
- Anulowanie z tokenami anulowania.  
  
- Dwa rodzaje wyliczenia z `foreach` (w`For Each` języku Visual Basic):  
  
    1. Wyliczenie tylko do odczytu.  
  
    2. Wyliczenie, które usuwa elementy, ponieważ są one wyliczane.  
  
## <a name="bounding-and-blocking-support"></a>Obsługa ograniczających i blokujących  
 <xref:System.Collections.Concurrent.BlockingCollection%601>obsługuje ograniczanie i blokowanie. Ograniczanie oznacza, że można ustawić maksymalną pojemność kolekcji. Ograniczanie jest ważne w niektórych scenariuszach, ponieważ umożliwia kontrolowanie maksymalny rozmiar kolekcji w pamięci i uniemożliwia wątków produkcji z przesuwanie się zbyt daleko przed wątków zużywających.  
  
 Wiele wątków lub zadań można dodawać elementy do kolekcji jednocześnie, a jeśli kolekcja osiągnie określoną maksymalną pojemność, wątki produkcji będzie blokować, dopóki element zostanie usunięty. Wielu konsumentów można usunąć elementy jednocześnie, a jeśli kolekcja staje się pusta, wątki zużywające będzie blokować, dopóki producent dodaje element. Wątku produkcji można <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> wywołać, aby wskazać, że nie więcej elementów zostaną dodane. Konsumenci monitorują <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> właściwość, aby wiedzieć, kiedy kolekcja jest pusta i nie więcej elementów zostaną dodane. W poniższym przykładzie przedstawiono proste BlockingCollection o ograniczonej pojemności 100. Zadanie producenta dodaje elementy do kolekcji, o ile spełniony <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>jest jakiś warunek zewnętrzny, a następnie wywołuje . Zadanie konsumenta pobiera <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> elementy, dopóki właściwość nie zostanie true.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Aby uzyskać pełny przykład, zobacz [Jak: Dodawanie i odbieranie elementów pojedynczo z BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="timed-blocking-operations"></a>Operacje blokowania z czasem  
 W czasie <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> blokowania <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> i operacji na ograniczone kolekcje, metoda próbuje dodać lub wziąć element. Jeśli element jest dostępny, jest umieszczany w zmiennej, która została przekazana przez odwołanie, a metoda zwraca wartość true. Jeśli żaden element nie jest pobierany po określonym przedziale czasu, metoda zwraca wartość false. Wątek jest następnie swobodnie wykonać kilka innych przydatnych prac przed ponowną próbą uzyskania dostępu do kolekcji. Na przykład czasowego blokowania dostępu, zobacz drugi przykład w [Jak: Dodawanie i przyjmować elementy indywidualnie z BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="cancelling-add-and-take-operations"></a>Anulowanie operacji dodawania i podejmowania  
 Operacje Dodawania i Przyjmowania są zazwyczaj wykonywane w pętli. Można anulować pętli, przekazując <xref:System.Threading.CancellationToken> <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> w <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> do lub metody, a następnie <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> sprawdzanie wartości właściwości tokenu na każdej iteracji. Jeśli wartość jest true, to do Ciebie, aby odpowiedzieć na żądanie anulowania, czyszcząc wszystkie zasoby i wyjście z pętli. W poniższym przykładzie przedstawiono <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> przeciążenie, które ma token anulowania i kod, który go używa:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 Na przykład, jak dodać obsługę anulowania, zobacz drugi przykład w [Jak: Dodawanie i przyjmować elementy indywidualnie z BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md).  
  
## <a name="specifying-the-collection-type"></a>Określanie typu kolekcji  
 Podczas tworzenia <xref:System.Collections.Concurrent.BlockingCollection%601>, można określić nie tylko ograniczone zdolności produkcyjnych, ale także typ kolekcji do użycia. Na przykład można określić <xref:System.Collections.Concurrent.ConcurrentQueue%601> zachowanie dla pierwszego wyjścia (FIFO) <xref:System.Collections.Concurrent.ConcurrentStack%601> lub zachowanie dla ostatniego wyjścia (LIFO). Można użyć dowolnej klasy kolekcji, <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> która implementuje interfejs. Domyślnym typem <xref:System.Collections.Concurrent.BlockingCollection%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601>kolekcji jest . W poniższym przykładzie kodu <xref:System.Collections.Concurrent.BlockingCollection%601> pokazano, jak utworzyć ciągi o pojemności <xref:System.Collections.Concurrent.ConcurrentBag%601>1000 i używa:  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Aby uzyskać więcej informacji, zobacz [Jak: Dodawanie funkcji ograniczających i blokujących do kolekcji](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md).  
  
## <a name="ienumerable-support"></a>Obsługa ienumerable  
 <xref:System.Collections.Concurrent.BlockingCollection%601>Udostępnia <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metodę, która umożliwia `foreach` `For Each` konsumentom użycie (w języku Visual Basic) do usuwania elementów, dopóki kolekcja nie zostanie ukończona, co oznacza, że jest pusta i nie więcej elementów zostaną dodane. Aby uzyskać więcej informacji, zobacz [Jak: Użyj ForEach do usuwania elementów w BlockingCollection](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md).  
  
## <a name="using-many-blockingcollections-as-one"></a>Używanie wielu kolekcji blokujących jako jeden  
 W scenariuszach, w których konsument musi wziąć elementy z wielu kolekcji <xref:System.Collections.Concurrent.BlockingCollection%601> jednocześnie, można utworzyć <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> tablice i używać metod statycznych, takich jak i <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> które będą dodawać do lub wziąć z dowolnej kolekcji w tablicy. Jeśli jedna kolekcja blokuje, metoda natychmiast próbuje innego, dopóki nie znajdzie taki, który można wykonać operację. Aby uzyskać więcej informacji, zobacz [Jak: Korzystanie z tablic blokowania kolekcji w potoku](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje i struktury danych](../../../../docs/standard/collections/index.md)
- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
