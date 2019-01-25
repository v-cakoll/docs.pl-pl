---
title: Wykonywanie zapytań w relacjach
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: 783ecb35408f63c7f3e7299e503c3f0fda3f36ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666439"
---
# <a name="querying-across-relationships"></a>Wykonywanie zapytań w relacjach
Odwołania do innych obiektów lub kolekcji innych obiektów w definicji klasy odpowiadają bezpośrednio relacje klucza obcego w bazie danych. Możesz użyć tych relacji, zapytania przy użyciu notacji z kropką dostęp do właściwości relacji i przejść z jednego obiektu do drugiego. Te operacje dostępu wykonuje translację elementu do bardziej złożonych sprzężeń lub skorelowany podzapytań równoważne SQL.  
  
 Na przykład następujące zapytanie powoduje przejście z zamówień dla klientów jako sposób, aby ograniczyć wyniki do tylko zamówień dla klientów znajdujących się w Londynie.  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 Jeśli nie istniał właściwości relacji trzeba będzie zapisanie ich ręcznie jako *sprzężeń*tak samo, tak jak w zapytaniu SQL, tak jak w poniższym kodzie:  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 Możesz użyć *relacji* właściwości do definiowania tego konkretną relację jeden raz. Następnie można użyć bardziej wygodne składni z kropkami. Ale właściwości relacji istnieje, co ważniejsze, ponieważ modeli obiektów specyficznych dla domeny są zazwyczaj definiowane jako hierarchie lub wykresów. Obiekty, które możesz programować przy użyciu odwołują się do innych obiektów. Jest tylko wszystkiego zbieżność relacji obiektu do obiektu odnoszą się do relacji obcych różne klucza w bazach danych. Dostęp do właściwości następnie zapewnia wygodny sposób zapisu sprzężenia.  
  
 W efekcie właściwości relacji są niezwykle ważne po stronie wyników zapytań niż w ramach samo zapytanie. Po zapytanie pobierze dane dotyczące określonego klienta, definicja klasy informuje, że klienci zamówienia. Innymi słowy, oczekujesz, że `Orders` właściwości określonego klienta jako kolekcja, która jest wypełniana przy użyciu wszystkich zamówień tego klienta. W rzeczywistości to kontrakt, który zadeklarowana przez definiowanie klas w ten sposób. Powinna się pojawić zamówienia istnieje, nawet wtedy, gdy zapytanie nie żądanie zamówienia. Oczekujesz, że model obiektów do utrzymania wrażenie, że jest to rozszerzenie w pamięci, bazy danych z pokrewnymi obiektami, od razu dostępna.  
  
 Teraz, gdy masz relacji, możesz pisać zapytania, odwołując się do właściwości relacji zdefiniowanych w Twoich zajęciach. Te odwołania relacji odpowiadają relacje klucza obcego w bazie danych. Przetłumacz operacji korzystających z tych relacji do bardziej złożonych sprzężeń w równoważnych SQL. Tak długo, jak zdefiniowano relacji (przy użyciu <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybut), nie masz kodu za pomocą jawnego sprzężenia w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Pomagających zapewnić tym wrażenie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implementuje technikę o nazwie *odroczone ładowanie*. Aby uzyskać więcej informacji, zobacz [odroczone a ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
 Należy wziąć pod uwagę następujące zapytanie SQL, aby wyświetlić listę `CustomerID` - `OrderID` pary:  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 Aby uzyskać te same wyniki przy użyciu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], możesz użyć `Orders` właściwość odwoływać się do już istniejących w `Customer` klasy. `Orders` Dokumentacja zawiera informacje niezbędne do wykonywania zapytań i projektu `CustomerID` - `OrderID` pary, zgodnie z poniższym kodem:  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 Można również wykonać odwrotnie. Oznacza to, że można tworzyć zapytania `Orders` i używać jej `Customer` relacji odwołanie do uzyskiwania dostępu do informacji o skojarzonego `Customer` obiektu. Poniższy kod projekty takie same `CustomerID` - `OrderID` par tak jak poprzednio, ale tym razem, badając `Orders` zamiast `Customers`.  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także
- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
