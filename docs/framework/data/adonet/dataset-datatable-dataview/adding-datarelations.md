---
title: Dodawanie elementów DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: d0f481979ead7af775d462a2624ec43080e2c5a9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749960"
---
# <a name="adding-datarelations"></a>Dodawanie elementów DataRelation
W <xref:System.Data.DataSet> z wieloma <xref:System.Data.DataTable> obiektów, można użyć <xref:System.Data.DataRelation> obiektów do powiązania z jednej tabeli do innej, aby poruszać się po w tabelach i zwracanie podrzędnej lub nadrzędnej wierszy z tabeli powiązanej.  
  
 Argumenty wymagane do utworzenia **DataRelation** są nazwę **DataRelation** tworzona i tablicę co najmniej jeden <xref:System.Data.DataColumn> odwołania do kolumn, które służą jako nadrzędne i podrzędne kolumny w relacji. Po utworzeniu **DataRelation**, można użyć go do nawigacji między tabelami i pobierać wartości.  
  
 Dodawanie **DataRelation** do <xref:System.Data.DataSet> dodaje domyślnie <xref:System.Data.UniqueConstraint> tabeli nadrzędnej i <xref:System.Data.ForeignKeyConstraint> do tabeli podrzędnej. Aby uzyskać więcej informacji o tych ograniczeniach domyślnych, zobacz [ograniczenia elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Poniższy przykład kodu tworzy **DataRelation** za pomocą dwóch <xref:System.Data.DataTable> obiekty w <xref:System.Data.DataSet>. Każdy <xref:System.Data.DataTable> zawiera kolumnę o nazwie **CustID**, który służy jako łącza między tymi dwoma <xref:System.Data.DataTable> obiektów. W przykładzie dodano pojedynczej **DataRelation** do **relacji** zbiór <xref:System.Data.DataSet>. Pierwszy argument w przykładzie określa nazwę **DataRelation** tworzona. Drugi argument określa element nadrzędny **DataColumn** i trzeci argument ustawia element podrzędny **DataColumn**.  
  
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
  
 A **DataRelation** ma również **zagnieżdżone** właściwość, która po ustawieniu **true**, powoduje, że wiersze z tabeli podrzędnej na być zagnieżdżony w skojarzonych wiersz z tabeli nadrzędnej Podczas zapisywania jako elementów XML przy użyciu <xref:System.Data.DataSet.WriteXml%2A> . Aby uzyskać więcej informacji, zobacz [za pomocą XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataSet, DataTable i DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
