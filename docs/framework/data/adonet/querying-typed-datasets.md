---
title: Wykonywanie zapytania Typizowane zbiory danych
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
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c232ca2888c957bea33d06c84a62b00fdc7fd80c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="querying-typed-datasets"></a><span data-ttu-id="116bd-102">Wykonywanie zapytania Typizowane zbiory danych</span><span class="sxs-lookup"><span data-stu-id="116bd-102">Querying Typed DataSets</span></span>
<span data-ttu-id="116bd-103">Jeśli schemat <xref:System.Data.DataSet> jest znany w czasie projektowania aplikacji, zalecane jest użycie typu <xref:System.Data.DataSet> przy użyciu [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="116bd-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="116bd-104">Typizowany <xref:System.Data.DataSet> jest klasą pochodną <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="116bd-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="116bd-105">W efekcie dziedziczy wszystkie metody, zdarzeń i właściwości <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="116bd-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="116bd-106">Ponadto maszynowy <xref:System.Data.DataSet> udostępnia silnie typizowane metody, zdarzeń i właściwości.</span><span class="sxs-lookup"><span data-stu-id="116bd-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="116bd-107">Oznacza to, że masz dostęp tabele i kolumny według nazwy, zamiast za pomocą metody opartej na kolekcji.</span><span class="sxs-lookup"><span data-stu-id="116bd-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="116bd-108">Dzięki temu zapytania prostszy i bardziej czytelne.</span><span class="sxs-lookup"><span data-stu-id="116bd-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="116bd-109">Aby uzyskać więcej informacji, zobacz [wpisanych zestawów danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="116bd-109">For more information, see [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="116bd-110">obsługuje również obsługę zapytań typu <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="116bd-110"> also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="116bd-111">Z typu <xref:System.Data.DataSet>, nie trzeba używać ogólnych <xref:System.Data.DataRowExtensions.Field%2A> metody lub <xref:System.Data.DataRowExtensions.SetField%2A> metodę dostępu do danych kolumny.</span><span class="sxs-lookup"><span data-stu-id="116bd-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span>  <span data-ttu-id="116bd-112">Nazwy właściwości są dostępne w czasie kompilacji, ponieważ zawiera informacje o typie <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="116bd-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="116bd-113">zapewnia dostęp do wartości w kolumnie jako poprawny typ, dzięki czemu błędy niezgodności typów są przechwytywane podczas kompilowania kodu zamiast w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="116bd-113"> provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>  
  
 <span data-ttu-id="116bd-114">Przed rozpoczęciem wykonywania zapytania typu <xref:System.Data.DataSet>, należy wygenerować za pomocą Projektanta obiektów DataSet w klasie [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="116bd-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the DataSet Designer in [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].</span></span>  <span data-ttu-id="116bd-115">Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="116bd-115">For more information, see [Create and configure datasets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>  
  
## <a name="example"></a><span data-ttu-id="116bd-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="116bd-116">Example</span></span>  
 <span data-ttu-id="116bd-117">W poniższym przykładzie przedstawiono zapytania za pośrednictwem typu <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="116bd-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="116bd-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="116bd-118">See Also</span></span>  
 [<span data-ttu-id="116bd-119">Wykonywanie zapytania do zestawów danych</span><span class="sxs-lookup"><span data-stu-id="116bd-119">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="116bd-120">Zapytania wielotabelowe</span><span class="sxs-lookup"><span data-stu-id="116bd-120">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [<span data-ttu-id="116bd-121">Zapytania jednotabelowe</span><span class="sxs-lookup"><span data-stu-id="116bd-121">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
