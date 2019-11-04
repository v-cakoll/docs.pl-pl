---
title: Rozpoczynanie pracy z usługą Azure Table Storage przy użyciu języka F#
description: Przechowuj dane strukturalne w chmurze przy użyciu usługi Azure Table Storage lub Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 6833e2264f7543f50b94892b6980140e4bf1cdd1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424608"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="3a273-103">Rozpoczynanie pracy z usługą Azure Table Storage i interfejs API tabel Azure Cosmos DB przy użyciu języka F\#</span><span class="sxs-lookup"><span data-stu-id="3a273-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F\#</span></span>

<span data-ttu-id="3a273-104">Azure Table Storage to usługa, która przechowuje strukturalne dane NoSQL w chmurze.</span><span class="sxs-lookup"><span data-stu-id="3a273-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="3a273-105">Magazyn tabel jest magazynem kluczy/atrybutów z projektem bez schematu.</span><span class="sxs-lookup"><span data-stu-id="3a273-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="3a273-106">Ponieważ magazyn tabel jest bezschematowy, można łatwo dostosować dane w miarę rozwoju aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a273-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="3a273-107">Dostęp do danych jest szybki i opłacalny dla wszystkich rodzajów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a273-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="3a273-108">Magazyn tabel jest zwykle znacząco niższy niż tradycyjny kod SQL dla podobnych ilości danych.</span><span class="sxs-lookup"><span data-stu-id="3a273-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="3a273-109">Usługa Table Storage umożliwia przechowywanie elastycznych zestawów danych, takich jak dane użytkowników dla aplikacji sieci Web, książek adresowych, informacji o urządzeniach i innych typów metadanych wymaganych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="3a273-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="3a273-110">Można przechowywać dowolną liczbę jednostek w tabeli, a konto magazynu może zawierać dowolną liczbę tabel, aż do limitu pojemności konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="3a273-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="3a273-111">Azure Cosmos DB zapewnia interfejs API tabel dla aplikacji, które są przeznaczone dla usługi Azure Table Storage, które wymagają funkcji premium, takich jak:</span><span class="sxs-lookup"><span data-stu-id="3a273-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="3a273-112">Gotowe globalna.</span><span class="sxs-lookup"><span data-stu-id="3a273-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="3a273-113">Dedykowana przepływność na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="3a273-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="3a273-114">Opóźnienia o pojedynczej liczbie milisekund w 99 percentylu.</span><span class="sxs-lookup"><span data-stu-id="3a273-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="3a273-115">Gwarantowana wysoka dostępność.</span><span class="sxs-lookup"><span data-stu-id="3a273-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="3a273-116">Automatyczne indeksowanie pomocnicze.</span><span class="sxs-lookup"><span data-stu-id="3a273-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="3a273-117">Aplikacje przeznaczone dla usługi Azure Table Storage można migrować do Azure Cosmos DB przy użyciu interfejs API tabel bez zmian w kodzie i korzystać z funkcji Premium.</span><span class="sxs-lookup"><span data-stu-id="3a273-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="3a273-118">Interfejs API tabel udostępnia zestawy SDK klienta dostępne dla platform .NET, Java, Python i Node. js.</span><span class="sxs-lookup"><span data-stu-id="3a273-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="3a273-119">Aby uzyskać więcej informacji, zobacz [wprowadzenie do Azure Cosmos DB interfejs API tabel](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="3a273-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="3a273-120">Informacje o tym samouczku</span><span class="sxs-lookup"><span data-stu-id="3a273-120">About this tutorial</span></span>

<span data-ttu-id="3a273-121">W tym samouczku pokazano, F# jak napisać kod, aby wykonać kilka typowych zadań za pomocą usługi Azure Table storage lub interfejs API tabel Azure Cosmos DB, w tym tworzenie i usuwanie tabeli oraz wstawianie, aktualizowanie, usuwanie i wykonywanie zapytań dotyczących danych tabeli.</span><span class="sxs-lookup"><span data-stu-id="3a273-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a273-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="3a273-122">Prerequisites</span></span>

<span data-ttu-id="3a273-123">Aby skorzystać z tego przewodnika, musisz najpierw [utworzyć konto usługi Azure Storage](/azure/storage/storage-create-storage-account) lub [konto Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="3a273-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="3a273-124">Utwórz F# skrypt i uruchom F# interaktywny</span><span class="sxs-lookup"><span data-stu-id="3a273-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="3a273-125">Przykłady w tym artykule mogą być używane w F# aplikacji lub F# skrypcie.</span><span class="sxs-lookup"><span data-stu-id="3a273-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="3a273-126">Aby utworzyć F# skrypt, Utwórz plik z rozszerzeniem `.fsx`, na przykład `tables.fsx` w środowisku F# deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="3a273-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="3a273-127">Następnie należy użyć [Menedżera pakietów](package-management.md) , takiego jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) , aby zainstalować pakiet `WindowsAzure.Storage` i odwołanie `WindowsAzure.Storage.dll` w skrypcie przy użyciu dyrektywy `#r`.</span><span class="sxs-lookup"><span data-stu-id="3a273-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="3a273-128">Zrób to ponownie dla `Microsoft.WindowsAzure.ConfigurationManager` w celu uzyskania przestrzeni nazw Microsoft. Azure.</span><span class="sxs-lookup"><span data-stu-id="3a273-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="3a273-129">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="3a273-129">Add namespace declarations</span></span>

<span data-ttu-id="3a273-130">Dodaj następujące instrukcje `open` na początku pliku `tables.fsx`:</span><span class="sxs-lookup"><span data-stu-id="3a273-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="3a273-131">Pobieranie parametrów połączenia usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="3a273-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="3a273-132">W przypadku nawiązywania połączenia z usługą Azure Storage Table service potrzebne są parametry połączenia dla tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="3a273-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="3a273-133">Parametry połączenia można skopiować z Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="3a273-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="3a273-134">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [Konfigurowanie parametrów połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="3a273-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="3a273-135">Pobierz parametry połączenia Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="3a273-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="3a273-136">W przypadku nawiązywania połączenia z usługą Azure Cosmos DB potrzebne są parametry połączenia dla tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="3a273-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="3a273-137">Parametry połączenia można skopiować z Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="3a273-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="3a273-138">W Azure Portal na koncie Cosmos DB przejdź do pozycji **ustawienia** > **Parametry połączenia**, a następnie kliknij przycisk **Kopiuj** , aby skopiować podstawowe parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="3a273-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span>

<span data-ttu-id="3a273-139">Dla samouczka wprowadź parametry połączenia w skrypcie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a273-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="3a273-140">Nie jest to jednak **zalecane** w przypadku rzeczywistych projektów.</span><span class="sxs-lookup"><span data-stu-id="3a273-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="3a273-141">Klucz konta magazynu jest podobny do hasła głównego dla konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="3a273-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="3a273-142">Zawsze należy zachować ostrożność, aby chronić klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="3a273-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="3a273-143">Należy unikać dystrybuowania go do innych użytkowników, ich trwałego kodowania lub zapisywania w pliku w formacie zwykłego tekstu, który jest dostępny dla innych.</span><span class="sxs-lookup"><span data-stu-id="3a273-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="3a273-144">Możesz ponownie wygenerować klucz za pomocą witryny Azure Portal, jeśli uważasz, że jego zabezpieczenia mogły zostać naruszone.</span><span class="sxs-lookup"><span data-stu-id="3a273-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="3a273-145">W przypadku prawdziwych aplikacji najlepszym sposobem obsługi parametrów połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3a273-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="3a273-146">Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="3a273-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="3a273-147">Korzystanie z usługi Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="3a273-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="3a273-148">Można również użyć interfejsu API, takiego jak typ `ConfigurationManager` .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3a273-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="3a273-149">Analizowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="3a273-149">Parse the connection string</span></span>

<span data-ttu-id="3a273-150">Aby przeanalizować parametry połączenia, użyj:</span><span class="sxs-lookup"><span data-stu-id="3a273-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="3a273-151">Zwraca `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="3a273-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="3a273-152">Tworzenie klienta Table service</span><span class="sxs-lookup"><span data-stu-id="3a273-152">Create the Table service client</span></span>

<span data-ttu-id="3a273-153">Klasa `CloudTableClient` umożliwia pobieranie tabel i jednostek w magazynie tabel.</span><span class="sxs-lookup"><span data-stu-id="3a273-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="3a273-154">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="3a273-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="3a273-155">Teraz możesz przystąpić do pisania kodu, który odczytuje dane z magazynu tabel i zapisuje je.</span><span class="sxs-lookup"><span data-stu-id="3a273-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="3a273-156">Tworzenie tabeli</span><span class="sxs-lookup"><span data-stu-id="3a273-156">Create a table</span></span>

<span data-ttu-id="3a273-157">Ten przykład pokazuje, jak utworzyć tabelę, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="3a273-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="3a273-158">Dodawanie jednostki do tabeli</span><span class="sxs-lookup"><span data-stu-id="3a273-158">Add an entity to a table</span></span>

<span data-ttu-id="3a273-159">Jednostka musi mieć typ, który dziedziczy po `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="3a273-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="3a273-160">Możesz w dowolny sposób rozciągnąć `TableEntity`, ale typ *musi* mieć konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="3a273-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="3a273-161">W tabeli platformy Azure są przechowywane tylko właściwości `get` i `set`.</span><span class="sxs-lookup"><span data-stu-id="3a273-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="3a273-162">Partycja i klucz wiersza jednostki jednoznacznie identyfikują jednostkę w tabeli.</span><span class="sxs-lookup"><span data-stu-id="3a273-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="3a273-163">Jednostki z tym samym kluczem partycji mogą być przeszukiwane szybciej niż te z różnymi kluczami partycji, ale użycie różnych kluczy partycji umożliwia zwiększenie skalowalności operacji równoległych.</span><span class="sxs-lookup"><span data-stu-id="3a273-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="3a273-164">Oto przykład `Customer`, który używa `lastName` jako klucza partycji i `firstName` jako klucza wiersza.</span><span class="sxs-lookup"><span data-stu-id="3a273-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="3a273-165">Teraz Dodaj `Customer` do tabeli.</span><span class="sxs-lookup"><span data-stu-id="3a273-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="3a273-166">W tym celu należy utworzyć `TableOperation`, która jest wykonywana na tabeli.</span><span class="sxs-lookup"><span data-stu-id="3a273-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="3a273-167">W takim przypadku należy utworzyć operację `Insert`.</span><span class="sxs-lookup"><span data-stu-id="3a273-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="3a273-168">Wstawianie partii jednostek</span><span class="sxs-lookup"><span data-stu-id="3a273-168">Insert a batch of entities</span></span>

<span data-ttu-id="3a273-169">Można wstawić partię jednostek do tabeli przy użyciu jednej operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="3a273-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="3a273-170">Operacje wsadowe umożliwiają łączenie operacji w pojedynczym wykonaniu, ale mają pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="3a273-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="3a273-171">Można wykonywać aktualizacje, usuwać i wstawiać w tej samej operacji wsadowej.</span><span class="sxs-lookup"><span data-stu-id="3a273-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="3a273-172">Operacja wsadowa może obejmować do 100 jednostek.</span><span class="sxs-lookup"><span data-stu-id="3a273-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="3a273-173">Wszystkie jednostki w operacji wsadowej muszą mieć ten sam klucz partycji.</span><span class="sxs-lookup"><span data-stu-id="3a273-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="3a273-174">Chociaż istnieje możliwość wykonania zapytania w operacji wsadowej, musi to być jedyna operacja w partii.</span><span class="sxs-lookup"><span data-stu-id="3a273-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="3a273-175">Oto kod, który łączy dwa wstawienia w operację wsadową:</span><span class="sxs-lookup"><span data-stu-id="3a273-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="3a273-176">Pobieranie wszystkich jednostek w partycji</span><span class="sxs-lookup"><span data-stu-id="3a273-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="3a273-177">Aby wykonać zapytanie dotyczące tabeli dla wszystkich jednostek w partycji, użyj obiektu `TableQuery`.</span><span class="sxs-lookup"><span data-stu-id="3a273-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="3a273-178">Tutaj należy odfiltrować jednostki, w których "Smith" jest kluczem partycji.</span><span class="sxs-lookup"><span data-stu-id="3a273-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="3a273-179">Wyniki są teraz drukowane:</span><span class="sxs-lookup"><span data-stu-id="3a273-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="3a273-180">Pobieranie zakresu jednostek w partycji</span><span class="sxs-lookup"><span data-stu-id="3a273-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="3a273-181">Jeśli nie chcesz wykonywać zapytania dla wszystkich jednostek w partycji, możesz określić zakres, łącząc filtr klucza partycji z filtrem klucza wiersza.</span><span class="sxs-lookup"><span data-stu-id="3a273-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="3a273-182">W tym miejscu należy użyć dwóch filtrów do pobrania wszystkich jednostek w partycji "Smith", w których klucz wiersza (imię) rozpoczyna się od litery "M" w alfabecie.</span><span class="sxs-lookup"><span data-stu-id="3a273-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="3a273-183">Wyniki są teraz drukowane:</span><span class="sxs-lookup"><span data-stu-id="3a273-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="3a273-184">Pobieranie pojedynczej jednostki</span><span class="sxs-lookup"><span data-stu-id="3a273-184">Retrieve a single entity</span></span>

<span data-ttu-id="3a273-185">Można napisać zapytanie w celu pobrania pojedynczej określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="3a273-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="3a273-186">W tym miejscu należy użyć `TableOperation`, aby określić klienta "Ben Kowalski".</span><span class="sxs-lookup"><span data-stu-id="3a273-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="3a273-187">Zamiast kolekcji można wrócić `Customer`.</span><span class="sxs-lookup"><span data-stu-id="3a273-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="3a273-188">Określenie zarówno klucza partycji, jak i klucza wiersza w zapytaniu jest najszybszym sposobem na pobranie pojedynczej jednostki z Table service.</span><span class="sxs-lookup"><span data-stu-id="3a273-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="3a273-189">Wyniki są teraz drukowane:</span><span class="sxs-lookup"><span data-stu-id="3a273-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a><span data-ttu-id="3a273-190">Zastępowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="3a273-190">Replace an entity</span></span>

<span data-ttu-id="3a273-191">Aby zaktualizować jednostkę, pobierz ją z Table service, zmodyfikuj obiekt Entity, a następnie Zapisz zmiany z powrotem do Table service przy użyciu operacji `Replace`.</span><span class="sxs-lookup"><span data-stu-id="3a273-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="3a273-192">Powoduje to, że jednostka zostanie całkowicie zastąpiona na serwerze, chyba że jednostka na serwerze zmieniła się od czasu jej pobrania. w takim przypadku operacja nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="3a273-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="3a273-193">Ten błąd uniemożliwia aplikacji przypadkowe zastąpienie zmian z innych źródeł.</span><span class="sxs-lookup"><span data-stu-id="3a273-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="3a273-194">Wstawianie lub zastępowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="3a273-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="3a273-195">Czasami nie wiadomo, czy jednostka istnieje w tabeli.</span><span class="sxs-lookup"><span data-stu-id="3a273-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="3a273-196">A jeśli tak, bieżące wartości przechowywane w niej nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="3a273-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="3a273-197">Za pomocą `InsertOrReplace` można utworzyć jednostkę lub zastąpić ją, jeśli istnieje, niezależnie od jej stanu.</span><span class="sxs-lookup"><span data-stu-id="3a273-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="3a273-198">Wykonywanie zapytania dotyczącego podzbioru właściwości jednostki</span><span class="sxs-lookup"><span data-stu-id="3a273-198">Query a subset of entity properties</span></span>

<span data-ttu-id="3a273-199">Zapytanie tabeli może pobrać tylko kilka właściwości z jednostki zamiast wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="3a273-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="3a273-200">Ta technika, nazywana projekcją, może poprawić wydajność zapytań, szczególnie w przypadku dużych jednostek.</span><span class="sxs-lookup"><span data-stu-id="3a273-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="3a273-201">Tutaj zwracasz tylko adresy e-mail przy użyciu `DynamicTableEntity` i `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="3a273-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="3a273-202">Należy zauważyć, że projekcja nie jest obsługiwana w lokalnym emulatorze magazynu, więc ten kod jest uruchamiany tylko wtedy, gdy używasz konta w Table service.</span><span class="sxs-lookup"><span data-stu-id="3a273-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="3a273-203">Odzyskiwanie jednostek na stronach asynchronicznie</span><span class="sxs-lookup"><span data-stu-id="3a273-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="3a273-204">Jeśli czytasz dużą liczbę jednostek i chcesz przetworzyć je w miarę ich pobierania, zamiast czekać, aż wszystkie mają być zwracane, możesz użyć zapytania z segmentami.</span><span class="sxs-lookup"><span data-stu-id="3a273-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="3a273-205">Tutaj zwracasz wyniki na stronach przy użyciu asynchronicznego przepływu pracy, tak aby wykonywanie nie było blokowane podczas oczekiwania na zwrócenie dużych zestawów wyników.</span><span class="sxs-lookup"><span data-stu-id="3a273-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="3a273-206">To obliczenie jest teraz wykonywane synchronicznie:</span><span class="sxs-lookup"><span data-stu-id="3a273-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="3a273-207">Usuwanie jednostki</span><span class="sxs-lookup"><span data-stu-id="3a273-207">Delete an entity</span></span>

<span data-ttu-id="3a273-208">Możesz usunąć jednostkę po jej pobraniu.</span><span class="sxs-lookup"><span data-stu-id="3a273-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="3a273-209">Podobnie jak w przypadku aktualizowania jednostki, to nie powiedzie się, jeśli jednostka została zmieniona od czasu jej pobrania.</span><span class="sxs-lookup"><span data-stu-id="3a273-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="3a273-210">Usuń tabelę</span><span class="sxs-lookup"><span data-stu-id="3a273-210">Delete a table</span></span>

<span data-ttu-id="3a273-211">Tabelę można usunąć z konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="3a273-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="3a273-212">Usunięta tabela będzie niedostępna do ponownego utworzenia przez pewien czas po usunięciu.</span><span class="sxs-lookup"><span data-stu-id="3a273-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="3a273-213">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="3a273-213">Next steps</span></span>

<span data-ttu-id="3a273-214">Teraz, gdy znasz już podstawowe informacje o usłudze Table Storage, Skorzystaj z poniższych linków, aby dowiedzieć się więcej na temat bardziej złożonych zadań magazynu i interfejs API tabel Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="3a273-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="3a273-215">Wprowadzenie do Azure Cosmos DB interfejs API tabel</span><span class="sxs-lookup"><span data-stu-id="3a273-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="3a273-216">Dokumentacja biblioteki klienta usługi Storage dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="3a273-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="3a273-217">Dostawca typów usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="3a273-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="3a273-218">Blog zespołu usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="3a273-218">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="3a273-219">Konfigurowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="3a273-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
