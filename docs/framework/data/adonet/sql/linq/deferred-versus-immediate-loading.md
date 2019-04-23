---
title: Odroczone a bezpośrednie ładowanie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
ms.openlocfilehash: ae20dbe557c3cf56a273556c24578056843e9af6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096995"
---
# <a name="deferred-versus-immediate-loading"></a>Odroczone a bezpośrednie ładowanie
Po wykonaniu zapytania dotyczącego obiektu, możesz pobrać faktycznie tylko żądanego obiektu. *Powiązane* obiekty nie są automatycznie pobrać w tym samym czasie. (Aby uzyskać więcej informacji, zobacz [zapytań w relacjach](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) Nie widzisz, że fakt, że obiekty powiązane nie są już załadowane, ponieważ próba dostępu do nich generuje żądanie, która pobiera je.  
  
 Na przykład można znaleźć określonego zestawu zamówienia, a następnie tylko sporadycznie wyśle wiadomość e-mail z powiadomieniem do klientów danego. Nie zawsze należałoby początkowo można pobrać wszystkich danych klientów z każdego zamówienia. Za pomocą odroczonego ładowania mają być odroczone pobieranie dodatkowych informacji, dopóki nie jest bezwzględnie konieczne. Rozważmy następujący przykład:  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 Przeciwieństwo również może mieć wartość true. Może być aplikacja, która ma wyświetlić dane klienta i zamówienia w tym samym czasie. Wiesz, że potrzebujesz oba zestawy danych. Wiesz, że Twoja aplikacja potrzebuje informacji o zamówieniach dla każdego klienta, tak szybko, jak uzyskać wyniki. Czy chcesz przesłać poszczególnych kwerend w obsłudze zamówień dla każdego klienta. Co naprawdę jest do pobierania danych zlecenia wraz z klientów.  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 Można również dołączyć klienci i zamówienia w zapytaniu, tworzących obejmujących wiele produktów i pobieranie względne bity danych jako jeden duży projekcji. Te wyniki nie są jednak jednostek. (Aby uzyskać więcej informacji, zobacz [LINQ to SQL Model obiektów](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)). Jednostki są obiekty, które mają tożsamości i że można modyfikować, te wyniki byłyby projekcji, które nie mogą być zmienione i utrwalone. Co gorsza można będzie można pobierania wiele nadmiarowych danych zgodnie z każdego klienta powtarza się dla każdego zamówienia w danych wyjściowych spłaszczonych sprzężenia.  
  
 Co naprawdę potrzebne jest sposobem pobrania zestawu powiązanych obiektów w tym samym czasie. Zestaw jest nakreślonego części wykres, dzięki czemu można będzie nigdy nie być pobierania więcej lub mniej niż niezbędne do zamierzonego użycia. W tym celu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia <xref:System.Data.Linq.DataLoadOptions> dla bezpośrednie ładowanie region modelu obiektu. Metody obejmują:  
  
-   <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Metody, można od razu załadować dane powiązane z głównym celem.  
  
-   <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> Metod w celu Filtruj obiekty pobranych dla określonej relacji.  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
