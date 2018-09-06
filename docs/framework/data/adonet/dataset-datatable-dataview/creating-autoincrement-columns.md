---
title: Tworzenie kolumn typu AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 9c6b5393e1928828bca001ba1d2336f09e64c22c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776963"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="9ce13-102">Tworzenie kolumn typu AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="9ce13-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="9ce13-103">Aby zapewnić unikatową kolumnę wartości, można ustawić wartości kolumn, aby zwiększyć automatycznie po dodaniu nowych wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="9ce13-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="9ce13-104">Do utworzenia, zwiększając automatycznie <xref:System.Data.DataColumn>ustaw <xref:System.Data.DataColumn.AutoIncrement%2A> właściwości kolumny, która ma **true**.</span><span class="sxs-lookup"><span data-stu-id="9ce13-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="9ce13-105"><xref:System.Data.DataColumn> Następnie rozpoczyna się od wartości zdefiniowanej w <xref:System.Data.DataColumn.AutoIncrementSeed%2A> właściwości i z każdego wiersza dodano wartość **AutoIncrement** zwiększa wartość zdefiniowana w kolumnie <xref:System.Data.DataColumn.AutoIncrementStep%2A> właściwości kolumny.</span><span class="sxs-lookup"><span data-stu-id="9ce13-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="9ce13-106">Dla **AutoIncrement** kolumn, zaleca się <xref:System.Data.DataColumn.ReadOnly%2A> właściwość **DataColumn** można ustawić **true**.</span><span class="sxs-lookup"><span data-stu-id="9ce13-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="9ce13-107">Poniższy przykład przedstawia sposób tworzenia kolumny, która rozpoczyna się o wartości 200 i dodaje stopniowo w krokach 3.</span><span class="sxs-lookup"><span data-stu-id="9ce13-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ce13-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ce13-108">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 [<span data-ttu-id="9ce13-109">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="9ce13-109">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="9ce13-110">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="9ce13-110">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="9ce13-111">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="9ce13-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
