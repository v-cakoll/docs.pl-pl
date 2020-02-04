---
title: Pobieranie i modyfikowanie danych
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 65c373ecff004e219527754bf2e9cc56837dc305
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980057"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="c04b7-102">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c04b7-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="c04b7-103">Podstawowa funkcja dowolnej aplikacji bazy danych nawiązuje połączenie ze źródłem danych i pobiera dane, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="c04b7-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="c04b7-104">.NET Framework dostawcy danych ADO.NET służy jako Most między aplikacją a źródłem danych, co umożliwia wykonywanie poleceń oraz pobieranie danych przy użyciu elementu **DataReader** lub **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="c04b7-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="c04b7-105">Kluczową funkcją dowolnej aplikacji bazy danych jest możliwość aktualizowania danych przechowywanych w bazie danych programu.</span><span class="sxs-lookup"><span data-stu-id="c04b7-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="c04b7-106">W ADO.NET, aktualizowanie danych odbywa się przy użyciu obiektów **DataAdapter** i <xref:System.Data.DataSet>, a następnie obiekty **poleceń** ; może również wymagać korzystania z transakcji.</span><span class="sxs-lookup"><span data-stu-id="c04b7-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c04b7-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c04b7-107">In This Section</span></span>  
 [<span data-ttu-id="c04b7-108">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="c04b7-108">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)  
 <span data-ttu-id="c04b7-109">Opisuje sposób nawiązywania połączenia ze źródłem danych i sposobu pracy ze zdarzeniami połączenia.</span><span class="sxs-lookup"><span data-stu-id="c04b7-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="c04b7-110">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="c04b7-110">Connection Strings</span></span>](connection-strings.md)  
 <span data-ttu-id="c04b7-111">Zawiera tematy opisujące różne aspekty używania parametrów połączenia, w tym słowa kluczowe parametrów połączenia, informacje zabezpieczające i przechowywania i pobierania.</span><span class="sxs-lookup"><span data-stu-id="c04b7-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="c04b7-112">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="c04b7-112">Connection Pooling</span></span>](connection-pooling.md)  
 <span data-ttu-id="c04b7-113">Opisuje pule połączeń dla dostawców danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c04b7-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="c04b7-114">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="c04b7-114">Commands and Parameters</span></span>](commands-and-parameters.md)  
 <span data-ttu-id="c04b7-115">Zawiera tematy opisujące sposób tworzenia poleceń i konstruktorów poleceń, konfigurowania parametrów oraz wykonywania poleceń w celu pobierania i modyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="c04b7-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="c04b7-116">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="c04b7-116">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)  
 <span data-ttu-id="c04b7-117">Zawiera tematy opisujące operacje odczytujące, dataadaptery, parametry, obsługa zdarzeń DataAdapter i wykonywanie operacji wsadowych.</span><span class="sxs-lookup"><span data-stu-id="c04b7-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="c04b7-118">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="c04b7-118">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)  
 <span data-ttu-id="c04b7-119">Zawiera tematy opisujące sposób wykonywania transakcji lokalnych, transakcji rozproszonych i pracy z optymistyczną współbieżnością.</span><span class="sxs-lookup"><span data-stu-id="c04b7-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="c04b7-120">Pobieranie tożsamości lub wartości automatycznych numerów</span><span class="sxs-lookup"><span data-stu-id="c04b7-120">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="c04b7-121">Zawiera przykład mapowania wartości wygenerowanych dla kolumny **tożsamości** w tabeli SQL Server lub dla pola **AutoNumber** w tabeli programu Microsoft Access do kolumny wstawionego wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="c04b7-121">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="c04b7-122">W tym artykule omówiono scalanie wartości tożsamości w `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="c04b7-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="c04b7-123">Pobieranie danych binarnych</span><span class="sxs-lookup"><span data-stu-id="c04b7-123">Retrieving Binary Data</span></span>](retrieving-binary-data.md)  
 <span data-ttu-id="c04b7-124">Opisuje sposób pobierania danych binarnych lub dużych struktur danych przy użyciu `CommandBehavior`.`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="c04b7-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="c04b7-125">Aby zmodyfikować zachowanie domyślne `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="c04b7-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="c04b7-126">Modyfikowanie danych za pomocą procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="c04b7-126">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="c04b7-127">Opisuje, jak używać parametrów wejściowych procedury składowanej i parametrów wyjściowych, aby wstawić wiersz w bazie danych, zwracając nową wartość tożsamości.</span><span class="sxs-lookup"><span data-stu-id="c04b7-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="c04b7-128">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="c04b7-128">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)  
 <span data-ttu-id="c04b7-129">Opisuje sposób uzyskiwania dostępnych baz danych lub wykazów, tabel i widoków w bazie danych, ograniczeń istniejących dla tabel oraz innych informacji o schemacie ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c04b7-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="c04b7-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="c04b7-130">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="c04b7-131">Opisuje model fabryki dostawcy i pokazuje, jak używać klas bazowych w przestrzeni nazw `System.Data.Common`.</span><span class="sxs-lookup"><span data-stu-id="c04b7-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="c04b7-132">Śledzenie danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c04b7-132">Data Tracing in ADO.NET</span></span>](data-tracing.md)  
 <span data-ttu-id="c04b7-133">Opisuje sposób, w jaki ADO.NET zapewnia wbudowaną funkcję śledzenia danych.</span><span class="sxs-lookup"><span data-stu-id="c04b7-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="c04b7-134">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="c04b7-134">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="c04b7-135">Opisuje liczniki wydajności dostępne dla `SqlClient` i `OracleClient`.</span><span class="sxs-lookup"><span data-stu-id="c04b7-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="c04b7-136">Programowanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="c04b7-136">Asynchronous Programming</span></span>](asynchronous-programming.md)  
 <span data-ttu-id="c04b7-137">Opisuje obsługę ADO.NET w programowaniu asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="c04b7-137">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="c04b7-138">Obsługa przesyłania strumieniowego SqlClient</span><span class="sxs-lookup"><span data-stu-id="c04b7-138">SqlClient Streaming Support</span></span>](sqlclient-streaming-support.md)  
 <span data-ttu-id="c04b7-139">W tym artykule omówiono sposób pisania aplikacji, które przesyła strumieniowo dane z SQL Server bez całkowitego ładowania w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c04b7-139">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04b7-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c04b7-140">See also</span></span>

- [<span data-ttu-id="c04b7-141">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c04b7-141">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="c04b7-142">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="c04b7-142">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="c04b7-143">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c04b7-143">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- [<span data-ttu-id="c04b7-144">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c04b7-144">SQL Server and ADO.NET</span></span>](./sql/index.md)
- [<span data-ttu-id="c04b7-145">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c04b7-145">ADO.NET Overview</span></span>](ado-net-overview.md)
