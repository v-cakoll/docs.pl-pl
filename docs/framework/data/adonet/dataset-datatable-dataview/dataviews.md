---
title: DataViews
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 26fbae0474253dc9792a0290a36dd52044d148b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="dataviews"></a><span data-ttu-id="b48de-102">DataViews</span><span class="sxs-lookup"><span data-stu-id="b48de-102">DataViews</span></span>
<span data-ttu-id="b48de-103">A <xref:System.Data.DataView> można tworzyć widoki danych przechowywanych w <xref:System.Data.DataTable>, możliwość, która jest często używana w aplikacjach powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="b48de-103">A <xref:System.Data.DataView> enables you to create different views of the data stored in a <xref:System.Data.DataTable>, a capability that is often used in data-binding applications.</span></span> <span data-ttu-id="b48de-104">Przy użyciu **DataView**, można udostępnić dane w tabeli z innego sortowania i dane można filtrować według wierszy stanu lub w oparciu o wyrażenie filtru.</span><span class="sxs-lookup"><span data-stu-id="b48de-104">Using a **DataView**, you can expose the data in a table with different sort orders, and you can filter the data by row state or based on a filter expression.</span></span>  
  
 <span data-ttu-id="b48de-105">A **DataView** udostępnia dynamiczny widok danych podstawowych **DataTable**: zawartość, kolejność i członkostwa odzwierciedlenia zmian w miarę ich występowania.</span><span class="sxs-lookup"><span data-stu-id="b48de-105">A **DataView** provides a dynamic view of data in the underlying **DataTable**: the content, ordering, and membership reflect changes as they occur.</span></span> <span data-ttu-id="b48de-106">To zachowanie różni się od **wybierz** metody **DataTable**, która zwraca <xref:System.Data.DataRow> tablicy z tabeli na podstawie w określonej kolejności filtru i/lub sortowania: thiscontent odzwierciedla zmiany podstawowy w tabeli, ale jego członkostwa i kolejność pozostały niezmienione.</span><span class="sxs-lookup"><span data-stu-id="b48de-106">This behavior differs from the **Select** method of the **DataTable**, which returns a <xref:System.Data.DataRow> array from a table based on a particular filter and/or sort order: thiscontent reflects changes to the underlying table, but its membership and ordering remain static.</span></span> <span data-ttu-id="b48de-107">Dynamiczne możliwości środowiska **DataView** była idealne dla powiązania danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b48de-107">The dynamic capabilities of the **DataView** make it ideal for data-binding applications.</span></span>  
  
 <span data-ttu-id="b48de-108">A **DataView** udostępnia dynamiczny widok jednego zestawu danych, tak jak widok bazy danych, do której można zastosować różne sortowanie i kryteria filtrowania.</span><span class="sxs-lookup"><span data-stu-id="b48de-108">A **DataView** provides you with a dynamic view of a single set of data, much like a database view, to which you can apply different sorting and filtering criteria.</span></span> <span data-ttu-id="b48de-109">W przeciwieństwie do widoku bazy danych, jednak **DataView** nie może być traktowane jako tabelę i nie umożliwia wyświetlanie połączonych tabel.</span><span class="sxs-lookup"><span data-stu-id="b48de-109">Unlike a database view, however, a **DataView** cannot be treated as a table and cannot provide a view of joined tables.</span></span> <span data-ttu-id="b48de-110">Również nie można wykluczyć kolumny, które istnieją w tabeli źródłowej i nie można dodać kolumny, takich jak kolumny obliczeniowej, które nie istnieją w tabeli źródłowej.</span><span class="sxs-lookup"><span data-stu-id="b48de-110">You also cannot exclude columns that exist in the source table, nor can you append columns, such as computational columns, that do not exist in the source table.</span></span>  
  
 <span data-ttu-id="b48de-111">Można użyć <xref:System.Data.DataView.DataViewManager%2A> umożliwia zarządzanie ustawieniami widoku wszystkie tabele w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="b48de-111">You can use a <xref:System.Data.DataView.DataViewManager%2A> to manage view settings for all the tables in a **DataSet**.</span></span> <span data-ttu-id="b48de-112">**DataViewManager** zapewnia wygodny sposób zarządzania domyślne ustawienia widoku dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="b48de-112">The **DataViewManager** provides you with a convenient way to manage default view settings for each table.</span></span> <span data-ttu-id="b48de-113">Podczas tworzenia wiązania formantu więcej niż jednej tabeli **DataSet**, powiązania do **DataViewManager** jest idealnym wyborem.</span><span class="sxs-lookup"><span data-stu-id="b48de-113">When binding a control to more than one table of a **DataSet**, binding to a **DataViewManager** is the ideal choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b48de-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b48de-114">In This Section</span></span>  
 [<span data-ttu-id="b48de-115">Tworzenie elementu DataView</span><span class="sxs-lookup"><span data-stu-id="b48de-115">Creating a DataView</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataview.md)  
 <span data-ttu-id="b48de-116">Opisuje sposób tworzenia **DataView** dla **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="b48de-116">Describes how to create a **DataView** for a **DataTable**.</span></span>  
  
 [<span data-ttu-id="b48de-117">Sortowanie i filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="b48de-117">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 <span data-ttu-id="b48de-118">Opisuje sposób ustawiania właściwości **DataView** zwracanie podzbiorów danych wiersze spełniające kryteria określony filtr lub zwróć dane określony porządek sortowania.</span><span class="sxs-lookup"><span data-stu-id="b48de-118">Describes how to set the properties of a **DataView** to return subsets of data rows meeting specific filter criteria, or to return data in a particular sort order.</span></span>  
  
 [<span data-ttu-id="b48de-119">Elementy DataRow i DataRowView</span><span class="sxs-lookup"><span data-stu-id="b48de-119">DataRows and DataRowViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarows-and-datarowviews.md)  
 <span data-ttu-id="b48de-120">Zawiera opis sposobu uzyskiwania dostępu do danych udostępnianych przez **DataView**.</span><span class="sxs-lookup"><span data-stu-id="b48de-120">Describes how to access the data exposed by the **DataView**.</span></span>  
  
 [<span data-ttu-id="b48de-121">Znajdowanie wierszy</span><span class="sxs-lookup"><span data-stu-id="b48de-121">Finding Rows</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)  
 <span data-ttu-id="b48de-122">Opisuje sposób wyszukiwania określonego wiersza w **DataView**.</span><span class="sxs-lookup"><span data-stu-id="b48de-122">Describes how to find a particular row in a **DataView**.</span></span>  
  
 [<span data-ttu-id="b48de-123">Elementy ChildView i relacje</span><span class="sxs-lookup"><span data-stu-id="b48de-123">ChildViews and Relations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/childviews-and-relations.md)  
 <span data-ttu-id="b48de-124">Opisuje sposób tworzenia widoków danych z relacji nadrzędny podrzędny przy użyciu **DataView**.</span><span class="sxs-lookup"><span data-stu-id="b48de-124">Describes how to create views of data from a parent-child relationship using a **DataView**.</span></span>  
  
 [<span data-ttu-id="b48de-125">Modyfikowanie elementów DataView</span><span class="sxs-lookup"><span data-stu-id="b48de-125">Modifying DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/modifying-dataviews.md)  
 <span data-ttu-id="b48de-126">Opisuje sposób modyfikowania danych podstawowych **DataTable** za pośrednictwem **DataView**, w tym o włączeniu lub wyłączeniu aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="b48de-126">Describes how to modify the data in the underlying **DataTable** via the **DataView**, including enabling or disabling updates.</span></span>  
  
 [<span data-ttu-id="b48de-127">Obsługa zdarzeń elementu DataView</span><span class="sxs-lookup"><span data-stu-id="b48de-127">Handling DataView Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataview-events.md)  
 <span data-ttu-id="b48de-128">Informacje dotyczące używania **ListChanged** zdarzeń, aby otrzymać powiadomienie po zawartości lub kolejność **DataView** jest aktualizowana.</span><span class="sxs-lookup"><span data-stu-id="b48de-128">Describes how to use the **ListChanged** event to receive notification when the contents or order of a **DataView** is being updated.</span></span>  
  
 [<span data-ttu-id="b48de-129">Zarządzanie elementami DataView</span><span class="sxs-lookup"><span data-stu-id="b48de-129">Managing DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/managing-dataviews.md)  
 <span data-ttu-id="b48de-130">Informacje dotyczące używania **DataViewManager** do zarządzania **DataView** ustawienia dla każdej tabeli w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="b48de-130">Describes how to use a **DataViewManager** to manage **DataView** settings for each table in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b48de-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b48de-131">Related Sections</span></span>  
 [<span data-ttu-id="b48de-132">Aplikacje sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b48de-132">ASP.NET Web Applications</span></span>](http://msdn.microsoft.com/en-us/a812d7b7-049e-4234-a4c2-6acf690301f6)  
 <span data-ttu-id="b48de-133">Zawiera przegląd i szczegółowe procedury krok po kroku dotyczące tworzenia aplikacji ASP.NET, formularzy sieci Web i usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b48de-133">Provides overviews and detailed, step-by-step procedures for creating ASP.NET applications, Web Forms, and Web Services.</span></span>  
  
 [<span data-ttu-id="b48de-134">Aplikacje systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b48de-134">Windows Applications</span></span>](http://msdn.microsoft.com/en-us/a6bb2180-09b1-4738-b9fd-7fb05fc92f23)  
 <span data-ttu-id="b48de-135">Zawiera szczegółowe informacje dotyczące pracy z formularzy systemu Windows i aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="b48de-135">Provides detailed information about working with Windows Forms and console applications.</span></span>  
  
 [<span data-ttu-id="b48de-136">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="b48de-136">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="b48de-137">W tym artykule opisano **DataSet** obiektu i jak go używać do zarządzania danymi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b48de-137">Describes the **DataSet** object and how you can use it to manage application data.</span></span>  
  
 [<span data-ttu-id="b48de-138">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="b48de-138">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="b48de-139">W tym artykule opisano **DataTable** obiektu i jak go używać do zarządzania danymi aplikacji, samodzielnie lub w ramach **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="b48de-139">Describes the **DataTable** object and how you can use it to manage application data by itself or as part of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="b48de-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b48de-140">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="b48de-141">W tym artykule opisano ADO.NET architektury i składników oraz sposób ADO.NET umożliwia dostęp do istniejących źródeł danych i zarządzanie danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b48de-141">Describes the ADO.NET architecture and components, and how to use ADO.NET to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b48de-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b48de-142">See Also</span></span>  
 [<span data-ttu-id="b48de-143">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="b48de-143">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
