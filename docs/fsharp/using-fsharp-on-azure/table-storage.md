---
title: 'Rozpoczynanie pracy z magazynem tabel Azure przy użyciu języka F #'
description: Przechowywanie danych strukturalnych w chmurze przy użyciu magazynu tabel Azure lub bazy danych Azure rozwiązania Cosmos.
keywords: visual f#, f#, functional programming, .NET, .NET Core, Azure
author: sylvanc
ms.author: phcart
ms.date: 03/26/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9e5d6cea-a98c-461e-a5cc-75f1d154eafd
ms.openlocfilehash: 6d40211e13e8d213aa5a40d585dd384abf49ddfa
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="c9155-104">Rozpoczynanie pracy z magazynem tabel Azure i rozwiązania Cosmos DB tabeli interfejsu API Azure przy użyciu języka F #</span><span class="sxs-lookup"><span data-stu-id="c9155-104">Get started with Azure Table storage and the Azure Cosmos DB Table API using F#</span></span> # 

<span data-ttu-id="c9155-105">Magazyn tabel Azure to usługa, która przechowuje dane strukturalne NoSQL w chmurze.</span><span class="sxs-lookup"><span data-stu-id="c9155-105">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="c9155-106">Magazyn tabel jest magazynem kluczy/atrybutów bez schematu.</span><span class="sxs-lookup"><span data-stu-id="c9155-106">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="c9155-107">Ponieważ Magazyn tabel nie korzysta ze schematów, jest łatwo zaadaptować dane rozwijających się potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9155-107">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="c9155-108">Dostęp do danych jest szybki i ekonomiczny dla wszystkich rodzajów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9155-108">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="c9155-109">Magazyn tabel jest zwykle znacznie tańszy niż tradycyjne bazy SQL dla podobnych ilości danych.</span><span class="sxs-lookup"><span data-stu-id="c9155-109">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="c9155-110">Magazyn tabel umożliwia przechowywanie elastycznych zestawów danych, takich jak dane użytkownika dla aplikacji sieci web, książki adresowe, informacje o urządzeniach i inne rodzaje metadanych, których wymaga Twoja usługa.</span><span class="sxs-lookup"><span data-stu-id="c9155-110">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="c9155-111">W tabeli można przechowywać dowolną liczbę jednostek, a konto magazynu może zawierać dowolną liczbę tabel w granicach pojemności konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="c9155-111">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="c9155-112">Azure DB rozwiązania Cosmos zawiera tabelę interfejsu API dla aplikacji, które są przeznaczone dla magazynu tabel Azure i wymagają możliwości premium takich jak:</span><span class="sxs-lookup"><span data-stu-id="c9155-112">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="c9155-113">Gotowe dystrybucji globalnego.</span><span class="sxs-lookup"><span data-stu-id="c9155-113">Turnkey global distribution.</span></span>
- <span data-ttu-id="c9155-114">Dedykowany przepływności na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="c9155-114">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="c9155-115">Jednocyfrowej milisekundy opóźnienia w 99-ty percentyl.</span><span class="sxs-lookup"><span data-stu-id="c9155-115">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="c9155-116">Gwarantuje wysoką dostępność.</span><span class="sxs-lookup"><span data-stu-id="c9155-116">Guaranteed high availability.</span></span>
- <span data-ttu-id="c9155-117">Automatyczne indeksowanie dodatkowej.</span><span class="sxs-lookup"><span data-stu-id="c9155-117">Automatic secondary indexing.</span></span>

<span data-ttu-id="c9155-118">Aplikacje napisane dla magazynu tabel Azure można migrować do bazy danych rozwiązania Cosmos Azure przy użyciu interfejsu API tabeli bez zmian kodu i korzystać z funkcji premium.</span><span class="sxs-lookup"><span data-stu-id="c9155-118">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="c9155-119">Interfejs API tabeli ma dostępne zestawy SDK klientów dla platformy .NET, Java, Python i Node.js.</span><span class="sxs-lookup"><span data-stu-id="c9155-119">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="c9155-120">Aby uzyskać więcej informacji, zobacz [wprowadzenie do interfejsu API Azure rozwiązania Cosmos DB tabeli](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="c9155-120">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="c9155-121">Informacje o tym samouczku</span><span class="sxs-lookup"><span data-stu-id="c9155-121">About this tutorial</span></span>

<span data-ttu-id="c9155-122">Ten samouczek pokazuje, jak napisać kod F # do wykonania niektórych typowych zadań przy użyciu magazynu tabel Azure lub rozwiązania Cosmos DB tabeli interfejsu API Azure, w tym tworzenie i usuwaniem tabel i wstawianie, aktualizowanie, usuwanie i przeszukiwaniem danych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="c9155-122">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c9155-123">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c9155-123">Prerequisites</span></span>

<span data-ttu-id="c9155-124">Aby użyć tego przewodnika, należy najpierw [utworzyć konto magazynu Azure](/azure/storage/storage-create-storage-account) lub [konta bazy danych Azure rozwiązania Cosmos](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="c9155-124">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>


## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="c9155-125">Tworzenie skryptu języka F # i rozpocząć F # Interactive</span><span class="sxs-lookup"><span data-stu-id="c9155-125">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="c9155-126">Przykłady w tym artykule można używać w F # aplikacji lub skryptu języka F #.</span><span class="sxs-lookup"><span data-stu-id="c9155-126">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="c9155-127">Aby utworzyć skrypt F #, Utwórz plik o `.fsx` rozszerzenie, na przykład `tables.fsx`, w środowiska deweloperskiego F #.</span><span class="sxs-lookup"><span data-stu-id="c9155-127">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="c9155-128">Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) do zainstalowania `WindowsAzure.Storage` odwołanie do pakietu i `WindowsAzure.Storage.dll` skryptu za pomocą `#r`dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="c9155-128">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="c9155-129">Wykonaj ponownie ją `Microsoft.WindowsAzure.ConfigurationManager` Aby uzyskać Microsoft.Azure przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c9155-129">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="c9155-130">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="c9155-130">Add namespace declarations</span></span>

<span data-ttu-id="c9155-131">Dodaj następujące `open` instrukcje na początku `tables.fsx` pliku:</span><span class="sxs-lookup"><span data-stu-id="c9155-131">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="c9155-132">Pobierz ciąg połączenia usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="c9155-132">Get your Azure Storage connection string</span></span>

<span data-ttu-id="c9155-133">Jeśli łączysz się do usługi tabel magazynu Azure, konieczne będzie parametrów połączenia w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="c9155-133">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="c9155-134">Parametry połączenia można skopiować z portalu Azure.</span><span class="sxs-lookup"><span data-stu-id="c9155-134">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="c9155-135">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="c9155-135">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="c9155-136">Pobierz ciąg połączenia bazy danych Azure rozwiązania Cosmos</span><span class="sxs-lookup"><span data-stu-id="c9155-136">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="c9155-137">Jeśli łączysz się do bazy danych rozwiązania Cosmos Azure, konieczne będzie parametrów połączenia w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="c9155-137">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="c9155-138">Parametry połączenia można skopiować z portalu Azure.</span><span class="sxs-lookup"><span data-stu-id="c9155-138">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="c9155-139">W portalu Azure, na Twoim koncie rozwiązania Cosmos bazy danych, przejdź do **ustawienia** > **ciąg połączenia**i kliknij przycisk **kopiowania** przycisk, aby skopiować podstawowego połączenia Ciąg.</span><span class="sxs-lookup"><span data-stu-id="c9155-139">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="c9155-140">Samouczek wprowadź parametry połączenia za pomocą skryptu, jak w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c9155-140">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="c9155-141">Jest to jednak **niezalecane** rzeczywiste projektów.</span><span class="sxs-lookup"><span data-stu-id="c9155-141">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="c9155-142">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="c9155-142">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="c9155-143">Zawsze starannie Chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="c9155-143">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="c9155-144">Unikaj udostępniaj go innym użytkownikom, kodować je lub zapisać go w pliku jako zwykły tekst, który jest dostępny do innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="c9155-144">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="c9155-145">Można ponownie wygenerować klucz przy użyciu portalu Azure, jeśli uważasz, że mogą zostać naruszone.</span><span class="sxs-lookup"><span data-stu-id="c9155-145">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="c9155-146">Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c9155-146">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="c9155-147">Aby pobrać parametry połączenia w pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="c9155-147">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="c9155-148">Przy użyciu programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="c9155-148">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="c9155-149">Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="c9155-149">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="c9155-150">Przeanalizować parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="c9155-150">Parse the connection string</span></span>

<span data-ttu-id="c9155-151">Aby przeanalizować parametrów połączenia, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="c9155-151">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="c9155-152">To polecenie zwróci `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="c9155-152">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="c9155-153">Tworzenie klienta usługi tabel</span><span class="sxs-lookup"><span data-stu-id="c9155-153">Create the Table service client</span></span>

<span data-ttu-id="c9155-154">`CloudTableClient` Klasa umożliwia pobieranie tabel i jednostek w magazynie tabel.</span><span class="sxs-lookup"><span data-stu-id="c9155-154">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="c9155-155">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="c9155-155">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="c9155-156">Teraz można przystąpić do pisania kodu, która odczytuje i zapisuje dane do magazynu tabel.</span><span class="sxs-lookup"><span data-stu-id="c9155-156">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="c9155-157">Utwórz tabelę</span><span class="sxs-lookup"><span data-stu-id="c9155-157">Create a table</span></span>

<span data-ttu-id="c9155-158">W tym przykładzie pokazano, jak utworzyć tabelę, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="c9155-158">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="c9155-159">Dodawanie jednostki do tabeli</span><span class="sxs-lookup"><span data-stu-id="c9155-159">Add an entity to a table</span></span>

<span data-ttu-id="c9155-160">Jednostka musi mieć typ, który dziedziczy z `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="c9155-160">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="c9155-161">Można rozszerzyć `TableEntity` w żaden sposób Ci się podoba, ale danego typu *musi* ma konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="c9155-161">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="c9155-162">Tylko te właściwości, które mają zarówno `get` i `set` są przechowywane w tabeli platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="c9155-162">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="c9155-163">Jednostka partycji i klucz wiersza jednostki jednoznacznie identyfikują jednostkę w tabeli.</span><span class="sxs-lookup"><span data-stu-id="c9155-163">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="c9155-164">Jednostki z tym samym kluczem partycji mogą być przeszukiwane szybciej niż jednostki o różnych kluczach partycji, ale przy użyciu różnych kluczy partycji umożliwia zwiększenie skalowalności operacji równoległych.</span><span class="sxs-lookup"><span data-stu-id="c9155-164">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="c9155-165">Oto przykład `Customer` używającą `lastName` jako klucza partycji i `firstName` jako klucz wiersza.</span><span class="sxs-lookup"><span data-stu-id="c9155-165">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="c9155-166">Teraz Dodaj `Customer` do tabeli.</span><span class="sxs-lookup"><span data-stu-id="c9155-166">Now add `Customer` to the table.</span></span> <span data-ttu-id="c9155-167">Aby to zrobić, należy utworzyć `TableOperation` , który jest wykonywany w tabeli.</span><span class="sxs-lookup"><span data-stu-id="c9155-167">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="c9155-168">W takim przypadku należy utworzyć `Insert` operacji.</span><span class="sxs-lookup"><span data-stu-id="c9155-168">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="c9155-169">Wstawić partię jednostek</span><span class="sxs-lookup"><span data-stu-id="c9155-169">Insert a batch of entities</span></span>

<span data-ttu-id="c9155-170">Można wstawić partię jednostek do tabeli za pomocą operacji zapisu pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="c9155-170">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="c9155-171">Operacje partii pozwalają połączyć operacje w pojedynczej operacji, ale mają pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="c9155-171">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="c9155-172">Możesz przeprowadzić aktualizację, usuwanie i wstawianie w tej samej operacji zbiorczej.</span><span class="sxs-lookup"><span data-stu-id="c9155-172">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="c9155-173">Operacja zbiorcza może zawierać maksymalnie 100 jednostek.</span><span class="sxs-lookup"><span data-stu-id="c9155-173">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="c9155-174">Wszystkie jednostki w operacji zbiorczej muszą mieć ten sam klucz partycji.</span><span class="sxs-lookup"><span data-stu-id="c9155-174">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="c9155-175">W trakcie można wykonać zapytania w operacji zbiorczej musi być jedyną operacją w partii.</span><span class="sxs-lookup"><span data-stu-id="c9155-175">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="c9155-176">Oto niektóre kod, który łączy dwie wstawki w operacji zbiorczej:</span><span class="sxs-lookup"><span data-stu-id="c9155-176">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="c9155-177">Pobieranie wszystkich jednostek w partycji</span><span class="sxs-lookup"><span data-stu-id="c9155-177">Retrieve all entities in a partition</span></span>

<span data-ttu-id="c9155-178">Aby sprawdzić tabelę dla wszystkich jednostek w partycji, użyj `TableQuery` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c9155-178">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="c9155-179">W tym miejscu można filtrować dla jednostek gdzie "Smith" jest kluczem partycji.</span><span class="sxs-lookup"><span data-stu-id="c9155-179">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="c9155-180">Teraz drukowanie wyników:</span><span class="sxs-lookup"><span data-stu-id="c9155-180">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="c9155-181">Pobieranie zakresu jednostek w partycji</span><span class="sxs-lookup"><span data-stu-id="c9155-181">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="c9155-182">Jeśli nie chcesz zbadać wszystkich jednostek w partycji, można określić zakres, łącząc filtr klucza partycji z filtrem klucza wiersza.</span><span class="sxs-lookup"><span data-stu-id="c9155-182">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="c9155-183">W tym miejscu służy dwa filtry do pobrania wszystkich jednostek w partycji "Smith" gdzie klucz wiersza (imię) rozpoczyna się od litery wcześniejszej niż "M" alfabetu.</span><span class="sxs-lookup"><span data-stu-id="c9155-183">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="c9155-184">Teraz drukowanie wyników:</span><span class="sxs-lookup"><span data-stu-id="c9155-184">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="c9155-185">Pobieranie pojedynczej jednostki</span><span class="sxs-lookup"><span data-stu-id="c9155-185">Retrieve a single entity</span></span>

<span data-ttu-id="c9155-186">Można napisać zapytanie do pobrania jednej, określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="c9155-186">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="c9155-187">W tym miejscu użyć `TableOperation` do określenia klienta "Ben Smith".</span><span class="sxs-lookup"><span data-stu-id="c9155-187">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="c9155-188">Zamiast kolekcji, możesz wrócić `Customer`.</span><span class="sxs-lookup"><span data-stu-id="c9155-188">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="c9155-189">Określenie zarówno klucz partycji i klucz wiersza w zapytaniu jest najszybszym sposobem na pobranie jednej jednostki z usługi tabel.</span><span class="sxs-lookup"><span data-stu-id="c9155-189">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="c9155-190">Teraz drukowanie wyników:</span><span class="sxs-lookup"><span data-stu-id="c9155-190">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a><span data-ttu-id="c9155-191">Zastępowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="c9155-191">Replace an entity</span></span>

<span data-ttu-id="c9155-192">Aby zaktualizować jednostkę, pobierz ją z usługi tabel, zmodyfikuj obiekt jednostki, a następnie zapisz zmiany powrót do tabeli usługi przy użyciu `Replace` operacji.</span><span class="sxs-lookup"><span data-stu-id="c9155-192">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="c9155-193">Powoduje to, że jednostka będzie całkowicie zastąpiona na serwerze, chyba że jednostka na serwerze została zmieniona, ponieważ został on pobrany, w którym to przypadku kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c9155-193">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="c9155-194">Jest to błąd uniemożliwia aplikacji nieodwracalne nadpisanie zmiany z innych źródeł.</span><span class="sxs-lookup"><span data-stu-id="c9155-194">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="c9155-195">Wstawianie lub zastępowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="c9155-195">Insert-or-replace an entity</span></span>

<span data-ttu-id="c9155-196">Czasami nie wiadomo, czy obiekt istnieje w tabeli.</span><span class="sxs-lookup"><span data-stu-id="c9155-196">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="c9155-197">A jeśli tak, czy obecne wartości przechowywane w nim nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="c9155-197">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="c9155-198">Można użyć `InsertOrReplace` w celu utworzenia jednostki lub zastąp ją, jeśli istnieje, niezależnie od jego stanu.</span><span class="sxs-lookup"><span data-stu-id="c9155-198">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="c9155-199">Tworzenie zapytania do podzbioru właściwości jednostki</span><span class="sxs-lookup"><span data-stu-id="c9155-199">Query a subset of entity properties</span></span>

<span data-ttu-id="c9155-200">Zapytanie tabeli może pobrać kilka właściwości jednostki zamiast wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="c9155-200">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="c9155-201">Ta technika, zwana projekcją, może poprawić wydajność zapytań, zwłaszcza w przypadku dużych jednostek.</span><span class="sxs-lookup"><span data-stu-id="c9155-201">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="c9155-202">W tym miejscu zwracać dotyczy tylko wiadomości e-mail przy użyciu `DynamicTableEntity` i `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="c9155-202">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="c9155-203">Należy pamiętać, że projekcji nie jest obsługiwana w lokalnym emulatorze magazynu, dlatego ten kod zadziała tylko wtedy, gdy używasz konta w usłudze tabel.</span><span class="sxs-lookup"><span data-stu-id="c9155-203">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="c9155-204">Pobieranie asynchroniczne jednostek na stronach</span><span class="sxs-lookup"><span data-stu-id="c9155-204">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="c9155-205">Jeśli odczytujesz dużą liczbę jednostek i chcesz przetworzyć je zgodnie z ich pobraniu, zamiast oczekiwania na zwrócenie ich wszystkich, można użyć zapytania segmentowanego.</span><span class="sxs-lookup"><span data-stu-id="c9155-205">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="c9155-206">W tym miejscu możesz zwracania wyników na stronach za pomocą async przepływu pracy, dzięki czemu wykonanie nie jest blokowane podczas oczekiwania dla dużych zestawów wyników do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="c9155-206">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="c9155-207">Można teraz wykonywać te obliczenia synchronicznie:</span><span class="sxs-lookup"><span data-stu-id="c9155-207">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="c9155-208">Usuwanie jednostki</span><span class="sxs-lookup"><span data-stu-id="c9155-208">Delete an entity</span></span>

<span data-ttu-id="c9155-209">Po jej pobraniu, można usunąć jednostki.</span><span class="sxs-lookup"><span data-stu-id="c9155-209">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="c9155-210">Podobnie jak w przypadku aktualizowania jednostki, to nie powiedzie się, jeśli jednostka została zmieniona od czasu jej pobrania.</span><span class="sxs-lookup"><span data-stu-id="c9155-210">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="c9155-211">Usuwanie tabeli</span><span class="sxs-lookup"><span data-stu-id="c9155-211">Delete a table</span></span>

<span data-ttu-id="c9155-212">Z konta magazynu można usunąć tabeli.</span><span class="sxs-lookup"><span data-stu-id="c9155-212">You can delete a table from a storage account.</span></span> <span data-ttu-id="c9155-213">Tabela, która została usunięta będzie mógł zostać ponownie utworzone w danym okresie czasu po jej usunięciu.</span><span class="sxs-lookup"><span data-stu-id="c9155-213">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="c9155-214">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="c9155-214">Next steps</span></span>

<span data-ttu-id="c9155-215">Teraz, kiedy znasz już podstawy magazynu tabel, skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu i interfejsu API Azure rozwiązania Cosmos bazy danych tabeli.</span><span class="sxs-lookup"><span data-stu-id="c9155-215">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="c9155-216">Wprowadzenie do platformy Azure rozwiązania Cosmos API tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="c9155-216">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="c9155-217">Biblioteka klienta usługi Storage dla platformy .NET odwołania</span><span class="sxs-lookup"><span data-stu-id="c9155-217">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="c9155-218">Dostawca typów magazynu Azure</span><span class="sxs-lookup"><span data-stu-id="c9155-218">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="c9155-219">Azure Storage Team Blog</span><span class="sxs-lookup"><span data-stu-id="c9155-219">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="c9155-220">Konfigurowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="c9155-220">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="c9155-221">Rozpoczynanie pracy z magazynem tabel Azure w .NET</span><span class="sxs-lookup"><span data-stu-id="c9155-221">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
