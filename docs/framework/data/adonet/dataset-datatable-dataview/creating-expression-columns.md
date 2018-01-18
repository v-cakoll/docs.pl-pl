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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 03c049ea3fb4b0f75418de4f9e8318512c198f41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="creating-expression-columns"></a><span data-ttu-id="b6572-102">Tworzenie kolumn wyrażeń</span><span class="sxs-lookup"><span data-stu-id="b6572-102">Creating Expression Columns</span></span>
<span data-ttu-id="b6572-103">Wyrażenie dla kolumny można zdefiniować, umożliwiając zawierać wartość obliczana z innych wartości kolumn, w tym samym wierszu lub wartości w kolumnie wielu wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="b6572-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="b6572-104">Aby zdefiniować wyrażenie, które ma zostać obliczone, należy użyć <xref:System.Data.DataColumn.Expression%2A> właściwość kolumny docelowej i użyj <xref:System.Data.DataColumn.ColumnName%2A> właściwości do odwoływania się do kolumn w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="b6572-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="b6572-105"><xref:System.Data.DataColumn.DataType%2A> Dla wyrażenia musi być zgodna wartość, która zwraca wyrażenie kolumny.</span><span class="sxs-lookup"><span data-stu-id="b6572-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="b6572-106">W poniższej tabeli wymieniono kilka możliwych zastosowań dla kolumny wyrażenia w tabeli.</span><span class="sxs-lookup"><span data-stu-id="b6572-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="b6572-107">Typ wyrażenia</span><span class="sxs-lookup"><span data-stu-id="b6572-107">Expression type</span></span>|<span data-ttu-id="b6572-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6572-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="b6572-109">Porównanie</span><span class="sxs-lookup"><span data-stu-id="b6572-109">Comparison</span></span>|<span data-ttu-id="b6572-110">"Całkowita > = 500"</span><span class="sxs-lookup"><span data-stu-id="b6572-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="b6572-111">Obliczenia</span><span class="sxs-lookup"><span data-stu-id="b6572-111">Computation</span></span>|<span data-ttu-id="b6572-112">"UnitPrice \* ilość"</span><span class="sxs-lookup"><span data-stu-id="b6572-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="b6572-113">Agregacji</span><span class="sxs-lookup"><span data-stu-id="b6572-113">Aggregation</span></span>|<span data-ttu-id="b6572-114">Sum(price)</span><span class="sxs-lookup"><span data-stu-id="b6572-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="b6572-115">Można ustawić **wyrażenie** właściwości na istniejącym **DataColumn** obiekt, lub można dodać właściwość jako trzeci argument przekazany do <xref:System.Data.DataColumn> konstruktora, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b6572-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="b6572-116">Wyrażenia mogą odwoływać się do innych kolumn wyrażenie; Jednak odwołanie cykliczne, w którym dwóch wyrażeń zależą od siebie, zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b6572-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="b6572-117">W przypadku reguł dotyczących wyrażeń, zobacz <xref:System.Data.DataColumn.Expression%2A> właściwość **DataColumn** klasy.</span><span class="sxs-lookup"><span data-stu-id="b6572-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6572-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6572-118">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="b6572-119">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="b6572-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="b6572-120">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="b6572-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="b6572-121">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="b6572-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
