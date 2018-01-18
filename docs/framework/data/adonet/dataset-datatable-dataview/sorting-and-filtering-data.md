---
title: Sortowanie i filtrowanie danych
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
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2411307623c714ae521d00dcffca05d3569a656e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="20b75-102">Sortowanie i filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="20b75-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="20b75-103"><xref:System.Data.DataView> Udostępnia kilka sposobów, sortowanie i filtrowanie danych w <xref:System.Data.DataTable>:</span><span class="sxs-lookup"><span data-stu-id="20b75-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
-   <span data-ttu-id="20b75-104">Można użyć <xref:System.Data.DataView.Sort%2A> właściwości w celu określenia jednej lub wielu kolumn sortowanie zleceń i mają (rosnąco) ASC i DESC (malejąco) parametry.</span><span class="sxs-lookup"><span data-stu-id="20b75-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
-   <span data-ttu-id="20b75-105">Można użyć <xref:System.Data.DataView.ApplyDefaultSort%2A> właściwość, aby automatycznie utworzyć porządek sortowania, w kolejności rosnącej na podstawie kolumny klucza podstawowego lub kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="20b75-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="20b75-106"><xref:System.Data.DataView.ApplyDefaultSort%2A>ma zastosowanie tylko w przypadku **sortowania** właściwość jest odwołanie o wartości null lub pusty ciąg, i gdy tabela ma zdefiniowany klucz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="20b75-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
-   <span data-ttu-id="20b75-107">Można użyć <xref:System.Data.DataView.RowFilter%2A> właściwości w celu określenia podzbiór wierszy na podstawie ich kolumny wartości.</span><span class="sxs-lookup"><span data-stu-id="20b75-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="20b75-108">Aby uzyskać więcej informacji o prawidłowe wyrażenia dla **RowFilter** właściwości, zobacz informacje referencyjne dotyczące <xref:System.Data.DataColumn.Expression%2A> właściwość <xref:System.Data.DataColumn> klasy.</span><span class="sxs-lookup"><span data-stu-id="20b75-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="20b75-109">Jeśli chcesz zwrócić wyników określonego zapytania na danych, a nie udostępnia dynamiczny widok podzbiór danych, użyj <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody **DataView** Aby uzyskać najlepszą wydajność, a nie ustawienie **RowFilter** właściwości.</span><span class="sxs-lookup"><span data-stu-id="20b75-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="20b75-110">Ustawienie **RowFilter** właściwości odtwarza indeksu dla danych narzut dodawanie do swojej aplikacji i zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="20b75-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="20b75-111">**RowFilter** właściwości najlepiej sprawdza się w aplikacji powiązanych z danymi gdzie powiązanej kontrolki wyświetla filtrowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="20b75-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="20b75-112">**Znaleźć** i **FindRows** metody wykorzystać bieżącego indeksu bez konieczności indeksu, który ma zostać również przebudowany.</span><span class="sxs-lookup"><span data-stu-id="20b75-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="20b75-113">Aby uzyskać więcej informacji na temat **znaleźć** i **FindRows** metod, zobacz [znajdowanie wierszy](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="20b75-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
-   <span data-ttu-id="20b75-114">Można użyć <xref:System.Data.DataView.RowStateFilter%2A> właściwości w celu określenia, które wersje wierszy do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="20b75-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="20b75-115">**DataView** niejawnie zarządza wersji wierszy do udostępnienia, w zależności od **RowState** podstawowej wiersza.</span><span class="sxs-lookup"><span data-stu-id="20b75-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="20b75-116">Na przykład jeśli **Element RowStateFilter** ustawiono **DataViewRowState.Deleted**, **DataView** przedstawia **oryginalnego** wersja wiersza wszystkie **usunięte** wierszy, ponieważ nie istnieje żadne **bieżącego** wersja wiersza.</span><span class="sxs-lookup"><span data-stu-id="20b75-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="20b75-117">Można określić wersji wiersza wiersza jest ujawniany przy użyciu **RowVersion** właściwość **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="20b75-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="20b75-118">W poniższej tabeli przedstawiono opcje **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="20b75-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="20b75-119">Opcje DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="20b75-119">DataViewRowState options</span></span>|<span data-ttu-id="20b75-120">Opis</span><span class="sxs-lookup"><span data-stu-id="20b75-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="20b75-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="20b75-121">**CurrentRows**</span></span>|<span data-ttu-id="20b75-122">**Bieżącego** wersja wiersza wszystkich **Unchanged**, **Added**, i **zmodyfikowane** wierszy.</span><span class="sxs-lookup"><span data-stu-id="20b75-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="20b75-123">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="20b75-123">This is the default.</span></span>|  
    |<span data-ttu-id="20b75-124">**Dodane**</span><span class="sxs-lookup"><span data-stu-id="20b75-124">**Added**</span></span>|<span data-ttu-id="20b75-125">**Bieżącego** wersja wiersza wszystkich **Added** wierszy.</span><span class="sxs-lookup"><span data-stu-id="20b75-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="20b75-126">**Usunięte**</span><span class="sxs-lookup"><span data-stu-id="20b75-126">**Deleted**</span></span>|<span data-ttu-id="20b75-127">**Oryginalnego** wersja wiersza wszystkich **usunięte** wierszy.</span><span class="sxs-lookup"><span data-stu-id="20b75-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="20b75-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="20b75-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="20b75-129">**Bieżącego** wersja wiersza wszystkich **zmodyfikowane** wierszy.</span><span class="sxs-lookup"><span data-stu-id="20b75-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="20b75-130">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="20b75-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="20b75-131">**Oryginalnego** wersja wiersza wszystkich **zmodyfikowane** wierszy.</span><span class="sxs-lookup"><span data-stu-id="20b75-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="20b75-132">**Brak**</span><span class="sxs-lookup"><span data-stu-id="20b75-132">**None**</span></span>|<span data-ttu-id="20b75-133">Żadne wiersze.</span><span class="sxs-lookup"><span data-stu-id="20b75-133">No rows.</span></span>|  
    |<span data-ttu-id="20b75-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="20b75-134">**OriginalRows**</span></span>|<span data-ttu-id="20b75-135">**Oryginalnego** wersja wiersza wszystkich **Unchanged**, **zmodyfikowane**, i **usunięte** wierszy.</span><span class="sxs-lookup"><span data-stu-id="20b75-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="20b75-136">**Unchanged**</span><span class="sxs-lookup"><span data-stu-id="20b75-136">**Unchanged**</span></span>|<span data-ttu-id="20b75-137">**Bieżącego** wersja wiersza wszystkich **Unchanged** wierszy.</span><span class="sxs-lookup"><span data-stu-id="20b75-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="20b75-138">Aby uzyskać więcej informacji na temat stany wiersza i wersje wiersza, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="20b75-138">For more information about row states and row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="20b75-139">Poniższy przykład kodu tworzy widok czy przedstawia wszystkie produkty, których liczba jednostek w magazynie jest mniejsza lub równa poziomu zmiany kolejności, w najpierw posortowane według Identyfikatora dostawcy, a następnie według nazwy produktu.</span><span class="sxs-lookup"><span data-stu-id="20b75-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a><span data-ttu-id="20b75-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20b75-140">See Also</span></span>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="20b75-141">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="20b75-141">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="20b75-142">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="20b75-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
