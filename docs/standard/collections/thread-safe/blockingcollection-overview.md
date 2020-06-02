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
ms.openlocfilehash: 708ab9dc8df2ee3128036ffc71e9abc51a56e33b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287916"
---
# <a name="blockingcollection-overview"></a>BlockingCollection — Przegląd
<xref:System.Collections.Concurrent.BlockingCollection%601>to Klasa kolekcji z bezpieczną wątkiem, która udostępnia następujące funkcje:  
  
- Implementacja wzorca producent-odbiorca.  
  
- Jednoczesne Dodawanie i pobieranie elementów z wielu wątków.  
  
- Opcjonalna Maksymalna pojemność.  
  
- Operacje wstawiania i usuwania, które są blokowane, gdy kolekcja jest pusta lub pełna.  
  
- Wstawianie i usuwanie operacji "try", które nie blokują ani nie blokują w określonym przedziale czasu.  
  
- Hermetyzuje wszystkie typy kolekcji implementujące<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>  
  
- Anulowanie z tokenami anulowania.  
  
- Dwa rodzaje wyliczania z `foreach` ( `For Each` w Visual Basic):  
  
    1. Wyliczenie tylko do odczytu.  
  
    2. Wyliczenie, które usuwa elementy po ich wyliczeniu.  
  
## <a name="bounding-and-blocking-support"></a>Obsługa ograniczenia i blokowanie  
 <xref:System.Collections.Concurrent.BlockingCollection%601>obsługuje ograniczenia i blokowanie. Ograniczenia — można ustawić maksymalną pojemność kolekcji. Ograniczenia są istotne w niektórych scenariuszach, ponieważ umożliwiają kontrolowanie maksymalnego rozmiaru kolekcji w pamięci i uniemożliwia przechodzenie przez nie wątki do zużywanych wątków.  
  
 Wiele wątków lub zadań może jednocześnie dodawać elementy do kolekcji, a jeśli kolekcja osiągnie swoją określoną maksymalną pojemność, wątki wytwarzające będą blokować do momentu usunięcia elementu. Wielu odbiorców może usuwać elementy współbieżnie, a jeśli kolekcja stanie się pusta, zużywające wątki będą blokować do momentu dodania elementu do producenta. Wątek produkcji może wywoływać <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> , aby wskazać, że nie zostaną dodane żadne dodatkowe elementy. Odbiorcy monitorują <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> Właściwość, aby wiedzieć, kiedy kolekcja jest pusta i nie zostaną dodane żadne elementy. W poniższym przykładzie przedstawiono prostą BlockingCollection o ograniczonej pojemności 100. Zadanie producenta dodaje elementy do kolekcji, o ile warunek zewnętrzny ma wartość true, a następnie wywołuje <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> . Zadanie odbiorcy Pobiera elementy do momentu, gdy <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> Właściwość ma wartość true.  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 Pełny przykład można znaleźć w temacie [How to: Add and Take Items osobno from a BlockingCollection](how-to-add-and-take-items.md).  
  
## <a name="timed-blocking-operations"></a>Operacje blokowania czasu  
 W czasie blokowania <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operacji na powiązanych kolekcjach Metoda próbuje dodać lub pobrać element. Jeśli element jest dostępny, jest umieszczany w zmiennej przekazanej przez odwołanie, a metoda zwraca wartość true. Jeśli żaden element nie zostanie pobrany po upływie określonego limitu czasu, metoda zwróci wartość false. Wątek jest następnie bezpłatny, aby wykonać inną użyteczną pomoc przed ponowną próbą uzyskania dostępu do kolekcji. Przykład przekroczenia limitu czasu dostępu można znaleźć w drugim przykładzie w temacie [How to: Add and Take Items from BlockingCollection](how-to-add-and-take-items.md).  
  
## <a name="cancelling-add-and-take-operations"></a>Anulowanie operacji dodawania i podejmij  
 Operacje dodawania i podejmowania operacji są zwykle wykonywane w pętli. Możesz anulować pętlę, przechodząc <xref:System.Threading.CancellationToken> do <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody lub, a następnie sprawdzając wartość <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> Właściwości token dla każdej iteracji. Jeśli wartość jest równa true, wówczas można odpowiedzieć na żądanie anulowania przez oczyszczenie wszystkich zasobów i wyjście z pętli. Poniższy przykład pokazuje Przeciążenie, <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> które ma token anulowania i kod, który go używa:  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 Aby zapoznać się z przykładem dodawania obsługi anulowania, zobacz drugi przykład, w [jaki sposób: dodawać i przyjmować elementy indywidualnie z BlockingCollection](how-to-add-and-take-items.md).  
  
## <a name="specifying-the-collection-type"></a>Określanie typu kolekcji  
 Podczas tworzenia <xref:System.Collections.Concurrent.BlockingCollection%601> , można określić nie tylko powiązane pojemności, ale również typ kolekcji do użycia. Można na przykład określić <xref:System.Collections.Concurrent.ConcurrentQueue%601> zachowanie podczas pierwszego (FIFO) lub w <xref:System.Collections.Concurrent.ConcurrentStack%601> przypadku ostatniego zachowania w pierwszej kolejności (LIFO). Można użyć dowolnej klasy kolekcji, która implementuje <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> interfejs. Domyślnym typem kolekcji <xref:System.Collections.Concurrent.BlockingCollection%601> jest <xref:System.Collections.Concurrent.ConcurrentQueue%601> . Poniższy przykład kodu pokazuje, jak utworzyć ciągi o <xref:System.Collections.Concurrent.BlockingCollection%601> pojemności 1000 i użyć <xref:System.Collections.Concurrent.ConcurrentBag%601> :  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 Aby uzyskać więcej informacji, zobacz [jak: Dodawanie funkcji ograniczania i blokowania do kolekcji](how-to-add-bounding-and-blocking.md).  
  
## <a name="ienumerable-support"></a>Obsługa interfejsu IEnumerable  
 <xref:System.Collections.Concurrent.BlockingCollection%601>zapewnia <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metodę, która umożliwia użytkownikom używanie `foreach` ( `For Each` w Visual Basic) do usuwania elementów do momentu ukończenia kolekcji, co oznacza, że jest pusta i nie zostaną dodane żadne dodatkowe elementy. Aby uzyskać więcej informacji, zobacz [How to: use foreach to Remove Items in BlockingCollection](how-to-use-foreach-to-remove.md).  
  
## <a name="using-many-blockingcollections-as-one"></a>Używanie wielu BlockingCollections jako jednej  
 W przypadku scenariuszy, w których odbiorca musi przeszukiwać elementy z wielu kolekcji jednocześnie, można tworzyć tablice <xref:System.Collections.Concurrent.BlockingCollection%601> i używać metod statycznych, takich jak <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> , które będą dodawać lub przyjmować dowolne kolekcje w tablicy. Jeśli jedna kolekcja blokuje, Metoda natychmiast podejmie próbę, aż znajdzie ją, która może wykonać operację. Aby uzyskać więcej informacji, zobacz [How to: use Arrays of blocked Collections w potoku](how-to-use-arrays-of-blockingcollections.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje i struktury danych](../index.md)
- [Kolekcje bezpieczne dla wątków](index.md)
