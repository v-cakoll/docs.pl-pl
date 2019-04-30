---
title: Rozpoczynanie pracy z usługą Azure Table storage przy użyciuF#
description: Store ustrukturyzowanych danych w chmurze przy użyciu usługi Azure Table storage lub Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 54c777acd454e4f675175b814675c185e41ad9a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756354"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Rozpoczynanie pracy z usługą Azure Table storage i Azure Cosmos DB interfejsu API tabel przy użyciu F\#

Usługa Azure Table storage to usługa, która przechowuje dane strukturalne NoSQL w chmurze. Magazyn tabel to magazyn klucz/atrybutów bez schematu. Ponieważ Magazyn tabel nie ma, to można łatwo zaadaptować dane aplikacji rozwijających się potrzeb. Dostęp do danych jest szybki i ekonomiczny dla wszystkich rodzajów aplikacji. Magazyn tabel jest zwykle znacznie tańszy od tradycyjnego rozwiązania SQL dla podobnych ilości danych.

Magazyn tabel umożliwia przechowywanie elastycznych zestawów danych, takich jak dane użytkownika dla aplikacji sieci web, książek adresowych, informacji o urządzeniach i inne rodzaje metadanych, których wymaga Twoja usługa. Dowolną liczbę jednostek można przechowywać w tabeli, a konto magazynu może zawierać dowolną liczbę tabel w granicach pojemności konta magazynu.

Usługa Azure Cosmos DB zapewnia interfejs API tabel dla aplikacji korzystających z usługi Azure Table Storage, które wymagają funkcji warstwy premium takich jak:

- Kompleksowa dystrybucja globalna.
- Dedykowana przepływność na całym świecie.
- Milisekundowe opóźnienia w 99. percentylu.
- Gwarantowana wysoka dostępność.
- Automatyczne indeksowanie pomocnicze.

Aplikacje napisane dla usługi Azure Table storage można migrować do usługi Azure Cosmos DB przy użyciu interfejsu API tabel bez zmian w kodzie i mogą korzystać z funkcji premium. Interfejs API tabel udostępnia dostępne zestawy SDK klientów, dla platformy .NET, Java, Python i Node.js.

Aby uzyskać więcej informacji, zobacz [wprowadzenie do interfejsu API tabeli usługi Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>Informacje o tym samouczku

Ten samouczek przedstawia sposób zapisania F# kod, aby wykonywać niektóre typowe zadania za pomocą usługi Azure Table storage lub Azure Cosmos DB interfejsu API tabel, w tym tworzenie i usuwanie tabeli i wstawianie, aktualizowanie, usuwanie i odpytywanie danych tabeli.

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć tego przewodnika, należy najpierw [Tworzenie konta usługi Azure storage](/azure/storage/storage-create-storage-account) lub [konta usługi Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).

## <a name="create-an-f-script-and-start-f-interactive"></a>Tworzenie F# skrypt i uruchomić F# interaktywne

Przykłady w tym artykule mogą być używane w jednej F# aplikacji lub F# skryptu. Aby utworzyć F# skrypt, Utwórz plik o `.fsx` rozszerzenia, na przykład `tables.fsx`w usługi F# środowiska deweloperskiego.

Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) zainstalował `WindowsAzure.Storage` pakietów i odwołań `WindowsAzure.Storage.dll` w skrypcie za pomocą `#r`dyrektywy. Wykonaj ponownie ją `Microsoft.WindowsAzure.ConfigurationManager` celu uzyskanie Microsoft.Azure przestrzeni nazw.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujący kod `open` instrukcji na górze `tables.fsx` pliku:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Pobieranie parametrów połączenia usługi Azure Storage

Jeśli łączysz się do usługi Azure Storage Table, konieczne będzie parametry połączenia na potrzeby tego samouczka. Parametry połączenia można skopiować z witryny Azure portal. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Pobieranie parametrów połączenia usługi Azure Cosmos DB

Jeśli łączysz się do usługi Azure Cosmos DB, konieczne będzie parametry połączenia na potrzeby tego samouczka. Parametry połączenia można skopiować z witryny Azure portal. W witrynie Azure portal w ramach konta usługi Cosmos DB, przejdź do **ustawienia** > **parametry połączenia**i kliknij przycisk **kopiowania** przycisk, aby skopiować podstawowe połączenie Ciąg. 

Samouczek należy wprowadzić parametry połączenia w skrypcie, jak w poniższym przykładzie:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

Jest to jednak **niezalecane** rzeczywiste projektów. Klucz konta magazynu jest podobny do hasła głównego konta magazynu. Zawsze starannie Chroń klucz konta magazynu. Należy unikać, ich dystrybucję w innym użytkownikom, kodować je lub zapisanie go w pliku tekstowego, który jest dostępny dla innych użytkowników. Można ponownie wygenerować klucz za pośrednictwem witryny Azure Portal, jeśli uważasz, że mogą zostać przejęte.

Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Użycie programu Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Przeanalizować parametrów połączenia

Aby przeanalizować parametrów połączenia, należy użyć:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Spowoduje to zwrócenie `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Tworzenie klienta usługi Table service

`CloudTableClient` Klasy umożliwia pobieranie tabel i jednostek w usłudze Table storage. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Teraz możesz przystąpić do pisania kodu, który odczytuje dane z i zapisuje dane w usłudze Table storage.

### <a name="create-a-table"></a>Tworzenie tabeli

Ten przykład pokazuje, jak utworzyć tabelę, jeśli jeszcze nie istnieje:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Dodawanie jednostki do tabeli

Określona jednostka ma typ, który dziedziczy z `TableEntity`. Możesz rozszerzyć `TableEntity` w jakikolwiek sposób, chcesz, ale typu *musi* ma konstruktora bez parametrów. Tylko te właściwości, które mają zarówno `get` i `set` są przechowywane w tabeli platformy Azure.

Jednostka partycji i klucz wiersza jednoznacznie identyfikują jednostkę w tabeli. Jednostki z tym samym kluczem partycji, które mogą być przeszukiwane szybciej niż te o różnych kluczach partycji, ale użycie różnych kluczy partycji umożliwia zwiększenie skalowalności operacji równoległych.

Oto przykład `Customer` , który używa `lastName` jako klucza partycji i `firstName` jako klucz wiersza.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Teraz Dodaj `Customer` do tabeli. Aby to zrobić, należy utworzyć `TableOperation` , który jest wykonywany w tabeli. W takim przypadku należy utworzyć `Insert` operacji.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Wstawić partię jednostek

Możesz wstawić partię jednostek do tabeli za pomocą operacji zapisu w jednym. Operacji wsadowych pozwalają na łączenie operacji na pojedyncze wykonanie, ale mają pewne ograniczenia:

- Możesz przeprowadzić aktualizację, usuwanie i wstawianie w jednej operacji wsadowej.
- Operacja zbiorcza może zawierać do 100 jednostek.
- Wszystkie jednostki w operacji zbiorczej muszą mieć ten sam klucz partycji.
- Choć jest możliwe do wykonania zapytania w operacji zbiorczej, należy wykonać tylko w partii.

Poniżej przedstawiono niektóre kodu, który łączy dwie wstawki w operacji zbiorczej:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Pobieranie wszystkich jednostek w partycji

Aby wysłać zapytanie do tabeli dla wszystkich jednostek w partycji, należy użyć `TableQuery` obiektu. W tym miejscu możesz filtrować dla obiektów gdzie "Smith" jest kluczem partycji.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Teraz możesz wydrukować wyniki:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Pobieranie zakresu jednostek w partycji

Jeśli nie chcesz wykonywać zapytania dla wszystkich jednostek w partycji, można określić zakres, łącząc filtr klucza partycji z filtrem klucza wiersza. Używamy tutaj dwa filtry do pobrania wszystkich jednostek w partycji "Smith" gdzie klucz wiersza (imię) rozpoczyna się od litery starszych niż "M" alfabetu.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Teraz możesz wydrukować wyniki:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Pobieranie pojedynczej jednostki

Można napisać zapytanie w celu pobrania jednej, określonej jednostki. W tym miejscu możesz użyć `TableOperation` do określenia klienta "Ben Smith". Zamiast kolekcji, można wrócić `Customer`. Określenie klucza partycji i klucz wiersza w zapytaniu jest najszybszym sposobem na pobranie jednej jednostki z usługi tabel.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Teraz możesz wydrukować wyniki:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a>Zastępowanie jednostki

Aby zaktualizować jednostkę, pobierz ją z usługi tabel, zmodyfikuj obiekt jednostki i następnie zapisz zmiany z powrotem do tabeli usługi przy użyciu `Replace` operacji. To powoduje, że jednostka będzie całkowicie zastąpiona na serwerze, chyba że jednostka na serwerze zmieniła się od czasu jej pobrania, w którym to przypadku kończy się niepowodzeniem. Jest ten błąd uniemożliwia aplikacji nieodwracalne nadpisanie zmiany z innych źródeł.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Wstawianie lub zastępowanie jednostki

Czasami nie wiadomo, czy obiekt istnieje w tabeli. A jeśli tak jest, czy obecne wartości przechowywane w nim nie są już potrzebne. Możesz użyć `InsertOrReplace` utworzyć jednostkę, lub zastąp ją, jeśli istnieje, niezależnie od jego stanu.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Tworzenie zapytania do podzbioru właściwości jednostki

Zapytanie tabeli może pobrać kilka właściwości jednostki zamiast wszystkich z nich. Ta technika, zwana projekcją, może poprawić wydajność zapytań, szczególnie w przypadku dużych jednostek. W tym miejscu zwrócić tylko wiadomości e-mail, adresy, za pomocą `DynamicTableEntity` i `EntityResolver`. Należy pamiętać, że projekcji nie jest obsługiwana w emulatorze magazynu lokalnego, dlatego ten kod zadziała tylko wtedy, gdy używasz konta w usłudze tabel.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Pobieranie asynchroniczne jednostek na stronach

Jeśli odczytujesz dużą liczbę jednostek i chcesz je przetworzyć, ich pobraniu, zamiast oczekiwanie na zwrócenie ich wszystkich, można użyć zapytania segmentowanego. W tym miejscu możesz zwracania wyników na stronach za pomocą asynchronicznego przepływu pracy, dzięki czemu wykonanie nie jest blokowane podczas oczekiwania dużych zestawów wyników do zwrócenia.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

Możesz teraz wykonać to obliczenie synchronicznie:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Usunięcie jednostki

Można usunąć jednostkę po jej pobraniu. Podobnie jak w przypadku aktualizowania jednostki, to nie powiedzie się jeśli jednostka zmieniła się od pobrano go.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Usuwanie tabeli

Możesz usunąć tabelę z konta magazynu. Tabela, która została usunięta, będą niedostępne, można ponownie utworzyć w okresie czasu po jej usunięciu.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Następne kroki

Teraz, kiedy znasz już podstawy usługi Table storage, skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu i interfejsu API tabeli usługi Azure Cosmos DB.

- [Wprowadzenie do usługi Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [Biblioteka klienta usługi Storage dla platformy .NET odwołania](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [Dostawcy typów usługi Azure Storage](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Blog zespołu usługi Azure Storage](https://blogs.msdn.com/b/windowsazurestorage/)
- [Konfigurowanie parametrów połączenia](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [Wprowadzenie do usługi Azure Table Storage na platformie .NET](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
