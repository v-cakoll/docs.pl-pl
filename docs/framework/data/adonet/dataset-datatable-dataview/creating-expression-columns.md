---
title: "Tworzenie kolumn wyrażeń"
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
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c1b0b7be8be6bec0c5a8850029bd3336d107f0a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-expression-columns"></a><span data-ttu-id="7cdb5-102">Tworzenie kolumn wyrażeń</span><span class="sxs-lookup"><span data-stu-id="7cdb5-102">Creating Expression Columns</span></span>
<span data-ttu-id="7cdb5-103">Wyrażenie dla kolumny można zdefiniować, umożliwiając zawierać wartość obliczana z innych wartości kolumn, w tym samym wierszu lub wartości w kolumnie wielu wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="7cdb5-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="7cdb5-104">Aby zdefiniować wyrażenie, które ma zostać obliczone, należy użyć <xref:System.Data.DataColumn.Expression%2A> właściwość kolumny docelowej i użyj <xref:System.Data.DataColumn.ColumnName%2A> właściwości do odwoływania się do kolumn w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="7cdb5-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="7cdb5-105"><xref:System.Data.DataColumn.DataType%2A> Dla wyrażenia musi być zgodna wartość, która zwraca wyrażenie kolumny.</span><span class="sxs-lookup"><span data-stu-id="7cdb5-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="7cdb5-106">W poniższej tabeli wymieniono kilka możliwych zastosowań dla kolumny wyrażenia w tabeli.</span><span class="sxs-lookup"><span data-stu-id="7cdb5-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="7cdb5-107">Typ wyrażenia</span><span class="sxs-lookup"><span data-stu-id="7cdb5-107">Expression type</span></span>|<span data-ttu-id="7cdb5-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cdb5-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="7cdb5-109">Porównanie</span><span class="sxs-lookup"><span data-stu-id="7cdb5-109">Comparison</span></span>|<span data-ttu-id="7cdb5-110">"Całkowita > = 500"</span><span class="sxs-lookup"><span data-stu-id="7cdb5-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="7cdb5-111">Obliczenia</span><span class="sxs-lookup"><span data-stu-id="7cdb5-111">Computation</span></span>|<span data-ttu-id="7cdb5-112">"UnitPrice * ilość"</span><span class="sxs-lookup"><span data-stu-id="7cdb5-112">"UnitPrice * Quantity"</span></span>|  
|<span data-ttu-id="7cdb5-113">Agregacji</span><span class="sxs-lookup"><span data-stu-id="7cdb5-113">Aggregation</span></span>|<span data-ttu-id="7cdb5-114">Sum(price)</span><span class="sxs-lookup"><span data-stu-id="7cdb5-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="7cdb5-115">Można ustawić **wyrażenie** właściwości na istniejącym **DataColumn** obiekt, lub można dodać właściwość jako trzeci argument przekazany do <xref:System.Data.DataColumn> konstruktora, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7cdb5-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="7cdb5-116">Wyrażenia mogą odwoływać się do innych kolumn wyrażenie; Jednak odwołanie cykliczne, w którym dwóch wyrażeń zależą od siebie, zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7cdb5-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="7cdb5-117">W przypadku reguł dotyczących wyrażeń, zobacz <xref:System.Data.DataColumn.Expression%2A> właściwość **DataColumn** klasy.</span><span class="sxs-lookup"><span data-stu-id="7cdb5-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cdb5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cdb5-118">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="7cdb5-119">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="7cdb5-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="7cdb5-120">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="7cdb5-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="7cdb5-121">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="7cdb5-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
