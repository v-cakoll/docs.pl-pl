---
title: Pobieranie i modyfikowanie danych
description: W .NET Framework dostawcy danych w ADO.NET pełnią rolę mostka między aplikacją a źródłem danych, aby odczytywać i aktualizować dane.
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: f916324dc829526a5e6b0078021b09786755f666
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286614"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="0feac-103">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0feac-103">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="0feac-104">Podstawowa funkcja dowolnej aplikacji bazy danych nawiązuje połączenie ze źródłem danych i pobiera dane, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="0feac-104">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="0feac-105">.NET Framework dostawcy danych ADO.NET służy jako Most między aplikacją a źródłem danych, co umożliwia wykonywanie poleceń oraz pobieranie danych przy użyciu elementu **DataReader** lub **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="0feac-105">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="0feac-106">Kluczową funkcją dowolnej aplikacji bazy danych jest możliwość aktualizowania danych przechowywanych w bazie danych programu.</span><span class="sxs-lookup"><span data-stu-id="0feac-106">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="0feac-107">W ADO.NET, aktualizowanie danych obejmuje użycie obiektów **DataAdapter** i i <xref:System.Data.DataSet> i **Command** może również wymagać korzystania z transakcji.</span><span class="sxs-lookup"><span data-stu-id="0feac-107">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0feac-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0feac-108">In This Section</span></span>  
 [<span data-ttu-id="0feac-109">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="0feac-109">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)  
 <span data-ttu-id="0feac-110">Opisuje sposób nawiązywania połączenia ze źródłem danych i sposobu pracy ze zdarzeniami połączenia.</span><span class="sxs-lookup"><span data-stu-id="0feac-110">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="0feac-111">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="0feac-111">Connection Strings</span></span>](connection-strings.md)  
 <span data-ttu-id="0feac-112">Zawiera tematy opisujące różne aspekty używania parametrów połączenia, w tym słowa kluczowe parametrów połączenia, informacje zabezpieczające i przechowywania i pobierania.</span><span class="sxs-lookup"><span data-stu-id="0feac-112">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="0feac-113">Buforowanie połączeń</span><span class="sxs-lookup"><span data-stu-id="0feac-113">Connection Pooling</span></span>](connection-pooling.md)  
 <span data-ttu-id="0feac-114">Opisuje pule połączeń dla dostawców danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0feac-114">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="0feac-115">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="0feac-115">Commands and Parameters</span></span>](commands-and-parameters.md)  
 <span data-ttu-id="0feac-116">Zawiera tematy opisujące sposób tworzenia poleceń i konstruktorów poleceń, konfigurowania parametrów oraz wykonywania poleceń w celu pobierania i modyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="0feac-116">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="0feac-117">Elementy DataAdapter i DataReader</span><span class="sxs-lookup"><span data-stu-id="0feac-117">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)  
 <span data-ttu-id="0feac-118">Zawiera tematy opisujące operacje odczytujące, dataadaptery, parametry, obsługa zdarzeń DataAdapter i wykonywanie operacji wsadowych.</span><span class="sxs-lookup"><span data-stu-id="0feac-118">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="0feac-119">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="0feac-119">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)  
 <span data-ttu-id="0feac-120">Zawiera tematy opisujące sposób wykonywania transakcji lokalnych, transakcji rozproszonych i pracy z optymistyczną współbieżnością.</span><span class="sxs-lookup"><span data-stu-id="0feac-120">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="0feac-121">Pobieranie tożsamości lub wartości automatycznych numerów</span><span class="sxs-lookup"><span data-stu-id="0feac-121">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="0feac-122">Zawiera przykład mapowania wartości wygenerowanych dla kolumny **tożsamości** w tabeli SQL Server lub dla pola **AutoNumber** w tabeli programu Microsoft Access do kolumny wstawionego wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="0feac-122">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="0feac-123">Omawia scalanie wartości tożsamości w `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="0feac-123">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="0feac-124">Pobieranie danych binarnych</span><span class="sxs-lookup"><span data-stu-id="0feac-124">Retrieving Binary Data</span></span>](retrieving-binary-data.md)  
 <span data-ttu-id="0feac-125">Opisuje sposób pobierania danych binarnych lub dużych struktur danych przy użyciu programu `CommandBehavior` .`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="0feac-125">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="0feac-126">Aby zmodyfikować zachowanie domyślne `DataReader` .</span><span class="sxs-lookup"><span data-stu-id="0feac-126">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="0feac-127">Modyfikowanie danych za pomocą procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="0feac-127">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="0feac-128">Opisuje, jak używać parametrów wejściowych procedury składowanej i parametrów wyjściowych, aby wstawić wiersz w bazie danych, zwracając nową wartość tożsamości.</span><span class="sxs-lookup"><span data-stu-id="0feac-128">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="0feac-129">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="0feac-129">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)  
 <span data-ttu-id="0feac-130">Opisuje sposób uzyskiwania dostępnych baz danych lub wykazów, tabel i widoków w bazie danych, ograniczeń istniejących dla tabel oraz innych informacji o schemacie ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0feac-130">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="0feac-131">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="0feac-131">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="0feac-132">Opisuje model fabryki dostawców i pokazuje, jak używać klas bazowych w `System.Data.Common` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0feac-132">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="0feac-133">Śledzenie danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0feac-133">Data Tracing in ADO.NET</span></span>](data-tracing.md)  
 <span data-ttu-id="0feac-134">Opisuje sposób, w jaki ADO.NET zapewnia wbudowaną funkcję śledzenia danych.</span><span class="sxs-lookup"><span data-stu-id="0feac-134">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="0feac-135">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="0feac-135">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="0feac-136">Opisuje liczniki wydajności dostępne dla `SqlClient` i `OracleClient` .</span><span class="sxs-lookup"><span data-stu-id="0feac-136">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="0feac-137">Programowanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="0feac-137">Asynchronous Programming</span></span>](asynchronous-programming.md)  
 <span data-ttu-id="0feac-138">Opisuje obsługę ADO.NET w programowaniu asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="0feac-138">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="0feac-139">Obsługa przesyłania strumieniowego SqlClient</span><span class="sxs-lookup"><span data-stu-id="0feac-139">SqlClient Streaming Support</span></span>](sqlclient-streaming-support.md)  
 <span data-ttu-id="0feac-140">W tym artykule omówiono sposób pisania aplikacji, które przesyła strumieniowo dane z SQL Server bez całkowitego ładowania w pamięci.</span><span class="sxs-lookup"><span data-stu-id="0feac-140">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0feac-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0feac-141">See also</span></span>

- [<span data-ttu-id="0feac-142">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0feac-142">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="0feac-143">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="0feac-143">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="0feac-144">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0feac-144">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- [<span data-ttu-id="0feac-145">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0feac-145">SQL Server and ADO.NET</span></span>](./sql/index.md)
- [<span data-ttu-id="0feac-146">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0feac-146">ADO.NET Overview</span></span>](ado-net-overview.md)
