---
title: Tworzenie zestawu danych
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
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8ae997822d71a0a0a4276b8b32b963149a8ed67a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-dataset"></a><span data-ttu-id="c68ba-102">Tworzenie zestawu danych</span><span class="sxs-lookup"><span data-stu-id="c68ba-102">Creating a DataSet</span></span>
<span data-ttu-id="c68ba-103">Utwórz wystąpienie <xref:System.Data.DataSet> przez wywołanie metody <xref:System.Data.DataSet> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c68ba-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="c68ba-104">Opcjonalnie można określić argument nazwy.</span><span class="sxs-lookup"><span data-stu-id="c68ba-104">Optionally specify a name argument.</span></span> <span data-ttu-id="c68ba-105">Jeśli nie określisz nazwy <xref:System.Data.DataSet>, nazwa jest równa "NewDataSet".</span><span class="sxs-lookup"><span data-stu-id="c68ba-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="c68ba-106">Można również utworzyć nowy <xref:System.Data.DataSet> oparte na istniejącym <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c68ba-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c68ba-107">Nowy <xref:System.Data.DataSet> może być dokładną kopię istniejącej <xref:System.Data.DataSet>; klonu <xref:System.Data.DataSet> który kopiuje relacyjne struktury lub schematu, ale który nie zawiera żadnych danych z istniejącego <xref:System.Data.DataSet>; lub podzbiór <xref:System.Data.DataSet>, zawierający tylko zmodyfikowanych wierszy z istniejącego <xref:System.Data.DataSet> przy użyciu <xref:System.Data.DataSet.GetChanges%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c68ba-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="c68ba-108">Aby uzyskać więcej informacji, zobacz [kopiowanie zawartości zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="c68ba-108">For more information, see [Copying DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="c68ba-109">Poniższy przykład kodu pokazuje sposób tworzenia wystąpienia <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="c68ba-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="c68ba-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c68ba-110">See Also</span></span>  
 [<span data-ttu-id="c68ba-111">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="c68ba-111">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="c68ba-112">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="c68ba-112">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="c68ba-113">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="c68ba-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
