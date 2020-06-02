---
title: Elementy DataSet, DataTable i DataView
description: Zapoznaj się z kilkoma sposobami pracy z zestawem danych ADO.NET, czyli reprezentacją pamięci, która zapewnia spójny relacyjny model programowania.
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: f6562452261cbc1f7ee36fb264b858646a42e4f5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286898"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="1b3f5-103">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="1b3f5-103">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="1b3f5-104">ADO.NET <xref:System.Data.DataSet> to reprezentacja danych znajdujących się w pamięci, która zapewnia spójny relacyjny model programowania niezależnie od źródła danych, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="1b3f5-105"><xref:System.Data.DataSet>Reprezentuje kompletny zestaw danych, w tym tabele, które zawierają, porządkują i ograniczają dane, a także relacje między tabelami.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-105">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="1b3f5-106">Istnieje kilka sposobów pracy z <xref:System.Data.DataSet> , które mogą być stosowane niezależnie lub w połączeniu.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-106">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="1b3f5-107">Dostępne możliwości:</span><span class="sxs-lookup"><span data-stu-id="1b3f5-107">You can:</span></span>  
  
- <span data-ttu-id="1b3f5-108"><xref:System.Data.DataTable>Programowe tworzenie, <xref:System.Data.DataRelation> , i <xref:System.Data.Constraint> wewnątrz <xref:System.Data.DataSet> i wypełnianie tabel danymi.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-108">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="1b3f5-109">Wypełnij <xref:System.Data.DataSet> tabele danych z istniejącego relacyjnego źródła danych przy użyciu `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="1b3f5-109">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="1b3f5-110">Ładowanie i utrwalanie <xref:System.Data.DataSet> zawartości przy użyciu XML.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-110">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="1b3f5-111">Aby uzyskać więcej informacji, zobacz [Używanie języka XML w zestawie danych](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="1b3f5-111">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="1b3f5-112">Silnie wpisaną <xref:System.Data.DataSet> można również transportować za pomocą usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-112">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="1b3f5-113">Projekt <xref:System.Data.DataSet> ułatwia transportowanie danych przy użyciu usług sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-113">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="1b3f5-114">Aby zapoznać się z omówieniem usług sieci Web XML, zobacz [Omówienie usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1b3f5-114">For an overview of XML Web services, see [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="1b3f5-115">Przykład korzystania z <xref:System.Data.DataSet> usługi sieci Web XML można znaleźć w temacie wykorzystywanie [zestawu danych z usługi sieci Web XML](consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="1b3f5-115">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b3f5-116">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1b3f5-116">In This Section</span></span>  
 [<span data-ttu-id="1b3f5-117">Tworzenie elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="1b3f5-117">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="1b3f5-118">Opisuje składnię tworzenia wystąpienia obiektu <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="1b3f5-118">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="1b3f5-119">Dodawanie elementu DataTable do elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="1b3f5-119">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="1b3f5-120">Opisuje sposób tworzenia i dodawania tabel i kolumn do <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="1b3f5-120">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="1b3f5-121">Dodawanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="1b3f5-121">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="1b3f5-122">Opisuje sposób tworzenia relacji między tabelami w <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="1b3f5-122">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="1b3f5-123">Nawigowanie w elementach DataRelation</span><span class="sxs-lookup"><span data-stu-id="1b3f5-123">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="1b3f5-124">Opisuje sposób użycia relacji między tabelami w a w <xref:System.Data.DataSet> celu zwrócenia podrzędnych lub nadrzędnych wierszy relacji nadrzędny-podrzędny.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-124">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="1b3f5-125">Scalanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="1b3f5-125">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="1b3f5-126">Opisuje sposób scalania zawartości jednej <xref:System.Data.DataSet> <xref:System.Data.DataTable> lub <xref:System.Data.DataRow> tablicy w innej <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="1b3f5-126">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="1b3f5-127">Kopiowanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="1b3f5-127">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="1b3f5-128">Opisuje sposób tworzenia kopii programu <xref:System.Data.DataSet> , która może zawierać schemat, a także określone dane.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-128">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="1b3f5-129">Obsługa zdarzeń elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="1b3f5-129">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="1b3f5-130">Opisuje zdarzenia a <xref:System.Data.DataSet> i sposobu ich używania.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-130">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="1b3f5-131">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="1b3f5-131">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="1b3f5-132">Omawia wpisany typ <xref:System.Data.DataSet> i sposób jego tworzenia i używania.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-132">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="1b3f5-133">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="1b3f5-133">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="1b3f5-134">Opisuje sposób tworzenia <xref:System.Data.DataTable> , definiowania schematu i manipulowania danymi.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-134">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="1b3f5-135">Elementy DataTableReader</span><span class="sxs-lookup"><span data-stu-id="1b3f5-135">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="1b3f5-136">Opisuje sposób tworzenia i używania <xref:System.Data.DataTableReader> .</span><span class="sxs-lookup"><span data-stu-id="1b3f5-136">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="1b3f5-137">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="1b3f5-137">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="1b3f5-138">Opisuje sposób tworzenia i pracy ze `DataViews` zdarzeniami oraz pracy z nim <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="1b3f5-138">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="1b3f5-139">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="1b3f5-139">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="1b3f5-140">Opisuje sposób <xref:System.Data.DataSet> interakcji z danymi XML jako źródła danych, w tym ładowanie i utrwalanie zawartości <xref:System.Data.DataSet> w postaci danych XML.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-140">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="1b3f5-141">Korzystanie z elementu DataSet w usłudze internetowej XML</span><span class="sxs-lookup"><span data-stu-id="1b3f5-141">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="1b3f5-142">Zawiera opis sposobu tworzenia usługi sieci Web XML, która używa <xref:System.Data.DataSet> do przesyłania danych.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-142">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1b3f5-143">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="1b3f5-143">Related Sections</span></span>  
 [<span data-ttu-id="1b3f5-144">Nowości w programie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1b3f5-144">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="1b3f5-145">Wprowadza funkcje, które są nowe w ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-145">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="1b3f5-146">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1b3f5-146">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="1b3f5-147">Zawiera wprowadzenie do projektowania i składników ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-147">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="1b3f5-148">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="1b3f5-148">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="1b3f5-149">Opisuje sposób ładowania **zestawu danych** z danymi ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-149">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="1b3f5-150">Aktualizowanie źródeł danych za pomocą elementów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="1b3f5-150">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="1b3f5-151">Opisuje sposób rozwiązywania zmian w danych w **zestawie** danych z powrotem do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-151">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="1b3f5-152">Dodawanie istniejących ograniczeń do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="1b3f5-152">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="1b3f5-153">Opisuje sposób wypełniania **zestawu danych** z informacjami o kluczu podstawowym ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1b3f5-153">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b3f5-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b3f5-154">See also</span></span>

- [<span data-ttu-id="1b3f5-155">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1b3f5-155">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="1b3f5-156">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1b3f5-156">ADO.NET Overview</span></span>](../ado-net-overview.md)
