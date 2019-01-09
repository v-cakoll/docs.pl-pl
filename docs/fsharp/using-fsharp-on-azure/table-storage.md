---
title: Rozpoczynanie pracy z usługą Azure Table storage przy użyciuF#
description: Store ustrukturyzowanych danych w chmurze przy użyciu usługi Azure Table storage lub Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 45a5d845dcedb5c3ea07cc4540f66bad23338a88
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152076"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="2f3e3-103">Rozpoczynanie pracy z usługą Azure Table storage i przy użyciu interfejsu API tabeli usługi Azure Cosmos DBF#</span><span class="sxs-lookup"><span data-stu-id="2f3e3-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F#</span></span> # 

<span data-ttu-id="2f3e3-104">Usługa Azure Table storage to usługa, która przechowuje dane strukturalne NoSQL w chmurze.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="2f3e3-105">Magazyn tabel to magazyn klucz/atrybutów bez schematu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="2f3e3-106">Ponieważ Magazyn tabel nie ma, to można łatwo zaadaptować dane aplikacji rozwijających się potrzeb.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="2f3e3-107">Dostęp do danych jest szybki i ekonomiczny dla wszystkich rodzajów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="2f3e3-108">Magazyn tabel jest zwykle znacznie tańszy od tradycyjnego rozwiązania SQL dla podobnych ilości danych.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="2f3e3-109">Magazyn tabel umożliwia przechowywanie elastycznych zestawów danych, takich jak dane użytkownika dla aplikacji sieci web, książek adresowych, informacji o urządzeniach i inne rodzaje metadanych, których wymaga Twoja usługa.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="2f3e3-110">Dowolną liczbę jednostek można przechowywać w tabeli, a konto magazynu może zawierać dowolną liczbę tabel w granicach pojemności konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="2f3e3-111">Usługa Azure Cosmos DB zapewnia interfejs API tabel dla aplikacji korzystających z usługi Azure Table Storage, które wymagają funkcji warstwy premium takich jak:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="2f3e3-112">Kompleksowa dystrybucja globalna.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="2f3e3-113">Dedykowana przepływność na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="2f3e3-114">Milisekundowe opóźnienia w 99. percentylu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="2f3e3-115">Gwarantowana wysoka dostępność.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="2f3e3-116">Automatyczne indeksowanie pomocnicze.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="2f3e3-117">Aplikacje napisane dla usługi Azure Table storage można migrować do usługi Azure Cosmos DB przy użyciu interfejsu API tabel bez zmian w kodzie i mogą korzystać z funkcji premium.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="2f3e3-118">Interfejs API tabel udostępnia dostępne zestawy SDK klientów, dla platformy .NET, Java, Python i Node.js.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="2f3e3-119">Aby uzyskać więcej informacji, zobacz [wprowadzenie do interfejsu API tabeli usługi Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="2f3e3-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="2f3e3-120">Informacje o tym samouczku</span><span class="sxs-lookup"><span data-stu-id="2f3e3-120">About this tutorial</span></span>

<span data-ttu-id="2f3e3-121">Ten samouczek przedstawia sposób zapisania F# kod, aby wykonywać niektóre typowe zadania za pomocą usługi Azure Table storage lub Azure Cosmos DB interfejsu API tabel, w tym tworzenie i usuwanie tabeli i wstawianie, aktualizowanie, usuwanie i odpytywanie danych tabeli.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2f3e3-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="2f3e3-122">Prerequisites</span></span>

<span data-ttu-id="2f3e3-123">Aby użyć tego przewodnika, należy najpierw [Tworzenie konta usługi Azure storage](/azure/storage/storage-create-storage-account) lub [konta usługi Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="2f3e3-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>


## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="2f3e3-124">Tworzenie F# skrypt i uruchomić F# interaktywne</span><span class="sxs-lookup"><span data-stu-id="2f3e3-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="2f3e3-125">Przykłady w tym artykule mogą być używane w jednej F# aplikacji lub F# skryptu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="2f3e3-126">Aby utworzyć F# skrypt, Utwórz plik o `.fsx` rozszerzenia, na przykład `tables.fsx`w usługi F# środowiska deweloperskiego.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="2f3e3-127">Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) zainstalował `WindowsAzure.Storage` pakietów i odwołań `WindowsAzure.Storage.dll` w skrypcie za pomocą `#r`dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="2f3e3-128">Wykonaj ponownie ją `Microsoft.WindowsAzure.ConfigurationManager` celu uzyskanie Microsoft.Azure przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="2f3e3-129">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="2f3e3-129">Add namespace declarations</span></span>

<span data-ttu-id="2f3e3-130">Dodaj następujący kod `open` instrukcji na górze `tables.fsx` pliku:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="2f3e3-131">Pobieranie parametrów połączenia usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="2f3e3-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="2f3e3-132">Jeśli łączysz się do usługi Azure Storage Table, konieczne będzie parametry połączenia na potrzeby tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="2f3e3-133">Parametry połączenia można skopiować z witryny Azure portal.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="2f3e3-134">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="2f3e3-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="2f3e3-135">Pobieranie parametrów połączenia usługi Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="2f3e3-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="2f3e3-136">Jeśli łączysz się do usługi Azure Cosmos DB, konieczne będzie parametry połączenia na potrzeby tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="2f3e3-137">Parametry połączenia można skopiować z witryny Azure portal.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="2f3e3-138">W witrynie Azure portal w ramach konta usługi Cosmos DB, przejdź do **ustawienia** > **parametry połączenia**i kliknij przycisk **kopiowania** przycisk, aby skopiować podstawowe połączenie Ciąg.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="2f3e3-139">Samouczek należy wprowadzić parametry połączenia w skrypcie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="2f3e3-140">Jest to jednak **niezalecane** rzeczywiste projektów.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="2f3e3-141">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="2f3e3-142">Zawsze starannie Chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="2f3e3-143">Należy unikać, ich dystrybucję w innym użytkownikom, kodować je lub zapisanie go w pliku tekstowego, który jest dostępny dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="2f3e3-144">Można ponownie wygenerować klucz za pośrednictwem witryny Azure Portal, jeśli uważasz, że mogą zostać przejęte.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="2f3e3-145">Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="2f3e3-146">Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="2f3e3-147">Użycie programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="2f3e3-148">Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="2f3e3-149">Przeanalizować parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="2f3e3-149">Parse the connection string</span></span>

<span data-ttu-id="2f3e3-150">Aby przeanalizować parametrów połączenia, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="2f3e3-151">Spowoduje to zwrócenie `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="2f3e3-152">Tworzenie klienta usługi Table service</span><span class="sxs-lookup"><span data-stu-id="2f3e3-152">Create the Table service client</span></span>

<span data-ttu-id="2f3e3-153">`CloudTableClient` Klasy umożliwia pobieranie tabel i jednostek w usłudze Table storage.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="2f3e3-154">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="2f3e3-155">Teraz możesz przystąpić do pisania kodu, który odczytuje dane z i zapisuje dane w usłudze Table storage.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="2f3e3-156">Tworzenie tabeli</span><span class="sxs-lookup"><span data-stu-id="2f3e3-156">Create a table</span></span>

<span data-ttu-id="2f3e3-157">Ten przykład pokazuje, jak utworzyć tabelę, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="2f3e3-158">Dodawanie jednostki do tabeli</span><span class="sxs-lookup"><span data-stu-id="2f3e3-158">Add an entity to a table</span></span>

<span data-ttu-id="2f3e3-159">Określona jednostka ma typ, który dziedziczy z `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="2f3e3-160">Możesz rozszerzyć `TableEntity` w jakikolwiek sposób, chcesz, ale typu *musi* ma konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="2f3e3-161">Tylko te właściwości, które mają zarówno `get` i `set` są przechowywane w tabeli platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="2f3e3-162">Jednostka partycji i klucz wiersza jednoznacznie identyfikują jednostkę w tabeli.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="2f3e3-163">Jednostki z tym samym kluczem partycji, które mogą być przeszukiwane szybciej niż te o różnych kluczach partycji, ale użycie różnych kluczy partycji umożliwia zwiększenie skalowalności operacji równoległych.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="2f3e3-164">Oto przykład `Customer` , który używa `lastName` jako klucza partycji i `firstName` jako klucz wiersza.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="2f3e3-165">Teraz Dodaj `Customer` do tabeli.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="2f3e3-166">Aby to zrobić, należy utworzyć `TableOperation` , który jest wykonywany w tabeli.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="2f3e3-167">W takim przypadku należy utworzyć `Insert` operacji.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="2f3e3-168">Wstawić partię jednostek</span><span class="sxs-lookup"><span data-stu-id="2f3e3-168">Insert a batch of entities</span></span>

<span data-ttu-id="2f3e3-169">Możesz wstawić partię jednostek do tabeli za pomocą operacji zapisu w jednym.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="2f3e3-170">Operacji wsadowych pozwalają na łączenie operacji na pojedyncze wykonanie, ale mają pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="2f3e3-171">Możesz przeprowadzić aktualizację, usuwanie i wstawianie w jednej operacji wsadowej.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="2f3e3-172">Operacja zbiorcza może zawierać do 100 jednostek.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="2f3e3-173">Wszystkie jednostki w operacji zbiorczej muszą mieć ten sam klucz partycji.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="2f3e3-174">Choć jest możliwe do wykonania zapytania w operacji zbiorczej, należy wykonać tylko w partii.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="2f3e3-175">Poniżej przedstawiono niektóre kodu, który łączy dwie wstawki w operacji zbiorczej:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="2f3e3-176">Pobieranie wszystkich jednostek w partycji</span><span class="sxs-lookup"><span data-stu-id="2f3e3-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="2f3e3-177">Aby wysłać zapytanie do tabeli dla wszystkich jednostek w partycji, należy użyć `TableQuery` obiektu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="2f3e3-178">W tym miejscu możesz filtrować dla obiektów gdzie "Smith" jest kluczem partycji.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="2f3e3-179">Teraz możesz wydrukować wyniki:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="2f3e3-180">Pobieranie zakresu jednostek w partycji</span><span class="sxs-lookup"><span data-stu-id="2f3e3-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="2f3e3-181">Jeśli nie chcesz wykonywać zapytania dla wszystkich jednostek w partycji, można określić zakres, łącząc filtr klucza partycji z filtrem klucza wiersza.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="2f3e3-182">Używamy tutaj dwa filtry do pobrania wszystkich jednostek w partycji "Smith" gdzie klucz wiersza (imię) rozpoczyna się od litery starszych niż "M" alfabetu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="2f3e3-183">Teraz możesz wydrukować wyniki:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="2f3e3-184">Pobieranie pojedynczej jednostki</span><span class="sxs-lookup"><span data-stu-id="2f3e3-184">Retrieve a single entity</span></span>

<span data-ttu-id="2f3e3-185">Można napisać zapytanie w celu pobrania jednej, określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="2f3e3-186">W tym miejscu możesz użyć `TableOperation` do określenia klienta "Ben Smith".</span><span class="sxs-lookup"><span data-stu-id="2f3e3-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="2f3e3-187">Zamiast kolekcji, można wrócić `Customer`.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="2f3e3-188">Określenie klucza partycji i klucz wiersza w zapytaniu jest najszybszym sposobem na pobranie jednej jednostki z usługi tabel.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="2f3e3-189">Teraz możesz wydrukować wyniki:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a><span data-ttu-id="2f3e3-190">Zastępowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="2f3e3-190">Replace an entity</span></span>

<span data-ttu-id="2f3e3-191">Aby zaktualizować jednostkę, pobierz ją z usługi tabel, zmodyfikuj obiekt jednostki i następnie zapisz zmiany z powrotem do tabeli usługi przy użyciu `Replace` operacji.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="2f3e3-192">To powoduje, że jednostka będzie całkowicie zastąpiona na serwerze, chyba że jednostka na serwerze zmieniła się od czasu jej pobrania, w którym to przypadku kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="2f3e3-193">Jest ten błąd uniemożliwia aplikacji nieodwracalne nadpisanie zmiany z innych źródeł.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="2f3e3-194">Wstawianie lub zastępowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="2f3e3-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="2f3e3-195">Czasami nie wiadomo, czy obiekt istnieje w tabeli.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="2f3e3-196">A jeśli tak jest, czy obecne wartości przechowywane w nim nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="2f3e3-197">Możesz użyć `InsertOrReplace` utworzyć jednostkę, lub zastąp ją, jeśli istnieje, niezależnie od jego stanu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="2f3e3-198">Tworzenie zapytania do podzbioru właściwości jednostki</span><span class="sxs-lookup"><span data-stu-id="2f3e3-198">Query a subset of entity properties</span></span>

<span data-ttu-id="2f3e3-199">Zapytanie tabeli może pobrać kilka właściwości jednostki zamiast wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="2f3e3-200">Ta technika, zwana projekcją, może poprawić wydajność zapytań, szczególnie w przypadku dużych jednostek.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="2f3e3-201">W tym miejscu zwrócić tylko wiadomości e-mail, adresy, za pomocą `DynamicTableEntity` i `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="2f3e3-202">Należy pamiętać, że projekcji nie jest obsługiwana w emulatorze magazynu lokalnego, dlatego ten kod zadziała tylko wtedy, gdy używasz konta w usłudze tabel.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="2f3e3-203">Pobieranie asynchroniczne jednostek na stronach</span><span class="sxs-lookup"><span data-stu-id="2f3e3-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="2f3e3-204">Jeśli odczytujesz dużą liczbę jednostek i chcesz je przetworzyć, ich pobraniu, zamiast oczekiwanie na zwrócenie ich wszystkich, można użyć zapytania segmentowanego.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="2f3e3-205">W tym miejscu możesz zwracania wyników na stronach za pomocą asynchronicznego przepływu pracy, dzięki czemu wykonanie nie jest blokowane podczas oczekiwania dużych zestawów wyników do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="2f3e3-206">Możesz teraz wykonać to obliczenie synchronicznie:</span><span class="sxs-lookup"><span data-stu-id="2f3e3-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="2f3e3-207">Usunięcie jednostki</span><span class="sxs-lookup"><span data-stu-id="2f3e3-207">Delete an entity</span></span>

<span data-ttu-id="2f3e3-208">Można usunąć jednostkę po jej pobraniu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="2f3e3-209">Podobnie jak w przypadku aktualizowania jednostki, to nie powiedzie się jeśli jednostka zmieniła się od pobrano go.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="2f3e3-210">Usuwanie tabeli</span><span class="sxs-lookup"><span data-stu-id="2f3e3-210">Delete a table</span></span>

<span data-ttu-id="2f3e3-211">Możesz usunąć tabelę z konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="2f3e3-212">Tabela, która została usunięta, będą niedostępne, można ponownie utworzyć w okresie czasu po jej usunięciu.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="2f3e3-213">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="2f3e3-213">Next steps</span></span>

<span data-ttu-id="2f3e3-214">Teraz, kiedy znasz już podstawy usługi Table storage, skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu i interfejsu API tabeli usługi Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="2f3e3-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="2f3e3-215">Wprowadzenie do usługi Azure Cosmos DB Table API</span><span class="sxs-lookup"><span data-stu-id="2f3e3-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="2f3e3-216">Biblioteka klienta usługi Storage dla platformy .NET odwołania</span><span class="sxs-lookup"><span data-stu-id="2f3e3-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="2f3e3-217">Dostawcy typów usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="2f3e3-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="2f3e3-218">Blog zespołu usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="2f3e3-218">Azure Storage Team Blog</span></span>](https://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="2f3e3-219">Konfigurowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="2f3e3-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="2f3e3-220">Wprowadzenie do usługi Azure Table Storage na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="2f3e3-220">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
