---
title: Rozpoczynanie pracy z usługą Azure Blob Storage przy użyciu języka F#
description: Przechowuj dane niestrukturalne w chmurze za pomocą usługi Azure Blob Storage.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: c8b42339ff1d76f262e956b5e34cc598e0fc855d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630510"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>Rozpoczynanie pracy z usługą Azure Blob Storage przy użyciu języka F\#

Azure Blob Storage to usługa, która przechowuje dane niestrukturalne w chmurze w postaci obiektów BLOB. Magazyn obiektów BLOB umożliwia przechowywanie dowolnego typu danych tekstowych lub binarnych, takich jak dokument, plik multimedialny lub Instalator aplikacji. Magazyn obiektów BLOB jest również określany jako Storage Object.

W tym artykule przedstawiono sposób wykonywania typowych zadań za pomocą usługi BLOB Storage. Przykłady są zapisywane przy użyciu F# biblioteki klienckiej usługi Azure Storage dla platformy .NET. Objęte zadaniami obejmują sposób przekazywania, wyświetlania, pobierania i usuwania obiektów BLOB.

Ogólne omówienie usługi BLOB Storage można znaleźć [w przewodniku .NET dla usługi BLOB Storage](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Wymagania wstępne

Aby skorzystać z tego przewodnika, musisz najpierw [utworzyć konto usługi Azure Storage](/azure/storage/storage-create-storage-account). Wymagany jest również klucz dostępu do magazynu dla tego konta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Utwórz F# skrypt i uruchom F# interaktywny

Przykłady w tym artykule mogą być używane w F# aplikacji lub F# skrypcie. Aby utworzyć F# skrypt, Utwórz plik z `.fsx` rozszerzeniem, na przykład `blobs.fsx`w środowisku F# deweloperskim.

Następnie należy użyć [Menedżera pakietów](package-management.md) , takiego jak [Paket](https://fsprojects.github.io/Paket/) lub [](https://www.nuget.org/) `WindowsAzure.Storage` NuGet, aby zainstalować `Microsoft.WindowsAzure.ConfigurationManager` pakiety i odwołania `WindowsAzure.Storage.dll` `Microsoft.WindowsAzure.Configuration.dll` oraz w skrypcie przy użyciu `#r` dyrektywy.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujące `open` instrukcje na początku `blobs.fsx` pliku:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Pobierz parametry połączenia

Potrzebujesz parametrów połączenia usługi Azure Storage dla tego samouczka. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [Konfigurowanie parametrów połączenia magazynu](/azure/storage/storage-configure-connection-string).

W samouczku wprowadzono parametry połączenia w skrypcie, takie jak:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

Nie jest to jednak **zalecane** w przypadku rzeczywistych projektów. Klucz konta magazynu jest podobny do hasła głównego dla konta magazynu. Zawsze należy zachować ostrożność, aby chronić klucz konta magazynu. Należy unikać dystrybuowania go do innych użytkowników, ich trwałego kodowania lub zapisywania w pliku w formacie zwykłego tekstu, który jest dostępny dla innych. Możesz ponownie wygenerować klucz za pomocą witryny Azure Portal, jeśli uważasz, że jego zabezpieczenia mogły zostać naruszone.

W przypadku prawdziwych aplikacji najlepszym sposobem obsługi parametrów połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Korzystanie z usługi Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takiego jak `ConfigurationManager` typ .NET Framework.

### <a name="parse-the-connection-string"></a>Analizowanie parametrów połączenia

Aby przeanalizować parametry połączenia, użyj:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Spowoduje to zwrócenie `CloudStorageAccount`elementu.

### <a name="create-some-local-dummy-data"></a>Tworzenie niektórych lokalnych danych fikcyjnych

Przed rozpoczęciem Utwórz własne fikcyjne dane lokalne w katalogu naszego skryptu. Później przekażesz te dane.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Tworzenie klienta Blob service

`CloudBlobClient` Typ umożliwia pobieranie kontenerów i obiektów BLOB przechowywanych w usłudze BLOB Storage. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Teraz możesz przystąpić do pisania kodu, który odczytuje dane z usługi BLOB Storage i zapisuje dane.

## <a name="create-a-container"></a>Tworzenie kontenera

Ten przykład pokazuje, jak utworzyć kontener, jeśli jeszcze nie istnieje:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Domyślnie nowy kontener jest prywatny, co oznacza, że należy określić klucz dostępu do magazynu w celu pobrania obiektów blob z tego kontenera. Jeśli chcesz, aby pliki w kontenerze były dostępne dla wszystkich użytkowników, możesz ustawić kontener jako publiczny przy użyciu następującego kodu:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Każda osoba w Internecie może wyświetlać obiekty blob w kontenerze publicznym, ale można je modyfikować lub usuwać tylko wtedy, gdy masz odpowiedni klucz dostępu do konta lub sygnaturę dostępu współdzielonego.

## <a name="upload-a-blob-into-a-container"></a>Przekazywanie obiektu BLOB do kontenera

Usługa Azure Blob Storage obsługuje blokowe obiekty blob i stronicowe obiekty blob. W większości przypadków zalecanym typem jest blokowy obiekt BLOB.

Aby przekazać plik do blokowego obiektu BLOB, Pobierz odwołanie do kontenera i użyj go, aby uzyskać odwołanie do blokowego obiektu BLOB. Po uzyskaniu odwołania do obiektu BLOB możesz przekazać do niego dowolny strumień danych, wywołując `UploadFromFile` metodę. Ta operacja tworzy obiekt BLOB, jeśli jeszcze nie istnieje, lub go zastępuje, jeśli istnieje.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Wyświetlanie listy obiektów BLOB w kontenerze

Aby wyświetlić listę obiektów BLOB w kontenerze, należy najpierw pobrać odwołanie do kontenera. Następnie można użyć `ListBlobs` metody kontenera do pobrania obiektów blob i/lub znajdujących się w niej katalogów. Aby uzyskać dostęp do bogatego zestawu właściwości `IListBlobItem`i metod dla zwracanych danych, należy rzutować je `CloudBlockBlob`na obiekt, `CloudBlobDirectory` `CloudPageBlob`lub. Jeśli typ jest nieznany, możesz użyć sprawdzenia typu, aby określić, do którego rzutowania. Poniższy kod ilustruje sposób pobierania i wyprowadzania identyfikatorów URI poszczególnych elementów w `mydata` kontenerze:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Można także nazywać obiekty blob z informacjami o ścieżce w ich nazwach. Spowoduje to utworzenie struktury katalogów wirtualnych, którą można organizować i przechodzić w taki sam sposób jak w przypadku tradycyjnego systemu plików. Należy pamiętać, że struktura katalogów jest tylko wirtualna — jedyne zasoby dostępne w usłudze BLOB Storage to kontenery i obiekty blob. Jednak Biblioteka klienta magazynu oferuje `CloudBlobDirectory` obiekt do odwoływania się do katalogu wirtualnego i upraszcza proces pracy z obiektami BLOB zorganizowanymi w ten sposób.

Rozważmy na przykład następujący zestaw blokowych obiektów BLOB w kontenerze o `photos`nazwie:

*Photo1. jpg*\
*2015/Architecture/Description. txt*\
*2015/Architecture/photo3. jpg*\
*2015/Architecture/photo4. jpg*\
*2016/Architecture/photo5. jpg*\
*2016/Architecture/photo6. jpg*\
*2016/architektura/opis. txt*\
*2016/photo7. jpg*\

Po wywołaniu `ListBlobs` kontenera (jak w powyższym przykładzie) zwracana jest lista hierarchiczna. Jeśli zawiera zarówno `CloudBlobDirectory` obiekt, `CloudBlockBlob` jak i obiekty, reprezentujące katalogi i obiekty blob w kontenerze, dane wyjściowe wyglądają podobnie do tego:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Opcjonalnie można ustawić `UseFlatBlobListing` parametr `ListBlobs` metody na `true`. W takim przypadku każdy obiekt BLOB w kontenerze jest zwracany jako `CloudBlockBlob` obiekt. Wywołanie `ListBlobs` do zwrócenia płaskiej listy wygląda następująco:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

w zależności od bieżącej zawartości kontenera wyniki wyglądają następująco:

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

## <a name="download-blobs"></a>Pobieranie obiektów BLOB

Aby pobrać obiekty blob, najpierw Pobierz odwołanie do obiektu BLOB, a `DownloadToStream` następnie Wywołaj metodę. W poniższym przykładzie zastosowano `DownloadToStream` metodę transferu zawartości obiektu BLOB do obiektu strumienia, który można następnie przechowywać do pliku lokalnego.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Możesz również użyć `DownloadToStream` metody, aby pobrać zawartość obiektu BLOB jako ciąg tekstowy.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Usuwanie obiektów BLOB

Aby usunąć obiekt BLOB, należy najpierw pobrać odwołanie do obiektu BLOB, a `Delete` następnie wywołać metodę.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Wyświetlanie listy obiektów BLOB na stronach asynchronicznie

Jeśli wyświetlasz dużą liczbę obiektów blob lub chcesz kontrolować liczbę wyników zwracanych w ramach jednej operacji tworzenia listy, możesz wyświetlić listę obiektów BLOB na stronach wyników. Ten przykład pokazuje, jak zwracać wyniki na stronach asynchronicznie, tak że wykonywanie nie jest blokowane podczas oczekiwania na zwrócenie dużego zestawu wyników.

Ten przykład pokazuje płaską listę obiektów blob, ale można również wykonać listę hierarchiczną, ustawiając `useFlatBlobListing` parametr `ListBlobsSegmentedAsync` metody na `false`.

Przykład definiuje metodę asynchroniczną przy użyciu `async` bloku. ``let!`` Słowo kluczowe zawiesza wykonywanie przykładowej metody do momentu zakończenia zadania tworzenia listy.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Teraz można użyć tej procedury asynchronicznej w następujący sposób. Najpierw przekażesz niektóre fikcyjne dane (przy użyciu pliku lokalnego utworzonego wcześniej w tym samouczku).

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Teraz Wywołaj procedurę. Używasz, `Async.RunSynchronously` aby wymusić wykonanie operacji asynchronicznej.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Zapisywanie do dołączanego obiektu BLOB

Obiekt BLOB dołączania jest zoptymalizowany pod kątem operacji dołączania, takich jak rejestrowanie. Podobnie jak blokowy obiekt BLOB, obiekt BLOB dołączania składa się z bloków, ale po dodaniu nowego bloku do obiektu BLOB dołączania jest on zawsze dołączany na końcu obiektu BLOB. Nie można zaktualizować lub usunąć istniejącego bloku w obiekcie blob dołączania. Identyfikatory bloków dla obiektu BLOB dołączania nie są ujawniane, ponieważ są dla blokowych obiektów BLOB.

Każdy blok w obiekcie blob dołączania może mieć inny rozmiar, maksymalnie 4 MB, a obiekt BLOB dołączania może zawierać maksymalnie 50 000 bloków. Maksymalny rozmiar obiektu BLOB dołączania jest z tego powodu nieco większy niż 195 GB (bloki 4 MB X 50 000).

Poniższy przykład tworzy nowy obiekt BLOB dołączania i dołącza do niego pewne dane, symulując prostą operację rejestrowania.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Zobacz [Opis blokowych obiektów blob, stronicowych obiektów blob i dołączanie obiektów BLOB](https://msdn.microsoft.com/library/azure/ee691964.aspx) , aby uzyskać więcej informacji o różnicach między trzema typami obiektów BLOB.

## <a name="concurrent-access"></a>Dostęp współbieżny

Aby zapewnić obsługę współbieżnego dostępu do obiektu BLOB z wielu klientów lub wielu wystąpień procesów, można użyć elementów ETags lub **leases**.

* **ETag** — umożliwia wykrycie, że obiekt BLOB lub kontener został zmodyfikowany przez inny proces

* **Dzierżawa** — umożliwia uzyskanie dostępu do obiektu BLOB z wyłącznym, odnawialnym, zapisem lub usunięciem w danym okresie czasu

Aby uzyskać więcej informacji, zobacz [Zarządzanie współbieżnością w Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Nazywanie kontenerów

Każdy obiekt BLOB w usłudze Azure Storage musi znajdować się w kontenerze. Kontener stanowi część nazwy obiektu BLOB. Na przykład `mydata` jest nazwą kontenera w następujących przykładowych identyfikatorach URI obiektów blob:

- https://storagesample.blob.core.windows.net/mydata/blob1.txt
- https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Nazwa kontenera musi być prawidłową nazwą DNS, zgodnie z następującymi regułami nazewnictwa:

1. Nazwy kontenerów muszą zaczynać się literą lub cyfrą i mogą zawierać tylko litery, cyfry i znak kreski (-).
1. Każdy znak kreski (-) musi być bezpośrednio poprzedzony literą lub cyfrą; kolejne kreski są niedozwolone w nazwach kontenerów.
1. Wszystkie litery w nazwie kontenera muszą być małymi literami.
1. Nazwy kontenerów muszą zawierać od 3 do 63 znaków.

Należy pamiętać, że nazwa kontenera musi być zawsze małymi literami. Jeśli w nazwie kontenera dołączysz wielką literę lub w inny sposób naruszasz reguły nazewnictwa kontenerów, może wystąpić błąd 400 (Nieprawidłowe żądanie).

## <a name="managing-security-for-blobs"></a>Zarządzanie zabezpieczeniami dla obiektów BLOB

Domyślnie usługa Azure Storage zabezpiecza dane przez ograniczenie dostępu do właściciela konta, który jest w posiadaniu kluczy dostępu do konta. Gdy musisz udostępnić dane obiektów BLOB na koncie magazynu, ważne jest, aby to zrobić bez naruszania zabezpieczeń kluczy dostępu do konta. Ponadto można szyfrować dane obiektów BLOB w celu zapewnienia bezpieczeństwa przechodzenia przez sieć i w usłudze Azure Storage.

### <a name="controlling-access-to-blob-data"></a>Kontrolowanie dostępu do danych obiektów BLOB

Domyślnie dane obiektów BLOB na koncie magazynu są dostępne tylko dla właściciela konta magazynu. Uwierzytelnianie żądań w usłudze BLOB Storage wymaga domyślnie klucza dostępu do konta. Jednak może być konieczne udostępnienie pewnych danych obiektów BLOB innym użytkownikom.

### <a name="encrypting-blob-data"></a>Szyfrowanie danych obiektów BLOB

Usługa Azure Storage obsługuje szyfrowanie danych obiektów BLOB zarówno na kliencie, jak i na serwerze.

## <a name="next-steps"></a>Następne kroki

Teraz, gdy znasz już podstawowe informacje o usłudze BLOB Storage, Skorzystaj z poniższych linków, aby dowiedzieć się więcej.

### <a name="tools"></a>Narzędzia

- [F#AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
Dostawca F# typów, który może służyć do eksplorowania obiektów blob, tabel i kolejek zasobów usługi Azure Storage oraz łatwego zastosowania na nich CRUD operacji.

- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
F# Interfejs API służący do korzystania z usługi Microsoft Azure Table Storage

- [Eksplorator usługi Microsoft Azure Storage (darmową)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Bezpłatna, autonomiczna aplikacja oferowana przez firmę Microsoft, która umożliwia wizualne korzystanie z danych usługi Azure Storage w systemach Windows, OS X i Linux.

### <a name="blob-storage-reference"></a>Odwołanie do magazynu obiektów BLOB

- [Interfejsy API usługi Azure Storage dla platformy .NET](/dotnet/api/overview/azure/storage)
- [Dokumentacja interfejsu API REST usług Azure Storage](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>Pokrewne prowadnice

- [Wprowadzenie z usługą Azure Blob Storage wC#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Transferowanie danych za pomocą narzędzia wiersza polecenia AzCopy w systemie Windows](/azure/storage/common/storage-use-azcopy)
- [Transferowanie danych za pomocą narzędzia wiersza polecenia AzCopy w systemie Linux](/azure/storage/common/storage-use-azcopy-linux)
- [Konfigurowanie parametrów połączenia usługi Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Blog zespołu usługi Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Szybki start: Tworzenie obiektu BLOB w magazynie obiektów przy użyciu platformy .NET](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
