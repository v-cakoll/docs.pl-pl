---
title: Dodawanie DataRelations
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
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4650ccc5324489fb5c577cf2542ae95e1904441a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="adding-datarelations"></a>Dodawanie DataRelations
W <xref:System.Data.DataSet> w wielu <xref:System.Data.DataTable> obiekty, można użyć <xref:System.Data.DataRelation> obiektów do powiązania z jednej tabeli do innego, przejdź do tabel i zwracanie wszystkich wierszy podrzędnej lub nadrzędnej z powiązanej tabeli.  
  
 Argumenty wymagane do utworzenia **DataRelation** są nazwę **DataRelation** tworzona i tablicę co najmniej jeden <xref:System.Data.DataColumn> odwołania do kolumn, które służą jako nadrzędne i podrzędne kolumny w relacji. Po utworzeniu **DataRelation**, go do przechodzenia między tabelami i służy do pobierania wartości.  
  
 Dodawanie **DataRelation** do <xref:System.Data.DataSet> dodaje domyślnie <xref:System.Data.UniqueConstraint> tabelą nadrzędną i <xref:System.Data.ForeignKeyConstraint> do tabeli podrzędnej. Aby uzyskać więcej informacji o tych ograniczeniach domyślnych, zobacz [ograniczenia DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Poniższy przykład kodu tworzy **DataRelation** za pomocą dwóch <xref:System.Data.DataTable> obiekty w <xref:System.Data.DataSet>. Każdy <xref:System.Data.DataTable> zawiera kolumny o nazwie **IDKlienta**, która służy jako łącza między dwoma <xref:System.Data.DataTable> obiektów. W przykładzie dodano pojedynczy **DataRelation** do **relacji** kolekcji <xref:System.Data.DataSet>. Pierwszy argument w przykładzie nazwa **DataRelation** tworzona. Drugi argument ustawia element nadrzędny **DataColumn** i trzeci argument zestawów dziecka **DataColumn**.  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 A **DataRelation** ma również **zagnieżdżone** właściwości, gdy wartość **true**, powoduje, że wiersze z tabeli podrzędnej, aby być zagnieżdżone w obrębie skojarzone wiersza z tabeli nadrzędnej gdy zapisywane jako elementów XML za pomocą <xref:System.Data.DataSet.WriteXml%2A> . Aby uzyskać więcej informacji, zobacz [za pomocą XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
