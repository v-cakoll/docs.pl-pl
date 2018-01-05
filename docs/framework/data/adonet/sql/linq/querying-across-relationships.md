---
title: "Wykonywanie zapytań w relacjach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 03c2da9f65964a9ed43d1e82abf779b43be733ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="querying-across-relationships"></a>Wykonywanie zapytań w relacjach
Odwołania do innych obiektów lub kolekcje innych obiektów w definicji klasy bezpośrednio odpowiadają relacje klucza obcego w bazie danych. Te relacje można użyć w przypadku zapytania według używając zapisu kropkowego dostępu do właściwości relacji i przejść z jednego obiektu do innego. Wykonuje te operacje związane z dostępem do bardziej złożonych sprzężeń ani podzapytań skorelowane równoważne SQL.  
  
 Na przykład następujące zapytanie powoduje przejście zleceń klientom sposób, aby ograniczyć wyniki do tylko zamówień dla klientów w Londynie.  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 Jeśli właściwości relacji nie istnieje. należy zapisać je ręcznie jako *sprzężenia*, tak jak w zapytaniu SQL, zgodnie z poniższym kodem:  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 Można użyć *relacji* właściwość, aby zdefiniować tego konkretnego relacji jeden raz. Następnie można użyć wygodniejsze składni z kropkami. Ale właściwości relacji ważniejsze istnieje ponieważ modele obiektów specyficznego dla domeny są zazwyczaj definiowane jako hierarchii lub wykresy. Obiekty, które program względem odwołują się do innych obiektów. Jest tylko wszystkiego zbieżność odpowiadające relacji obiektu do obiektu obcego wstawiony klucza relacje w bazach danych. Dostęp do właściwości następnie oferuje wygodny sposób zapisu sprzężenia.  
  
 W odniesieniu do tego właściwości relacji są ważniejsze po stronie wyników zapytania niż jako część samą kwerendę. Po pobraniu zapytanie dane dotyczące określonego klienta definicji klasy oznacza, że klienci mają zleceń. Innymi słowy, planujesz `Orders` właściwości określonego klienta jako kolekcja, która jest wypełniana wszystkich zamówień z tego klienta. W rzeczywistości to kontrakt, który jest zadeklarowany przez definiowanie klas w ten sposób. Powinny być widoczne zamówienia istnieje, nawet wtedy, gdy zapytanie nie żądał zleceń. Spodziewasz się modelu obiektu do obsługi iluzji jest rozszerzenie bazy danych z powiązanych obiektów natychmiast dostępna w pamięci.  
  
 Teraz, gdy masz relacje możesz pisać zapytania, odwołując się do właściwości relacji zdefiniowanych w klas. Te odwołania relacji odpowiadają relacje klucza obcego w bazie danych. Tłumaczenie operacji korzystających z tych relacji do bardziej złożonych sprzężeń równoważne SQL. Tak długo, jak zdefiniowano relacji (przy użyciu <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybut), nie masz kodu jawne sprzężenia w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Pomagających zapewnić tym wrażenie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technika wywołuje implementuje *odroczonego ładowania*. Aby uzyskać więcej informacji, zobacz [odroczone i ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 Należy wziąć pod uwagę następujące zapytanie SQL, aby wyświetlić listę `CustomerID` - `OrderID` pary:  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Aby uzyskać takie same wyniki za pomocą [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], możesz użyć `Orders` właściwości odwołania już istniejącego w `Customer` klasy. `Orders` Zawiera informacje niezbędne do wykonywania zapytań i projektu `CustomerID` - `OrderID` pary, zgodnie z poniższym kodem:  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Można także utworzyć odwrotnej. Oznacza to, że można zbadać `Orders` i używać jej `Customer` relacji odwołania do dostępu do informacji o skojarzony `Customer` obiektu. Poniższy kod projektów takie same `CustomerID` - `OrderID` pary jak poprzednio, ale tym razem badając `Orders` zamiast `Customers`.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
