---
title: Wykonywanie zapytań w relacjach
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: 1675e4c6a610373e1c981b383ae0229739d96dd0
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003330"
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
  
 W związku z tym właściwości relacji są ważniejsze od wyników zapytania, a nie jako część samego zapytania. Po pobraniu przez zapytanie danych dotyczących określonego klienta definicja klasy wskazuje, że klienci mają zamówienia. Innymi słowy, oczekujesz, że właściwość `Orders` określonego klienta ma być kolekcją, która jest wypełniana wszystkimi zamówieniami od tego klienta. Jest to w rzeczywistości umową zadeklarowaną przez zdefiniowanie klas w ten sposób. Można oczekiwać, że zamówienia są widoczne nawet wtedy, gdy zapytanie nie zażądało zamówień. Oczekujesz, że Twój model obiektów utrzymuje wrażenie, że jest to rozszerzenie bazy danych z pokrewnymi obiektami natychmiast dostępnych.  
  
 Teraz, gdy masz relacje, możesz pisać zapytania, odwołując się do właściwości relacji zdefiniowanych w klasach. Te odwołania do relacji odnoszą się do relacji klucza obcego w bazie danych. Operacje, które używają tych relacji, przekładają się na bardziej złożone sprzężenia w równoważnej tabeli SQL. Tak długo, jak definiujesz relację (przy użyciu atrybutu <xref:System.Data.Linq.Mapping.AssociationAttribute>), nie musisz kodować jawnego sprzężenia w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Aby pomóc w utrzymaniu tego iluzji, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje technikę nazywaną *ładowaniem odroczonym*. Aby uzyskać więcej informacji, zobacz [odroczone względem natychmiastowego ładowania](deferred-versus-immediate-loading.md).  
  
 Rozważmy następujące zapytanie SQL, aby wyświetlić listę par `CustomerID`-`OrderID`:  
  
```sql
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Aby uzyskać te same wyniki przy użyciu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], należy użyć odwołania do właściwości `Orders` już istniejącej w klasie `Customer`. Odwołanie `Orders` zawiera informacje niezbędne do wykonania zapytania i projektu `CustomerID`-`OrderID` par, jak w poniższym kodzie:  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Możesz również wykonać odwrotność. Oznacza to, że możesz wysyłać zapytania do `Orders` i użyć odwołania do relacji `Customer`, aby uzyskać dostęp do informacji o skojarzonym obiekcie `Customer`. Poniższe projekty kodują ten sam `CustomerID`-`OrderID` par jak poprzednio, ale tym razem, wykonując zapytania `Orders` zamiast `Customers`.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](query-concepts.md)
