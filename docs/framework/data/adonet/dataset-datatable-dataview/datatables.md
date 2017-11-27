---
title: DataTables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d1222d3df30bf2b3de1761b8fa5c702dc687d0a0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="datatables"></a><span data-ttu-id="c5143-102">DataTables</span><span class="sxs-lookup"><span data-stu-id="c5143-102">DataTables</span></span>
<span data-ttu-id="c5143-103">A <xref:System.Data.DataSet> składa się z kolekcją tabel, zależności i ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="c5143-103">A <xref:System.Data.DataSet> is made up of a collection of tables, relationships, and constraints.</span></span> <span data-ttu-id="c5143-104">W ADO.NET <xref:System.Data.DataTable> obiekty są wykorzystywane do reprezentowania tabele w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="c5143-104">In ADO.NET, <xref:System.Data.DataTable> objects are used to represent the tables in a **DataSet**.</span></span> <span data-ttu-id="c5143-105">A **DataTable** reprezentuje jednej tabeli w pamięci danych relacyjnych; dane są lokalne. Aplikacji opartej na sieci, w którym znajduje się, lecz można wypełniać ze źródła danych, takich jak Microsoft SQL Server przy użyciu **element DataAdapter** uzyskać więcej informacji, zobacz [wypełnianie zestawu danych z element DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md) .</span><span class="sxs-lookup"><span data-stu-id="c5143-105">A **DataTable** represents one table of in-memory relational data; the data is local to the .NET-based application in which it resides, but can be populated from a data source such as Microsoft SQL Server using a **DataAdapter** For more information, see [Populating a DataSet from a DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md).</span></span>  
  
 <span data-ttu-id="c5143-106">**DataTable** klasa jest elementem członkowskim **system.dane** przestrzeni nazw w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5143-106">The **DataTable** class is a member of the **System.Data** namespace within the .NET Framework class library.</span></span> <span data-ttu-id="c5143-107">Można tworzyć i używać **DataTable** niezależnie lub jako członek **DataSet**, i **DataTable** obiekty mogą być również używane w połączeniu z innymi obiektami środowiska .NET Framework w tym <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="c5143-107">You can create and use a **DataTable** independently or as a member of a **DataSet**, and **DataTable** objects can also be used in conjunction with other .NET Framework objects, including the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="c5143-108">Możesz uzyskać dostępu do kolekcji tabel w **zestawu danych** za pośrednictwem **tabel** właściwość **DataSet** obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5143-108">You access the collection of tables in a **DataSet** through the **Tables** property of the **DataSet** object.</span></span>  
  
 <span data-ttu-id="c5143-109">Schemat lub struktura tabeli jest reprezentowana przez kolumn i ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="c5143-109">The schema, or structure of a table is represented by columns and constraints.</span></span> <span data-ttu-id="c5143-110">Zdefiniuj schemat **DataTable** przy użyciu <xref:System.Data.DataColumn> obiektów oraz <xref:System.Data.ForeignKeyConstraint> i <xref:System.Data.UniqueConstraint> obiektów.</span><span class="sxs-lookup"><span data-stu-id="c5143-110">You define the schema of a **DataTable** using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="c5143-111">Kolumn w tabeli można mapować do kolumn w źródle danych, zawierać obliczone wartości w wyrażeniach, automatycznie zwiększyć ich wartości lub wartości klucza podstawowego.</span><span class="sxs-lookup"><span data-stu-id="c5143-111">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="c5143-112">Oprócz schemat **DataTable** musi mieć również wierszy, które zawierają i kolejność danych.</span><span class="sxs-lookup"><span data-stu-id="c5143-112">In addition to a schema, a **DataTable** must also have rows to contain and order data.</span></span> <span data-ttu-id="c5143-113"><xref:System.Data.DataRow> Klasa reprezentuje rzeczywisty danych zawartych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="c5143-113">The <xref:System.Data.DataRow> class represents the actual data contained in a table.</span></span> <span data-ttu-id="c5143-114">Możesz użyć **DataRow** i jego właściwości i metody, aby pobrać, oceny i manipulowanie danymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="c5143-114">You use the **DataRow** and its properties and methods to retrieve, evaluate, and manipulate the data in a table.</span></span> <span data-ttu-id="c5143-115">Jak dostępu i zmiany danych w wierszu, a **DataRow** obiekt zachowuje jego bieżące i oryginalne stanu.</span><span class="sxs-lookup"><span data-stu-id="c5143-115">As you access and change the data within a row, the **DataRow** object maintains both its current and original state.</span></span>  
  
 <span data-ttu-id="c5143-116">Nadrzędny podrzędny można utworzyć relacji między tabelami, używając jednego lub więcej powiązanych kolumn w tabelach.</span><span class="sxs-lookup"><span data-stu-id="c5143-116">You can create parent-child relationships between tables using one or more related columns in the tables.</span></span> <span data-ttu-id="c5143-117">Utwórz relację między **DataTable** obiektów przy użyciu <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="c5143-117">You create a relationship between **DataTable** objects using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="c5143-118">**DataRelation** obiektów następnie może służyć do zwrócenia powiązane podrzędnej lub nadrzędnej wiersze określonego wiersza.</span><span class="sxs-lookup"><span data-stu-id="c5143-118">**DataRelation** objects can then be used to return the related child or parent rows of a particular row.</span></span> <span data-ttu-id="c5143-119">Aby uzyskać więcej informacji, zobacz [Dodawanie DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="c5143-119">For more information, see [Adding DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c5143-120">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c5143-120">In This Section</span></span>  
 [<span data-ttu-id="c5143-121">Tworzenie DataTable</span><span class="sxs-lookup"><span data-stu-id="c5143-121">Creating a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datatable.md)  
 <span data-ttu-id="c5143-122">Wyjaśnia sposób tworzenia **DataTable** i dodaj go do **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="c5143-122">Explains how to create a **DataTable** and add it to a **DataSet**.</span></span>  
  
 [<span data-ttu-id="c5143-123">Definicja schematu tabeli DataTable</span><span class="sxs-lookup"><span data-stu-id="c5143-123">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 <span data-ttu-id="c5143-124">Informacje na temat tworzenia i używania **DataColumn** obiektów i ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="c5143-124">Provides information about creating and using **DataColumn** objects and constraints.</span></span>  
  
 [<span data-ttu-id="c5143-125">Manipulowanie danymi w DataTable</span><span class="sxs-lookup"><span data-stu-id="c5143-125">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="c5143-126">Opisano sposób dodawania, modyfikowania i usuwania danych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="c5143-126">Explains how to add, modify, and delete data in a table.</span></span> <span data-ttu-id="c5143-127">Wyjaśniono, jak używać **DataTable** zdarzeń w celu zbadania zmian danych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="c5143-127">Explains how to use **DataTable** events to examine changes to data in the table.</span></span>  
  
 [<span data-ttu-id="c5143-128">Obsługa zdarzeń DataTable</span><span class="sxs-lookup"><span data-stu-id="c5143-128">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 <span data-ttu-id="c5143-129">Zawiera informacje o zdarzeniach, które są dostępne do użycia z **DataTable**, w tym zdarzenia, gdy wartości w kolumnach są modyfikowane, a wiersze są dodawane lub usuwane.</span><span class="sxs-lookup"><span data-stu-id="c5143-129">Provides information about the events available for use with a **DataTable**, including events when column values are modified and rows are added or deleted.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c5143-130">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c5143-130">Related Sections</span></span>  
 [<span data-ttu-id="c5143-131">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c5143-131">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="c5143-132">W tym artykule opisano ADO.NET architektury i składników oraz sposób ich używać do dostęp do istniejących źródeł danych i zarządzanie danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c5143-132">Describes the ADO.NET architecture and components, and how to use them to access existing data sources and manage application data.</span></span>  
  
 [<span data-ttu-id="c5143-133">Zbiory danych, DataTables i DataViews</span><span class="sxs-lookup"><span data-stu-id="c5143-133">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="c5143-134">Informacje na temat ADO.NET **DataSet** łącznie ze sposobem tworzenia relacji między tabelami.</span><span class="sxs-lookup"><span data-stu-id="c5143-134">Provides information about the ADO.NET **DataSet** including how to create relationships between tables.</span></span>  
  
 <xref:System.Data.Constraint>  
 <span data-ttu-id="c5143-135">Zawiera informacje na temat **ograniczenia** obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5143-135">Provides reference information about the **Constraint** object.</span></span>  
  
 <xref:System.Data.DataColumn>  
 <span data-ttu-id="c5143-136">Zawiera informacje na temat **DataColumn** obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5143-136">Provides reference information about the **DataColumn** object.</span></span>  
  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="c5143-137">Zawiera informacje na temat **DataSet** obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5143-137">Provides reference information about the **DataSet** object.</span></span>  
  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="c5143-138">Zawiera informacje na temat **DataTable** obiektu.</span><span class="sxs-lookup"><span data-stu-id="c5143-138">Provides reference information about the **DataTable** object.</span></span>  
  
 [<span data-ttu-id="c5143-139">Przegląd biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="c5143-139">Class Library Overview</span></span>](../../../../../docs/standard/class-library-overview.md)  
 <span data-ttu-id="c5143-140">Zawiera omówienie bibliotece klas programu .NET Framework w tym **systemu** przestrzeni nazw oraz jego nazw drugiego poziomu **system.dane**.</span><span class="sxs-lookup"><span data-stu-id="c5143-140">Provides an overview of the .NET Framework class library, including the **System** namespace as well as its second-level namespace, **System.Data**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5143-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5143-141">See Also</span></span>  
 [<span data-ttu-id="c5143-142">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="c5143-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
