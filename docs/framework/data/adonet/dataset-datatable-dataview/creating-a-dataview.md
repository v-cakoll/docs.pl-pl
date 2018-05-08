---
title: Tworzenie widoku danych.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: d118f97e425782dbdf89c7e5d1eccd4d371b419c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-dataview"></a>Tworzenie widoku danych.
Istnieją dwa sposoby tworzenia <xref:System.Data.DataView>. Można użyć **DataView** konstruktora, lub można utworzyć odwołania do <xref:System.Data.DataTable.DefaultView%2A> właściwość <xref:System.Data.DataTable>. **DataView** Konstruktor może być pusta lub może potrwać albo **DataTable** jako jeden argument lub **DataTable** wraz z kryteria filtrowania, sortowania kryteria i wiersza Stan filtru. Aby uzyskać więcej informacji o dodatkowe argumenty do użycia z **DataView**, zobacz [sortowanie i filtrowanie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Ponieważ indeks **DataView** składa się zarówno w przypadku **DataView** jest tworzony i przy **sortowania**, **RowFilter**, lub  **Element RowStateFilter** właściwości są modyfikowane, uzyskać najlepszą wydajność przez dostarczanie dowolnej kolejności sortowania początkowej lub kryteria filtrowania jako argumenty konstruktora, podczas tworzenia **DataView**. Tworzenie **DataView** bez określania kryteriów sortowania lub filtr, a następnie ustawić **sortowania**, **RowFilter**, lub **Element RowStateFilter** właściwości później powoduje indeksu, który ma zostać utworzony co najmniej dwa razy: po podczas **DataView** jest tworzony, i ponownie gdy dowolne z właściwości sortowania i filtrowania są modyfikowane.  
  
 Należy pamiętać, że w przypadku utworzenia **DataView** przy użyciu konstruktora, który nie przyjmuje żadnych argumentów, nie będzie mógł używać **DataView** zdefiniowania **tabeli** właściwości .  
  
 Poniższy przykładowy kod przedstawia sposób tworzenia **DataView** przy użyciu **DataView** konstruktora. A **RowFilter**, **sortowania** kolumny, a **DataViewRowState** są dostarczane wraz z programem **DataTable**.  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 W poniższym przykładzie pokazano, jak uzyskać odwołania do domyślnej **DataView** z **DataTable** przy użyciu **DefaultView** właściwość tabeli.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [Elementy DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [Sortowanie i filtrowanie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
