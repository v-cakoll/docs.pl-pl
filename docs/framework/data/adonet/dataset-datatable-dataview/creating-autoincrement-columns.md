---
title: Tworzenie kolumn typu AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 5e4a36829107480a44980c7210b39c21231c67f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786454"
---
# <a name="creating-autoincrement-columns"></a><span data-ttu-id="705ce-102">Tworzenie kolumn typu AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="705ce-102">Creating AutoIncrement Columns</span></span>
<span data-ttu-id="705ce-103">Aby zapewnić unikatowe wartości kolumn, można ustawić wartości kolumn, które mają być zwiększane automatycznie po dodaniu nowych wierszy do tabeli.</span><span class="sxs-lookup"><span data-stu-id="705ce-103">To ensure unique column values, you can set the column values to increment automatically when new rows are added to the table.</span></span> <span data-ttu-id="705ce-104">Aby utworzyć funkcję autozwiększania <xref:System.Data.DataColumn>, <xref:System.Data.DataColumn.AutoIncrement%2A> ustaw właściwość kolumny na **true**.</span><span class="sxs-lookup"><span data-stu-id="705ce-104">To create an auto-incrementing <xref:System.Data.DataColumn>, set the <xref:System.Data.DataColumn.AutoIncrement%2A> property of the column to **true**.</span></span> <span data-ttu-id="705ce-105">Następnie rozpoczyna się od wartości zdefiniowanej <xref:System.Data.DataColumn.AutoIncrementSeed%2A> we właściwości, a każdy wiersz dodaliśmy wartość kolumny **AutoIncrement** <xref:System.Data.DataColumn.AutoIncrementStep%2A> zwiększa się o wartość zdefiniowaną we właściwości kolumny. <xref:System.Data.DataColumn></span><span class="sxs-lookup"><span data-stu-id="705ce-105">The <xref:System.Data.DataColumn> then starts with the value defined in the <xref:System.Data.DataColumn.AutoIncrementSeed%2A> property, and with each row added the value of the **AutoIncrement** column increases by the value defined in the <xref:System.Data.DataColumn.AutoIncrementStep%2A> property of the column.</span></span>  
  
 <span data-ttu-id="705ce-106">W przypadku kolumn typu **AutoIncrement** <xref:System.Data.DataColumn.ReadOnly%2A> zalecamy, aby właściwość **DataColumn** była ustawiona na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="705ce-106">For **AutoIncrement** columns, we recommend that the <xref:System.Data.DataColumn.ReadOnly%2A> property of the **DataColumn** be set to **true**.</span></span>  
  
 <span data-ttu-id="705ce-107">W poniższym przykładzie pokazano, jak utworzyć kolumnę rozpoczynającą się od wartości 200 i dodać przyrostowo w krokach 3.</span><span class="sxs-lookup"><span data-stu-id="705ce-107">The following example demonstrates how to create a column that starts with a value of 200 and adds incrementally in steps of 3.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="705ce-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="705ce-108">See also</span></span>

- <xref:System.Data.DataColumn>
- [<span data-ttu-id="705ce-109">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="705ce-109">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="705ce-110">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="705ce-110">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="705ce-111">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="705ce-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
