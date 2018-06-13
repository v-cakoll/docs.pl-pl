---
title: Nawigowanie po DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: c46007fb86a76405fd99d6e943779238d6885aa8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761431"
---
# <a name="navigating-datarelations"></a>Nawigowanie po DataRelations
Jeden z podstawowych funkcji <xref:System.Data.DataRelation> jest umożliwienie nawigacji z jednego <xref:System.Data.DataTable> do drugiej w ramach <xref:System.Data.DataSet>. Dzięki temu można pobrać wszystkich odnośnych <xref:System.Data.DataRow> obiektów w jednym **DataTable** , gdy jeden **DataRow** z powiązanego **DataTable**. Na przykład po ustanowieniu **DataRelation** między spisu klientów i tabela zamówienia, możesz pobrać wszystkie wiersze kolejności dla wiersza określonego klienta przy użyciu **GetChildRows**.  
  
 Poniższy przykład kodu tworzy **DataRelation** między **klientów** tabeli i **zamówień** spis **DataSet** i zwraca wszystkie zamówienia dla każdego klienta.  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 Kolejnym przykładzie opiera się na poprzednim przykładzie związanych ze sobą czterech tabel i nawigowanie po relacjach tych. Tak jak w poprzednim przykładzie **CustomerID** odnosi się **klientów** do tabeli **zamówień** tabeli. Dla każdego klienta w **klientów** tabeli wierszy podrzędnych w **zamówień** tabeli są określone, aby można było zwrócenie liczby zamówień ma konkretnego klienta i ich **OrderID** wartości.  
  
 Przykład rozwinięte również zwraca wartości z **SzczegółyZamówienia** i **produktów** tabel. **Zamówień** tabela jest powiązana z **SzczegółyZamówienia** tabeli, używając **OrderID** ustalenie, dla każdego klienta kolejności, jakie produktów i ilości zostały uporządkowane. Ponieważ **SzczegółyZamówienia** tabela zawiera tylko **ProductID** uporządkowanej produktu **SzczegółyZamówienia** jest powiązany z **produktów** przy użyciu **ProductID** celu powrotu **ProductName**. W tej relacji **produktów** tabeli jest nadrzędny i **szczegółów zamówienia** tabeli jest elementem podrzędnym. W wyniku iteracja **SzczegółyZamówienia** tabeli **element GetParentRow** jest wywoływana w celu pobrania pokrewny **ProductName** wartość.  
  
 Zwróć uwagę, że w przypadku **DataRelation** jest tworzona dla **klientów** i **zamówień** tabel, nie określono wartości dla **createConstraints**flagi (wartość domyślna to **true**). Przy założeniu, że wszystkie wiersze w **zamówień** tabela ma **CustomerID** wartość, która istnieje w obiekcie nadrzędnym **klientów** tabeli. Jeśli **CustomerID** istnieje w **zamówień** tabeli, która nie istnieje w **klientów** tabeli <xref:System.Data.ForeignKeyConstraint> powoduje zgłoszenie wyjątku zostanie wygenerowany.  
  
 Jeśli kolumna podrzędnych może zawierać wartości, które nie zawiera kolumny nadrzędnej, należy skonfigurować **createConstraints** flaga **false** podczas dodawania **DataRelation**. W tym przykładzie **createConstraints** flaga jest ustawiona na **false** dla **DataRelation** między **zamówień** tabeli i  **SzczegółyZamówień** tabeli. Umożliwia to aplikacji zwrócić wszystkie rekordy z **SzczegółyZamówienia** tabeli i tylko podzestaw rekordów z **zamówień** tabeli bez generowania wyjątku czasu wykonywania. Przykładowe rozwinięte generuje dane wyjściowe w następującym formacie.  
  
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
  
 Poniższy przykładowy kod jest przykładem rozszerzonej gdzie wartości z **SzczegółyZamówienia** i **produktów** tabele są zwracane z tylko podzestaw rekordów **zamówień**tabeli są zwracane.  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
