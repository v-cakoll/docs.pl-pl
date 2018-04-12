---
title: 'Rozpoczynanie pracy z magazynem obiektów Blob platformy Azure przy użyciu języka F #'
description: Przechowuj dane niestrukturalne w chmurze za pomocą magazynu obiektów Blob platformy Azure.
keywords: visual f#, f#, functional programming, .NET, .NET Core, Azure
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c5b74a4f-dcd1-4849-930c-904b6c8a04e1
ms.openlocfilehash: 14ccba36638c724536793a6a589cf1c0a6186eeb
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>Rozpoczynanie pracy z magazynem obiektów Blob platformy Azure przy użyciu języka F # #

Magazyn obiektów Blob Azure to usługa, która przechowywania danych niestrukturalnych w chmurze w postaci obiektów blob. Magazyn obiektów blob umożliwia przechowywanie dowolnego typu tekstu lub danych binarnych, takich jak dokument, plik multimedialny lub Instalator aplikacji. Magazyn obiektów blob jest również nazywany magazynem obiektów.

W tym artykule przedstawiono sposób wykonywania typowych zadań przy użyciu magazynu obiektów Blob. Przykłady są napisane przy użyciu F # za pomocą biblioteki klienta magazynu Azure dla platformy .NET. Zadania, jest objęty obejmują jak przekazywanie, listy, pobieranie i usuwanie obiektów blob.

Omówienie koncepcji magazynu obiektów blob, zobacz [przewodnik .NET dla magazynu obiektów blob](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć tego przewodnika, należy najpierw [utworzyć konto magazynu Azure](/azure/storage/storage-create-storage-account). Należy również klucz dostępu do magazynu dla tego konta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Tworzenie skryptu języka F # i rozpocząć F # Interactive

Przykłady w tym artykule można używać w F # aplikacji lub skryptu języka F #. Aby utworzyć skrypt F #, Utwórz plik o `.fsx` rozszerzenie, na przykład `blobs.fsx`, w środowiska deweloperskiego F #.

Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) do zainstalowania `WindowsAzure.Storage` i `Microsoft.WindowsAzure.ConfigurationManager` pakietów i odwołanie `WindowsAzure.Storage.dll` i `Microsoft.WindowsAzure.Configuration.dll` w za pomocą skryptu `#r` dyrektywy.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujące `open` instrukcje na początku `blobs.fsx` pliku:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Pobierz ciąg połączenia

Parametry połączenia magazynu Azure są wymagane dla tego samouczka. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).

Samouczek możesz wprowadzić parametry połączenia za pomocą skryptu, jak to:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

Jest to jednak **niezalecane** rzeczywiste projektów. Klucz konta magazynu jest podobny do hasła głównego konta magazynu. Zawsze starannie Chroń klucz konta magazynu. Unikaj udostępniaj go innym użytkownikom, kodować je lub zapisać go w pliku jako zwykły tekst, który jest dostępny do innych użytkowników. Można ponownie wygenerować klucz przy użyciu portalu Azure, jeśli uważasz, że mogą zostać naruszone.

Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia w pliku konfiguracji, można to zrobić:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Przy użyciu programu Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Przeanalizować parametrów połączenia

Aby przeanalizować parametrów połączenia, należy użyć:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

To polecenie zwróci `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Tworzenie niektórych fikcyjny dane lokalne

Przed rozpoczęciem należy utworzyć niektórych fikcyjny danych lokalnych w katalogu naszych skryptu. Później możesz przekazać dane.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Tworzenie klienta usługi Blob

`CloudBlobClient` Typu umożliwia pobieranie kontenerów i obiektów blob przechowywanych w magazynie obiektów Blob. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Teraz można przystąpić do pisania kodu, która odczytuje i zapisuje dane do magazynu obiektów Blob.

## <a name="create-a-container"></a>Tworzenie kontenera

W tym przykładzie pokazano, jak utworzyć kontener, jeśli jeszcze nie istnieje:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Domyślnie nowy kontener jest prywatny, co oznacza, że należy określić klucz dostępu do magazynu, aby pobierać obiekty BLOB z tego kontenera. Jeśli chcesz udostępnić pliki w kontenerze wszystkim użytkownikom, możesz ustawić kontener jako publiczny przy użyciu następującego kodu:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Wszyscy użytkownicy Internetu mogą wyświetlać obiekty BLOB w kontenerze publicznym, ale można zmodyfikować lub usunąć je tylko wtedy, gdy klucz dostępu do odpowiedniego konta lub sygnatury dostępu współdzielonego.

## <a name="upload-a-blob-into-a-container"></a>Przekazywanie obiektu blob do kontenera

Azure Blob Storage obsługuje blokowe i stronicowe obiekty BLOB. W większości przypadków blokowych obiektów blob jest zalecany typ do użycia.

Aby przekazać plik do blokowego obiektu blob, Pobierz odwołanie do kontenera i użyj go, aby pobrać odwołanie do obiektu blob bloku. Po utworzeniu odwołanie do obiektu blob, dowolny strumień danych można przekazać do niej przez wywołanie metody `UploadFromFile` metody. Ta operacja tworzy obiektu blob, jeśli on nie istnieje, lub go zastąpić, jeśli istnieje.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Wyświetlanie obiektów blob w kontenerze

Aby wyświetlić listę obiektów blob w kontenerze, należy najpierw pobrać odwołanie do kontenera. Następnie można użyć kontenera `ListBlobs` metodę, aby pobrać obiekty BLOB i/lub zawarte w nim katalogi. Aby dostęp do bogatego zestawu właściwości i metod zwróconego `IListBlobItem`, należy rzutować go do `CloudBlockBlob`, `CloudPageBlob`, lub `CloudBlobDirectory` obiektu. Jeśli typ jest nieznany, umożliwia sprawdzanie typu określenie, które można rzutować na. Poniższy kod przedstawia sposób pobierania i zwracania identyfikatora URI poszczególnych elementów w `mydata` kontenera:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Można także obiekty BLOB nazwy zawierające informacje o ścieżce ich nazw. Spowoduje to utworzenie wirtualnej struktury katalogów, które można organizować i przechodzić między nimi tak jak w przypadku tradycyjnego systemu plików. Należy pamiętać, że struktura katalogów jest wyłącznie wirtualna — jedyne zasoby dostępne w magazynie obiektów Blob to kontenery i obiekty BLOB. Jednak biblioteka klienta magazynu zapewnia `CloudBlobDirectory` obiekt, aby odwoływać się do katalogu wirtualnego i uprościć proces Praca z obiektami blob zorganizowanymi w ten sposób.

Rozważmy na przykład następujący zestaw blokowych obiektów blob w kontenerze o nazwie `photos`:

*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*

Podczas wywoływania `ListBlobs` kontenera (jak w powyższym przykładzie), zwrócenie listy hierarchicznej. Jeśli oba zawiera `CloudBlobDirectory` i `CloudBlockBlob` obiektów reprezentujących katalogi i obiekty BLOB w kontenerze, odpowiednio, a następnie dane wyjściowe podobny do poniższego:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Opcjonalnie można ustawić `UseFlatBlobListing` parametr `ListBlobs` metodę `true`. W takim przypadku każdy obiekt blob w kontenerze jest zwracana jako `CloudBlockBlob` obiektu. Wywołanie `ListBlobs` do zwrócenia listy niezhierarchizowanej wygląda następująco:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

i, w zależności od bieżącej zawartości z kontenera wyniki wyglądają następująco:

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a>Pobieranie obiektów blob

Aby pobrać obiekty BLOB, należy najpierw pobrać odwołanie do obiektu blob, a następnie wywołać `DownloadToStream` metody. W poniższym przykładzie użyto `DownloadToStream` metodę, aby przesłać zawartość obiektu blob do obiektu strumienia, który można następnie zachować do pliku lokalnego.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Można również użyć `DownloadToStream` metodę, aby pobrać zawartość obiektu blob jako ciąg tekstowy.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Usuwanie obiektów blob

Aby usunąć obiekt blob, najpierw pobrać odwołanie do obiektu blob, a następnie wywołać `Delete` dla niego metodę.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Asynchroniczne wyświetlanie obiektów blob na stronach

Jeśli chcesz wyświetlić dużą liczbę obiektów blob lub chcesz kontrolować liczbę wyników zwracanych przez jedną operację wyświetlania listy, można wyświetlić listę obiektów blob na stronach wyników. Ten przykład przedstawia sposób zwracania wyników na stronach asynchronicznie, dzięki czemu wykonanie nie jest blokowane podczas oczekiwania na zwrócenie dużych zestawów wyników.

W tym przykładzie przedstawiono niezhierarchizowaną listę obiektów blob, ale można również wykonywać listę hierarchiczną, ustawiając `useFlatBlobListing` parametr `ListBlobsSegmentedAsync` metodę `false`.

Przykład definiuje metodę asynchroniczną, przy użyciu `async` bloku. ``let!`` — Słowo kluczowe wstrzymuje wykonywanie przykładowej metody do momentu ukończenia zadania wyświetlania listy.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Firma Microsoft mogą teraz używać tej procedury asynchronicznych w następujący sposób. Najpierw należy przekazywania danych zastępczego (przy użyciu lokalnego pliku utworzona we wcześniejszej części tego samouczka).

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Teraz wywoła procedurę. Możesz użyć ``Async.RunSynchronously`` Aby wymusić wykonanie operacji asynchronicznej.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Zapisywanie do uzupełnialnego obiektu blob

Uzupełnialny obiekt blob jest zoptymalizowana pod kątem operacji dołączania, takich jak rejestrowanie. Podobnie jak blokowy obiekt blob uzupełnialny obiekt blob jest złożony z bloków, ale po dodaniu nowego bloku do uzupełnialnego obiektu blob jest zawsze dołączany na końcu obiektu blob. Nie można zaktualizować lub usunąć istniejącego bloku w uzupełnialnym obiekcie blob. Identyfikatory bloków w uzupełnialnym obiekcie blob nie są widoczne, jak w przypadku blokowego obiektu blob.

Każdy blok w uzupełnialnym obiekcie blob może być inny rozmiar maksymalnie 4 MB, a uzupełnialny obiekt blob może zawierać maksymalnie 50 000 bloków. Maksymalny rozmiar uzupełnialnego obiektu blob w związku z tym jest nieco przekraczać 195 GB (4 MB X 50 000 bloków).

Poniższy przykład tworzy nowy uzupełnialny obiekt blob i dołącza niektóre dane, symulując prostą operację rejestrowania.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Zobacz [opis blokowe, stronicowe obiekty BLOB i Dołącz obiektów blob](https://msdn.microsoft.com/library/azure/ee691964.aspx) Aby uzyskać więcej informacji o różnicach między tymi trzema typami obiektów blob.

## <a name="concurrent-access"></a>Współbieżny dostęp

Aby obsługiwać równoczesny dostęp do obiektu blob z wielu klientów lub wielu wystąpień procesu, można użyć **elementy etag** lub **dzierżawy**.

* **Element etag** — pozwala wykryć, że obiekt blob lub kontener został zmodyfikowany przez inny proces

* **Dzierżawy** — pozwala uzyskać wyłącznej, odnawialnymi, zapisu albo usuwania dostępu do obiektu blob w danym okresie czasu

Aby uzyskać więcej informacji, zobacz [Zarządzanie współbieżność w magazynie platformy Microsoft Azure](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Kontenery nazewnictwa

Każdy obiekt blob w magazynie Azure musi znajdować się w kontenerze. Kontener jest częścią nazwy obiektu blob. Na przykład `mydata` to nazwa kontenera w tych przykładowych identyfikatorach URI obiektów blob:

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Nazwa kontenera musi być prawidłową nazwą DNS zgodną z następującymi zasadami nazewnictwa:

1. Nazwy kontenerów muszą zaczynać się literą lub cyfrą i może zawierać tylko litery, cyfry i znak kreski (-).
1. Każdy znak kreski (-) musi być od razu poprzedzone i następuje literą lub cyfrą; następujących po sobie kresek nie są dozwolone w nazwach kontenerów.
1. Wszystkie litery w nazwie kontenera muszą być małymi literami.
1. Nazwy kontenerów muszą mieć od 3 do 63 znaków.

Należy pamiętać, że nazwa kontenera musi być zawsze małe litery. Jeśli zawierać wielką literę w nazwie kontenera lub reguły nazewnictwa dotyczące kontenerów zostaną naruszone w przeciwnym razie, może zostać wyświetlony błąd 400 (nieprawidłowe żądanie).

## <a name="managing-security-for-blobs"></a>Zarządzanie zabezpieczeniami obiektów blob

Domyślnie usługi Azure Storage chroni dane przez ograniczenie dostępu do właściciela konta, który znajduje się w posiadaniu klucze dostępu do konta. Potrzebne do udostępnienia danych obiektów blob na koncie magazynu, należy to zrobić bez uszczerbku dla bezpieczeństwa kluczy dostępu konta. Ponadto można zaszyfrować dane obiektu blob, aby zapewnić bezpieczeństwo podczas przesyłania przez sieć oraz w usłudze Azure Storage.

### <a name="controlling-access-to-blob-data"></a>Kontrolowanie dostępu do danych obiektów blob

Domyślnie dane obiektów blob na koncie magazynu jest dostępny tylko dla właściciela konta magazynu. Uwierzytelniania żądań dotyczących magazynu obiektów Blob wymaga klucz dostępu do konta domyślnie. Możesz jednak udostępnić określone dane obiektów blob innym użytkownikom.

Aby uzyskać więcej informacji na temat kontrolowania dostępu do magazynu obiektów blob, zobacz [przewodniku .NET dla sekcji magazynu obiektów blob w kontroli dostępu](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).


### <a name="encrypting-blob-data"></a>Szyfrowanie danych obiektów blob

Usługa Azure Storage obsługuje szyfrowanie danych obiektów blob zarówno po stronie klienta, jak i na serwerze.

Aby uzyskać więcej informacji na temat szyfrowania danych obiektów blob, zobacz [.NET przewodnik dla sekcji magazynu obiektów blob w szyfrowania](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).

## <a name="next-steps"></a>Następne kroki

Teraz, kiedy znasz już podstawy magazynu obiektów Blob, skorzystaj z poniższych linków, aby dowiedzieć się więcej.

### <a name="tools"></a>Narzędzia
- [F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) F # typ dostawcy, który może służyć do eksplorowania zasobów obiektów Blob, tabel i kolejek usługi Azure Storage i łatwo zastosować operacji CRUD na nich.
- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) F # interfejsu API przy użyciu usługi Microsoft Azure Table Storage
- [Microsoft Azure magazynu Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) jest bezpłatna, aplikacja autonomiczny firmy Microsoft, który umożliwia pracę wizualnie z danymi usługi Azure Storage w systemie Windows, OS X i Linux.

### <a name="blob-storage-reference"></a>Odwołanie do obiektu blob magazynu

- [Interfejsy API usługi Azure Storage dla platformy .NET](/dotnet/api/overview/azure/storage)
- [Dokumentacja interfejsu API REST usług magazynu Azure](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>Przewodniki pokrewne

- [Wprowadzenie do magazynu obiektów Blob platformy Azure w języku C#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Transfer danych za pomocą wiersza polecenia azcopy w systemie Windows](/azure/storage/common/storage-use-azcopy)
- [Transfer danych za pomocą wiersza polecenia azcopy w systemie Linux](/azure/storage/common/storage-use-azcopy-linux)
- [Konfigurowanie parametrów połączenia usługi Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Azure Storage Team Blog](https://blogs.msdn.microsoft.com/windowsazurestorage/)
