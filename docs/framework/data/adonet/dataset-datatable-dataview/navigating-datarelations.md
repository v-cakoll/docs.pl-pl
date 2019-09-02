---
title: Nawigowanie w elementach DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: b7b1717317bb119538497f60bae48ec1da2286c8
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203326"
---
# <a name="navigating-datarelations"></a>Nawigowanie w elementach DataRelation
Jedną z podstawowych funkcji <xref:System.Data.DataRelation> programu jest umożliwienie nawigacji od jednego <xref:System.Data.DataTable> do drugiego w obrębie <xref:System.Data.DataSet>. Dzięki temu <xref:System.Data.DataRow> można pobrać wszystkie powiązane obiekty w jednej **DataTable** , gdy podaje jeden element **DataRow** z powiązanej **tabeli DataTable**. Na przykład po ustaleniu **relacji** między tabelą klientów a tabelą zamówień można pobrać wszystkie wiersze zamówienia dla danego wiersza klienta przy użyciu **GetChildRows**.  
  
 Poniższy przykład kodu tworzy relację między tabelą **Customers** i tabelą **Orders** **zestawu danych** i zwraca wszystkie zamówienia dla każdego klienta.  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 Następny przykład jest oparty na powyższym przykładzie, łącznie z czterema tabelami i nawigowaniem w tych relacjach. Tak jak w poprzednim przykładzie, **CustomerID** powiąże tabelę **Customers** z tabelą Orders. Dla każdego klienta w tabeli **Customers** są określane wszystkie wiersze podrzędne w tabeli **Orders** , aby można było zwrócić liczbę zamówień określonych przez określonego klienta i ich wartości **IDZamówienia** .  
  
 Rozwinięty przykład zwraca również wartości z tabel **OrderDetails** i **Products** . Tabela **Orders** jest powiązana z tabelą **OrderDetails** przy użyciu funkcji **IDZamówienia** , aby określić, jakie produkty i ilości zostały uporządkowane według kolejności. Ponieważ tabela **OrderDetails** zawiera tylko identyfikator **ProductID** uporządkowanego produktu, **OrderDetails** jest związana z **produktami** przy użyciu klasy **ProductID** w celu zwrócenia **ProductName**. W tej relacji tabela **Products** jest elementem nadrzędnym, a tabela **Order** Details jest elementem podrzędnym. W związku z tym podczas iterowania za pomocą tabeli **OrderDetails** zostaje wywołana funkcja **GetParentRow** w celu pobrania pokrewnej wartości **ProductName** .  
  
 Należy zauważyć, że po utworzeniu **relacji** dla tabel **Customers** i Orders nie określono żadnej wartości dla flagi **xmlconstraint** (wartość domyślna to **true**). Przyjęto założenie, że wszystkie wiersze w tabeli Orders mają wartość **CustomerID** , która istnieje w tabeli nadrzędnych **klientów** . Jeśli element **CustomerID** istnieje w tabeli **Orders** , która nie istnieje w tabeli <xref:System.Data.ForeignKeyConstraint> Customers, powoduje to wystąpienie wyjątku.  
  
 Gdy kolumna podrzędna może zawierać wartości, których kolumna nadrzędna nie zawiera, ustaw dla flagi "isconstraint **" wartość false** podczas dodawania **relacji**między elementami. W przykładzie flaga " **isconstraint** " ma wartość **false** dla **relacji** między tabelą **Orders** i tabelą **OrderDetails** . Dzięki temu aplikacja zwróci wszystkie rekordy z tabeli **OrderDetails** i tylko podzestaw rekordów z tabeli Orders bez generowania wyjątku w czasie wykonywania. Rozwinięty przykład generuje dane wyjściowe w następującym formacie.  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 Poniższy przykład kodu jest rozwiniętą próbką, gdy zwracane są wartości z tabeli **OrderDetails** i **Products** , z tylko podzbiorem rekordów w tabeli Orders .  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
