---
title: Tworzenie kolumn wyrażeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: db38d42e9c7dc1657e06030599ae2b8ba66ef6b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549879"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="14c00-102">Tworzenie kolumn wyrażeń</span><span class="sxs-lookup"><span data-stu-id="14c00-102">Creating Expression Columns</span></span>
<span data-ttu-id="14c00-103">Można zdefiniować wyrażenie dla kolumny, dzięki czemu może zawierać wartość obliczana z innych wartości kolumn, w tym samym wierszu lub wartości w kolumnach wiele wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="14c00-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="14c00-104">Aby określić wyrażenie, które ma zostać obliczone, użyj <xref:System.Data.DataColumn.Expression%2A> właściwość kolumna docelowa i użyj <xref:System.Data.DataColumn.ColumnName%2A> właściwości do odwoływania się do innych kolumn w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="14c00-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="14c00-105"><xref:System.Data.DataColumn.DataType%2A> Wyrażenia kolumny musi być zgodna wartość, która zwraca wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="14c00-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="14c00-106">Poniższa tabela zawiera listę kilku możliwych zastosowań wyrażenie kolumny w tabeli.</span><span class="sxs-lookup"><span data-stu-id="14c00-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="14c00-107">Typ wyrażenia</span><span class="sxs-lookup"><span data-stu-id="14c00-107">Expression type</span></span>|<span data-ttu-id="14c00-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="14c00-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="14c00-109">Porównanie</span><span class="sxs-lookup"><span data-stu-id="14c00-109">Comparison</span></span>|<span data-ttu-id="14c00-110">"Całkowitą > = 500"</span><span class="sxs-lookup"><span data-stu-id="14c00-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="14c00-111">Obliczenie</span><span class="sxs-lookup"><span data-stu-id="14c00-111">Computation</span></span>|<span data-ttu-id="14c00-112">"UnitPrice \* Quantity"</span><span class="sxs-lookup"><span data-stu-id="14c00-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="14c00-113">Agregacji</span><span class="sxs-lookup"><span data-stu-id="14c00-113">Aggregation</span></span>|<span data-ttu-id="14c00-114">Sum(price)</span><span class="sxs-lookup"><span data-stu-id="14c00-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="14c00-115">Możesz ustawić **wyrażenie** właściwości na istniejącym **DataColumn** obiektu lub mogą one obejmować właściwość trzeci argument przekazany do <xref:System.Data.DataColumn> konstruktora, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="14c00-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="14c00-116">Wyrażenia mogą odwoływać się do innych kolumn wyrażenie; Jednak odwołanie cykliczne, w którym dwóch wyrażeń odwoływać się do siebie nawzajem, spowoduje wygenerowanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="14c00-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="14c00-117">Reguły dotyczące wyrażeń, zobacz <xref:System.Data.DataColumn.Expression%2A> właściwość **DataColumn** klasy.</span><span class="sxs-lookup"><span data-stu-id="14c00-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14c00-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14c00-118">See also</span></span>
- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="14c00-119">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="14c00-119">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="14c00-120">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="14c00-120">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="14c00-121">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="14c00-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
