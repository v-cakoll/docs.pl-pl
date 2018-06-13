---
title: Odroczone i ładowania bezpośredniego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
ms.openlocfilehash: 5955d7361658c825c120e62e531b72d402a12650
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360353"
---
# <a name="deferred-versus-immediate-loading"></a>Odroczone i ładowania bezpośredniego
Określona w zapytaniu dla obiekt faktycznie pobrać tylko żądanego obiektu. *Powiązane* obiekty nie są automatycznie dołączone w tym samym czasie. (Aby uzyskać więcej informacji, zobacz [zapytań w relacji](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) Nie widać fakt, że powiązane obiekty nie są już załadowana, ponieważ próba dostępu do nich tworzy żądanie, które pobierają je.  
  
 Na przykład możesz chcieć zapytania dla określonego zestawu zamówienia, a następnie tylko od czasu do czasu Wyślij wiadomość e-mail z powiadomieniem do konkretnego klientów. Nie zawsze konieczne będzie początkowo pobrać wszystkich danych klientów z każdej kolejności. Ładowanie odłożone umożliwia odroczenie pobierania dodatkowe informacje do momentu bezwzględnie konieczne. Rozważmy następujący przykład:  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 Wartość true, może być również odwrotnie. Może być aplikacji, aby wyświetlić klienta i kolejność danych w tym samym czasie. Wiadomo, że należy oba zestawy danych. Wiadomo, że aplikacja wymaga informacji o zamówieniu dla każdego klienta, jak uzyskać wyniki. Czy chcesz przesłać poszczególnych zapytania dotyczące zamówienia dla każdego klienta. Co naprawdę jest pobrać dane zlecenia wraz z klientów.  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 Można również dołączyć klienci i zamówienia w zapytaniu tworzące iloczyn wektorowy i pobierania względną bitów danych jako jeden rzut duże. Jednak te wyniki nie są jednostek. (Aby uzyskać więcej informacji, zobacz [LINQ w modelu obiektu SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)). Jednostki są obiektów, które mają tożsamości i że można modyfikować, te wyniki byłoby projekcje, które nie mogą być zmienione i utrwalone. Nawet gorsza można będzie można pobieranie wiele zbędnych danych zgodnie z każdego klienta powtarza się dla każdej kolejności w danych wyjściowych spłaszczoną sprzężenia.  
  
 Co naprawdę potrzebne jest sposobem pobrania zestawu powiązanych obiektów w tym samym czasie. Zestaw jest nakreślono części wykres, dzięki czemu można będzie nigdy nie być pobierania większa lub mniejsza niż niezbędne do zamierzonego użycia. W tym celu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia <xref:System.Data.Linq.DataLoadOptions> do ładowania bezpośredniego regionu modelu obiektu. Metody obejmują:  
  
-   <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Metody, aby natychmiast załadować dane powiązane z głównym celem.  
  
-   <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> Sposób pobrane dla określonego relacji obiekty filtru.  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
