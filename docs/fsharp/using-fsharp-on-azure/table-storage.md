---
title: 'Rozpoczynanie pracy z magazynem tabel Azure przy użyciu języka F #'
description: Przechowywanie danych strukturalnych w chmurze przy użyciu magazynu tabel Azure lub bazy danych Azure rozwiązania Cosmos.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: ac81bc88db1436aa4d5f576da61a90839df04b99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="b24c0-103">Rozpoczynanie pracy z magazynem tabel Azure i rozwiązania Cosmos DB tabeli interfejsu API Azure przy użyciu języka F #</span><span class="sxs-lookup"><span data-stu-id="b24c0-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F#</span></span> # 

<span data-ttu-id="b24c0-104">Magazyn tabel Azure to usługa, która przechowuje dane strukturalne NoSQL w chmurze.</span><span class="sxs-lookup"><span data-stu-id="b24c0-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="b24c0-105">Magazyn tabel jest magazynem kluczy/atrybutów bez schematu.</span><span class="sxs-lookup"><span data-stu-id="b24c0-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="b24c0-106">Ponieważ Magazyn tabel nie korzysta ze schematów, jest łatwo zaadaptować dane rozwijających się potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b24c0-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="b24c0-107">Dostęp do danych jest szybki i ekonomiczny dla wszystkich rodzajów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b24c0-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="b24c0-108">Magazyn tabel jest zwykle znacznie tańszy niż tradycyjne bazy SQL dla podobnych ilości danych.</span><span class="sxs-lookup"><span data-stu-id="b24c0-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="b24c0-109">Magazyn tabel umożliwia przechowywanie elastycznych zestawów danych, takich jak dane użytkownika dla aplikacji sieci web, książki adresowe, informacje o urządzeniach i inne rodzaje metadanych, których wymaga Twoja usługa.</span><span class="sxs-lookup"><span data-stu-id="b24c0-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="b24c0-110">W tabeli można przechowywać dowolną liczbę jednostek, a konto magazynu może zawierać dowolną liczbę tabel w granicach pojemności konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="b24c0-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="b24c0-111">Azure DB rozwiązania Cosmos zawiera tabelę interfejsu API dla aplikacji, które są przeznaczone dla magazynu tabel Azure i wymagają możliwości premium takich jak:</span><span class="sxs-lookup"><span data-stu-id="b24c0-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="b24c0-112">Gotowe dystrybucji globalnego.</span><span class="sxs-lookup"><span data-stu-id="b24c0-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="b24c0-113">Dedykowany przepływności na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="b24c0-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="b24c0-114">Jednocyfrowej milisekundy opóźnienia w 99-ty percentyl.</span><span class="sxs-lookup"><span data-stu-id="b24c0-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="b24c0-115">Gwarantuje wysoką dostępność.</span><span class="sxs-lookup"><span data-stu-id="b24c0-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="b24c0-116">Automatyczne indeksowanie dodatkowej.</span><span class="sxs-lookup"><span data-stu-id="b24c0-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="b24c0-117">Aplikacje napisane dla magazynu tabel Azure można migrować do bazy danych rozwiązania Cosmos Azure przy użyciu interfejsu API tabeli bez zmian kodu i korzystać z funkcji premium.</span><span class="sxs-lookup"><span data-stu-id="b24c0-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="b24c0-118">Interfejs API tabeli ma dostępne zestawy SDK klientów dla platformy .NET, Java, Python i Node.js.</span><span class="sxs-lookup"><span data-stu-id="b24c0-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="b24c0-119">Aby uzyskać więcej informacji, zobacz [wprowadzenie do interfejsu API Azure rozwiązania Cosmos DB tabeli](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="b24c0-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="b24c0-120">Informacje o tym samouczku</span><span class="sxs-lookup"><span data-stu-id="b24c0-120">About this tutorial</span></span>

<span data-ttu-id="b24c0-121">Ten samouczek pokazuje, jak napisać kod F # do wykonania niektórych typowych zadań przy użyciu magazynu tabel Azure lub rozwiązania Cosmos DB tabeli interfejsu API Azure, w tym tworzenie i usuwaniem tabel i wstawianie, aktualizowanie, usuwanie i przeszukiwaniem danych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="b24c0-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b24c0-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b24c0-122">Prerequisites</span></span>

<span data-ttu-id="b24c0-123">Aby użyć tego przewodnika, należy najpierw [utworzyć konto magazynu Azure](/azure/storage/storage-create-storage-account) lub [konta bazy danych Azure rozwiązania Cosmos](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="b24c0-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>


## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="b24c0-124">Tworzenie skryptu języka F # i rozpocząć F # Interactive</span><span class="sxs-lookup"><span data-stu-id="b24c0-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="b24c0-125">Przykłady w tym artykule można używać w F # aplikacji lub skryptu języka F #.</span><span class="sxs-lookup"><span data-stu-id="b24c0-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="b24c0-126">Aby utworzyć skrypt F #, Utwórz plik o `.fsx` rozszerzenie, na przykład `tables.fsx`, w środowiska deweloperskiego F #.</span><span class="sxs-lookup"><span data-stu-id="b24c0-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="b24c0-127">Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) do zainstalowania `WindowsAzure.Storage` odwołanie do pakietu i `WindowsAzure.Storage.dll` skryptu za pomocą `#r`dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="b24c0-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="b24c0-128">Wykonaj ponownie ją `Microsoft.WindowsAzure.ConfigurationManager` Aby uzyskać Microsoft.Azure przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b24c0-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="b24c0-129">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="b24c0-129">Add namespace declarations</span></span>

<span data-ttu-id="b24c0-130">Dodaj następujące `open` instrukcje na początku `tables.fsx` pliku:</span><span class="sxs-lookup"><span data-stu-id="b24c0-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="b24c0-131">Pobierz ciąg połączenia usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="b24c0-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="b24c0-132">Jeśli łączysz się do usługi tabel magazynu Azure, konieczne będzie parametrów połączenia w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="b24c0-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="b24c0-133">Parametry połączenia można skopiować z portalu Azure.</span><span class="sxs-lookup"><span data-stu-id="b24c0-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="b24c0-134">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="b24c0-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="b24c0-135">Pobierz ciąg połączenia bazy danych Azure rozwiązania Cosmos</span><span class="sxs-lookup"><span data-stu-id="b24c0-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="b24c0-136">Jeśli łączysz się do bazy danych rozwiązania Cosmos Azure, konieczne będzie parametrów połączenia w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="b24c0-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="b24c0-137">Parametry połączenia można skopiować z portalu Azure.</span><span class="sxs-lookup"><span data-stu-id="b24c0-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="b24c0-138">W portalu Azure, na Twoim koncie rozwiązania Cosmos bazy danych, przejdź do **ustawienia** > **ciąg połączenia**i kliknij przycisk **kopiowania** przycisk, aby skopiować podstawowego połączenia Ciąg.</span><span class="sxs-lookup"><span data-stu-id="b24c0-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="b24c0-139">Samouczek wprowadź parametry połączenia za pomocą skryptu, jak w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b24c0-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="b24c0-140">Jest to jednak **niezalecane** rzeczywiste projektów.</span><span class="sxs-lookup"><span data-stu-id="b24c0-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="b24c0-141">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="b24c0-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="b24c0-142">Zawsze starannie Chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="b24c0-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="b24c0-143">Unikaj udostępniaj go innym użytkownikom, kodować je lub zapisać go w pliku jako zwykły tekst, który jest dostępny do innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="b24c0-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="b24c0-144">Można ponownie wygenerować klucz przy użyciu portalu Azure, jeśli uważasz, że mogą zostać naruszone.</span><span class="sxs-lookup"><span data-stu-id="b24c0-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="b24c0-145">Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b24c0-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="b24c0-146">Aby pobrać parametry połączenia w pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="b24c0-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="b24c0-147">Przy użyciu programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="b24c0-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="b24c0-148">Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="b24c0-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="b24c0-149">Przeanalizować parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="b24c0-149">Parse the connection string</span></span>

<span data-ttu-id="b24c0-150">Aby przeanalizować parametrów połączenia, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="b24c0-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="b24c0-151">To polecenie zwróci `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="b24c0-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="b24c0-152">Tworzenie klienta usługi tabel</span><span class="sxs-lookup"><span data-stu-id="b24c0-152">Create the Table service client</span></span>

<span data-ttu-id="b24c0-153">`CloudTableClient` Klasa umożliwia pobieranie tabel i jednostek w magazynie tabel.</span><span class="sxs-lookup"><span data-stu-id="b24c0-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="b24c0-154">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="b24c0-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="b24c0-155">Teraz można przystąpić do pisania kodu, która odczytuje i zapisuje dane do magazynu tabel.</span><span class="sxs-lookup"><span data-stu-id="b24c0-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="b24c0-156">Utwórz tabelę</span><span class="sxs-lookup"><span data-stu-id="b24c0-156">Create a table</span></span>

<span data-ttu-id="b24c0-157">W tym przykładzie pokazano, jak utworzyć tabelę, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="b24c0-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="b24c0-158">Dodawanie jednostki do tabeli</span><span class="sxs-lookup"><span data-stu-id="b24c0-158">Add an entity to a table</span></span>

<span data-ttu-id="b24c0-159">Jednostka musi mieć typ, który dziedziczy z `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="b24c0-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="b24c0-160">Można rozszerzyć `TableEntity` w żaden sposób Ci się podoba, ale danego typu *musi* ma konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="b24c0-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="b24c0-161">Tylko te właściwości, które mają zarówno `get` i `set` są przechowywane w tabeli platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b24c0-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="b24c0-162">Jednostka partycji i klucz wiersza jednostki jednoznacznie identyfikują jednostkę w tabeli.</span><span class="sxs-lookup"><span data-stu-id="b24c0-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="b24c0-163">Jednostki z tym samym kluczem partycji mogą być przeszukiwane szybciej niż jednostki o różnych kluczach partycji, ale przy użyciu różnych kluczy partycji umożliwia zwiększenie skalowalności operacji równoległych.</span><span class="sxs-lookup"><span data-stu-id="b24c0-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="b24c0-164">Oto przykład `Customer` używającą `lastName` jako klucza partycji i `firstName` jako klucz wiersza.</span><span class="sxs-lookup"><span data-stu-id="b24c0-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="b24c0-165">Teraz Dodaj `Customer` do tabeli.</span><span class="sxs-lookup"><span data-stu-id="b24c0-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="b24c0-166">Aby to zrobić, należy utworzyć `TableOperation` , który jest wykonywany w tabeli.</span><span class="sxs-lookup"><span data-stu-id="b24c0-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="b24c0-167">W takim przypadku należy utworzyć `Insert` operacji.</span><span class="sxs-lookup"><span data-stu-id="b24c0-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="b24c0-168">Wstawić partię jednostek</span><span class="sxs-lookup"><span data-stu-id="b24c0-168">Insert a batch of entities</span></span>

<span data-ttu-id="b24c0-169">Można wstawić partię jednostek do tabeli za pomocą operacji zapisu pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="b24c0-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="b24c0-170">Operacje partii pozwalają połączyć operacje w pojedynczej operacji, ale mają pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="b24c0-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="b24c0-171">Możesz przeprowadzić aktualizację, usuwanie i wstawianie w tej samej operacji zbiorczej.</span><span class="sxs-lookup"><span data-stu-id="b24c0-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="b24c0-172">Operacja zbiorcza może zawierać maksymalnie 100 jednostek.</span><span class="sxs-lookup"><span data-stu-id="b24c0-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="b24c0-173">Wszystkie jednostki w operacji zbiorczej muszą mieć ten sam klucz partycji.</span><span class="sxs-lookup"><span data-stu-id="b24c0-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="b24c0-174">W trakcie można wykonać zapytania w operacji zbiorczej musi być jedyną operacją w partii.</span><span class="sxs-lookup"><span data-stu-id="b24c0-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="b24c0-175">Oto niektóre kod, który łączy dwie wstawki w operacji zbiorczej:</span><span class="sxs-lookup"><span data-stu-id="b24c0-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="b24c0-176">Pobieranie wszystkich jednostek w partycji</span><span class="sxs-lookup"><span data-stu-id="b24c0-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="b24c0-177">Aby sprawdzić tabelę dla wszystkich jednostek w partycji, użyj `TableQuery` obiektu.</span><span class="sxs-lookup"><span data-stu-id="b24c0-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="b24c0-178">W tym miejscu można filtrować dla jednostek gdzie "Smith" jest kluczem partycji.</span><span class="sxs-lookup"><span data-stu-id="b24c0-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="b24c0-179">Teraz drukowanie wyników:</span><span class="sxs-lookup"><span data-stu-id="b24c0-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="b24c0-180">Pobieranie zakresu jednostek w partycji</span><span class="sxs-lookup"><span data-stu-id="b24c0-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="b24c0-181">Jeśli nie chcesz zbadać wszystkich jednostek w partycji, można określić zakres, łącząc filtr klucza partycji z filtrem klucza wiersza.</span><span class="sxs-lookup"><span data-stu-id="b24c0-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="b24c0-182">W tym miejscu służy dwa filtry do pobrania wszystkich jednostek w partycji "Smith" gdzie klucz wiersza (imię) rozpoczyna się od litery wcześniejszej niż "M" alfabetu.</span><span class="sxs-lookup"><span data-stu-id="b24c0-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="b24c0-183">Teraz drukowanie wyników:</span><span class="sxs-lookup"><span data-stu-id="b24c0-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="b24c0-184">Pobieranie pojedynczej jednostki</span><span class="sxs-lookup"><span data-stu-id="b24c0-184">Retrieve a single entity</span></span>

<span data-ttu-id="b24c0-185">Można napisać zapytanie do pobrania jednej, określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="b24c0-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="b24c0-186">W tym miejscu użyć `TableOperation` do określenia klienta "Ben Smith".</span><span class="sxs-lookup"><span data-stu-id="b24c0-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="b24c0-187">Zamiast kolekcji, możesz wrócić `Customer`.</span><span class="sxs-lookup"><span data-stu-id="b24c0-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="b24c0-188">Określenie zarówno klucz partycji i klucz wiersza w zapytaniu jest najszybszym sposobem na pobranie jednej jednostki z usługi tabel.</span><span class="sxs-lookup"><span data-stu-id="b24c0-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="b24c0-189">Teraz drukowanie wyników:</span><span class="sxs-lookup"><span data-stu-id="b24c0-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a><span data-ttu-id="b24c0-190">Zastępowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="b24c0-190">Replace an entity</span></span>

<span data-ttu-id="b24c0-191">Aby zaktualizować jednostkę, pobierz ją z usługi tabel, zmodyfikuj obiekt jednostki, a następnie zapisz zmiany powrót do tabeli usługi przy użyciu `Replace` operacji.</span><span class="sxs-lookup"><span data-stu-id="b24c0-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="b24c0-192">Powoduje to, że jednostka będzie całkowicie zastąpiona na serwerze, chyba że jednostka na serwerze została zmieniona, ponieważ został on pobrany, w którym to przypadku kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="b24c0-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="b24c0-193">Jest to błąd uniemożliwia aplikacji nieodwracalne nadpisanie zmiany z innych źródeł.</span><span class="sxs-lookup"><span data-stu-id="b24c0-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="b24c0-194">Wstawianie lub zastępowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="b24c0-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="b24c0-195">Czasami nie wiadomo, czy obiekt istnieje w tabeli.</span><span class="sxs-lookup"><span data-stu-id="b24c0-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="b24c0-196">A jeśli tak, czy obecne wartości przechowywane w nim nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="b24c0-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="b24c0-197">Można użyć `InsertOrReplace` w celu utworzenia jednostki lub zastąp ją, jeśli istnieje, niezależnie od jego stanu.</span><span class="sxs-lookup"><span data-stu-id="b24c0-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="b24c0-198">Tworzenie zapytania do podzbioru właściwości jednostki</span><span class="sxs-lookup"><span data-stu-id="b24c0-198">Query a subset of entity properties</span></span>

<span data-ttu-id="b24c0-199">Zapytanie tabeli może pobrać kilka właściwości jednostki zamiast wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="b24c0-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="b24c0-200">Ta technika, zwana projekcją, może poprawić wydajność zapytań, zwłaszcza w przypadku dużych jednostek.</span><span class="sxs-lookup"><span data-stu-id="b24c0-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="b24c0-201">W tym miejscu zwracać dotyczy tylko wiadomości e-mail przy użyciu `DynamicTableEntity` i `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="b24c0-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="b24c0-202">Należy pamiętać, że projekcji nie jest obsługiwana w lokalnym emulatorze magazynu, dlatego ten kod zadziała tylko wtedy, gdy używasz konta w usłudze tabel.</span><span class="sxs-lookup"><span data-stu-id="b24c0-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="b24c0-203">Pobieranie asynchroniczne jednostek na stronach</span><span class="sxs-lookup"><span data-stu-id="b24c0-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="b24c0-204">Jeśli odczytujesz dużą liczbę jednostek i chcesz przetworzyć je zgodnie z ich pobraniu, zamiast oczekiwania na zwrócenie ich wszystkich, można użyć zapytania segmentowanego.</span><span class="sxs-lookup"><span data-stu-id="b24c0-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="b24c0-205">W tym miejscu możesz zwracania wyników na stronach za pomocą async przepływu pracy, dzięki czemu wykonanie nie jest blokowane podczas oczekiwania dla dużych zestawów wyników do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="b24c0-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="b24c0-206">Można teraz wykonywać te obliczenia synchronicznie:</span><span class="sxs-lookup"><span data-stu-id="b24c0-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="b24c0-207">Usuwanie jednostki</span><span class="sxs-lookup"><span data-stu-id="b24c0-207">Delete an entity</span></span>

<span data-ttu-id="b24c0-208">Po jej pobraniu, można usunąć jednostki.</span><span class="sxs-lookup"><span data-stu-id="b24c0-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="b24c0-209">Podobnie jak w przypadku aktualizowania jednostki, to nie powiedzie się, jeśli jednostka została zmieniona od czasu jej pobrania.</span><span class="sxs-lookup"><span data-stu-id="b24c0-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="b24c0-210">Usuwanie tabeli</span><span class="sxs-lookup"><span data-stu-id="b24c0-210">Delete a table</span></span>

<span data-ttu-id="b24c0-211">Z konta magazynu można usunąć tabeli.</span><span class="sxs-lookup"><span data-stu-id="b24c0-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="b24c0-212">Tabela, która została usunięta będzie mógł zostać ponownie utworzone w danym okresie czasu po jej usunięciu.</span><span class="sxs-lookup"><span data-stu-id="b24c0-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="b24c0-213">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b24c0-213">Next steps</span></span>

<span data-ttu-id="b24c0-214">Teraz, kiedy znasz już podstawy magazynu tabel, skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu i interfejsu API Azure rozwiązania Cosmos bazy danych tabeli.</span><span class="sxs-lookup"><span data-stu-id="b24c0-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="b24c0-215">Wprowadzenie do platformy Azure rozwiązania Cosmos API tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="b24c0-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="b24c0-216">Biblioteka klienta usługi Storage dla platformy .NET odwołania</span><span class="sxs-lookup"><span data-stu-id="b24c0-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="b24c0-217">Dostawca typów magazynu Azure</span><span class="sxs-lookup"><span data-stu-id="b24c0-217">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="b24c0-218">Blog zespołu usługi Magazyn Azure</span><span class="sxs-lookup"><span data-stu-id="b24c0-218">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="b24c0-219">Konfigurowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="b24c0-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="b24c0-220">Rozpoczynanie pracy z magazynem tabel Azure w .NET</span><span class="sxs-lookup"><span data-stu-id="b24c0-220">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
