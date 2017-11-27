---
title: Uzyskiwanie DbProviderFactory
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d230a122cbc02521c8d300d96cdd074bd7faa979
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="obtaining-a-dbproviderfactory"></a><span data-ttu-id="3ed5b-102">Uzyskiwanie DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="3ed5b-102">Obtaining a DbProviderFactory</span></span>
<span data-ttu-id="3ed5b-103">Proces uzyskiwania <xref:System.Data.Common.DbProviderFactory> obejmuje przekazanie informacji o dostawcy danych do <xref:System.Data.Common.DbProviderFactories> klasy.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-103">The process of obtaining a <xref:System.Data.Common.DbProviderFactory> involves passing information about a data provider to the <xref:System.Data.Common.DbProviderFactories> class.</span></span> <span data-ttu-id="3ed5b-104">Na podstawie tych informacji <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metoda tworzy fabrykę jednoznacznie dostawcy.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-104">Based on this information, the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method creates a strongly typed provider factory.</span></span> <span data-ttu-id="3ed5b-105">Na przykład, aby utworzyć <xref:System.Data.SqlClient.SqlClientFactory>, można przekazać `GetFactory` ciągu o podanej nazwie dostawcy jako "System.Data.SqlClient".</span><span class="sxs-lookup"><span data-stu-id="3ed5b-105">For example, to create a <xref:System.Data.SqlClient.SqlClientFactory>, you can pass `GetFactory` a string with the provider name specified as "System.Data.SqlClient".</span></span> <span data-ttu-id="3ed5b-106">Inne przeciążenia `GetFactory` przyjmuje <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-106">The other overload of `GetFactory` takes a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="3ed5b-107">Po utworzeniu fabryki dostawców można następnie użyć jego metody można utworzyć dodatkowe obiekty.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-107">Once you create the provider factory, you can then use its methods to create additional objects.</span></span> <span data-ttu-id="3ed5b-108">Niektóre metody `SqlClientFactory` obejmują <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, i <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-108">Some of the methods of a `SqlClientFactory` include <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, and <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ed5b-109">.NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, i <xref:System.Data.OleDb.OleDbFactory> klasy udostępniają podobnych możliwościach.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-109">The .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, and <xref:System.Data.OleDb.OleDbFactory> classes also provide similar functionality.</span></span>  
  
## <a name="registering-dbproviderfactories"></a><span data-ttu-id="3ed5b-110">Rejestrowanie DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="3ed5b-110">Registering DbProviderFactories</span></span>  
 <span data-ttu-id="3ed5b-111">Każdy dostawca danych .NET Framework obsługującą na podstawie fabryki klasy rejestruje informacje o konfiguracji w **DbProviderFactories** sekcji **machine.config** plik na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-111">Each .NET Framework data provider that supports a factory-based class registers configuration information in the **DbProviderFactories** section of the **machine.config** file on the local computer.</span></span> <span data-ttu-id="3ed5b-112">Poniższy fragment pliku konfiguracji przedstawiono składnię i format <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-112">The following configuration file fragment shows the syntax and format for <xref:System.Data.SqlClient>.</span></span>  
  
```xml  
<system.data>  
  <DbProviderFactories>  
    <add name="SqlClient Data Provider"  
     invariant="System.Data.SqlClient"   
     description=".Net Framework Data Provider for SqlServer"   
     type="System.Data.SqlClient.SqlClientFactory, System.Data,   
     Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
    />  
  </DbProviderFactories>  
</system.data>  
```  
  
 <span data-ttu-id="3ed5b-113">**Niezmiennej** atrybut określa podstawowego dostawcy danych.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-113">The **invariant** attribute identifies the underlying data provider.</span></span> <span data-ttu-id="3ed5b-114">Ta składnia nazwy trzyczęściowej służy również podczas tworzenia nowego fabryki i identyfikowania dostawcy w pliku konfiguracji aplikacji, aby nazwa dostawcy, wraz z jego parametrów połączenia skojarzone, mogą być pobierane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-114">This three-part naming syntax is also used when creating a new factory and for identifying the provider in an application configuration file so that the provider name, along with its associated connection string, can be retrieved at run time.</span></span>  
  
## <a name="retrieving-provider-information"></a><span data-ttu-id="3ed5b-115">Trwa pobieranie informacji o dostawcy</span><span class="sxs-lookup"><span data-stu-id="3ed5b-115">Retrieving Provider Information</span></span>  
 <span data-ttu-id="3ed5b-116">Można pobrać informacji o wszystkich dostawców danych zainstalowany na komputerze lokalnym przy użyciu <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-116">You can retrieve information about all of the data providers installed on the local computer by using the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method.</span></span> <span data-ttu-id="3ed5b-117">Zwraca <xref:System.Data.DataTable> o nazwie **DbProviderFactories** zawiera kolumny opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-117">It returns a <xref:System.Data.DataTable> named **DbProviderFactories** that contains the columns described in the following table.</span></span>  
  
|<span data-ttu-id="3ed5b-118">Kolumny o liczbie porządkowej</span><span class="sxs-lookup"><span data-stu-id="3ed5b-118">Column ordinal</span></span>|<span data-ttu-id="3ed5b-119">Nazwa kolumny</span><span class="sxs-lookup"><span data-stu-id="3ed5b-119">Column name</span></span>|<span data-ttu-id="3ed5b-120">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="3ed5b-120">Example output</span></span>|<span data-ttu-id="3ed5b-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3ed5b-121">Description</span></span>|  
|--------------------|-----------------|--------------------|-----------------|  
|<span data-ttu-id="3ed5b-122">0</span><span class="sxs-lookup"><span data-stu-id="3ed5b-122">0</span></span>|<span data-ttu-id="3ed5b-123">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="3ed5b-123">**Name**</span></span>|<span data-ttu-id="3ed5b-124">Dostawca danych SqlClient</span><span class="sxs-lookup"><span data-stu-id="3ed5b-124">SqlClient Data Provider</span></span>|<span data-ttu-id="3ed5b-125">Czytelna nazwa dostawcy danych</span><span class="sxs-lookup"><span data-stu-id="3ed5b-125">Readable name for the data provider</span></span>|  
|<span data-ttu-id="3ed5b-126">1</span><span class="sxs-lookup"><span data-stu-id="3ed5b-126">1</span></span>|<span data-ttu-id="3ed5b-127">**Opis**</span><span class="sxs-lookup"><span data-stu-id="3ed5b-127">**Description**</span></span>|<span data-ttu-id="3ed5b-128">Dostawca danych programu .net framework dla serwera SQL</span><span class="sxs-lookup"><span data-stu-id="3ed5b-128">.Net Framework Data Provider for SqlServer</span></span>|<span data-ttu-id="3ed5b-129">Czytelny opis dostawcy danych</span><span class="sxs-lookup"><span data-stu-id="3ed5b-129">Readable description of the data provider</span></span>|  
|<span data-ttu-id="3ed5b-130">2</span><span class="sxs-lookup"><span data-stu-id="3ed5b-130">2</span></span>|<span data-ttu-id="3ed5b-131">**Invatiantname**</span><span class="sxs-lookup"><span data-stu-id="3ed5b-131">**InvariantName**</span></span>|<span data-ttu-id="3ed5b-132">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="3ed5b-132">System.Data.SqlClient</span></span>|<span data-ttu-id="3ed5b-133">Nazwa programowo służący do odwoływania się do dostawcy danych</span><span class="sxs-lookup"><span data-stu-id="3ed5b-133">Name that can be used programmatically to refer to the data provider</span></span>|  
|<span data-ttu-id="3ed5b-134">3</span><span class="sxs-lookup"><span data-stu-id="3ed5b-134">3</span></span>|<span data-ttu-id="3ed5b-135">**AssemblyQualifiedName**</span><span class="sxs-lookup"><span data-stu-id="3ed5b-135">**AssemblyQualifiedName**</span></span>|<span data-ttu-id="3ed5b-136">System.Data.SqlClient.SqlClientFactory, dane systemowe, wersja = 2.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="3ed5b-136">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span></span>|<span data-ttu-id="3ed5b-137">Pełna nazwa klasy fabryki, która zawiera wystarczających informacji do utworzenia wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="3ed5b-137">Fully qualified name of the factory class, which contains enough information to instantiate the object</span></span>|  
  
 <span data-ttu-id="3ed5b-138">To `DataTable` może służyć do włączenia użytkownikowi na wybranie <xref:System.Data.DataRow> w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-138">This `DataTable` can be used to enable a user to select a <xref:System.Data.DataRow> at run time.</span></span> <span data-ttu-id="3ed5b-139">Wybrane `DataRow` można następnie przekazać do <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metodę w celu utworzenia silnie typizowaną <xref:System.Data.Common.DbProviderFactory>.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-139">The selected `DataRow` can then be passed to the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method to create a strongly typed <xref:System.Data.Common.DbProviderFactory>.</span></span> <span data-ttu-id="3ed5b-140">Zaznaczony <xref:System.Data.DataRow> mogą zostać przekazane do `GetFactory` metodę w celu utworzenia żądaną `DbProviderFactory` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-140">A selected <xref:System.Data.DataRow> can be passed to the `GetFactory` method to create the desired `DbProviderFactory` object.</span></span>  
  
## <a name="listing-the-installed-provider-factory-classes"></a><span data-ttu-id="3ed5b-141">Lista zainstalowanego dostawcę fabryki klas</span><span class="sxs-lookup"><span data-stu-id="3ed5b-141">Listing the Installed Provider Factory Classes</span></span>  
 <span data-ttu-id="3ed5b-142">W tym przykładzie przedstawiono sposób użycia <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metodę, aby zwrócić <xref:System.Data.DataTable> zawierający informacje o zainstalowanych dostawców.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-142">This example demonstrates how to use the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method to return a <xref:System.Data.DataTable> containing information about the installed providers.</span></span> <span data-ttu-id="3ed5b-143">Kod iteruje każdego wiersza w `DataTable`, wyświetlane informacje dotyczące poszczególnych zainstalowanych dostawców w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-143">The code iterates through each row in the `DataTable`, displaying information for each installed provider in the console window.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a><span data-ttu-id="3ed5b-144">Za pomocą plików konfiguracji aplikacji do przechowywania informacji o fabryki</span><span class="sxs-lookup"><span data-stu-id="3ed5b-144">Using Application Configuration Files to Store Factory Information</span></span>  
 <span data-ttu-id="3ed5b-145">Wzorzec projektowy używane do pracy z fabryki pociąga za sobą przechowywania informacji o ciągu połączenia i dostawcy w pliku konfiguracji aplikacji, takich jak **app.config** dla aplikacji systemu Windows i **pliku web.config**  dla aplikacji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-145">The design pattern used for working with factories entails storing provider and connection string information in an application configuration file, such as **app.config** for a Windows application, and **web.config** for an ASP.NET application.</span></span>  
  
 <span data-ttu-id="3ed5b-146">Poniższy fragment pliku konfiguracji pokazano, jak zapisać dwa parametry połączenia nazwanego, "NorthwindSQL" dla połączenia z bazą danych Northwind w programie SQL Server, a "NorthwindAccess" dla połączenia z bazą danych Northwind w dostępu/Jet.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-146">The following configuration file fragment demonstrates how to save two named connection strings, "NorthwindSQL" for a connection to the Northwind database in SQL Server, and "NorthwindAccess" for a connection to the Northwind database in Access/Jet.</span></span> <span data-ttu-id="3ed5b-147">**Niezmiennej** nazwa jest używana przez **providerName** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-147">The **invariant** name is used for the **providerName** attribute.</span></span>  
  
```xml  
<configuration>  
  <connectionStrings>  
    <clear/>  
    <add name="NorthwindSQL"   
     providerName="System.Data.SqlClient"   
     connectionString=  
     "Data Source=MSSQL1;Initial Catalog=Northwind;Integrated Security=true"  
    />  
  
    <add name="NorthwindAccess"   
     providerName="System.Data.OleDb"   
     connectionString=  
     "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Data\Northwind.mdb;"  
    />  
  </connectionStrings>  
</configuration>  
```  
  
### <a name="retrieving-a-connection-string-by-provider-name"></a><span data-ttu-id="3ed5b-148">Podczas pobierania ciągu połączenia, według nazwy dostawcy</span><span class="sxs-lookup"><span data-stu-id="3ed5b-148">Retrieving a Connection String by Provider Name</span></span>  
 <span data-ttu-id="3ed5b-149">Aby można było utworzyć fabryki dostawcy, musisz podać parametry połączenia, a także nazwę dostawcy.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-149">In order to create a provider factory, you must supply a connection string as well as the provider name.</span></span> <span data-ttu-id="3ed5b-150">W tym przykładzie pokazano, jak pobrać parametry połączenia z pliku konfiguracji aplikacji przez przekazanie w formacie niezmiennej nazwy dostawcy "*System.Data.ProviderName*".</span><span class="sxs-lookup"><span data-stu-id="3ed5b-150">This example demonstrates how to retrieve a connection string from an application configuration file by passing the provider name in the invariant format "*System.Data.ProviderName*".</span></span> <span data-ttu-id="3ed5b-151">Iteruje po kodzie <xref:System.Configuration.ConnectionStringSettingsCollection>.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-151">The code iterates through the <xref:System.Configuration.ConnectionStringSettingsCollection>.</span></span> <span data-ttu-id="3ed5b-152">Zwraca <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> w przypadku powodzenia; w przeciwnym razie `null` (`Nothing` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="3ed5b-152">It returns the <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> on success; otherwise `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="3ed5b-153">Jeśli istnieje wiele wpisów dla dostawcy, zwracana jest pierwsza z nich znalezione.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-153">If there are multiple entries for a provider, the first one found is returned.</span></span> <span data-ttu-id="3ed5b-154">Aby uzyskać dodatkowe informacje i przykłady pobierania parametrów połączenia z plików konfiguracyjnych, zobacz [parametry połączenia i pliki konfiguracyjne](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="3ed5b-154">For more information and examples of retrieving connection strings from configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ed5b-155">Odwołanie do `System.Configuration.dll` jest wymagane dla kodu do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-155">A reference to `System.Configuration.dll` is required in order for the code to run.</span></span>  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a><span data-ttu-id="3ed5b-156">Tworzenie DbProviderFactory i DbConnection</span><span class="sxs-lookup"><span data-stu-id="3ed5b-156">Creating the DbProviderFactory and DbConnection</span></span>  
 <span data-ttu-id="3ed5b-157">W tym przykładzie pokazano, jak utworzyć <xref:System.Data.Common.DbProviderFactory> i <xref:System.Data.Common.DbConnection> obiektu przez przekazanie jej nazwa dostawcy w formacie "*System.Data.ProviderName*" i parametrów połączenia.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-157">This example demonstrates how to create a <xref:System.Data.Common.DbProviderFactory> and <xref:System.Data.Common.DbConnection> object by passing it the provider name in the format "*System.Data.ProviderName*" and a connection string.</span></span> <span data-ttu-id="3ed5b-158">A `DbConnection` obiekt jest zwracany w przypadku powodzenia; `null` (`Nothing` w języku Visual Basic) każdy błąd.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-158">A `DbConnection` object is returned on success; `null` (`Nothing` in Visual Basic) on any error.</span></span>  
  
 <span data-ttu-id="3ed5b-159">Kod uzyskuje `DbProviderFactory` przez wywołanie metody <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-159">The code obtains the `DbProviderFactory` by calling <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span></span> <span data-ttu-id="3ed5b-160">Następnie przy użyciu <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metoda tworzy <xref:System.Data.Common.DbConnection> obiektu i <xref:System.Data.Common.DbConnection.ConnectionString%2A> właściwość jest ustawiona w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="3ed5b-160">Then the <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> method creates the <xref:System.Data.Common.DbConnection> object and the <xref:System.Data.Common.DbConnection.ConnectionString%2A> property is set to the connection string.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3ed5b-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ed5b-161">See Also</span></span>  
 [<span data-ttu-id="3ed5b-162">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="3ed5b-162">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="3ed5b-163">Parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="3ed5b-163">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="3ed5b-164">Używanie klas konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3ed5b-164">Using the Configuration Classes</span></span>](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [<span data-ttu-id="3ed5b-165">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="3ed5b-165">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
