---
title: Sortowanie i filtrowanie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 8d8bd85f65adfde5f239e1e2dd79d65517b745a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166247"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="78a8f-102">Sortowanie i filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="78a8f-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="78a8f-103"><xref:System.Data.DataView> Oferuje kilka sposobów, sortowania i filtrowania danych w <xref:System.Data.DataTable>:</span><span class="sxs-lookup"><span data-stu-id="78a8f-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
-   <span data-ttu-id="78a8f-104">Możesz użyć <xref:System.Data.DataView.Sort%2A> właściwości w celu określenia jednej lub wielu kolumn, sortowanie zleceń i mają (rosnąco) ASC i DESC (malejąco) parametry.</span><span class="sxs-lookup"><span data-stu-id="78a8f-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
-   <span data-ttu-id="78a8f-105">Możesz użyć <xref:System.Data.DataView.ApplyDefaultSort%2A> właściwości, aby automatycznie utworzyć porządek sortowania, w kolejności rosnącej na podstawie kolumny klucza podstawowego lub kolumny tabeli.</span><span class="sxs-lookup"><span data-stu-id="78a8f-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <xref:System.Data.DataView.ApplyDefaultSort%2A> <span data-ttu-id="78a8f-106">ma zastosowanie tylko jeśli **sortowania** właściwość jest odwołaniem do wartości null ani być pustym ciągiem, a jeśli ma zdefiniowany klucz podstawowy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="78a8f-106">only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
-   <span data-ttu-id="78a8f-107">Możesz użyć <xref:System.Data.DataView.RowFilter%2A> właściwości w celu określenia podzbiór wierszy na podstawie ich wartości w kolumnach.</span><span class="sxs-lookup"><span data-stu-id="78a8f-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="78a8f-108">Szczegółowe informacje na temat prawidłowych wyrażeń dla **RowFilter** właściwości, zobacz informacje referencyjne dotyczące <xref:System.Data.DataColumn.Expression%2A> właściwość <xref:System.Data.DataColumn> klasy.</span><span class="sxs-lookup"><span data-stu-id="78a8f-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="78a8f-109">Jeśli chcesz przywrócić, użyj wyników określonego zapytania na danych, zapewniając dynamiczny widok podzbiór danych, w przeciwieństwie <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody **DataView** do osiągnięcia najlepszej wydajności zamiast ustawienie **RowFilter** właściwości.</span><span class="sxs-lookup"><span data-stu-id="78a8f-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="78a8f-110">Ustawienie **RowFilter** właściwość odbudowania indeksu dla danych, obciążenie dodawanie do aplikacji i zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="78a8f-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="78a8f-111">**RowFilter** właściwość najlepiej sprawdza się w aplikacji powiązanych z danymi gdzie powiązanej kontrolki Wyświetla wyfiltrowanych wyników.</span><span class="sxs-lookup"><span data-stu-id="78a8f-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="78a8f-112">**Znaleźć** i **FindRows** metody wykorzystać bieżącego indeksu bez konieczności indeksu odbudowania.</span><span class="sxs-lookup"><span data-stu-id="78a8f-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="78a8f-113">Aby uzyskać więcej informacji na temat **znaleźć** i **FindRows** metod, zobacz [znajdowanie wierszy](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="78a8f-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
-   <span data-ttu-id="78a8f-114">Możesz użyć <xref:System.Data.DataView.RowStateFilter%2A> właściwości w celu określenia, które wersje wierszy do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="78a8f-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="78a8f-115">**DataView** niejawnie zarządza której wersji wiersza do udostępnienia, w zależności od **RowState** bazowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="78a8f-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="78a8f-116">Na przykład jeśli **Element RowStateFilter** ustawiono **DataViewRowState.Deleted**, **DataView** udostępnia **oryginalnego** wersji wierszy wszystkie **usunięte** wiersze, ponieważ nie istnieje żadne **bieżącego** wiersza wersji.</span><span class="sxs-lookup"><span data-stu-id="78a8f-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="78a8f-117">Można określić, której wersji wiersza wiersza jest ujawniany przy użyciu **RowVersion** właściwość **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="78a8f-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="78a8f-118">W poniższej tabeli przedstawiono opcje **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="78a8f-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="78a8f-119">Opcje DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="78a8f-119">DataViewRowState options</span></span>|<span data-ttu-id="78a8f-120">Opis</span><span class="sxs-lookup"><span data-stu-id="78a8f-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |**<span data-ttu-id="78a8f-121">CurrentRows</span><span class="sxs-lookup"><span data-stu-id="78a8f-121">CurrentRows</span></span>**|<span data-ttu-id="78a8f-122">**Bieżącego** wiersz wersję wszystkich **Unchanged**, **dodano**, i **zmodyfikowane** wierszy.</span><span class="sxs-lookup"><span data-stu-id="78a8f-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="78a8f-123">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="78a8f-123">This is the default.</span></span>|  
    |**<span data-ttu-id="78a8f-124">Dodano</span><span class="sxs-lookup"><span data-stu-id="78a8f-124">Added</span></span>**|<span data-ttu-id="78a8f-125">**Bieżącego** wiersz wersję wszystkich **dodano** wierszy.</span><span class="sxs-lookup"><span data-stu-id="78a8f-125">The **Current** row version of all **Added** rows.</span></span>|  
    |**<span data-ttu-id="78a8f-126">Usunięte</span><span class="sxs-lookup"><span data-stu-id="78a8f-126">Deleted</span></span>**|<span data-ttu-id="78a8f-127">**Oryginalnego** wiersz wersję wszystkich **usunięte** wierszy.</span><span class="sxs-lookup"><span data-stu-id="78a8f-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |**<span data-ttu-id="78a8f-128">ModifiedCurrent</span><span class="sxs-lookup"><span data-stu-id="78a8f-128">ModifiedCurrent</span></span>**|<span data-ttu-id="78a8f-129">**Bieżącego** wiersz wersję wszystkich **zmodyfikowane** wierszy.</span><span class="sxs-lookup"><span data-stu-id="78a8f-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |**<span data-ttu-id="78a8f-130">ModifiedOriginal</span><span class="sxs-lookup"><span data-stu-id="78a8f-130">ModifiedOriginal</span></span>**|<span data-ttu-id="78a8f-131">**Oryginalnego** wiersz wersję wszystkich **zmodyfikowane** wierszy.</span><span class="sxs-lookup"><span data-stu-id="78a8f-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |**<span data-ttu-id="78a8f-132">Brak</span><span class="sxs-lookup"><span data-stu-id="78a8f-132">None</span></span>**|<span data-ttu-id="78a8f-133">Brak wierszy.</span><span class="sxs-lookup"><span data-stu-id="78a8f-133">No rows.</span></span>|  
    |**<span data-ttu-id="78a8f-134">OriginalRows</span><span class="sxs-lookup"><span data-stu-id="78a8f-134">OriginalRows</span></span>**|<span data-ttu-id="78a8f-135">**Oryginalnego** wiersz wersję wszystkich **Unchanged**, **zmodyfikowane**, i **usunięte** wierszy.</span><span class="sxs-lookup"><span data-stu-id="78a8f-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |**<span data-ttu-id="78a8f-136">bez zmian</span><span class="sxs-lookup"><span data-stu-id="78a8f-136">Unchanged</span></span>**|<span data-ttu-id="78a8f-137">**Bieżącego** wiersz wersję wszystkich **Unchanged** wierszy.</span><span class="sxs-lookup"><span data-stu-id="78a8f-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="78a8f-138">Aby uzyskać więcej informacji na temat stany wiersza i wersje wiersza, zobacz [stany wiersza i wersje wiersza](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="78a8f-138">For more information about row states and row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="78a8f-139">Poniższy przykład kodu tworzy widok, przedstawia wszystkie produkty, których liczba jednostek w magazynie jest mniejsza lub równa z poziomu której kolejność chcesz zmienić, najpierw posortowane według Identyfikatora dostawcy, a następnie według nazwy produktu.</span><span class="sxs-lookup"><span data-stu-id="78a8f-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="78a8f-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78a8f-140">See also</span></span>

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="78a8f-141">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="78a8f-141">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [<span data-ttu-id="78a8f-142">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="78a8f-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
