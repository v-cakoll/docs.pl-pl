---
title: Tworzenie kolumn wyrażeń
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 8ae8c8e020a3d8ada5bdcd5037187e6f3abd33a4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203833"
---
# <a name="creating-expression-columns"></a><span data-ttu-id="c503e-102">Tworzenie kolumn wyrażeń</span><span class="sxs-lookup"><span data-stu-id="c503e-102">Creating Expression Columns</span></span>
<span data-ttu-id="c503e-103">Można zdefiniować wyrażenie dla kolumny, aby zawierało wartość obliczoną na podstawie innych wartości kolumn w tym samym wierszu lub z wartości kolumn obejmujących wiele wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="c503e-103">You can define an expression for a column, enabling it to contain a value calculated from other column values in the same row or from the column values of multiple rows in the table.</span></span> <span data-ttu-id="c503e-104">Aby zdefiniować wyrażenie do obliczenia, użyj <xref:System.Data.DataColumn.Expression%2A> właściwości kolumny Target i <xref:System.Data.DataColumn.ColumnName%2A> Użyj właściwości, aby odwołać się do innych kolumn w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="c503e-104">To define the expression to be evaluated, use the <xref:System.Data.DataColumn.Expression%2A> property of the target column, and use the <xref:System.Data.DataColumn.ColumnName%2A> property to refer to other columns in the expression.</span></span> <span data-ttu-id="c503e-105">Kolumna <xref:System.Data.DataColumn.DataType%2A> dla wyrażenia musi być odpowiednia dla wartości zwracanej przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="c503e-105">The <xref:System.Data.DataColumn.DataType%2A> for the expression column must be appropriate for the value that the expression returns.</span></span>  
  
 <span data-ttu-id="c503e-106">W poniższej tabeli przedstawiono kilka możliwych zastosowania kolumn wyrażeń w tabeli.</span><span class="sxs-lookup"><span data-stu-id="c503e-106">The following table lists several possible uses for expression columns in a table.</span></span>  
  
|<span data-ttu-id="c503e-107">Typ wyrażenia</span><span class="sxs-lookup"><span data-stu-id="c503e-107">Expression type</span></span>|<span data-ttu-id="c503e-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="c503e-108">Example</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="c503e-109">Porównanie</span><span class="sxs-lookup"><span data-stu-id="c503e-109">Comparison</span></span>|<span data-ttu-id="c503e-110">"Łącznie > = 500"</span><span class="sxs-lookup"><span data-stu-id="c503e-110">"Total >= 500"</span></span>|  
|<span data-ttu-id="c503e-111">Obliczeń</span><span class="sxs-lookup"><span data-stu-id="c503e-111">Computation</span></span>|<span data-ttu-id="c503e-112">"CenaJednostkowa \* ilooć"</span><span class="sxs-lookup"><span data-stu-id="c503e-112">"UnitPrice \* Quantity"</span></span>|  
|<span data-ttu-id="c503e-113">Agregacja</span><span class="sxs-lookup"><span data-stu-id="c503e-113">Aggregation</span></span>|<span data-ttu-id="c503e-114">Sum (cena)</span><span class="sxs-lookup"><span data-stu-id="c503e-114">Sum(Price)</span></span>|  
  
 <span data-ttu-id="c503e-115">Można ustawić właściwość **Expression** w istniejącym obiekcie DataColumn lub dodać właściwość jako trzeci argument do <xref:System.Data.DataColumn> konstruktora, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c503e-115">You can set the **Expression** property on an existing **DataColumn** object, or you can include the property as the third argument passed to the <xref:System.Data.DataColumn> constructor, as shown in the following example.</span></span>  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 <span data-ttu-id="c503e-116">Wyrażenia mogą odwoływać się do innych kolumn wyrażeń; jednak odwołanie cykliczne, w którym dwa wyrażenia odwołuje się nawzajem, wygeneruje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c503e-116">Expressions can reference other expression columns; however, a circular reference, in which two expressions reference each other, will generate an exception.</span></span> <span data-ttu-id="c503e-117">Aby uzyskać reguły dotyczące pisania wyrażeń, zobacz <xref:System.Data.DataColumn.Expression%2A> właściwość klasy DataColumn.</span><span class="sxs-lookup"><span data-stu-id="c503e-117">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c503e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c503e-118">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="c503e-119">Definicja schematu elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="c503e-119">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="c503e-120">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="c503e-120">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="c503e-121">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="c503e-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
