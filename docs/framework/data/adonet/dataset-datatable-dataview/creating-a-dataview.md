---
title: Tworzenie elementu DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: b88df66ef2e065d1db8d4033eb1fb0e47ebdd189
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44181407"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="841b2-102">Tworzenie elementu DataView</span><span class="sxs-lookup"><span data-stu-id="841b2-102">Creating a DataView</span></span>
<span data-ttu-id="841b2-103">Istnieją dwa sposoby tworzenia <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="841b2-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="841b2-104">Możesz użyć **DataView** konstruktora, lub można utworzyć odwołania do <xref:System.Data.DataTable.DefaultView%2A> właściwość <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="841b2-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="841b2-105">**DataView** Konstruktor może być pusta lub może potrwać, albo **DataTable** jako pojedynczy argument lub **DataTable** wraz z kryteriów filtrowania, sortowania kryteria i wiersz Filtr stanu.</span><span class="sxs-lookup"><span data-stu-id="841b2-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="841b2-106">Aby uzyskać więcej informacji o dodatkowe argumenty do użycia z usługą **DataView**, zobacz [sortowanie i filtrowanie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="841b2-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="841b2-107">Ponieważ indeks **DataView** powstała zarówno gdy **DataView** zostanie utworzony i gdy którykolwiek z **sortowania**, **RowFilter**, lub  **Element RowStateFilter** właściwości są modyfikowane, osiągnąć najlepszą wydajność przez dostarczanie w dowolnej kolejności sortowania początkowej lub kryteria filtrowania jako argumenty konstruktora, po utworzeniu **DataView**.</span><span class="sxs-lookup"><span data-stu-id="841b2-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="841b2-108">Tworzenie **DataView** bez określania kryteriów sortowania lub filtrowania, a następnie ustawiając **sortowania**, **RowFilter**, lub **Element RowStateFilter** właściwości powoduje później indeks ma zostać utworzony co najmniej dwa razy: po podczas **DataView** zostanie utworzony, i ponownie podczas sortowania lub filtrowania właściwości są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="841b2-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="841b2-109">Należy pamiętać, że jeśli utworzysz **DataView** przy użyciu konstruktora, który nie przyjmuje żadnych argumentów, nie będzie mógł używać **DataView** zdefiniowania **tabeli** właściwości .</span><span class="sxs-lookup"><span data-stu-id="841b2-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="841b2-110">Poniższy przykład kodu demonstruje sposób tworzenia **DataView** przy użyciu **DataView** konstruktora.</span><span class="sxs-lookup"><span data-stu-id="841b2-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="841b2-111">A **RowFilter**, **sortowania** kolumny, a **DataViewRowState** są dostarczane wraz z **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="841b2-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="841b2-112">Poniższy przykład kodu pokazuje, jak uzyskać odwołania do domyślnego **DataView** z **DataTable** przy użyciu **DefaultView** właściwości tabeli.</span><span class="sxs-lookup"><span data-stu-id="841b2-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="841b2-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="841b2-113">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="841b2-114">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="841b2-114">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="841b2-115">Sortowanie i filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="841b2-115">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [<span data-ttu-id="841b2-116">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="841b2-116">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="841b2-117">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="841b2-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
