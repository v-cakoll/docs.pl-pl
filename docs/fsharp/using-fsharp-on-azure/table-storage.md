---
title: Rozpoczynanie pracy z usługą Azure Table Storage przy użyciu języka F#
description: Przechowuj dane strukturalne w chmurze przy użyciu usługi Azure Table Storage lub Azure Cosmos DB.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 509435d47231040362586fa263fbecb1125f862b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182597"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>Rozpoczynanie pracy z usługą Azure Table Storage i interfejs API tabel Azure Cosmos DB przy użyciu języka F\#

Azure Table Storage to usługa, która przechowuje strukturalne dane NoSQL w chmurze. Magazyn tabel jest magazynem kluczy/atrybutów z projektem bez schematu. Ponieważ magazyn tabel jest bezschematowy, można łatwo dostosować dane w miarę rozwoju aplikacji. Dostęp do danych jest szybki i opłacalny dla wszystkich rodzajów aplikacji. Magazyn tabel jest zwykle znacząco niższy niż tradycyjny kod SQL dla podobnych ilości danych.

Usługa Table Storage umożliwia przechowywanie elastycznych zestawów danych, takich jak dane użytkowników dla aplikacji sieci Web, książek adresowych, informacji o urządzeniach i innych typów metadanych wymaganych przez usługę. Można przechowywać dowolną liczbę jednostek w tabeli, a konto magazynu może zawierać dowolną liczbę tabel, aż do limitu pojemności konta magazynu.

Azure Cosmos DB zapewnia interfejs API tabel dla aplikacji, które są przeznaczone dla usługi Azure Table Storage, które wymagają funkcji premium, takich jak:

- Gotowe globalna.
- Dedykowana przepływność na całym świecie.
- Opóźnienia o pojedynczej liczbie milisekund w 99 percentylu.
- Gwarantowana wysoka dostępność.
- Automatyczne indeksowanie pomocnicze.

Aplikacje przeznaczone dla usługi Azure Table Storage można migrować do Azure Cosmos DB przy użyciu interfejs API tabel bez zmian w kodzie i korzystać z funkcji Premium. Interfejs API tabel udostępnia zestawy SDK klienta dostępne dla platform .NET, Java, Python i Node. js.

Aby uzyskać więcej informacji, zobacz [wprowadzenie do Azure Cosmos DB interfejs API tabel](https://docs.microsoft.com/azure/cosmos-db/table-introduction).

## <a name="about-this-tutorial"></a>Informacje o tym samouczku

W tym samouczku pokazano, F# jak napisać kod, aby wykonać kilka typowych zadań za pomocą usługi Azure Table storage lub interfejs API tabel Azure Cosmos DB, w tym tworzenie i usuwanie tabeli oraz wstawianie, aktualizowanie, usuwanie i wykonywanie zapytań dotyczących danych tabeli.

## <a name="prerequisites"></a>Wymagania wstępne

Aby skorzystać z tego przewodnika, musisz najpierw [utworzyć konto usługi Azure Storage](/azure/storage/storage-create-storage-account) lub [konto Azure Cosmos DB](https://azure.microsoft.com/try/cosmosdb/).

## <a name="create-an-f-script-and-start-f-interactive"></a>Utwórz F# skrypt i uruchom F# interaktywny

Przykłady w tym artykule mogą być używane w F# aplikacji lub F# skrypcie. Aby utworzyć F# skrypt, Utwórz plik z `.fsx` rozszerzeniem, na przykład `tables.fsx`w środowisku F# deweloperskim.

Następnie należy użyć [Menedżera pakietów](package-management.md) , takiego jak [Paket](https://fsprojects.github.io/Paket/) lub [](https://www.nuget.org/) `WindowsAzure.Storage` NuGet, aby zainstalować `#r` pakiet i odwołanie `WindowsAzure.Storage.dll` w skrypcie przy użyciu dyrektywy. Zrób to ponownie `Microsoft.WindowsAzure.ConfigurationManager` w celu uzyskania przestrzeni nazw Microsoft. Azure.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujące `open` instrukcje na początku `tables.fsx` pliku:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Pobieranie parametrów połączenia usługi Azure Storage

W przypadku nawiązywania połączenia z usługą Azure Storage Table service potrzebne są parametry połączenia dla tego samouczka. Parametry połączenia można skopiować z Azure Portal. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [Konfigurowanie parametrów połączenia magazynu](/azure/storage/storage-configure-connection-string).

### <a name="get-your-azure-cosmos-db-connection-string"></a>Pobierz parametry połączenia Azure Cosmos DB

W przypadku nawiązywania połączenia z usługą Azure Cosmos DB potrzebne są parametry połączenia dla tego samouczka. Parametry połączenia można skopiować z Azure Portal. W Azure Portal na koncie Cosmos DB przejdź do pozycji **Ustawienia** > **Parametry połączenia**, a następnie kliknij przycisk **Kopiuj** , aby skopiować podstawowe parametry połączenia. 

Dla samouczka wprowadź parametry połączenia w skrypcie, jak w poniższym przykładzie:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

Nie jest to jednak **zalecane** w przypadku rzeczywistych projektów. Klucz konta magazynu jest podobny do hasła głównego dla konta magazynu. Zawsze należy zachować ostrożność, aby chronić klucz konta magazynu. Należy unikać dystrybuowania go do innych użytkowników, ich trwałego kodowania lub zapisywania w pliku w formacie zwykłego tekstu, który jest dostępny dla innych. Możesz ponownie wygenerować klucz za pomocą witryny Azure Portal, jeśli uważasz, że jego zabezpieczenia mogły zostać naruszone.

W przypadku prawdziwych aplikacji najlepszym sposobem obsługi parametrów połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Korzystanie z usługi Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takiego jak `ConfigurationManager` typ .NET Framework.

### <a name="parse-the-connection-string"></a>Analizowanie parametrów połączenia

Aby przeanalizować parametry połączenia, użyj:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Spowoduje to zwrócenie `CloudStorageAccount`elementu.

### <a name="create-the-table-service-client"></a>Tworzenie klienta Table service

`CloudTableClient` Klasa umożliwia pobieranie tabel i jednostek w magazynie tabel. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Teraz możesz przystąpić do pisania kodu, który odczytuje dane z magazynu tabel i zapisuje je.

### <a name="create-a-table"></a>Tworzenie tabeli

Ten przykład pokazuje, jak utworzyć tabelę, jeśli jeszcze nie istnieje:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>Dodawanie jednostki do tabeli

Jednostka musi mieć typ, który dziedziczy z `TableEntity`. Możesz to zrobić wdowolnysposób,aletypmusimiećkonstruktorabez`TableEntity` parametrów. Tylko właściwości, które mają `get` oba `set` te i są przechowywane w tabeli platformy Azure.

Partycja i klucz wiersza jednostki jednoznacznie identyfikują jednostkę w tabeli. Jednostki z tym samym kluczem partycji mogą być przeszukiwane szybciej niż te z różnymi kluczami partycji, ale użycie różnych kluczy partycji umożliwia zwiększenie skalowalności operacji równoległych.

Oto przykład `Customer` , który `lastName` używa jako klucza partycji i `firstName` klucza wiersza.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Teraz Dodaj `Customer` do tabeli. W tym celu należy utworzyć obiekt `TableOperation` , który jest wykonywany na tabeli. W takim przypadku należy utworzyć `Insert` operację.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>Wstawianie partii jednostek

Można wstawić partię jednostek do tabeli przy użyciu jednej operacji zapisu. Operacje wsadowe umożliwiają łączenie operacji w pojedynczym wykonaniu, ale mają pewne ograniczenia:

- Można wykonywać aktualizacje, usuwać i wstawiać w tej samej operacji wsadowej.
- Operacja wsadowa może obejmować do 100 jednostek.
- Wszystkie jednostki w operacji wsadowej muszą mieć ten sam klucz partycji.
- Chociaż istnieje możliwość wykonania zapytania w operacji wsadowej, musi to być jedyna operacja w partii.

Oto kod, który łączy dwa wstawienia w operację wsadową:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>Pobieranie wszystkich jednostek w partycji

Aby wykonać zapytanie dotyczące tabeli dla wszystkich jednostek w partycji, użyj `TableQuery` obiektu. Tutaj należy odfiltrować jednostki, w których "Smith" jest kluczem partycji.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

Wyniki są teraz drukowane:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a>Pobieranie zakresu jednostek w partycji

Jeśli nie chcesz wykonywać zapytania dla wszystkich jednostek w partycji, możesz określić zakres, łącząc filtr klucza partycji z filtrem klucza wiersza. W tym miejscu należy użyć dwóch filtrów do pobrania wszystkich jednostek w partycji "Smith", w których klucz wiersza (imię) rozpoczyna się od litery "M" w alfabecie.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Wyniki są teraz drukowane:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>Pobieranie pojedynczej jednostki

Można napisać zapytanie w celu pobrania pojedynczej określonej jednostki. W tym miejscu należy użyć `TableOperation` , aby określić klienta "Ben Kowalski". Zamiast kolekcji, odwracasz `Customer`. Określenie zarówno klucza partycji, jak i klucza wiersza w zapytaniu jest najszybszym sposobem na pobranie pojedynczej jednostki z Table service.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Wyniki są teraz drukowane:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a>Zastępowanie jednostki

Aby zaktualizować jednostkę, pobierz ją z Table Service, zmodyfikuj obiekt Entity, a następnie Zapisz zmiany z powrotem do Table Service przy użyciu `Replace` operacji. Powoduje to, że jednostka zostanie całkowicie zastąpiona na serwerze, chyba że jednostka na serwerze zmieniła się od czasu jej pobrania. w takim przypadku operacja nie powiedzie się. Ten błąd uniemożliwia aplikacji przypadkowe zastąpienie zmian z innych źródeł.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>Wstawianie lub zastępowanie jednostki

Czasami nie wiadomo, czy jednostka istnieje w tabeli. A jeśli tak, bieżące wartości przechowywane w niej nie są już potrzebne. Można użyć `InsertOrReplace` do utworzenia jednostki lub zamienić ją, jeśli istnieje, niezależnie od jej stanu.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>Wykonywanie zapytania dotyczącego podzbioru właściwości jednostki

Zapytanie tabeli może pobrać tylko kilka właściwości z jednostki zamiast wszystkich z nich. Ta technika, nazywana projekcją, może poprawić wydajność zapytań, szczególnie w przypadku dużych jednostek. Tutaj zwracasz tylko adresy e-mail przy użyciu `DynamicTableEntity` i `EntityResolver`. Należy zauważyć, że projekcja nie jest obsługiwana w lokalnym emulatorze magazynu, więc ten kod jest uruchamiany tylko wtedy, gdy używasz konta w Table service.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>Odzyskiwanie jednostek na stronach asynchronicznie

Jeśli czytasz dużą liczbę jednostek i chcesz przetworzyć je w miarę ich pobierania, zamiast czekać, aż wszystkie mają być zwracane, możesz użyć zapytania z segmentami. Tutaj zwracasz wyniki na stronach przy użyciu asynchronicznego przepływu pracy, tak aby wykonywanie nie było blokowane podczas oczekiwania na zwrócenie dużych zestawów wyników.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

To obliczenie jest teraz wykonywane synchronicznie:

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>Usuwanie jednostki

Możesz usunąć jednostkę po jej pobraniu. Podobnie jak w przypadku aktualizowania jednostki, to nie powiedzie się, jeśli jednostka została zmieniona od czasu jej pobrania.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>Usuń tabelę

Tabelę można usunąć z konta magazynu. Usunięta tabela będzie niedostępna do ponownego utworzenia przez pewien czas po usunięciu.

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>Następne kroki

Teraz, gdy znasz już podstawowe informacje o usłudze Table Storage, Skorzystaj z poniższych linków, aby dowiedzieć się więcej na temat bardziej złożonych zadań magazynu i interfejs API tabel Azure Cosmos DB.

- [Wprowadzenie do Azure Cosmos DB interfejs API tabel](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [Dokumentacja biblioteki klienta usługi Storage dla platformy .NET](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
- [Dostawca typów usługi Azure Storage](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Blog zespołu usługi Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Konfigurowanie parametrów połączenia](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [Wprowadzenie z usługą Azure Table Storage w środowisku .NET](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
