---
title: Wykonywanie zapytania do typizowanych zestawów danych
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 55714c4dae73cd17a849cc35681797dfa4266e3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782965"
---
# <a name="query-typed-datasets"></a>Zestawy danych z określonym typem zapytania

Jeśli schemat <xref:System.Data.DataSet> programu jest znany w czasie projektowania aplikacji, zalecamy użycie <xref:System.Data.DataSet> typu podczas korzystania z LINQ to DataSet. Typ <xref:System.Data.DataSet> to Klasa, która pochodzi <xref:System.Data.DataSet>od klasy. W związku z tym dziedziczy wszystkie metody, zdarzenia i właściwości <xref:System.Data.DataSet>. Ponadto typ <xref:System.Data.DataSet> udostępnia metody o jednoznacznie określonym typie, zdarzenia i właściwości. Oznacza to, że można uzyskać dostęp do tabel i kolumn według nazwy, zamiast korzystać z metod opartych na kolekcji. Sprawia to, że zapytania są prostsze i bardziej czytelne. Aby uzyskać więcej informacji, zobacz [typy zestawów danych](./dataset-datatable-dataview/typed-datasets.md).

LINQ to DataSet obsługuje również zapytania w określonym typie <xref:System.Data.DataSet>. Z określonym typem <xref:System.Data.DataSet>nie trzeba używać metody ogólnej <xref:System.Data.DataRowExtensions.Field%2A> ani <xref:System.Data.DataRowExtensions.SetField%2A> metody dostępu do danych kolumn. Nazwy właściwości są dostępne w czasie kompilacji, ponieważ informacje o typie są zawarte w <xref:System.Data.DataSet>. LINQ to DataSet zapewnia dostęp do wartości kolumn jako poprawny typ, dzięki czemu błędy niezgodności typów są przechwytywane podczas kompilowania kodu, a nie w czasie wykonywania.

Przed rozpoczęciem wykonywania zapytania o określony typ <xref:System.Data.DataSet>należy wygenerować klasę przy użyciu **projektanta obiektów DataSet** w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Tworzenie i konfigurowanie zestawów danych](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano zapytanie w określonym typie <xref:System.Data.DataSet>:

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

- [Wykonywanie zapytania do zestawów danych](querying-datasets-linq-to-dataset.md)
- [Zapytania wielotabelowe](cross-table-queries-linq-to-dataset.md)
- [Zapytania jednotabelowe](single-table-queries-linq-to-dataset.md)
