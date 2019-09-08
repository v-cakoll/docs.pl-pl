---
title: Odroczone a bezpośrednie ładowanie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
ms.openlocfilehash: 2045cab19e7400f94888297571a172de1578094d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794140"
---
# <a name="deferred-versus-immediate-loading"></a>Odroczone a bezpośrednie ładowanie
Podczas wykonywania zapytania o obiekt faktycznie pobierany jest tylko żądany obiekt. Obiekty *powiązane* nie są automatycznie pobierane w tym samym czasie. (Aby uzyskać więcej informacji, zobacz [zapytania dotyczące relacji](querying-across-relationships.md).) Nie widać faktu, że powiązane obiekty nie są już załadowane, ponieważ próba uzyskania do nich dostępu spowoduje utworzenie żądania, które je pobierze.  
  
 Można na przykład utworzyć zapytanie dotyczące określonego zestawu zamówień, a następnie wysłać powiadomienie e-mail do określonych klientów. W każdym porządku nie trzeba początkowo pobierać wszystkich danych klientów. Można użyć opóźnionego ładowania, aby odroczyć pobieranie dodatkowych informacji do momentu, gdy będzie to absolutnie konieczne. Rozważmy następujący przykład:  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 Przeciwieństwem może być również wartość true. Może istnieć aplikacja, która musi wyświetlać dane klienta i zamówienia w tym samym czasie. Wiadomo, że potrzebujesz obu zestawów danych. Wiadomo, że aplikacja wymaga informacji o zamówieniach dla każdego klienta, gdy tylko uzyskasz wyniki. Nie chcesz przesyłać poszczególnych zapytań dla zamówień dla każdego klienta. W rzeczywistości warto pobrać dane zamówienia razem z klientami.  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 Możesz również dołączać do klientów i zamówień w zapytaniu, tworząc iloczyn wielu elementów i pobierając wszystkie względne bity danych jako jedną dużą projekcję. Jednak te wyniki nie są jednostkami. (Aby uzyskać więcej informacji, zobacz [LINQ to SQL model obiektów](the-linq-to-sql-object-model.md)). Jednostki są obiektami, które mają tożsamość i można modyfikować, podczas gdy te wyniki byłyby projekcjami, których nie można zmienić ani utrwalić. Nawet gorsze, można pobrać wiele nadmiarowych danych, ponieważ każdy klient powtarza się dla każdego zamówienia w danych wyjściowych spłaszczonych sprzężeń.  
  
 To, co naprawdę konieczne, jest sposobem na pobranie zestawu obiektów pokrewnych w tym samym czasie. Zestaw jest przekreśloną sekcją wykresu, dzięki czemu nigdy nie będzie można pobrać więcej lub mniej niż było to konieczne do zamierzonego użycia. W tym celu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umożliwia <xref:System.Data.Linq.DataLoadOptions> natychmiastowe ładowanie regionu modelu obiektów. Metody obejmują:  
  
- <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Metoda, aby natychmiast załadować dane powiązane z głównym celem.  
  
- <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> Metoda służąca do filtrowania obiektów pobranych dla konkretnej relacji.  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](query-concepts.md)
