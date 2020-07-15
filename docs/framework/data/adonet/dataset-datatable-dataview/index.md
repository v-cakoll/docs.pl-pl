---
title: Elementy DataSet, DataTable i DataView
description: Zapoznaj się z kilkoma sposobami pracy z zestawem danych ADO.NET, czyli reprezentacją pamięci, która zapewnia spójny relacyjny model programowania.
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 53e12f701b9be1938d62f46bbeb6e63d95c03386
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374510"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="a7d24-103">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="a7d24-103">DataSets, DataTables, and DataViews</span></span>

<span data-ttu-id="a7d24-104">ADO.NET <xref:System.Data.DataSet> to reprezentacja danych znajdujących się w pamięci, która zapewnia spójny relacyjny model programowania niezależnie od źródła danych, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="a7d24-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="a7d24-105"><xref:System.Data.DataSet>Reprezentuje kompletny zestaw danych, w tym tabele, które zawierają, porządkują i ograniczają dane, a także relacje między tabelami.</span><span class="sxs-lookup"><span data-stu-id="a7d24-105">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
<span data-ttu-id="a7d24-106">Istnieje kilka sposobów pracy z <xref:System.Data.DataSet> , które mogą być stosowane niezależnie lub w połączeniu.</span><span class="sxs-lookup"><span data-stu-id="a7d24-106">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="a7d24-107">Możesz:</span><span class="sxs-lookup"><span data-stu-id="a7d24-107">You can:</span></span>  
  
- <span data-ttu-id="a7d24-108"><xref:System.Data.DataTable>Programowe tworzenie, <xref:System.Data.DataRelation> , i <xref:System.Data.Constraint> wewnątrz <xref:System.Data.DataSet> i wypełnianie tabel danymi.</span><span class="sxs-lookup"><span data-stu-id="a7d24-108">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="a7d24-109">Wypełnij <xref:System.Data.DataSet> tabele danych z istniejącego relacyjnego źródła danych przy użyciu `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="a7d24-109">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="a7d24-110">Ładowanie i utrwalanie <xref:System.Data.DataSet> zawartości przy użyciu XML.</span><span class="sxs-lookup"><span data-stu-id="a7d24-110">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="a7d24-111">Aby uzyskać więcej informacji, zobacz [Używanie języka XML w zestawie danych](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="a7d24-111">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
<span data-ttu-id="a7d24-112">Silnie wpisaną <xref:System.Data.DataSet> można również transportować za pomocą usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="a7d24-112">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="a7d24-113">Projekt <xref:System.Data.DataSet> ułatwia transportowanie danych przy użyciu usług sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="a7d24-113">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="a7d24-114">Aby zapoznać się z omówieniem usług sieci Web XML, zobacz [Omówienie usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a7d24-114">For an overview of XML Web services, see [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="a7d24-115">Przykład korzystania z <xref:System.Data.DataSet> usługi sieci Web XML można znaleźć w temacie wykorzystywanie [zestawu danych z usługi sieci Web XML](consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="a7d24-115">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7d24-116">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a7d24-116">In this section</span></span>

 [<span data-ttu-id="a7d24-117">Wskazówki dotyczące bezpieczeństwa</span><span class="sxs-lookup"><span data-stu-id="a7d24-117">Security guidance</span></span>](security-guidance.md)  
 <span data-ttu-id="a7d24-118">Zapewnia wskazówki dotyczące zabezpieczeń dla <xref:System.Data.DataSet> i <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="a7d24-118">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="a7d24-119">Tworzenie elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="a7d24-119">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="a7d24-120">Opisuje składnię tworzenia wystąpienia obiektu <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="a7d24-120">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="a7d24-121">Dodawanie elementu DataTable do elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="a7d24-121">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="a7d24-122">Opisuje sposób tworzenia i dodawania tabel i kolumn do <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="a7d24-122">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="a7d24-123">Dodawanie elementów DataRelation</span><span class="sxs-lookup"><span data-stu-id="a7d24-123">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="a7d24-124">Opisuje sposób tworzenia relacji między tabelami w <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="a7d24-124">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="a7d24-125">Nawigowanie w elementach DataRelation</span><span class="sxs-lookup"><span data-stu-id="a7d24-125">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="a7d24-126">Opisuje sposób użycia relacji między tabelami w a w <xref:System.Data.DataSet> celu zwrócenia podrzędnych lub nadrzędnych wierszy relacji nadrzędny-podrzędny.</span><span class="sxs-lookup"><span data-stu-id="a7d24-126">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="a7d24-127">Scalanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="a7d24-127">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="a7d24-128">Opisuje sposób scalania zawartości jednej <xref:System.Data.DataSet> <xref:System.Data.DataTable> lub <xref:System.Data.DataRow> tablicy w innej <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="a7d24-128">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="a7d24-129">Kopiowanie zawartości elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="a7d24-129">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="a7d24-130">Opisuje sposób tworzenia kopii programu <xref:System.Data.DataSet> , która może zawierać schemat, a także określone dane.</span><span class="sxs-lookup"><span data-stu-id="a7d24-130">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="a7d24-131">Obsługa zdarzeń elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="a7d24-131">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="a7d24-132">Opisuje zdarzenia a <xref:System.Data.DataSet> i sposobu ich używania.</span><span class="sxs-lookup"><span data-stu-id="a7d24-132">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="a7d24-133">Typizowane elementy DataSet</span><span class="sxs-lookup"><span data-stu-id="a7d24-133">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="a7d24-134">Omawia wpisany typ <xref:System.Data.DataSet> i sposób jego tworzenia i używania.</span><span class="sxs-lookup"><span data-stu-id="a7d24-134">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="a7d24-135">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="a7d24-135">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="a7d24-136">Opisuje sposób tworzenia <xref:System.Data.DataTable> , definiowania schematu i manipulowania danymi.</span><span class="sxs-lookup"><span data-stu-id="a7d24-136">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="a7d24-137">Elementy DataTableReader</span><span class="sxs-lookup"><span data-stu-id="a7d24-137">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="a7d24-138">Opisuje sposób tworzenia i używania <xref:System.Data.DataTableReader> .</span><span class="sxs-lookup"><span data-stu-id="a7d24-138">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="a7d24-139">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="a7d24-139">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="a7d24-140">Opisuje sposób tworzenia i pracy ze `DataViews` zdarzeniami oraz pracy z nim <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="a7d24-140">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="a7d24-141">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="a7d24-141">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="a7d24-142">Opisuje sposób <xref:System.Data.DataSet> interakcji z danymi XML jako źródła danych, w tym ładowanie i utrwalanie zawartości <xref:System.Data.DataSet> w postaci danych XML.</span><span class="sxs-lookup"><span data-stu-id="a7d24-142">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="a7d24-143">Korzystanie z elementu DataSet w usłudze internetowej XML</span><span class="sxs-lookup"><span data-stu-id="a7d24-143">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="a7d24-144">Zawiera opis sposobu tworzenia usługi sieci Web XML, która używa <xref:System.Data.DataSet> do przesyłania danych.</span><span class="sxs-lookup"><span data-stu-id="a7d24-144">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a7d24-145">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a7d24-145">Related sections</span></span>

 [<span data-ttu-id="a7d24-146">Nowości w programie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a7d24-146">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="a7d24-147">Wprowadza funkcje, które są nowe w ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a7d24-147">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="a7d24-148">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a7d24-148">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="a7d24-149">Zawiera wprowadzenie do projektowania i składników ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a7d24-149">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="a7d24-150">Wypełnianie zestawu danych z elementu DataAdapter</span><span class="sxs-lookup"><span data-stu-id="a7d24-150">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="a7d24-151">Opisuje sposób ładowania **zestawu danych** z danymi ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a7d24-151">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="a7d24-152">Aktualizowanie źródeł danych za pomocą elementów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="a7d24-152">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="a7d24-153">Opisuje sposób rozwiązywania zmian w danych w **zestawie** danych z powrotem do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a7d24-153">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="a7d24-154">Dodawanie istniejących ograniczeń do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="a7d24-154">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="a7d24-155">Opisuje sposób wypełniania **zestawu danych** z informacjami o kluczu podstawowym ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a7d24-155">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d24-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7d24-156">See also</span></span>

- [<span data-ttu-id="a7d24-157">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a7d24-157">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="a7d24-158">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a7d24-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
