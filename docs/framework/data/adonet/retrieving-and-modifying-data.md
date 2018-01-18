---
title: Trwa pobieranie i modyfikowanie danych ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ff937e619d449fbfbedb234749292b6acc4bdf50
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="b5551-102">Trwa pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b5551-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="b5551-103">Podstawową funkcją dowolnej aplikacji bazy danych jest połączenie ze źródłem danych i pobierania danych, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="b5551-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="b5551-104">Dostawcy danych .NET Framework ADO.NET służyć jako mostka między aplikacją a źródłem danych, co umożliwia wykonanie polecenia oraz do pobierania danych przy użyciu **DataReader** lub **element DataAdapter** .</span><span class="sxs-lookup"><span data-stu-id="b5551-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="b5551-105">Funkcji klucza dowolnej aplikacji bazy danych jest możliwość aktualizacji są przechowywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="b5551-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="b5551-106">W ADO.NET, aktualizowanie danych polega na użyciu **element DataAdapter** i <xref:System.Data.DataSet>, i **polecenia** obiektów; i może również obejmować przy użyciu transakcji.</span><span class="sxs-lookup"><span data-stu-id="b5551-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b5551-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b5551-107">In This Section</span></span>  
 [<span data-ttu-id="b5551-108">Nawiązywanie połączenia ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="b5551-108">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 <span data-ttu-id="b5551-109">Opisuje sposób nawiązania połączenia ze źródłem danych oraz sposób pracy z zdarzeń połączenia.</span><span class="sxs-lookup"><span data-stu-id="b5551-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="b5551-110">Parametry połączeń</span><span class="sxs-lookup"><span data-stu-id="b5551-110">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 <span data-ttu-id="b5551-111">Zawiera tematy zawierająca opis różnych aspektów przy użyciu parametrów połączenia, w tym słowa kluczowe z parametrów połączenia, informacje zabezpieczające i przechowywania i pobierania ich.</span><span class="sxs-lookup"><span data-stu-id="b5551-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="b5551-112">Pula połączeń</span><span class="sxs-lookup"><span data-stu-id="b5551-112">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 <span data-ttu-id="b5551-113">W tym artykule opisano tworzenie puli połączeń dla dostawcy danych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5551-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="b5551-114">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="b5551-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="b5551-115">Zawiera tematów opisujących sposób tworzenia poleceń i polecenia konstruktorów, skonfiguruj parametry i sposobu wykonania polecenia, aby pobrać i zmodyfikować danych.</span><span class="sxs-lookup"><span data-stu-id="b5551-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="b5551-116">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="b5551-116">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 <span data-ttu-id="b5551-117">Zawiera tematy opisujące DataReaders, obiektów DataAdapter, parametry, obsługa zdarzeń element DataAdapter i wykonywanie operacji wsadowych.</span><span class="sxs-lookup"><span data-stu-id="b5551-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="b5551-118">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="b5551-118">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="b5551-119">Zawiera tematy opisujące jak wykonywać transakcje lokalne transakcje rozproszone i pracować z optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="b5551-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="b5551-120">Pobieranie tożsamości lub wartości automatycznych numerów</span><span class="sxs-lookup"><span data-stu-id="b5551-120">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="b5551-121">Przykład mapowania wartości wygenerowany dla **tożsamości** kolumny w [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] tabeli lub **automatycznie numerowane** pola w tabeli programu Microsoft Access z kolumną zawierającą wstawionego wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="b5551-121">Provides an example of mapping the values generated for an **identity** column in a [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="b5551-122">W tym artykule omówiono scalania wartości tożsamości w `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="b5551-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="b5551-123">Pobieranie danych binarnych</span><span class="sxs-lookup"><span data-stu-id="b5551-123">Retrieving Binary Data</span></span>](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 <span data-ttu-id="b5551-124">Opisuje sposób pobrać dane binarne lub struktury dużej ilości danych przy użyciu `CommandBehavior`.`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="b5551-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="b5551-125">Aby zmodyfikować domyślne zachowanie `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="b5551-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="b5551-126">Modyfikowanie danych za pomocą procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="b5551-126">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="b5551-127">Opisuje sposób użyj procedury składowanej parametry wejściowe i wyjściowe parametry, aby wstawić nowy wiersz w bazie danych, zwraca nową wartość tożsamości.</span><span class="sxs-lookup"><span data-stu-id="b5551-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="b5551-128">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="b5551-128">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 <span data-ttu-id="b5551-129">W tym artykule opisano sposób uzyskiwania dostępnych baz danych lub katalogami, tabele i widoki w bazie danych ograniczenia występujące dla tabel i innych informacji o schemacie źródła danych.</span><span class="sxs-lookup"><span data-stu-id="b5551-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="b5551-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="b5551-130">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="b5551-131">W tym artykule opisano model fabryki dostawcy i przedstawiono sposób użycia klasy podstawowe w `System.Data.Common` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b5551-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="b5551-132">Śledzenie danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b5551-132">Data Tracing in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-tracing.md)  
 <span data-ttu-id="b5551-133">W tym artykule opisano, jak ADO.NET udostępnia dane wbudowana funkcja śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b5551-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="b5551-134">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="b5551-134">Performance Counters</span></span>](../../../../docs/framework/data/adonet/performance-counters.md)  
 <span data-ttu-id="b5551-135">Zawiera opis dostępnych dla liczników wydajności `SqlClient` i `OracleClient`.</span><span class="sxs-lookup"><span data-stu-id="b5551-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="b5551-136">Programowanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="b5551-136">Asynchronous Programming</span></span>](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 <span data-ttu-id="b5551-137">W tym artykule opisano [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] obsługę programowania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="b5551-137">Describes [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="b5551-138">Obsługa przesyłania strumieniowego SqlClient</span><span class="sxs-lookup"><span data-stu-id="b5551-138">SqlClient Streaming Support</span></span>](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 <span data-ttu-id="b5551-139">W tym artykule omówiono sposób pisania aplikacji, które strumienia danych z [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] bez konieczności jej pełni załadowanych do pamięci.</span><span class="sxs-lookup"><span data-stu-id="b5551-139">Discusses how to write applications that stream data from [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5551-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5551-140">See Also</span></span>  
 [<span data-ttu-id="b5551-141">Mapowanie typu danych w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b5551-141">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="b5551-142">Elementy DataSet, DataTable i DataView</span><span class="sxs-lookup"><span data-stu-id="b5551-142">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="b5551-143">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b5551-143">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="b5551-144">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b5551-144">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="b5551-145">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="b5551-145">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
