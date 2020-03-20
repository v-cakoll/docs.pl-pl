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
# <a name="creating-a-dataview"></a><span data-ttu-id="baaee-102">Tworzenie elementu DataView</span><span class="sxs-lookup"><span data-stu-id="baaee-102">Creating a DataView</span></span>
<span data-ttu-id="baaee-103">Istnieją dwa sposoby <xref:System.Data.DataView>tworzenia pliku .</span><span class="sxs-lookup"><span data-stu-id="baaee-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="baaee-104">Można użyć konstruktora **DataView** lub można utworzyć <xref:System.Data.DataTable.DefaultView%2A> odwołanie <xref:System.Data.DataTable>do właściwości .</span><span class="sxs-lookup"><span data-stu-id="baaee-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="baaee-105">**Konstruktor DataView** może być pusty lub może przyjmować **datatable** jako pojedynczy argument lub **DataTable** wraz z kryteriami filtrowania, kryteria sortowania i filtr stanu wiersza.</span><span class="sxs-lookup"><span data-stu-id="baaee-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="baaee-106">Aby uzyskać więcej informacji na temat dodatkowych argumentów dostępnych do użycia w **widoku DataView,** zobacz [Sortowanie i filtrowanie danych](sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="baaee-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="baaee-107">Ponieważ indeks **dla DataView** jest zbudowany zarówno podczas tworzenia **DataView,** jak i po zmodyfikowaniu dowolnych właściwości **Sort,** **RowFilter**lub **RowStateFilter,** uzyskujesz najlepszą wydajność, podając dowolną początkową kolejność sortowania lub kryteria filtrowania jako argumenty konstruktora podczas tworzenia **pliku DataView**.</span><span class="sxs-lookup"><span data-stu-id="baaee-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="baaee-108">Tworzenie **DataView** bez określania kryteriów sortowania lub filtrowania, a następnie ustawienie **Sort ,** **RowFilter**lub **RowStateFilter** właściwości później powoduje, że indeks ma być zbudowany co najmniej dwa razy: raz podczas tworzenia **DataView** i ponownie, gdy którykolwiek z sortowania lub właściwości filtru są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="baaee-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="baaee-109">Należy zauważyć, że jeśli utworzysz **DataView** przy użyciu konstruktora, który nie przyjmuje żadnych argumentów, nie będzie można użyć **DataView,** dopóki nie zostanie **ustawiona Table** właściwości.</span><span class="sxs-lookup"><span data-stu-id="baaee-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="baaee-110">Poniższy przykład kodu pokazuje, jak utworzyć **DataView** przy użyciu Konstruktora **DataView.**</span><span class="sxs-lookup"><span data-stu-id="baaee-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="baaee-111">A **RowFilter**, **Sort kolumna** i **DataViewRowState** są dostarczane wraz z **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="baaee-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="baaee-112">Poniższy przykład kodu pokazuje, jak uzyskać odwołanie do domyślnego **DataView** **datatable** przy użyciu **DefaultView** właściwości tabeli.</span><span class="sxs-lookup"><span data-stu-id="baaee-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="baaee-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="baaee-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="baaee-114">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="baaee-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="baaee-115">Sortowanie i filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="baaee-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="baaee-116">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="baaee-116">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="baaee-117">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="baaee-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
