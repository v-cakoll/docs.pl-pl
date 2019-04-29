---
title: Nawigowanie w elementach DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: f4dfccad23bf5d15f5cbd0a33e76a136417e13ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607267"
---
# <a name="navigating-datarelations"></a>Nawigowanie w elementach DataRelation
Jedną z podstawowych funkcji <xref:System.Data.DataRelation> jest umożliwienie nawigacji z jednego <xref:System.Data.DataTable> do drugiej w ramach <xref:System.Data.DataSet>. Dzięki temu można pobrać wszystkie powiązane <xref:System.Data.DataRow> obiekty w jednym **DataTable** , gdy jeden **DataRow** z powiązanych **DataTable**. Na przykład po ustanowieniu **DataRelation** między spisu klientów i tabelę zamówień, mogą pobierać wszystkie wiersze zamówienia dla wiersza określonego klienta za pomocą **GetChildRows**.  
  
 Poniższy przykład kodu tworzy **DataRelation** między **klientów** tabeli i **zamówienia** tabeli **DataSet** i zwraca wszystkie zamówienia dla każdego klienta.  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 Następny przykład opiera się na poprzednim przykładzie związanych ze sobą cztery tabele i nawigowanie po relacjach tych. Co w poprzednim przykładzie **CustomerID** odnosi się **klientów** do tabeli **zamówienia** tabeli. Dla każdego klienta w **klientów** tabeli wiersze podrzędne w **zamówienia** tabeli są określone, aby zwrócić liczbę zamówień ma określonego klienta i ich **OrderID** wartości.  
  
 Rozwinięty przykład zwraca również wartość wartości z **OrderDetails** i **produktów** tabel. **Zamówienia** tabela jest powiązana z **OrderDetails** tabeli, używając **OrderID** Aby ustalić, dla każdego zamówienia klienta, jakich produktów i ilości zostały uporządkowane. Ponieważ **OrderDetails** tabeli zawiera tylko **ProductID** produktu uporządkowane **OrderDetails** jest powiązany z **produktów** za pomocą **ProductID** celu zwrócenie **ProductName**. W tej relacji **produktów** tabeli jest elementem nadrzędnym i **Orderdetails** tabeli jest elementem podrzędnym. W rezultacie podczas iteracji przez **OrderDetails** tabeli **GetParentRow** jest wywoływana w celu pobrania powiązane **ProductName** wartość.  
  
 Należy zauważyć, że w przypadku **DataRelation** jest tworzona dla **klientów** i **zamówienia** tabele, nie określono wartości dla **createConstraints**flagi (wartość domyślna to **true**). To zakłada się, że wszystkie wiersze w **zamówienia** tabela ma **CustomerID** wartość, która istnieje w obiekcie nadrzędnym **klientów** tabeli. Jeśli **CustomerID** istnieje w **zamówienia** tabelę, która nie istnieje w **klientów** tabeli <xref:System.Data.ForeignKeyConstraint> powoduje zgłoszenie wyjątku.  
  
 Kolumna podrzędny może zawierać wartości, które nie zawiera kolumny nadrzędnej, ustawić **createConstraints** flaga **false** podczas dodawania **DataRelation**. W tym przykładzie **createConstraints** flaga jest ustawiona na **false** dla **DataRelation** między **zamówienia** tabeli i  **OrderDetails** tabeli. Umożliwia to aplikacji zwrócić wszystkie rekordy z **OrderDetails** tabeli i tylko podzestaw rekordów z **zamówienia** tabeli bez generowania wyjątku czasu wykonywania. Rozwinięty przykładowe generuje dane wyjściowe w następującym formacie.  
  
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
  
 Poniższy przykład kodu jest rozwinięty przykładowe gdzie wartości z **OrderDetails** i **produktów** tabele są zwracane, za pomocą tylko podzestaw rekordów w **zamówienia**tabeli są zwracane.  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
