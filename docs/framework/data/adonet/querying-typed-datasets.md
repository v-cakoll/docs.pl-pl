---
title: Wykonywanie zapytania Typizowane zbiory danych
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
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c232ca2888c957bea33d06c84a62b00fdc7fd80c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="querying-typed-datasets"></a>Wykonywanie zapytania Typizowane zbiory danych
Jeśli schemat <xref:System.Data.DataSet> jest znany w czasie projektowania aplikacji, zalecane jest użycie typu <xref:System.Data.DataSet> przy użyciu [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Typizowany <xref:System.Data.DataSet> jest klasą pochodną <xref:System.Data.DataSet>. W efekcie dziedziczy wszystkie metody, zdarzeń i właściwości <xref:System.Data.DataSet>. Ponadto maszynowy <xref:System.Data.DataSet> udostępnia silnie typizowane metody, zdarzeń i właściwości. Oznacza to, że masz dostęp tabele i kolumny według nazwy, zamiast za pomocą metody opartej na kolekcji. Dzięki temu zapytania prostszy i bardziej czytelne. Aby uzyskać więcej informacji, zobacz [wpisanych zestawów danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]obsługuje również obsługę zapytań typu <xref:System.Data.DataSet>. Z typu <xref:System.Data.DataSet>, nie trzeba używać ogólnych <xref:System.Data.DataRowExtensions.Field%2A> metody lub <xref:System.Data.DataRowExtensions.SetField%2A> metodę dostępu do danych kolumny.  Nazwy właściwości są dostępne w czasie kompilacji, ponieważ zawiera informacje o typie <xref:System.Data.DataSet>. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]zapewnia dostęp do wartości w kolumnie jako poprawny typ, dzięki czemu błędy niezgodności typów są przechwytywane podczas kompilowania kodu zamiast w czasie wykonywania.  
  
 Przed rozpoczęciem wykonywania zapytania typu <xref:System.Data.DataSet>, należy wygenerować za pomocą Projektanta obiektów DataSet w klasie [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono zapytania za pośrednictwem typu <xref:System.Data.DataSet>:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie zapytania do zestawów danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Zapytania wielotabelowe](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [Zapytania jednotabelowe](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
