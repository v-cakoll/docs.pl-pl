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
ms.openlocfilehash: 905374a60261b0c2a863edb956943d41ae80f04d
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-table-storage-using-f"></a>Rozpoczynanie pracy z magazynem tabel Azure przy użyciu języka F # #

Magazyn tabel Azure to usługa, która przechowuje dane strukturalne NoSQL w chmurze. Magazyn tabel jest magazynem kluczy/atrybutów bez schematu. Ponieważ Magazyn tabel nie korzysta ze schematów, jest łatwo zaadaptować dane rozwijających się potrzeb aplikacji. Dostęp do danych jest szybki i ekonomiczny dla wszystkich rodzajów aplikacji. Magazyn tabel jest zwykle znacznie tańszy niż tradycyjne bazy SQL dla podobnych ilości danych.

Magazyn tabel umożliwia przechowywanie elastycznych zestawów danych, takich jak dane użytkownika dla aplikacji sieci web, książki adresowe, informacje o urządzeniach i inne rodzaje metadanych, których wymaga Twoja usługa. W tabeli można przechowywać dowolną liczbę jednostek, a konto magazynu może zawierać dowolną liczbę tabel w granicach pojemności konta magazynu.

### <a name="about-this-tutorial"></a>Informacje o tym samouczku

Ten samouczek pokazuje, jak napisać kod F # do wykonania niektórych typowych zadań przy użyciu magazynu tabel Azure, w tym tworzenie i usuwaniem tabel i wstawianie, aktualizowanie, usuwanie i przeszukiwaniem danych w tabeli.

Omówienie pojęć dotyczących magazynu tabel, zobacz [przewodnik .NET dla magazynu tabel](/azure/storage/storage-dotnet-how-to-use-tables)

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć tego przewodnika, należy najpierw [utworzyć konto magazynu Azure](/azure/storage/storage-create-storage-account).
Należy również klucz dostępu do magazynu dla tego konta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Tworzenie skryptu języka F # i rozpocząć F # Interactive

Przykłady w tym artykule można używać w F # aplikacji lub skryptu języka F #. Aby utworzyć skrypt F #, Utwórz plik o `.fsx` rozszerzenie, na przykład `tables.fsx`, w środowiska deweloperskiego F #.

Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) do zainstalowania `WindowsAzure.Storage` odwołanie do pakietu i `WindowsAzure.Storage.dll` skryptu za pomocą `#r`dyrektywy. Należy go ponownie dla "Microsoft.WindowsAzure.ConfigurationManager" Aby uzyskać Microsoft.Azure przestrzeni nazw.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujące `open` instrukcje na początku `tables.fsx` pliku:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Pobierz ciąg połączenia

Parametry połączenia magazynu Azure należy w tym samouczku. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).

Samouczek będzie wprowadź parametry połączenia za pomocą skryptu, jak to:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

Jest to jednak **niezalecane** rzeczywiste projektów. Klucz konta magazynu jest podobny do hasła głównego konta magazynu. Zawsze starannie Chroń klucz konta magazynu. Unikaj udostępniaj go innym użytkownikom, kodować je lub zapisać go w pliku jako zwykły tekst, który jest dostępny do innych użytkowników. Można ponownie wygenerować klucz przy użyciu portalu Azure, jeśli uważasz, że mogą zostać naruszone.

Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia w pliku konfiguracji, można to zrobić:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Przy użyciu programu Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Przeanalizować parametrów połączenia

Aby przeanalizować parametrów połączenia, należy użyć:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

Spowoduje to zwrócenie `CloudStorageAccount`.

### <a name="create-the-table-service-client"></a>Tworzenie klienta usługi tabel

`CloudTableClient` Klasa umożliwia pobieranie tabel i jednostek przechowywanych w magazynie tabel. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

Teraz można przystąpić do pisania kodu, która odczytuje i zapisuje dane do magazynu tabel.

## <a name="create-a-table"></a>Utwórz tabelę

W tym przykładzie pokazano, jak utworzyć tabelę, jeśli jeszcze nie istnieje:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

## <a name="add-an-entity-to-a-table"></a>Dodawanie jednostki do tabeli

Jednostka musi mieć typ, który dziedziczy z `TableEntity`. Można rozszerzyć `TableEntity` w żaden sposób Ci się podoba, ale danego typu *musi* ma konstruktora bez parametrów. Tylko te właściwości, które mają zarówno `get` i `set` będą przechowywane w tabeli platformy Azure.

Jednostka partycji i klucz wiersza jednostki jednoznacznie identyfikują jednostkę w tabeli. Jednostki z tym samym kluczem partycji mogą być przeszukiwane szybciej niż jednostki o różnych kluczach partycji, ale przy użyciu różnych kluczy partycji umożliwia zwiększenie skalowalności operacji równoległych.

Oto przykład `Customer` używającą `lastName` jako klucza partycji i `firstName` jako klucz wiersza.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

Teraz dodamy naszych `Customer` do tabeli. Aby to zrobić, należy utworzyć `TableOperation` który zostanie wykonany w tabeli. W takim przypadku należy utworzyć `Insert` operacji.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

## <a name="insert-a-batch-of-entities"></a>Wstawić partię jednostek

Można wstawić partię jednostek do tabeli za pomocą operacji zapisu pojedynczego. Operacje partii pozwalają połączyć operacje w pojedynczej operacji, ale mają pewne ograniczenia:

- Możesz przeprowadzić aktualizację, usuwanie i wstawianie w tej samej operacji zbiorczej.
- Operacja zbiorcza może zawierać maksymalnie 100 jednostek.
- Wszystkie jednostki w operacji zbiorczej muszą mieć ten sam klucz partycji.
- W trakcie można wykonać zapytania w operacji zbiorczej musi być jedyną operacją w partii.

Oto niektóre kod, który łączy dwie wstawki w operacji zbiorczej:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

## <a name="retrieve-all-entities-in-a-partition"></a>Pobieranie wszystkich jednostek w partycji

Aby sprawdzić tabelę dla wszystkich jednostek w partycji, użyj `TableQuery` obiektu. W tym miejscu można filtrować dla jednostek gdzie "Buster" jest kluczem partycji.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L80)]

Teraz drukowanie wyników:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


## <a name="retrieve-a-range-of-entities-in-a-partition"></a>Pobieranie zakresu jednostek w partycji

Jeśli nie chcesz zbadać wszystkich jednostek w partycji, można określić zakres, łącząc filtr klucza partycji z filtrem klucza wiersza. W tym miejscu służy dwa filtry do pobrania wszystkich jednostek w partycji "Buster" gdzie klucz wiersza (imię) rozpoczyna się od litery wcześniejszej niż "M" alfabetu.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

Teraz drukowanie wyników:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

## <a name="retrieve-a-single-entity"></a>Pobieranie pojedynczej jednostki

Można napisać zapytanie do pobrania jednej, określonej jednostki. W tym miejscu użyć `TableOperation` do określenia klienta "Larry Buster". Zamiast kolekcji, możesz wrócić `Customer`. Określenie zarówno klucz partycji i klucz wiersza w zapytaniu jest najszybszym sposobem na pobranie jednej jednostki z usługi tabel.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

Teraz drukowanie wyników:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


## <a name="replace-an-entity"></a>Zastępowanie jednostki

Aby zaktualizować jednostkę, pobierz ją z usługi tabel, zmodyfikuj obiekt jednostki, a następnie zapisz zmiany powrót do tabeli usługi przy użyciu `Replace` operacji. Powoduje to, że jednostka będzie całkowicie zastąpiona na serwerze, chyba że jednostka na serwerze została zmieniona, ponieważ został on pobrany, w którym to przypadku operacja nie powiedzie. Jest to błąd uniemożliwia aplikacji nieodwracalne nadpisanie zmiany z innych źródeł.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

## <a name="insert-or-replace-an-entity"></a>Wstawianie lub zastępowanie jednostki

Czasami nie wiadomo, czy jednostka istnieje w tabeli lub nie. A jeśli tak, czy obecne wartości przechowywane w nim nie są już potrzebne. Można użyć `InsertOrReplace` w celu utworzenia jednostki lub zastąp ją, jeśli istnieje, niezależnie od jego stanu.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L140)]

## <a name="query-a-subset-of-entity-properties"></a>Tworzenie zapytania do podzbioru właściwości jednostki

Zapytanie tabeli może pobrać kilka właściwości jednostki zamiast wszystkich z nich. Ta technika, zwana projekcją, może poprawić wydajność zapytań, zwłaszcza w przypadku dużych jednostek. W tym miejscu zwracać dotyczy tylko wiadomości e-mail przy użyciu `DynamicTableEntity` i `EntityResolver`. Należy pamiętać, że projekcji nie jest obsługiwana w lokalnym emulatorze magazynu, dlatego ten kod zadziała tylko wtedy, gdy używasz konta w usłudze tabel.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L146-L157)]

## <a name="retrieve-entities-in-pages-asynchronously"></a>Pobieranie asynchroniczne jednostek na stronach

Jeśli odczytujesz dużą liczbę jednostek i chcesz przetworzyć je zgodnie z ich pobraniu, zamiast oczekiwania na zwrócenie ich wszystkich, można użyć zapytania segmentowanego. W tym miejscu możesz zwracania wyników na stronach za pomocą async przepływu pracy, dzięki czemu wykonanie nie jest blokowane podczas oczekiwania dla dużych zestawów wyników do zwrócenia.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L177)]

Można teraz wykonywać te obliczenia synchronicznie:

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L179-L179)]

## <a name="delete-an-entity"></a>Usuwanie jednostki

Po jej pobraniu, można usunąć jednostki. Podobnie jak w przypadku aktualizowania jednostki, to zakończy się niepowodzeniem, jeśli jednostka została zmieniona od czasu jej pobrania.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L185-L186)]

## <a name="delete-a-table"></a>Usuwanie tabeli

Z konta magazynu można usunąć tabeli. Tabela, która została usunięta będzie mógł zostać ponownie utworzone w danym okresie czasu po jej usunięciu.

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L192-L192)]

## <a name="next-steps"></a>Następne kroki

Teraz, kiedy znasz już podstawy magazynu tabel, skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu:

- [Interfejsy API usługi Azure Storage dla platformy .NET](/dotnet/api/overview/azure/storage)
- [Dostawca typów magazynu Azure](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Azure Storage Team Blog](https://blogs.msdn.microsoft.com/b/windowsazurestorage/)
- [Konfigurowanie parametrów połączenia usługi Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Rozpoczynanie pracy z magazynem tabel Azure w .NET](https://azure.microsoft.com/documentation/samples/storage-table-dotnet-getting-started/)
