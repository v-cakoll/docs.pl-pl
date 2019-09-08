---
title: Elementy DataSet, DataTable i DataView
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 1744f6c6d8ea3c28a8dab30c0d201ae1dacc7ee3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786196"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="68335-102">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="68335-102">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="68335-103">ADO.NET <xref:System.Data.DataSet> to reprezentacja danych znajdujących się w pamięci, która zapewnia spójny relacyjny model programowania niezależnie od źródła danych, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="68335-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="68335-104"><xref:System.Data.DataSet> Reprezentuje kompletny zestaw danych, w tym tabele, które zawierają, porządkują i ograniczają dane, a także relacje między tabelami.</span><span class="sxs-lookup"><span data-stu-id="68335-104">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="68335-105">Istnieje kilka sposobów pracy z <xref:System.Data.DataSet>, które mogą być stosowane niezależnie lub w połączeniu.</span><span class="sxs-lookup"><span data-stu-id="68335-105">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="68335-106">Można:</span><span class="sxs-lookup"><span data-stu-id="68335-106">You can:</span></span>  
  
- <span data-ttu-id="68335-107"><xref:System.Data.DataTable>Programowe tworzenie, <xref:System.Data.DataRelation>, i <xref:System.Data.Constraint> wewnątrz <xref:System.Data.DataSet> i wypełnianie tabel danymi.</span><span class="sxs-lookup"><span data-stu-id="68335-107">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="68335-108">Wypełnij tabele danych z istniejącego relacyjnego źródła danych `DataAdapter`przy użyciu. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="68335-108">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="68335-109">Ładowanie i utrwalanie <xref:System.Data.DataSet> zawartości przy użyciu XML.</span><span class="sxs-lookup"><span data-stu-id="68335-109">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="68335-110">Aby uzyskać więcej informacji, zobacz [Używanie języka XML w zestawie danych](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="68335-110">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="68335-111">Silnie wpisaną <xref:System.Data.DataSet> można również transportować za pomocą usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="68335-111">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="68335-112">Projekt <xref:System.Data.DataSet> ułatwia transportowanie danych przy użyciu usług sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="68335-112">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="68335-113">Aby zapoznać się z omówieniem usług sieci Web XML, zobacz [Omówienie usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="68335-113">For an overview of XML Web services, see [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="68335-114">Przykład <xref:System.Data.DataSet> korzystania z usługi sieci Web XML można znaleźć w temacie wykorzystywanie [zestawu danych z usługi sieci Web XML](consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="68335-114">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="68335-115">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="68335-115">In This Section</span></span>  
 [<span data-ttu-id="68335-116">Tworzenie elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="68335-116">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="68335-117">Opisuje składnię tworzenia wystąpienia <xref:System.Data.DataSet>obiektu.</span><span class="sxs-lookup"><span data-stu-id="68335-117">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="68335-118">Dodawanie elementu DataTable do elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="68335-118">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="68335-119">Opisuje sposób tworzenia i dodawania tabel i kolumn do <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="68335-119">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="68335-120">Dodawanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="68335-120">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="68335-121">Opisuje sposób tworzenia relacji między tabelami w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="68335-121">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="68335-122">Nawigowanie w elementach DataRelation</span><span class="sxs-lookup"><span data-stu-id="68335-122">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="68335-123">Opisuje sposób użycia relacji między tabelami w a <xref:System.Data.DataSet> w celu zwrócenia podrzędnych lub nadrzędnych wierszy relacji nadrzędny-podrzędny.</span><span class="sxs-lookup"><span data-stu-id="68335-123">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="68335-124">Scalanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="68335-124">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="68335-125">Opisuje <xref:System.Data.DataSet>sposób scalania zawartości jednej <xref:System.Data.DataTable>lub <xref:System.Data.DataRow> tablicy w innej <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="68335-125">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="68335-126">Kopiowanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="68335-126">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="68335-127">Opisuje sposób tworzenia kopii <xref:System.Data.DataSet> programu, która może zawierać schemat, a także określone dane.</span><span class="sxs-lookup"><span data-stu-id="68335-127">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="68335-128">Obsługa zdarzeń elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="68335-128">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="68335-129">Opisuje zdarzenia <xref:System.Data.DataSet> a i sposobu ich używania.</span><span class="sxs-lookup"><span data-stu-id="68335-129">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="68335-130">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="68335-130">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="68335-131">Omawia wpisany typ <xref:System.Data.DataSet> i sposób jego tworzenia i używania.</span><span class="sxs-lookup"><span data-stu-id="68335-131">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="68335-132">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="68335-132">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="68335-133">Opisuje sposób tworzenia <xref:System.Data.DataTable>, definiowania schematu i manipulowania danymi.</span><span class="sxs-lookup"><span data-stu-id="68335-133">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="68335-134">Elementy DataTableReader</span><span class="sxs-lookup"><span data-stu-id="68335-134">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="68335-135">Opisuje sposób tworzenia i używania <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="68335-135">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="68335-136">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="68335-136">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="68335-137">Opisuje sposób tworzenia i pracy `DataViews` ze zdarzeniami oraz pracy z <xref:System.Data.DataView> nim.</span><span class="sxs-lookup"><span data-stu-id="68335-137">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="68335-138">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="68335-138">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="68335-139">Opisuje sposób <xref:System.Data.DataSet> interakcji z danymi XML jako źródła danych, w tym ładowanie i utrwalanie zawartości <xref:System.Data.DataSet> w postaci danych XML.</span><span class="sxs-lookup"><span data-stu-id="68335-139">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="68335-140">Korzystanie z elementu DataSet w usłudze internetowej XML</span><span class="sxs-lookup"><span data-stu-id="68335-140">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="68335-141">Zawiera opis sposobu tworzenia usługi sieci Web XML, która używa <xref:System.Data.DataSet> do przesyłania danych.</span><span class="sxs-lookup"><span data-stu-id="68335-141">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="68335-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="68335-142">Related Sections</span></span>  
 [<span data-ttu-id="68335-143">Nowości w programie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="68335-143">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="68335-144">Wprowadza funkcje, które są nowe w ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="68335-144">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="68335-145">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="68335-145">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="68335-146">Zawiera wprowadzenie do projektowania i składników ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="68335-146">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="68335-147">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="68335-147">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="68335-148">Opisuje sposób ładowania **zestawu danych** z danymi ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="68335-148">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="68335-149">Aktualizowanie źródeł danych za pomocą elementów DataAdapters</span><span class="sxs-lookup"><span data-stu-id="68335-149">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="68335-150">Opisuje sposób rozwiązywania zmian w danych w **zestawie** danych z powrotem do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="68335-150">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="68335-151">Dodawanie istniejących ograniczeń do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="68335-151">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="68335-152">Opisuje sposób wypełniania **zestawu danych** z informacjami o kluczu podstawowym ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="68335-152">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68335-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68335-153">See also</span></span>

- [<span data-ttu-id="68335-154">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="68335-154">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="68335-155">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="68335-155">ADO.NET Overview</span></span>](../ado-net-overview.md)
