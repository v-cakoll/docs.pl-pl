---
title: Wykonywanie zapytań w relacjach
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: be0aea66f0923b8b353f42cecc9360731efc7bb9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792845"
---
# <a name="querying-across-relationships"></a>Wykonywanie zapytań w relacjach
Odwołania do innych obiektów lub kolekcji innych obiektów w definicjach klas bezpośrednio odpowiadają na relacje klucza obcego w bazie danych. Tych relacji można użyć podczas wykonywania zapytania przy użyciu notacji kropkowej w celu uzyskania dostępu do właściwości relacji i przechodzenia z jednego obiektu do drugiego. Te operacje dostępu są tłumaczone na bardziej złożone sprzężenia lub skorelowane podzapytania w odpowiedniku SQL.  
  
 Na przykład następujące zapytanie przechodzi od zamówień do klientów w taki sposób, aby ograniczyć wyniki do zamówień tylko dla klientów znajdujących się w Londynie.  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 Jeśli właściwości relacji nie istniały, należy napisać je ręcznie jako *sprzężenia*, tak jak w przypadku zapytania SQL, jak w poniższym kodzie:  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 Możesz użyć właściwości *relacji* , aby zdefiniować tę konkretną relację jeden raz. Następnie można użyć bardziej wygodnej składni kropki. Jednak właściwości relacji są ważniejsze, ponieważ modele obiektów specyficzne dla domeny są zwykle zdefiniowane jako hierarchie lub wykresy. Obiekty, względem których program ma odwoływać się do innych obiektów. Jest to tylko szczęśliwe współdziałanie, że relacje obiekt-obiekt odpowiadają relacji między kluczami obcym w bazach danych. Dostęp do właściwości zapewnia wygodny sposób zapisu sprzężeń.  
  
 W związku z tym właściwości relacji są ważniejsze od wyników zapytania, a nie jako część samego zapytania. Po pobraniu przez zapytanie danych dotyczących określonego klienta definicja klasy wskazuje, że klienci mają zamówienia. Innymi słowy, oczekujesz `Orders` , że właściwość określonego klienta ma być kolekcją, która jest wypełniana wszystkimi zamówieniami od tego klienta. Jest to w rzeczywistości umową zadeklarowaną przez zdefiniowanie klas w ten sposób. Można oczekiwać, że zamówienia są widoczne nawet wtedy, gdy zapytanie nie zażądało zamówień. Oczekujesz, że Twój model obiektów utrzymuje wrażenie, że jest to rozszerzenie bazy danych z pokrewnymi obiektami natychmiast dostępnych.  
  
 Teraz, gdy masz relacje, możesz pisać zapytania, odwołując się do właściwości relacji zdefiniowanych w klasach. Te odwołania do relacji odnoszą się do relacji klucza obcego w bazie danych. Operacje, które używają tych relacji, przekładają się na bardziej złożone sprzężenia w równoważnej tabeli SQL. Tak długo, jak definiujesz relację (przy użyciu <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybutu), nie musisz kodować jawnego sprzężenia w. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 Aby pomóc w utrzymaniu tego [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iluzji, implementuje technikę nazywaną *ładowanie odroczone*. Aby uzyskać więcej informacji, zobacz [odroczone względem natychmiastowego ładowania](deferred-versus-immediate-loading.md).  
  
 Rozważmy następujące zapytanie SQL, aby zaprojektować `CustomerID` listę - `OrderID` par:  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Aby uzyskać te same wyniki przy użyciu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], należy użyć `Customer` odwołania `Orders` do właściwości już istniejącej w klasie. Dokumentacja zawiera informacje niezbędne do wykonania zapytania - i `OrderID` `CustomerID` projektu par, jak w poniższym kodzie: `Orders`  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Możesz również wykonać odwrotność. Oznacza to, że można wysyłać `Orders` zapytania do informacji `Customer` o skojarzonym `Customer` obiekcie i używać ich. Poniższy kod koduje te same `CustomerID` - `OrderID` pary jak `Orders` poprzednio, `Customers`ale tym razem wykonując zapytania zamiast.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](query-concepts.md)
