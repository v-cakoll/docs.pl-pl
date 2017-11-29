---
title: Zbiory danych, DataTables i DataViews
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 642a81b926262fb8ea95234d90e4c1a0c49ea96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="65ab4-102">Zbiory danych, DataTables i DataViews</span><span class="sxs-lookup"><span data-stu-id="65ab4-102">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="65ab4-103">ADO.NET <xref:System.Data.DataSet> jest rezydentny reprezentację danych, która zapewnia spójny model programowania relacyjne niezależnie od tego źródła danych zawiera.</span><span class="sxs-lookup"><span data-stu-id="65ab4-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="65ab4-104">A <xref:System.Data.DataSet> reprezentuje kompletny zestaw danych w tym tabel, które zawierają, kolejność i Zachowaj dane, jak również relacje między tabelami.</span><span class="sxs-lookup"><span data-stu-id="65ab4-104">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="65ab4-105">Istnieje kilka sposobów pracy z <xref:System.Data.DataSet>, które można stosować niezależnie lub razem.</span><span class="sxs-lookup"><span data-stu-id="65ab4-105">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="65ab4-106">Można:</span><span class="sxs-lookup"><span data-stu-id="65ab4-106">You can:</span></span>  
  
-   <span data-ttu-id="65ab4-107">Programowe tworzenie <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, i <xref:System.Data.Constraint> w <xref:System.Data.DataSet> i wypełnić tabel z danymi.</span><span class="sxs-lookup"><span data-stu-id="65ab4-107">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
-   <span data-ttu-id="65ab4-108">Wypełnij <xref:System.Data.DataSet> z tabelami danych z istniejącego relacyjne źródła danych przy użyciu `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="65ab4-108">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
-   <span data-ttu-id="65ab4-109">Ładowanie i utrwalić <xref:System.Data.DataSet> zawartości za pomocą języka XML.</span><span class="sxs-lookup"><span data-stu-id="65ab4-109">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="65ab4-110">Aby uzyskać więcej informacji, zobacz [za pomocą XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="65ab4-110">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="65ab4-111">Silnie typizowaną <xref:System.Data.DataSet> również może być transportowane przy użyciu usługi XML sieci Web.</span><span class="sxs-lookup"><span data-stu-id="65ab4-111">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="65ab4-112">Projekt <xref:System.Data.DataSet> to idealny dla transportu danych przy użyciu usług XML sieci Web.</span><span class="sxs-lookup"><span data-stu-id="65ab4-112">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="65ab4-113">Omówienie usług XML sieci Web, zobacz [Omówienie usług XML sieci Web](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span><span class="sxs-lookup"><span data-stu-id="65ab4-113">For an overview of XML Web services, see [XML Web Services Overview](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span></span> <span data-ttu-id="65ab4-114">Na przykład eksploatującego <xref:System.Data.DataSet> usługi XML sieci Web, zobacz temat [korzystających z zestawu danych z usługi XML sieci Web](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="65ab4-114">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="65ab4-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="65ab4-115">In This Section</span></span>  
 [<span data-ttu-id="65ab4-116">Tworzenie zestawu danych</span><span class="sxs-lookup"><span data-stu-id="65ab4-116">Creating a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 <span data-ttu-id="65ab4-117">W tym artykule opisano składnia tworzenia wystąpienia <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="65ab4-117">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="65ab4-118">Dodawanie elementu DataTable z zestawem danych</span><span class="sxs-lookup"><span data-stu-id="65ab4-118">Adding a DataTable to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="65ab4-119">Opisuje sposób tworzenia i dodawanie tabel i kolumn do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="65ab4-119">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="65ab4-120">Dodawanie DataRelations</span><span class="sxs-lookup"><span data-stu-id="65ab4-120">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 <span data-ttu-id="65ab4-121">Opisuje sposób tworzenia relacji między tabelami w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="65ab4-121">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="65ab4-122">Nawigowanie po DataRelations</span><span class="sxs-lookup"><span data-stu-id="65ab4-122">Navigating DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 <span data-ttu-id="65ab4-123">Informacje dotyczące używania relacji między tabelami w <xref:System.Data.DataSet> do zwrócenia wierszy podrzędnej lub nadrzędnej w relacji nadrzędny podrzędny.</span><span class="sxs-lookup"><span data-stu-id="65ab4-123">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="65ab4-124">Scalanie zawartości zestawu danych</span><span class="sxs-lookup"><span data-stu-id="65ab4-124">Merging DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 <span data-ttu-id="65ab4-125">Opisuje sposób scalania zawartość jednej <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataRow> tablicy do innej <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="65ab4-125">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="65ab4-126">Kopiowanie zawartości zestawu danych</span><span class="sxs-lookup"><span data-stu-id="65ab4-126">Copying DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 <span data-ttu-id="65ab4-127">Opisuje sposób tworzenia kopii <xref:System.Data.DataSet> zawierających schematu, a także określonych danych.</span><span class="sxs-lookup"><span data-stu-id="65ab4-127">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="65ab4-128">Obsługa zdarzeń zestawu danych</span><span class="sxs-lookup"><span data-stu-id="65ab4-128">Handling DataSet Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 <span data-ttu-id="65ab4-129">Opisuje zdarzenia z <xref:System.Data.DataSet> i sposobu ich używania.</span><span class="sxs-lookup"><span data-stu-id="65ab4-129">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="65ab4-130">Typizowane zbiory danych</span><span class="sxs-lookup"><span data-stu-id="65ab4-130">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 <span data-ttu-id="65ab4-131">W tym artykule omówiono jakiego typu <xref:System.Data.DataSet> jest i jak utworzyć i użyć go.</span><span class="sxs-lookup"><span data-stu-id="65ab4-131">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="65ab4-132">DataTables</span><span class="sxs-lookup"><span data-stu-id="65ab4-132">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="65ab4-133">Opisuje sposób tworzenia <xref:System.Data.DataTable>, zdefiniować schemat i manipulowanie danymi.</span><span class="sxs-lookup"><span data-stu-id="65ab4-133">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="65ab4-134">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="65ab4-134">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 <span data-ttu-id="65ab4-135">Opisuje sposób tworzenia i używania <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="65ab4-135">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="65ab4-136">DataViews</span><span class="sxs-lookup"><span data-stu-id="65ab4-136">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="65ab4-137">Opisuje sposób tworzenia i pracy z `DataViews` i pracować z <xref:System.Data.DataView> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="65ab4-137">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="65ab4-138">Za pomocą języka XML w zestawie danych</span><span class="sxs-lookup"><span data-stu-id="65ab4-138">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="65ab4-139">Opisuje sposób <xref:System.Data.DataSet> współdziała z językiem XML jako źródło danych, w tym ładowanie i przechowywanie zawartości <xref:System.Data.DataSet> danych XML.</span><span class="sxs-lookup"><span data-stu-id="65ab4-139">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="65ab4-140">Korzystanie z zestawu danych z usługi sieci Web XML</span><span class="sxs-lookup"><span data-stu-id="65ab4-140">Consuming a DataSet from an XML Web Service</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="65ab4-141">Opisuje sposób tworzenia usługi XML sieci Web, która używa <xref:System.Data.DataSet> danych transportu.</span><span class="sxs-lookup"><span data-stu-id="65ab4-141">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="65ab4-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="65ab4-142">Related Sections</span></span>  
 [<span data-ttu-id="65ab4-143">What's New in ADO.NET</span><span class="sxs-lookup"><span data-stu-id="65ab4-143">What's New in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/whats-new.md)  
 <span data-ttu-id="65ab4-144">Zawiera funkcje, które są nowością w programie ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="65ab4-144">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="65ab4-145">ADO.NET — omówienie</span><span class="sxs-lookup"><span data-stu-id="65ab4-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 <span data-ttu-id="65ab4-146">Wprowadzenie do projektowania i składniki ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="65ab4-146">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="65ab4-147">Wypełnianie zestawu danych z element DataAdapter</span><span class="sxs-lookup"><span data-stu-id="65ab4-147">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="65ab4-148">Opisuje sposób załadować **DataSet** z danymi ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="65ab4-148">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="65ab4-149">Aktualizowanie źródła danych za pomocą obiektów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="65ab4-149">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="65ab4-150">Opisuje sposób rozwiązania zmiany danych w **DataSet** do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="65ab4-150">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="65ab4-151">Dodawanie istniejących ograniczeń do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="65ab4-151">Adding Existing Constraints to a DataSet</span></span>](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="65ab4-152">Opisuje sposób wypełnienia **DataSet** o informacje o kluczu podstawowym ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="65ab4-152">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ab4-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65ab4-153">See Also</span></span>  
 [<span data-ttu-id="65ab4-154">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="65ab4-154">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="65ab4-155">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="65ab4-155">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
