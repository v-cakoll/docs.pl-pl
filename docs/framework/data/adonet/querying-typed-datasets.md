---
title: Wykonywanie zapytania do typizowanych zestawów danych
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 55714c4dae73cd17a849cc35681797dfa4266e3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782965"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="be028-102">Zestawy danych z określonym typem zapytania</span><span class="sxs-lookup"><span data-stu-id="be028-102">Query typed DataSets</span></span>

<span data-ttu-id="be028-103">Jeśli schemat <xref:System.Data.DataSet> programu jest znany w czasie projektowania aplikacji, zalecamy użycie <xref:System.Data.DataSet> typu podczas korzystania z LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="be028-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="be028-104">Typ <xref:System.Data.DataSet> to Klasa, która pochodzi <xref:System.Data.DataSet>od klasy.</span><span class="sxs-lookup"><span data-stu-id="be028-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="be028-105">W związku z tym dziedziczy wszystkie metody, zdarzenia i właściwości <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="be028-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="be028-106">Ponadto typ <xref:System.Data.DataSet> udostępnia metody o jednoznacznie określonym typie, zdarzenia i właściwości.</span><span class="sxs-lookup"><span data-stu-id="be028-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="be028-107">Oznacza to, że można uzyskać dostęp do tabel i kolumn według nazwy, zamiast korzystać z metod opartych na kolekcji.</span><span class="sxs-lookup"><span data-stu-id="be028-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="be028-108">Sprawia to, że zapytania są prostsze i bardziej czytelne.</span><span class="sxs-lookup"><span data-stu-id="be028-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="be028-109">Aby uzyskać więcej informacji, zobacz [typy zestawów danych](./dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="be028-109">For more information, see [Typed DataSets](./dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="be028-110">LINQ to DataSet obsługuje również zapytania w określonym typie <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="be028-110">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="be028-111">Z określonym typem <xref:System.Data.DataSet>nie trzeba używać metody ogólnej <xref:System.Data.DataRowExtensions.Field%2A> ani <xref:System.Data.DataRowExtensions.SetField%2A> metody dostępu do danych kolumn.</span><span class="sxs-lookup"><span data-stu-id="be028-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="be028-112">Nazwy właściwości są dostępne w czasie kompilacji, ponieważ informacje o typie są zawarte w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="be028-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="be028-113">LINQ to DataSet zapewnia dostęp do wartości kolumn jako poprawny typ, dzięki czemu błędy niezgodności typów są przechwytywane podczas kompilowania kodu, a nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="be028-113">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="be028-114">Przed rozpoczęciem wykonywania zapytania o określony typ <xref:System.Data.DataSet>należy wygenerować klasę przy użyciu **projektanta obiektów DataSet** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="be028-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="be028-115">Aby uzyskać więcej informacji, zobacz [Tworzenie i konfigurowanie zestawów danych](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="be028-115">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="be028-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="be028-116">Example</span></span>

<span data-ttu-id="be028-117">W poniższym przykładzie pokazano zapytanie w określonym typie <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="be028-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="be028-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be028-118">See also</span></span>

- [<span data-ttu-id="be028-119">Wykonywanie zapytania do zestawów danych</span><span class="sxs-lookup"><span data-stu-id="be028-119">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="be028-120">Zapytania wielotabelowe</span><span class="sxs-lookup"><span data-stu-id="be028-120">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="be028-121">Zapytania jednotabelowe</span><span class="sxs-lookup"><span data-stu-id="be028-121">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)
