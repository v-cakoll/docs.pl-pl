---
title: Tworzenie elementu DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 9d21b17068ff3ce5b0bd3990144383d7f9ded2f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151341"
---
# <a name="creating-a-dataview"></a>Tworzenie elementu DataView
Istnieją dwa sposoby <xref:System.Data.DataView>tworzenia pliku . Można użyć konstruktora **DataView** lub można utworzyć <xref:System.Data.DataTable.DefaultView%2A> odwołanie <xref:System.Data.DataTable>do właściwości . **Konstruktor DataView** może być pusty lub może przyjmować **datatable** jako pojedynczy argument lub **DataTable** wraz z kryteriami filtrowania, kryteria sortowania i filtr stanu wiersza. Aby uzyskać więcej informacji na temat dodatkowych argumentów dostępnych do użycia w **widoku DataView,** zobacz [Sortowanie i filtrowanie danych](sorting-and-filtering-data.md).  
  
 Ponieważ indeks **dla DataView** jest zbudowany zarówno podczas tworzenia **DataView,** jak i po zmodyfikowaniu dowolnych właściwości **Sort,** **RowFilter**lub **RowStateFilter,** uzyskujesz najlepszą wydajność, podając dowolną początkową kolejność sortowania lub kryteria filtrowania jako argumenty konstruktora podczas tworzenia **pliku DataView**. Tworzenie **DataView** bez określania kryteriów sortowania lub filtrowania, a następnie ustawienie **Sort ,** **RowFilter**lub **RowStateFilter** właściwości później powoduje, że indeks ma być zbudowany co najmniej dwa razy: raz podczas tworzenia **DataView** i ponownie, gdy którykolwiek z sortowania lub właściwości filtru są modyfikowane.  
  
 Należy zauważyć, że jeśli utworzysz **DataView** przy użyciu konstruktora, który nie przyjmuje żadnych argumentów, nie będzie można użyć **DataView,** dopóki nie zostanie **ustawiona Table** właściwości.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć **DataView** przy użyciu Konstruktora **DataView.** A **RowFilter**, **Sort kolumna** i **DataViewRowState** są dostarczane wraz z **DataTable**.  
  
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
  
 Poniższy przykład kodu pokazuje, jak uzyskać odwołanie do domyślnego **DataView** **datatable** przy użyciu **DefaultView** właściwości tabeli.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [Elementy DataView](dataviews.md)
- [Sortowanie i filtrowanie danych](sorting-and-filtering-data.md)
- [Elementy DataTable](datatables.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
