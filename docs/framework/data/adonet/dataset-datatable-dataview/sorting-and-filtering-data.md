---
title: Sortowanie i filtrowanie danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 0907aa2a66e1bf51fefc7bed8ea2612cc0c830fa
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203218"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="6185c-102">Sortowanie i filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="6185c-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="6185c-103">Oferuje kilka sposobów sortowania i filtrowania danych <xref:System.Data.DataTable>w: <xref:System.Data.DataView></span><span class="sxs-lookup"><span data-stu-id="6185c-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
- <span data-ttu-id="6185c-104">Możesz użyć <xref:System.Data.DataView.Sort%2A> właściwości, aby określić pojedyncze lub wiele kolumn kolejności sortowania oraz uwzględnić parametry ASC (Ascending) i DESC (malejąco).</span><span class="sxs-lookup"><span data-stu-id="6185c-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
- <span data-ttu-id="6185c-105">Możesz użyć <xref:System.Data.DataView.ApplyDefaultSort%2A> właściwości, aby automatycznie utworzyć porządek sortowania w kolejności rosnącej na podstawie kolumny klucza podstawowego lub kolumn tabeli.</span><span class="sxs-lookup"><span data-stu-id="6185c-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="6185c-106"><xref:System.Data.DataView.ApplyDefaultSort%2A>stosuje się tylko wtedy, gdy właściwość **sort** jest odwołaniem null lub ciągiem pustym, a tabela ma zdefiniowany klucz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="6185c-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
- <span data-ttu-id="6185c-107">Możesz użyć właściwości, <xref:System.Data.DataView.RowFilter%2A> aby określić podzestawy wierszy na podstawie ich wartości kolumn.</span><span class="sxs-lookup"><span data-stu-id="6185c-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="6185c-108">Aby uzyskać szczegółowe informacje na temat prawidłowych wyrażeń dla właściwości **RowFilter** , zobacz informacje o <xref:System.Data.DataColumn.Expression%2A> odwołaniach dla <xref:System.Data.DataColumn> właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="6185c-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="6185c-109">Jeśli chcesz zwrócić wyniki konkretnego zapytania dotyczącego danych, w przeciwieństwie do udostępnienia dynamicznego widoku podzbioru danych, użyj <xref:System.Data.DataView.Find%2A> metody lub <xref:System.Data.DataView.FindRows%2A> obiektu **DataView** , aby osiągnąć najlepszą wydajność zamiast ustawić  **Właściwość RowFilter** .</span><span class="sxs-lookup"><span data-stu-id="6185c-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="6185c-110">Ustawienie właściwości **RowFilter** powoduje odbudowanie indeksu dla danych, dodanie obciążenia do aplikacji i zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="6185c-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="6185c-111">Właściwość **RowFilter** najlepiej używać w aplikacji powiązanej z danymi, gdzie kontrolka powiązania wyświetla filtrowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="6185c-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="6185c-112">Metody **Find** i **FindRows** wykorzystują bieżący indeks bez konieczności ponownego kompilowania indeksu.</span><span class="sxs-lookup"><span data-stu-id="6185c-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="6185c-113">Aby uzyskać więcej informacji na temat metod **Find** i **FindRows** , zobacz [Znajdowanie wierszy](finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="6185c-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](finding-rows.md).</span></span>  
  
- <span data-ttu-id="6185c-114">Możesz użyć właściwości, <xref:System.Data.DataView.RowStateFilter%2A> aby określić wersje wierszy do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="6185c-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="6185c-115">**Widok DataView** niejawnie określa wersję wiersza do udostępnienia w zależności od **RowState** podstawowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="6185c-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="6185c-116">Na przykład jeśli **RowStateFilter** jest ustawiony na **DataViewRowState. deleted**, **Widok DataView** ujawnia pierwotną wersję wiersza wszystkich usuniętych wierszy , ponieważ nie ma **bieżącej** wersji wiersza.</span><span class="sxs-lookup"><span data-stu-id="6185c-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="6185c-117">Możesz określić, która wersja wiersza ma być ujawniana przy użyciu właściwości **rowversion** **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="6185c-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="6185c-118">W poniższej tabeli przedstawiono opcje **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="6185c-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="6185c-119">Opcje DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="6185c-119">DataViewRowState options</span></span>|<span data-ttu-id="6185c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="6185c-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="6185c-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="6185c-121">**CurrentRows**</span></span>|<span data-ttu-id="6185c-122">Wersja **bieżącego** wiersza wszystkich niezmienionych, dodanychi zmodyfikowanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="6185c-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="6185c-123">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="6185c-123">This is the default.</span></span>|  
    |<span data-ttu-id="6185c-124">**Dołączony**</span><span class="sxs-lookup"><span data-stu-id="6185c-124">**Added**</span></span>|<span data-ttu-id="6185c-125">Wersja **bieżącego** wiersza wszystkich dodanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="6185c-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="6185c-126">**Skasowan**</span><span class="sxs-lookup"><span data-stu-id="6185c-126">**Deleted**</span></span>|<span data-ttu-id="6185c-127">**Oryginalna** wersja wiersza wszystkich usuniętych wierszy.</span><span class="sxs-lookup"><span data-stu-id="6185c-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="6185c-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="6185c-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="6185c-129">Wersja **bieżącego** wiersza wszystkich zmodyfikowanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="6185c-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="6185c-130">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="6185c-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="6185c-131">**Oryginalna** wersja wiersza wszystkich zmodyfikowanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="6185c-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="6185c-132">**Brak**</span><span class="sxs-lookup"><span data-stu-id="6185c-132">**None**</span></span>|<span data-ttu-id="6185c-133">Brak wierszy.</span><span class="sxs-lookup"><span data-stu-id="6185c-133">No rows.</span></span>|  
    |<span data-ttu-id="6185c-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="6185c-134">**OriginalRows**</span></span>|<span data-ttu-id="6185c-135">Wersja **oryginalnego** wiersza wszystkich niezmienionych, zmodyfikowanychi usuniętych wierszy.</span><span class="sxs-lookup"><span data-stu-id="6185c-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="6185c-136">**Bez zmian**</span><span class="sxs-lookup"><span data-stu-id="6185c-136">**Unchanged**</span></span>|<span data-ttu-id="6185c-137">Wersja **bieżącego** wiersza wszystkich niezmienionych wierszy.</span><span class="sxs-lookup"><span data-stu-id="6185c-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="6185c-138">Aby uzyskać więcej informacji o Stanach wierszy i wersjach wierszy, zobacz [Stany wiersza i wersje wierszy](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="6185c-138">For more information about row states and row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="6185c-139">Poniższy przykład kodu tworzy widok, który pokazuje wszystkie produkty, w których liczba jednostek w magazynie jest mniejsza lub równa poziomowi zmiany kolejności, posortowane najpierw według identyfikatora dostawcy, a następnie według nazwy produktu.</span><span class="sxs-lookup"><span data-stu-id="6185c-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6185c-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6185c-140">See also</span></span>

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="6185c-141">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="6185c-141">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="6185c-142">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="6185c-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
