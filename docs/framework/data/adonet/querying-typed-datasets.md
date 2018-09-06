---
title: Podczas badania zestawów
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: d956fd5f07c108146d20623bcf811266380c132c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739649"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="b94d0-102">Zapytanie wpisanych zestawów danych</span><span class="sxs-lookup"><span data-stu-id="b94d0-102">Query typed DataSets</span></span>

<span data-ttu-id="b94d0-103">Jeśli schemat <xref:System.Data.DataSet> jest znany w czasie projektowania aplikacji, zalecamy użycie wpisane <xref:System.Data.DataSet> podczas korzystania z LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="b94d0-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="b94d0-104">Wpisane <xref:System.Data.DataSet> jest klasa, która pochodzi od klasy <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b94d0-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b94d0-105">W efekcie dziedziczy wszystkie metody, zdarzenia i właściwości <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b94d0-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b94d0-106">Ponadto wpisane <xref:System.Data.DataSet> udostępnia silnie typizowane metody, zdarzenia i właściwości.</span><span class="sxs-lookup"><span data-stu-id="b94d0-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="b94d0-107">Oznacza to, że masz dostęp tabele i kolumny, według nazwy, zamiast korzystać z metody oparte na kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b94d0-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="b94d0-108">To sprawia, że zapytania prostszy i bardziej czytelny.</span><span class="sxs-lookup"><span data-stu-id="b94d0-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="b94d0-109">Aby uzyskać więcej informacji, zobacz [wpisanych zestawów danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="b94d0-109">For more information, see [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="b94d0-110">LINQ do zestawu danych obsługuje również zapytań wpisane <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b94d0-110">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b94d0-111">Z kontrolą typów <xref:System.Data.DataSet>, będą musieli używać ogólnych <xref:System.Data.DataRowExtensions.Field%2A> metody lub <xref:System.Data.DataRowExtensions.SetField%2A> metody dostępu do kolumny danych.</span><span class="sxs-lookup"><span data-stu-id="b94d0-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="b94d0-112">Nazwy właściwości są dostępne w czasie kompilacji, ponieważ informacje o typie jest uwzględniony w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b94d0-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b94d0-113">LINQ do zestawu danych zapewnia dostęp do wartości w kolumnie jako odpowiedniego typu, tak aby błędy niezgodności wpisywania są wyłapywane, gdy kod jest kompilowany zamiast w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b94d0-113">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="b94d0-114">Przed rozpoczęciem wykonywania zapytań wpisane <xref:System.Data.DataSet>, należy wygenerować klasę za pomocą **Projektanta obiektów DataSet** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b94d0-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="b94d0-115">Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="b94d0-115">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="b94d0-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="b94d0-116">Example</span></span>

<span data-ttu-id="b94d0-117">W poniższym przykładzie przedstawiono zapytanie, za pośrednictwem wpisane <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="b94d0-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a><span data-ttu-id="b94d0-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b94d0-118">See also</span></span>

- [<span data-ttu-id="b94d0-119">Wykonywanie zapytania do zestawów danych</span><span class="sxs-lookup"><span data-stu-id="b94d0-119">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="b94d0-120">Zapytania wielotabelowe</span><span class="sxs-lookup"><span data-stu-id="b94d0-120">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="b94d0-121">Zapytania jednotabelowe</span><span class="sxs-lookup"><span data-stu-id="b94d0-121">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
