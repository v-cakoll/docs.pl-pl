---
title: Tworzenie elementu DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 391c071f19149e9690c9121b1094aef5bfa605cd
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203843"
---
# <a name="creating-a-dataview"></a>Tworzenie elementu DataView
Istnieją dwa sposoby tworzenia <xref:System.Data.DataView>. Można użyć konstruktora **DataView** lub można utworzyć odwołanie do <xref:System.Data.DataTable.DefaultView%2A> właściwości. <xref:System.Data.DataTable> Konstruktor **DataView** może być pusty lub może przyjmować element **DataTable** jako pojedynczy argument lub element **DataTable** wraz z kryteriami filtrowania, kryteriami sortowania i filtrem stanu wiersza. Aby uzyskać więcej informacji na temat dodatkowych argumentów dostępnych do użycia z **widokiem DataView**, zobacz [Sortowanie i filtrowanie danych](sorting-and-filtering-data.md).  
  
 Ponieważ indeks dla elementu **DataView** jest kompilowany zarówno podczas tworzenia elementu **DataView** , jak i w przypadku zmodyfikowania właściwości **sort**, **RowFilter**lub **RowStateFilter** , można uzyskać najlepszą wydajność, dostarczając dowolny początkowy porządek sortowania lub kryteria filtrowania jako argumenty konstruktora podczas tworzenia **widoku**danych. Tworzenie elementu **DataView** bez określania kryteriów sortowania lub filtrowania, a następnie Ustawianie właściwości **sort**, **RowFilter**lub **RowStateFilter** później powoduje, że indeks zostanie skompilowany co najmniej dwa razy: raz, gdy **Widok** danych jest utworzone i ponownie, gdy właściwości sortowania lub filtrowania są modyfikowane.  
  
 Należy pamiętać, że jeśli utworzysz **Widok DataView** przy użyciu konstruktora, który nie przyjmuje żadnych argumentów, nie będzie można użyć **widoku** danych, dopóki właściwość **Table** nie zostanie ustawiona.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć **Widok DataView** przy użyciu konstruktora **DataView** . **RowFilter**, **sort** Column i **DataViewRowState** są dostarczane wraz z **DataTable**.  
  
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
  
 Poniższy przykład kodu demonstruje, jak uzyskać odwołanie do domyślnego elementu **DataView** obiektu **DataTable** przy użyciu właściwości **DefaultView** tabeli.  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [Elementy DataView](dataviews.md)
- [Sortowanie i filtrowanie danych](sorting-and-filtering-data.md)
- [Elementy DataTable](datatables.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
