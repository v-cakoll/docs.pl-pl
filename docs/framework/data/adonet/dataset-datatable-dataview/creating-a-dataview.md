---
title: Tworzenie elementu DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 3e1c31dac458594eee70ddd99469aca7cf63b848
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785475"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="c12f6-102">Tworzenie elementu DataView</span><span class="sxs-lookup"><span data-stu-id="c12f6-102">Creating a DataView</span></span>
<span data-ttu-id="c12f6-103">Istnieją dwa sposoby tworzenia <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="c12f6-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="c12f6-104">Można użyć konstruktora **DataView** lub można utworzyć odwołanie do <xref:System.Data.DataTable.DefaultView%2A> właściwości. <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="c12f6-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="c12f6-105">Konstruktor **DataView** może być pusty lub może przyjmować element **DataTable** jako pojedynczy argument lub element **DataTable** wraz z kryteriami filtrowania, kryteriami sortowania i filtrem stanu wiersza.</span><span class="sxs-lookup"><span data-stu-id="c12f6-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="c12f6-106">Aby uzyskać więcej informacji na temat dodatkowych argumentów dostępnych do użycia z **widokiem DataView**, zobacz [Sortowanie i filtrowanie danych](sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="c12f6-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="c12f6-107">Ponieważ indeks dla elementu **DataView** jest kompilowany zarówno podczas tworzenia elementu **DataView** , jak i w przypadku zmodyfikowania właściwości **sort**, **RowFilter**lub **RowStateFilter** , można uzyskać najlepszą wydajność, dostarczając dowolny początkowy porządek sortowania lub kryteria filtrowania jako argumenty konstruktora podczas tworzenia **widoku**danych.</span><span class="sxs-lookup"><span data-stu-id="c12f6-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="c12f6-108">Tworzenie elementu **DataView** bez określania kryteriów sortowania lub filtrowania, a następnie Ustawianie właściwości **sort**, **RowFilter**lub **RowStateFilter** później powoduje, że indeks zostanie skompilowany co najmniej dwa razy: raz, gdy **Widok** danych jest utworzone i ponownie, gdy właściwości sortowania lub filtrowania są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="c12f6-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="c12f6-109">Należy pamiętać, że jeśli utworzysz **Widok DataView** przy użyciu konstruktora, który nie przyjmuje żadnych argumentów, nie będzie można użyć **widoku** danych, dopóki właściwość **Table** nie zostanie ustawiona.</span><span class="sxs-lookup"><span data-stu-id="c12f6-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="c12f6-110">Poniższy przykład kodu pokazuje, jak utworzyć **Widok DataView** przy użyciu konstruktora **DataView** .</span><span class="sxs-lookup"><span data-stu-id="c12f6-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="c12f6-111">**RowFilter**, **sort** Column i **DataViewRowState** są dostarczane wraz z **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="c12f6-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="c12f6-112">Poniższy przykład kodu demonstruje, jak uzyskać odwołanie do domyślnego elementu **DataView** obiektu **DataTable** przy użyciu właściwości **DefaultView** tabeli.</span><span class="sxs-lookup"><span data-stu-id="c12f6-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="c12f6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c12f6-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="c12f6-114">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="c12f6-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="c12f6-115">Sortowanie i filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="c12f6-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="c12f6-116">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="c12f6-116">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="c12f6-117">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c12f6-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
