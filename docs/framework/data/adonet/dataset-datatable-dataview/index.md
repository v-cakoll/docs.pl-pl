---
title: Elementy DataSet, DataTable i DataView
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 5fe09601be7173fd1a9228dc090732ded7afdd90
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="ea441-102">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="ea441-102">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="ea441-103">ADO.NET <xref:System.Data.DataSet> jest rezydentny reprezentację danych, która zapewnia spójny model programowania relacyjne niezależnie od tego źródła danych zawiera.</span><span class="sxs-lookup"><span data-stu-id="ea441-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="ea441-104">A <xref:System.Data.DataSet> reprezentuje kompletny zestaw danych w tym tabel, które zawierają, kolejność i Zachowaj dane, jak również relacje między tabelami.</span><span class="sxs-lookup"><span data-stu-id="ea441-104">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="ea441-105">Istnieje kilka sposobów pracy z <xref:System.Data.DataSet>, które można stosować niezależnie lub razem.</span><span class="sxs-lookup"><span data-stu-id="ea441-105">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="ea441-106">Można:</span><span class="sxs-lookup"><span data-stu-id="ea441-106">You can:</span></span>  
  
-   <span data-ttu-id="ea441-107">Programowe tworzenie <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, i <xref:System.Data.Constraint> w <xref:System.Data.DataSet> i wypełnić tabel z danymi.</span><span class="sxs-lookup"><span data-stu-id="ea441-107">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
-   <span data-ttu-id="ea441-108">Wypełnij <xref:System.Data.DataSet> z tabelami danych z istniejącego relacyjne źródła danych przy użyciu `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="ea441-108">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
-   <span data-ttu-id="ea441-109">Ładowanie i utrwalić <xref:System.Data.DataSet> zawartości za pomocą języka XML.</span><span class="sxs-lookup"><span data-stu-id="ea441-109">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="ea441-110">Aby uzyskać więcej informacji, zobacz [za pomocą XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="ea441-110">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="ea441-111">Silnie typizowaną <xref:System.Data.DataSet> również może być transportowane przy użyciu usługi XML sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ea441-111">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="ea441-112">Projekt <xref:System.Data.DataSet> to idealny dla transportu danych przy użyciu usług XML sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ea441-112">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="ea441-113">Omówienie usług XML sieci Web, zobacz [Omówienie usług XML sieci Web](http://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span><span class="sxs-lookup"><span data-stu-id="ea441-113">For an overview of XML Web services, see [XML Web Services Overview](http://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span></span> <span data-ttu-id="ea441-114">Na przykład eksploatującego <xref:System.Data.DataSet> usługi XML sieci Web, zobacz temat [korzystających z zestawu danych z usługi XML sieci Web](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="ea441-114">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea441-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ea441-115">In This Section</span></span>  
 [<span data-ttu-id="ea441-116">Tworzenie elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="ea441-116">Creating a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 <span data-ttu-id="ea441-117">W tym artykule opisano składnia tworzenia wystąpienia <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ea441-117">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="ea441-118">Dodawanie elementu DataTable do elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="ea441-118">Adding a DataTable to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="ea441-119">Opisuje sposób tworzenia i dodawanie tabel i kolumn do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ea441-119">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="ea441-120">Dodawanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="ea441-120">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 <span data-ttu-id="ea441-121">Opisuje sposób tworzenia relacji między tabelami w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ea441-121">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="ea441-122">Nawigowanie w elementach DataRelation</span><span class="sxs-lookup"><span data-stu-id="ea441-122">Navigating DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 <span data-ttu-id="ea441-123">Informacje dotyczące używania relacji między tabelami w <xref:System.Data.DataSet> do zwrócenia wierszy podrzędnej lub nadrzędnej w relacji nadrzędny podrzędny.</span><span class="sxs-lookup"><span data-stu-id="ea441-123">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="ea441-124">Scalanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="ea441-124">Merging DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 <span data-ttu-id="ea441-125">Opisuje sposób scalania zawartość jednej <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataRow> tablicy do innej <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ea441-125">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="ea441-126">Kopiowanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="ea441-126">Copying DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 <span data-ttu-id="ea441-127">Opisuje sposób tworzenia kopii <xref:System.Data.DataSet> zawierających schematu, a także określonych danych.</span><span class="sxs-lookup"><span data-stu-id="ea441-127">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="ea441-128">Obsługa zdarzeń elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="ea441-128">Handling DataSet Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 <span data-ttu-id="ea441-129">Opisuje zdarzenia z <xref:System.Data.DataSet> i sposobu ich używania.</span><span class="sxs-lookup"><span data-stu-id="ea441-129">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="ea441-130">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="ea441-130">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 <span data-ttu-id="ea441-131">W tym artykule omówiono jakiego typu <xref:System.Data.DataSet> jest i jak utworzyć i użyć go.</span><span class="sxs-lookup"><span data-stu-id="ea441-131">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="ea441-132">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="ea441-132">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="ea441-133">Opisuje sposób tworzenia <xref:System.Data.DataTable>, zdefiniować schemat i manipulowanie danymi.</span><span class="sxs-lookup"><span data-stu-id="ea441-133">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="ea441-134">Elementy DataTableReader</span><span class="sxs-lookup"><span data-stu-id="ea441-134">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 <span data-ttu-id="ea441-135">Opisuje sposób tworzenia i używania <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="ea441-135">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="ea441-136">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="ea441-136">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="ea441-137">Opisuje sposób tworzenia i pracy z `DataViews` i pracować z <xref:System.Data.DataView> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ea441-137">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="ea441-138">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="ea441-138">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="ea441-139">Opisuje sposób <xref:System.Data.DataSet> współdziała z językiem XML jako źródło danych, w tym ładowanie i przechowywanie zawartości <xref:System.Data.DataSet> danych XML.</span><span class="sxs-lookup"><span data-stu-id="ea441-139">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="ea441-140">Korzystanie z elementu DataSet w usłudze internetowej XML</span><span class="sxs-lookup"><span data-stu-id="ea441-140">Consuming a DataSet from an XML Web Service</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="ea441-141">Opisuje sposób tworzenia usługi XML sieci Web, która używa <xref:System.Data.DataSet> danych transportu.</span><span class="sxs-lookup"><span data-stu-id="ea441-141">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ea441-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ea441-142">Related Sections</span></span>  
 [<span data-ttu-id="ea441-143">Nowości w programie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ea441-143">What's New in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/whats-new.md)  
 <span data-ttu-id="ea441-144">Zawiera funkcje, które są nowością w programie ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ea441-144">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="ea441-145">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ea441-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 <span data-ttu-id="ea441-146">Wprowadzenie do projektowania i składniki ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ea441-146">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="ea441-147">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="ea441-147">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="ea441-148">Opisuje sposób załadować **DataSet** z danymi ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ea441-148">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="ea441-149">Aktualizowanie źródeł danych za pomocą elementów DataAdapters</span><span class="sxs-lookup"><span data-stu-id="ea441-149">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="ea441-150">Opisuje sposób rozwiązania zmiany danych w **DataSet** do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ea441-150">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="ea441-151">Dodawanie istniejących ograniczeń do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ea441-151">Adding Existing Constraints to a DataSet</span></span>](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="ea441-152">Opisuje sposób wypełnienia **DataSet** o informacje o kluczu podstawowym ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ea441-152">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea441-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea441-153">See Also</span></span>  
 [<span data-ttu-id="ea441-154">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ea441-154">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="ea441-155">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="ea441-155">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
