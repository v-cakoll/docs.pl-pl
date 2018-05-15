---
title: Tworzenie kolumny typu AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 5972d9e3d84a236104e85e17d8df1e9ee7f56122
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="1bfb8-102">Tworzenie kolumny typu AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="1bfb8-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="1bfb8-103">Aby zapewnić unikatową kolumnę wartości, można ustawić wartości kolumn, aby zwiększyć automatycznie po dodaniu nowych wierszy do tabeli.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="1bfb8-104">Aby utworzyć przyrostową automatycznie <xref:System.Data.DataColumn>ustaw <xref:System.Data.DataColumn.AutoIncrement%2A> właściwości kolumny do **true**.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="1bfb8-105"><xref:System.Data.DataColumn> Następnie rozpoczyna się od wartości zdefiniowane w <xref:System.Data.DataColumn.AutoIncrementSeed%2A> właściwości i z każdego wiersza dodano wartość **AutoIncrement** kolumny zwiększa się wartość zdefiniowana w <xref:System.Data.DataColumn.AutoIncrementStep%2A> właściwości kolumny.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="1bfb8-106">Dla **AutoIncrement** kolumn, zaleca się <xref:System.Data.DataColumn.ReadOnly%2A> właściwość **DataColumn** można ustawić **true**.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="1bfb8-107">Poniższy przykład przedstawia sposób tworzenia kolumny, która rozpoczyna się od wartości 200 i dodaje przyrostowo w kroku 3.</span><span class="sxs-lookup"><span data-stu-id="1bfb8-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1bfb8-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1bfb8-108">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 [<span data-ttu-id="1bfb8-109">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="1bfb8-109">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="1bfb8-110">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="1bfb8-110">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="1bfb8-111">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="1bfb8-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
