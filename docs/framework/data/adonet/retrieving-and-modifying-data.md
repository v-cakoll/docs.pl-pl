---
title: Pobieranie i modyfikowanie danych ADO.NET
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 78012a6a5ecdfac0e4cd7c4939ae3ab0036ab716
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782850"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="96573-102">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="96573-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="96573-103">Podstawowa funkcja dowolnej aplikacji bazy danych nawiązuje połączenie ze źródłem danych i pobiera dane, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="96573-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="96573-104">.NET Framework dostawcy danych ADO.NET służy jako Most między aplikacją a źródłem danych, co umożliwia wykonywanie poleceń oraz pobieranie danych przy użyciu elementu **DataReader** lub **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="96573-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="96573-105">Kluczową funkcją dowolnej aplikacji bazy danych jest możliwość aktualizowania danych przechowywanych w bazie danych programu.</span><span class="sxs-lookup"><span data-stu-id="96573-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="96573-106">W ADO.NET, aktualizowanie danych obejmuje użycie obiektów **DataAdapter** i <xref:System.Data.DataSet> **i i** może również wymagać korzystania z transakcji.</span><span class="sxs-lookup"><span data-stu-id="96573-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96573-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="96573-107">In This Section</span></span>  
 [<span data-ttu-id="96573-108">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="96573-108">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)  
 <span data-ttu-id="96573-109">Opisuje sposób nawiązywania połączenia ze źródłem danych i sposobu pracy ze zdarzeniami połączenia.</span><span class="sxs-lookup"><span data-stu-id="96573-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="96573-110">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="96573-110">Connection Strings</span></span>](connection-strings.md)  
 <span data-ttu-id="96573-111">Zawiera tematy opisujące różne aspekty używania parametrów połączenia, w tym słowa kluczowe parametrów połączenia, informacje zabezpieczające i przechowywania i pobierania.</span><span class="sxs-lookup"><span data-stu-id="96573-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="96573-112">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="96573-112">Connection Pooling</span></span>](connection-pooling.md)  
 <span data-ttu-id="96573-113">Opisuje pule połączeń dla dostawców danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="96573-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="96573-114">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="96573-114">Commands and Parameters</span></span>](commands-and-parameters.md)  
 <span data-ttu-id="96573-115">Zawiera tematy opisujące sposób tworzenia poleceń i konstruktorów poleceń, konfigurowania parametrów oraz wykonywania poleceń w celu pobierania i modyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="96573-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="96573-116">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="96573-116">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)  
 <span data-ttu-id="96573-117">Zawiera tematy opisujące operacje odczytujące, dataadaptery, parametry, obsługa zdarzeń DataAdapter i wykonywanie operacji wsadowych.</span><span class="sxs-lookup"><span data-stu-id="96573-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="96573-118">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="96573-118">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)  
 <span data-ttu-id="96573-119">Zawiera tematy opisujące sposób wykonywania transakcji lokalnych, transakcji rozproszonych i pracy z optymistyczną współbieżnością.</span><span class="sxs-lookup"><span data-stu-id="96573-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="96573-120">Pobieranie tożsamości lub wartości automatycznych numerów</span><span class="sxs-lookup"><span data-stu-id="96573-120">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="96573-121">Zawiera przykład mapowania wartości wygenerowanych dla kolumny **tożsamości** w tabeli SQL Server lub dla pola **AutoNumber** w tabeli programu Microsoft Access do kolumny wstawionego wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="96573-121">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="96573-122">Omawia scalanie wartości tożsamości w `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="96573-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="96573-123">Pobieranie danych binarnych</span><span class="sxs-lookup"><span data-stu-id="96573-123">Retrieving Binary Data</span></span>](retrieving-binary-data.md)  
 <span data-ttu-id="96573-124">Opisuje sposób pobierania danych binarnych lub dużych struktur danych przy `CommandBehavior`użyciu programu.`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="96573-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="96573-125">Aby zmodyfikować zachowanie `DataReader`domyślne.</span><span class="sxs-lookup"><span data-stu-id="96573-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="96573-126">Modyfikowanie danych za pomocą procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="96573-126">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="96573-127">Opisuje, jak używać parametrów wejściowych procedury składowanej i parametrów wyjściowych, aby wstawić wiersz w bazie danych, zwracając nową wartość tożsamości.</span><span class="sxs-lookup"><span data-stu-id="96573-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="96573-128">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="96573-128">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)  
 <span data-ttu-id="96573-129">Opisuje sposób uzyskiwania dostępnych baz danych lub wykazów, tabel i widoków w bazie danych, ograniczeń istniejących dla tabel oraz innych informacji o schemacie ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="96573-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="96573-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="96573-130">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="96573-131">Opisuje model fabryki dostawców i pokazuje, jak używać klas bazowych w `System.Data.Common` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96573-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="96573-132">Śledzenie danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="96573-132">Data Tracing in ADO.NET</span></span>](data-tracing.md)  
 <span data-ttu-id="96573-133">Opisuje sposób, w jaki ADO.NET zapewnia wbudowaną funkcję śledzenia danych.</span><span class="sxs-lookup"><span data-stu-id="96573-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="96573-134">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="96573-134">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="96573-135">Opisuje liczniki wydajności dostępne dla `SqlClient` i `OracleClient`.</span><span class="sxs-lookup"><span data-stu-id="96573-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="96573-136">Programowanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="96573-136">Asynchronous Programming</span></span>](asynchronous-programming.md)  
 <span data-ttu-id="96573-137">Opisuje obsługę ADO.NET w programowaniu asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="96573-137">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="96573-138">Obsługa przesyłania strumieniowego SqlClient</span><span class="sxs-lookup"><span data-stu-id="96573-138">SqlClient Streaming Support</span></span>](sqlclient-streaming-support.md)  
 <span data-ttu-id="96573-139">W tym artykule omówiono sposób pisania aplikacji, które przesyła strumieniowo dane z SQL Server bez całkowitego ładowania w pamięci.</span><span class="sxs-lookup"><span data-stu-id="96573-139">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96573-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96573-140">See also</span></span>

- [<span data-ttu-id="96573-141">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="96573-141">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="96573-142">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="96573-142">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="96573-143">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="96573-143">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- [<span data-ttu-id="96573-144">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="96573-144">SQL Server and ADO.NET</span></span>](./sql/index.md)
- [<span data-ttu-id="96573-145">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="96573-145">ADO.NET Overview</span></span>](ado-net-overview.md)
