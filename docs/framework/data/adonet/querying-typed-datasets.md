---
title: Podczas badania zestawów
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: d956fd5f07c108146d20623bcf811266380c132c
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44270645"
---
# <a name="query-typed-datasets"></a>Zapytanie wpisanych zestawów danych

Jeśli schemat <xref:System.Data.DataSet> jest znany w czasie projektowania aplikacji, zalecamy użycie wpisane <xref:System.Data.DataSet> podczas korzystania z LINQ to DataSet. Wpisane <xref:System.Data.DataSet> jest klasa, która pochodzi od klasy <xref:System.Data.DataSet>. W efekcie dziedziczy wszystkie metody, zdarzenia i właściwości <xref:System.Data.DataSet>. Ponadto wpisane <xref:System.Data.DataSet> udostępnia silnie typizowane metody, zdarzenia i właściwości. Oznacza to, że masz dostęp tabele i kolumny, według nazwy, zamiast korzystać z metody oparte na kolekcji. To sprawia, że zapytania prostszy i bardziej czytelny. Aby uzyskać więcej informacji, zobacz [wpisanych zestawów danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).

LINQ do zestawu danych obsługuje również zapytań wpisane <xref:System.Data.DataSet>. Z kontrolą typów <xref:System.Data.DataSet>, będą musieli używać ogólnych <xref:System.Data.DataRowExtensions.Field%2A> metody lub <xref:System.Data.DataRowExtensions.SetField%2A> metody dostępu do kolumny danych. Nazwy właściwości są dostępne w czasie kompilacji, ponieważ informacje o typie jest uwzględniony w <xref:System.Data.DataSet>. LINQ do zestawu danych zapewnia dostęp do wartości w kolumnie jako odpowiedniego typu, tak aby błędy niezgodności wpisywania są wyłapywane, gdy kod jest kompilowany zamiast w czasie wykonywania.

Przed rozpoczęciem wykonywania zapytań wpisane <xref:System.Data.DataSet>, należy wygenerować klasę za pomocą **Projektanta obiektów DataSet** w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono zapytanie, za pośrednictwem wpisane <xref:System.Data.DataSet>:

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytania do zestawów danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Zapytania wielotabelowe](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [Zapytania jednotabelowe](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
