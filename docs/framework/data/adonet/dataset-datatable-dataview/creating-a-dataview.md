---
title: Tworzenie widoku danych.
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
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1a8529c317025dbabd9c7467557b244b2f452a77
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="creating-a-dataview"></a><span data-ttu-id="a5965-102">Tworzenie widoku danych.</span><span class="sxs-lookup"><span data-stu-id="a5965-102">Creating a DataView</span></span>
<span data-ttu-id="a5965-103">Istnieją dwa sposoby tworzenia <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="a5965-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="a5965-104">Można użyć **DataView** konstruktora, lub można utworzyć odwołania do <xref:System.Data.DataTable.DefaultView%2A> właściwość <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="a5965-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="a5965-105">**DataView** Konstruktor może być pusta lub może potrwać albo **DataTable** jako jeden argument lub **DataTable** wraz z kryteria filtrowania, sortowania kryteria i wiersza Stan filtru.</span><span class="sxs-lookup"><span data-stu-id="a5965-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="a5965-106">Aby uzyskać więcej informacji o dodatkowe argumenty do użycia z **DataView**, zobacz [sortowanie i filtrowanie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="a5965-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="a5965-107">Ponieważ indeks **DataView** składa się zarówno w przypadku **DataView** jest tworzony i przy **sortowania**, **RowFilter**, lub  **Element RowStateFilter** właściwości są modyfikowane, uzyskać najlepszą wydajność przez dostarczanie dowolnej kolejności sortowania początkowej lub kryteria filtrowania jako argumenty konstruktora, podczas tworzenia **DataView**.</span><span class="sxs-lookup"><span data-stu-id="a5965-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="a5965-108">Tworzenie **DataView** bez określania kryteriów sortowania lub filtr, a następnie ustawić **sortowania**, **RowFilter**, lub **Element RowStateFilter** właściwości później powoduje indeksu, który ma zostać utworzony co najmniej dwa razy: po podczas **DataView** jest tworzony, i ponownie gdy dowolne z właściwości sortowania i filtrowania są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="a5965-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="a5965-109">Należy pamiętać, że w przypadku utworzenia **DataView** przy użyciu konstruktora, który nie przyjmuje żadnych argumentów, nie będzie mógł używać **DataView** zdefiniowania **tabeli** właściwości .</span><span class="sxs-lookup"><span data-stu-id="a5965-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="a5965-110">Poniższy przykładowy kod przedstawia sposób tworzenia **DataView** przy użyciu **DataView** konstruktora.</span><span class="sxs-lookup"><span data-stu-id="a5965-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="a5965-111">A **RowFilter**, **sortowania** kolumny, a **DataViewRowState** są dostarczane wraz z programem **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="a5965-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="a5965-112">W poniższym przykładzie pokazano, jak uzyskać odwołania do domyślnej **DataView** z **DataTable** przy użyciu **DefaultView** właściwość tabeli.</span><span class="sxs-lookup"><span data-stu-id="a5965-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5965-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5965-113">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="a5965-114">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="a5965-114">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="a5965-115">Sortowanie i filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="a5965-115">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [<span data-ttu-id="a5965-116">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="a5965-116">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="a5965-117">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="a5965-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
