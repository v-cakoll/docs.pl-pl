---
title: "Rozpoczynanie pracy z magazynem tabel Azure przy użyciu języka F #"
description: "Przechowywanie danych strukturalnych w chmurze przy użyciu magazynu tabel Azure, Magazyn danych NoSQL."
keywords: visual f#, f#, functional programming, .NET, .NET Core, Azure
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9e5d6cea-a98c-461e-a5cc-75f1d154eafd
ms.openlocfilehash: e003f537c6f0f85b3b0ba932655ae2a54c980bc5
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2018
---
# <a name="get-started-with-azure-table-storage-using-f"></a><span data-ttu-id="36d76-104">Rozpoczynanie pracy z magazynem tabel Azure przy użyciu języka F #</span><span class="sxs-lookup"><span data-stu-id="36d76-104">Get started with Azure Table storage using F#</span></span> #

<span data-ttu-id="36d76-105">Magazyn tabel Azure to usługa, która przechowuje dane strukturalne NoSQL w chmurze.</span><span class="sxs-lookup"><span data-stu-id="36d76-105">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="36d76-106">Magazyn tabel jest magazynem kluczy/atrybutów bez schematu.</span><span class="sxs-lookup"><span data-stu-id="36d76-106">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="36d76-107">Ponieważ Magazyn tabel nie korzysta ze schematów, jest łatwo zaadaptować dane rozwijających się potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="36d76-107">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="36d76-108">Dostęp do danych jest szybki i ekonomiczny dla wszystkich rodzajów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="36d76-108">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="36d76-109">Magazyn tabel jest zwykle znacznie tańszy niż tradycyjne bazy SQL dla podobnych ilości danych.</span><span class="sxs-lookup"><span data-stu-id="36d76-109">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="36d76-110">Magazyn tabel umożliwia przechowywanie elastycznych zestawów danych, takich jak dane użytkownika dla aplikacji sieci web, książki adresowe, informacje o urządzeniach i inne rodzaje metadanych, których wymaga Twoja usługa.</span><span class="sxs-lookup"><span data-stu-id="36d76-110">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="36d76-111">W tabeli można przechowywać dowolną liczbę jednostek, a konto magazynu może zawierać dowolną liczbę tabel w granicach pojemności konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="36d76-111">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="36d76-112">Informacje o tym samouczku</span><span class="sxs-lookup"><span data-stu-id="36d76-112">About this tutorial</span></span>

<span data-ttu-id="36d76-113">Ten samouczek pokazuje, jak napisać kod F # do wykonania niektórych typowych zadań przy użyciu magazynu tabel Azure, w tym tworzenie i usuwaniem tabel i wstawianie, aktualizowanie, usuwanie i przeszukiwaniem danych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="36d76-113">This tutorial shows how to write F# code to do some common tasks using Azure Table storage, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

<span data-ttu-id="36d76-114">Omówienie pojęć dotyczących magazynu tabel, zobacz [przewodnik .NET dla magazynu tabel](/azure/storage/storage-dotnet-how-to-use-tables)</span><span class="sxs-lookup"><span data-stu-id="36d76-114">For a conceptual overview of table storage, please see [the .NET guide for table storage](/azure/storage/storage-dotnet-how-to-use-tables)</span></span>

## <a name="prerequisites"></a><span data-ttu-id="36d76-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="36d76-115">Prerequisites</span></span>

<span data-ttu-id="36d76-116">Aby użyć tego przewodnika, należy najpierw [utworzyć konto magazynu Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="36d76-116">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="36d76-117">Należy również klucz dostępu do magazynu dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="36d76-117">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="36d76-118">Tworzenie skryptu języka F # i rozpocząć F # Interactive</span><span class="sxs-lookup"><span data-stu-id="36d76-118">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="36d76-119">Przykłady w tym artykule można używać w F # aplikacji lub skryptu języka F #.</span><span class="sxs-lookup"><span data-stu-id="36d76-119">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="36d76-120">Aby utworzyć skrypt F #, Utwórz plik o `.fsx` rozszerzenie, na przykład `tables.fsx`, w środowiska deweloperskiego F #.</span><span class="sxs-lookup"><span data-stu-id="36d76-120">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="36d76-121">Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) do zainstalowania `WindowsAzure.Storage` odwołanie do pakietu i `WindowsAzure.Storage.dll` skryptu za pomocą `#r`dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="36d76-121">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="36d76-122">Należy go ponownie dla "Microsoft.WindowsAzure.ConfigurationManager" Aby uzyskać Microsoft.Azure przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="36d76-122">Do it again for \`Microsoft.WindowsAzure.ConfigurationManager' in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="36d76-123">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="36d76-123">Add namespace declarations</span></span>

<span data-ttu-id="36d76-124">Dodaj następujące `open` instrukcje na początku `tables.fsx` pliku:</span><span class="sxs-lookup"><span data-stu-id="36d76-124">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="36d76-125">Pobierz ciąg połączenia</span><span class="sxs-lookup"><span data-stu-id="36d76-125">Get your connection string</span></span>

<span data-ttu-id="36d76-126">Parametry połączenia magazynu Azure należy w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="36d76-126">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="36d76-127">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="36d76-127">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="36d76-128">Samouczek będzie wprowadź parametry połączenia za pomocą skryptu, jak to:</span><span class="sxs-lookup"><span data-stu-id="36d76-128">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="36d76-129">Jest to jednak **niezalecane** rzeczywiste projektów.</span><span class="sxs-lookup"><span data-stu-id="36d76-129">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="36d76-130">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="36d76-130">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="36d76-131">Zawsze starannie Chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="36d76-131">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="36d76-132">Unikaj udostępniaj go innym użytkownikom, kodować je lub zapisać go w pliku jako zwykły tekst, który jest dostępny do innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="36d76-132">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="36d76-133">Można ponownie wygenerować klucz przy użyciu portalu Azure, jeśli uważasz, że mogą zostać naruszone.</span><span class="sxs-lookup"><span data-stu-id="36d76-133">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="36d76-134">Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="36d76-134">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="36d76-135">Aby pobrać parametry połączenia w pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="36d76-135">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="36d76-136">Przy użyciu programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="36d76-136">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="36d76-137">Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="36d76-137">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="36d76-138">Przeanalizować parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="36d76-138">Parse the connection string</span></span>

<span data-ttu-id="36d76-139">Aby przeanalizować parametrów połączenia, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="36d76-139">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="36d76-140">Spowoduje to zwrócenie `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="36d76-140">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="36d76-141">Tworzenie klienta usługi tabel</span><span class="sxs-lookup"><span data-stu-id="36d76-141">Create the Table service client</span></span>

<span data-ttu-id="36d76-142">`CloudTableClient` Klasa umożliwia pobieranie tabel i jednostek przechowywanych w magazynie tabel.</span><span class="sxs-lookup"><span data-stu-id="36d76-142">The `CloudTableClient` class enables you to retrieve tables and entities stored in Table storage.</span></span> <span data-ttu-id="36d76-143">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="36d76-143">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="36d76-144">Teraz można przystąpić do pisania kodu, która odczytuje i zapisuje dane do magazynu tabel.</span><span class="sxs-lookup"><span data-stu-id="36d76-144">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

## <a name="create-a-table"></a><span data-ttu-id="36d76-145">Utwórz tabelę</span><span class="sxs-lookup"><span data-stu-id="36d76-145">Create a table</span></span>

<span data-ttu-id="36d76-146">W tym przykładzie pokazano, jak utworzyć tabelę, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="36d76-146">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

## <a name="add-an-entity-to-a-table"></a><span data-ttu-id="36d76-147">Dodawanie jednostki do tabeli</span><span class="sxs-lookup"><span data-stu-id="36d76-147">Add an entity to a table</span></span>

<span data-ttu-id="36d76-148">Jednostka musi mieć typ, który dziedziczy z `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="36d76-148">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="36d76-149">Można rozszerzyć `TableEntity` w żaden sposób Ci się podoba, ale danego typu *musi* ma konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="36d76-149">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="36d76-150">Tylko te właściwości, które mają zarówno `get` i `set` będą przechowywane w tabeli platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="36d76-150">Only properties that have both `get` and `set` will be stored in your Azure Table.</span></span>

<span data-ttu-id="36d76-151">Jednostka partycji i klucz wiersza jednostki jednoznacznie identyfikują jednostkę w tabeli.</span><span class="sxs-lookup"><span data-stu-id="36d76-151">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="36d76-152">Jednostki z tym samym kluczem partycji mogą być przeszukiwane szybciej niż jednostki o różnych kluczach partycji, ale przy użyciu różnych kluczy partycji umożliwia zwiększenie skalowalności operacji równoległych.</span><span class="sxs-lookup"><span data-stu-id="36d76-152">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="36d76-153">Oto przykład `Customer` używającą `lastName` jako klucza partycji i `firstName` jako klucz wiersza.</span><span class="sxs-lookup"><span data-stu-id="36d76-153">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="36d76-154">Teraz dodamy naszych `Customer` do tabeli.</span><span class="sxs-lookup"><span data-stu-id="36d76-154">Now we'll add our `Customer` to the table.</span></span> <span data-ttu-id="36d76-155">Aby to zrobić, należy utworzyć `TableOperation` który zostanie wykonany w tabeli.</span><span class="sxs-lookup"><span data-stu-id="36d76-155">To do so, you create a `TableOperation` that will execute on the table.</span></span> <span data-ttu-id="36d76-156">W takim przypadku należy utworzyć `Insert` operacji.</span><span class="sxs-lookup"><span data-stu-id="36d76-156">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

## <a name="insert-a-batch-of-entities"></a><span data-ttu-id="36d76-157">Wstawić partię jednostek</span><span class="sxs-lookup"><span data-stu-id="36d76-157">Insert a batch of entities</span></span>

<span data-ttu-id="36d76-158">Można wstawić partię jednostek do tabeli za pomocą operacji zapisu pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="36d76-158">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="36d76-159">Operacje partii pozwalają połączyć operacje w pojedynczej operacji, ale mają pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="36d76-159">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="36d76-160">Możesz przeprowadzić aktualizację, usuwanie i wstawianie w tej samej operacji zbiorczej.</span><span class="sxs-lookup"><span data-stu-id="36d76-160">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="36d76-161">Operacja zbiorcza może zawierać maksymalnie 100 jednostek.</span><span class="sxs-lookup"><span data-stu-id="36d76-161">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="36d76-162">Wszystkie jednostki w operacji zbiorczej muszą mieć ten sam klucz partycji.</span><span class="sxs-lookup"><span data-stu-id="36d76-162">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="36d76-163">W trakcie można wykonać zapytania w operacji zbiorczej musi być jedyną operacją w partii.</span><span class="sxs-lookup"><span data-stu-id="36d76-163">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="36d76-164">Oto niektóre kod, który łączy dwie wstawki w operacji zbiorczej:</span><span class="sxs-lookup"><span data-stu-id="36d76-164">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

## <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="36d76-165">Pobieranie wszystkich jednostek w partycji</span><span class="sxs-lookup"><span data-stu-id="36d76-165">Retrieve all entities in a partition</span></span>

<span data-ttu-id="36d76-166">Aby sprawdzić tabelę dla wszystkich jednostek w partycji, użyj `TableQuery` obiektu.</span><span class="sxs-lookup"><span data-stu-id="36d76-166">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="36d76-167">W tym miejscu można filtrować dla jednostek gdzie "Buster" jest kluczem partycji.</span><span class="sxs-lookup"><span data-stu-id="36d76-167">Here, you filter for entities where "Buster" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L80)]

<span data-ttu-id="36d76-168">Teraz drukowanie wyników:</span><span class="sxs-lookup"><span data-stu-id="36d76-168">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


## <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="36d76-169">Pobieranie zakresu jednostek w partycji</span><span class="sxs-lookup"><span data-stu-id="36d76-169">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="36d76-170">Jeśli nie chcesz zbadać wszystkich jednostek w partycji, można określić zakres, łącząc filtr klucza partycji z filtrem klucza wiersza.</span><span class="sxs-lookup"><span data-stu-id="36d76-170">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="36d76-171">W tym miejscu służy dwa filtry do pobrania wszystkich jednostek w partycji "Buster" gdzie klucz wiersza (imię) rozpoczyna się od litery wcześniejszej niż "M" alfabetu.</span><span class="sxs-lookup"><span data-stu-id="36d76-171">Here, you use two filters to get all entities in the "Buster" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="36d76-172">Teraz drukowanie wyników:</span><span class="sxs-lookup"><span data-stu-id="36d76-172">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

## <a name="retrieve-a-single-entity"></a><span data-ttu-id="36d76-173">Pobieranie pojedynczej jednostki</span><span class="sxs-lookup"><span data-stu-id="36d76-173">Retrieve a single entity</span></span>

<span data-ttu-id="36d76-174">Można napisać zapytanie do pobrania jednej, określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="36d76-174">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="36d76-175">W tym miejscu użyć `TableOperation` do określenia klienta "Larry Buster".</span><span class="sxs-lookup"><span data-stu-id="36d76-175">Here, you use a `TableOperation` to specify the customer "Larry Buster".</span></span> <span data-ttu-id="36d76-176">Zamiast kolekcji, możesz wrócić `Customer`.</span><span class="sxs-lookup"><span data-stu-id="36d76-176">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="36d76-177">Określenie zarówno klucz partycji i klucz wiersza w zapytaniu jest najszybszym sposobem na pobranie jednej jednostki z usługi tabel.</span><span class="sxs-lookup"><span data-stu-id="36d76-177">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="36d76-178">Teraz drukowanie wyników:</span><span class="sxs-lookup"><span data-stu-id="36d76-178">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


## <a name="replace-an-entity"></a><span data-ttu-id="36d76-179">Zastępowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="36d76-179">Replace an entity</span></span>

<span data-ttu-id="36d76-180">Aby zaktualizować jednostkę, pobierz ją z usługi tabel, zmodyfikuj obiekt jednostki, a następnie zapisz zmiany powrót do tabeli usługi przy użyciu `Replace` operacji.</span><span class="sxs-lookup"><span data-stu-id="36d76-180">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="36d76-181">Powoduje to, że jednostka będzie całkowicie zastąpiona na serwerze, chyba że jednostka na serwerze została zmieniona, ponieważ został on pobrany, w którym to przypadku operacja nie powiedzie.</span><span class="sxs-lookup"><span data-stu-id="36d76-181">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation will fail.</span></span> <span data-ttu-id="36d76-182">Jest to błąd uniemożliwia aplikacji nieodwracalne nadpisanie zmiany z innych źródeł.</span><span class="sxs-lookup"><span data-stu-id="36d76-182">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

## <a name="insert-or-replace-an-entity"></a><span data-ttu-id="36d76-183">Wstawianie lub zastępowanie jednostki</span><span class="sxs-lookup"><span data-stu-id="36d76-183">Insert-or-replace an entity</span></span>

<span data-ttu-id="36d76-184">Czasami nie wiadomo, czy jednostka istnieje w tabeli lub nie.</span><span class="sxs-lookup"><span data-stu-id="36d76-184">Sometimes, you don't know if the entity exists in the table or not.</span></span> <span data-ttu-id="36d76-185">A jeśli tak, czy obecne wartości przechowywane w nim nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="36d76-185">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="36d76-186">Można użyć `InsertOrReplace` w celu utworzenia jednostki lub zastąp ją, jeśli istnieje, niezależnie od jego stanu.</span><span class="sxs-lookup"><span data-stu-id="36d76-186">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L140)]

## <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="36d76-187">Tworzenie zapytania do podzbioru właściwości jednostki</span><span class="sxs-lookup"><span data-stu-id="36d76-187">Query a subset of entity properties</span></span>

<span data-ttu-id="36d76-188">Zapytanie tabeli może pobrać kilka właściwości jednostki zamiast wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="36d76-188">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="36d76-189">Ta technika, zwana projekcją, może poprawić wydajność zapytań, zwłaszcza w przypadku dużych jednostek.</span><span class="sxs-lookup"><span data-stu-id="36d76-189">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="36d76-190">W tym miejscu zwracać dotyczy tylko wiadomości e-mail przy użyciu `DynamicTableEntity` i `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="36d76-190">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="36d76-191">Należy pamiętać, że projekcji nie jest obsługiwana w lokalnym emulatorze magazynu, dlatego ten kod zadziała tylko wtedy, gdy używasz konta w usłudze tabel.</span><span class="sxs-lookup"><span data-stu-id="36d76-191">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L146-L157)]

## <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="36d76-192">Pobieranie asynchroniczne jednostek na stronach</span><span class="sxs-lookup"><span data-stu-id="36d76-192">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="36d76-193">Jeśli odczytujesz dużą liczbę jednostek i chcesz przetworzyć je zgodnie z ich pobraniu, zamiast oczekiwania na zwrócenie ich wszystkich, można użyć zapytania segmentowanego.</span><span class="sxs-lookup"><span data-stu-id="36d76-193">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="36d76-194">W tym miejscu możesz zwracania wyników na stronach za pomocą async przepływu pracy, dzięki czemu wykonanie nie jest blokowane podczas oczekiwania dla dużych zestawów wyników do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="36d76-194">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L177)]

<span data-ttu-id="36d76-195">Można teraz wykonywać te obliczenia synchronicznie:</span><span class="sxs-lookup"><span data-stu-id="36d76-195">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L179-L179)]

## <a name="delete-an-entity"></a><span data-ttu-id="36d76-196">Usuwanie jednostki</span><span class="sxs-lookup"><span data-stu-id="36d76-196">Delete an entity</span></span>

<span data-ttu-id="36d76-197">Po jej pobraniu, można usunąć jednostki.</span><span class="sxs-lookup"><span data-stu-id="36d76-197">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="36d76-198">Podobnie jak w przypadku aktualizowania jednostki, to zakończy się niepowodzeniem, jeśli jednostka została zmieniona od czasu jej pobrania.</span><span class="sxs-lookup"><span data-stu-id="36d76-198">As with updating an entity, this will fail if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L185-L186)]

## <a name="delete-a-table"></a><span data-ttu-id="36d76-199">Usuwanie tabeli</span><span class="sxs-lookup"><span data-stu-id="36d76-199">Delete a table</span></span>

<span data-ttu-id="36d76-200">Z konta magazynu można usunąć tabeli.</span><span class="sxs-lookup"><span data-stu-id="36d76-200">You can delete a table from a storage account.</span></span> <span data-ttu-id="36d76-201">Tabela, która została usunięta będzie mógł zostać ponownie utworzone w danym okresie czasu po jej usunięciu.</span><span class="sxs-lookup"><span data-stu-id="36d76-201">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L192-L192)]

## <a name="next-steps"></a><span data-ttu-id="36d76-202">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="36d76-202">Next steps</span></span>

<span data-ttu-id="36d76-203">Teraz, kiedy znasz już podstawy magazynu tabel, skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu:</span><span class="sxs-lookup"><span data-stu-id="36d76-203">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks:</span></span>

- [<span data-ttu-id="36d76-204">Interfejsy API usługi Azure Storage dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="36d76-204">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="36d76-205">Dostawca typów magazynu Azure</span><span class="sxs-lookup"><span data-stu-id="36d76-205">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="36d76-206">Azure Storage Team Blog</span><span class="sxs-lookup"><span data-stu-id="36d76-206">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="36d76-207">Konfigurowanie parametrów połączenia usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="36d76-207">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="36d76-208">Rozpoczynanie pracy z magazynem tabel Azure w .NET</span><span class="sxs-lookup"><span data-stu-id="36d76-208">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/documentation/samples/storage-table-dotnet-getting-started/)
