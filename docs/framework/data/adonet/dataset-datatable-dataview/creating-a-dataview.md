---
title: Tworzenie elementu DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: b88df66ef2e065d1db8d4033eb1fb0e47ebdd189
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108718"
---
# <a name="creating-a-dataview"></a>Tworzenie elementu DataView
Istnieją dwa sposoby tworzenia <xref:System.Data.DataView>. Możesz użyć **DataView** konstruktora, lub można utworzyć odwołania do <xref:System.Data.DataTable.DefaultView%2A> właściwość <xref:System.Data.DataTable>. **DataView** Konstruktor może być pusta lub może potrwać, albo **DataTable** jako pojedynczy argument lub **DataTable** wraz z kryteriów filtrowania, sortowania kryteria i wiersz Filtr stanu. Aby uzyskać więcej informacji o dodatkowe argumenty do użycia z usługą **DataView**, zobacz [sortowanie i filtrowanie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
 Ponieważ indeks **DataView** powstała zarówno gdy **DataView** zostanie utworzony i gdy którykolwiek z **sortowania**, **RowFilter**, lub  **Element RowStateFilter** właściwości są modyfikowane, osiągnąć najlepszą wydajność przez dostarczanie w dowolnej kolejności sortowania początkowej lub kryteria filtrowania jako argumenty konstruktora, po utworzeniu **DataView**. Tworzenie **DataView** bez określania kryteriów sortowania lub filtrowania, a następnie ustawiając **sortowania**, **RowFilter**, lub **Element RowStateFilter** właściwości powoduje później indeks ma zostać utworzony co najmniej dwa razy: po podczas **DataView** zostanie utworzony, i ponownie podczas sortowania lub filtrowania właściwości są modyfikowane.  
  
 Należy pamiętać, że jeśli utworzysz **DataView** przy użyciu konstruktora, który nie przyjmuje żadnych argumentów, nie będzie mógł używać **DataView** zdefiniowania **tabeli** właściwości .  
  
 Poniższy przykład kodu demonstruje sposób tworzenia **DataView** przy użyciu **DataView** konstruktora. A **RowFilter**, **sortowania** kolumny, a **DataViewRowState** są dostarczane wraz z **DataTable**.  
  
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
  
 Poniższy przykład kodu pokazuje, jak uzyskać odwołania do domyślnego **DataView** z **DataTable** przy użyciu **DefaultView** właściwości tabeli.  
  
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
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
