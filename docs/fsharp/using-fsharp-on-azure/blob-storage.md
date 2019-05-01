---
title: Rozpoczynanie pracy z usługą Azure Blob storage przy użyciuF#
description: Store danych bez struktury w chmurze za pomocą usługi Azure Blob storage.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 62178edf22ad48d0388f34488b68d135068d50a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982517"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>Rozpoczynanie pracy z usługą Azure Blob storage za pomocą F\#

Usługa Azure Blob storage to usługa, która przechowuje dane niestrukturalne w chmurze w postaci obiektów blob. Magazyn obiektów blob można przechowywać dowolnego typu dane tekstowe lub binarne, takie jak dokument, plik multimedialny lub Instalator aplikacji. Magazyn obiektów blob jest również określany jako magazyn obiektów.

W tym artykule przedstawiono sposób wykonywania typowych zadań przy użyciu usługi Blob storage. Przykłady są zapisywane z użyciem F# przy użyciu biblioteki klienta usługi Azure Storage dla platformy .NET. Zadania objęte obejmują jak przekazywanie, listy, pobieranie i usuwanie obiektów blob.

Aby uzyskać omówienie pojęć dotyczących magazynu obiektów blob, zobacz [przewodnik platformy .NET dla usługi blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć tego przewodnika, należy najpierw [Tworzenie konta usługi Azure storage](/azure/storage/storage-create-storage-account). Musisz mieć również klucz dostępu do magazynu dla tego konta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Tworzenie F# skrypt i uruchomić F# interaktywne

Przykłady w tym artykule mogą być używane w jednej F# aplikacji lub F# skryptu. Aby utworzyć F# skrypt, Utwórz plik o `.fsx` rozszerzenia, na przykład `blobs.fsx`w usługi F# środowiska deweloperskiego.

Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) zainstalował `WindowsAzure.Storage` i `Microsoft.WindowsAzure.ConfigurationManager` pakietów i odwołań `WindowsAzure.Storage.dll` i `Microsoft.WindowsAzure.Configuration.dll` przy użyciu skryptu `#r` dyrektywy.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujący kod `open` instrukcji na górze `blobs.fsx` pliku:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Pobieranie parametrów połączenia

Parametry połączenia usługi Azure Storage są potrzebne w tym samouczku. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).

Samouczek wprowadź parametry połączenia w skrypcie w następujący sposób:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

Jest to jednak **niezalecane** rzeczywiste projektów. Klucz konta magazynu jest podobny do hasła głównego konta magazynu. Zawsze starannie Chroń klucz konta magazynu. Należy unikać, ich dystrybucję w innym użytkownikom, kodować je lub zapisanie go w pliku tekstowego, który jest dostępny dla innych użytkowników. Można ponownie wygenerować klucz za pośrednictwem witryny Azure Portal, jeśli uważasz, że mogą zostać przejęte.

Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Użycie programu Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Przeanalizować parametrów połączenia

Aby przeanalizować parametrów połączenia, należy użyć:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Spowoduje to zwrócenie `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Tworzenie lokalnej fikcyjnego danych

Przed rozpoczęciem należy utworzyć pewnych fikcyjnego danych lokalnych w katalogu naszego skryptu. Później możesz przekazać te dane.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Tworzenie klienta usługi obiektów Blob

`CloudBlobClient` Typu umożliwia pobieranie kontenerów i obiektów blob przechowywanych w magazynie obiektów Blob. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Teraz możesz przystąpić do pisania kodu, który odczytuje i zapisuje dane do magazynu obiektów Blob.

## <a name="create-a-container"></a>Tworzenie kontenera

Ten przykład pokazuje, jak utworzyć kontener, jeśli jeszcze nie istnieje:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Domyślnie nowy kontener jest prywatny, co oznacza, że musisz podać klucz dostępu do magazynu, aby pobierać obiekty BLOB z tego kontenera. Jeśli chcesz udostępnić pliki znajdujące się w kontenerze wszystkim użytkownikom, można ustawić kontener jako publiczny, używając następującego kodu:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Wszyscy użytkownicy Internetu mogą wyświetlać obiekty BLOB w kontenerze publicznym, ale użytkownik może je modyfikować lub usuwać tylko wtedy, gdy masz klucz dostępu do odpowiedniego konta lub sygnatury dostępu współdzielonego.

## <a name="upload-a-blob-into-a-container"></a>Przekazywanie obiektu blob w kontenerze

Usługa Azure Blob Storage obsługuje blokowe i stronicowe obiekty BLOB. W większości przypadków blokowych obiektów blob to zalecany typ do użycia.

Aby przekazać plik do blokowego obiektu blob, Pobierz odwołanie do kontenera, a następnie użyj, aby uzyskać odwołanie do obiektu blob bloku. Po uzyskaniu odwołania do obiektu blob możesz przekazać dowolny strumień danych do niego, wywołując `UploadFromFile` metody. Ta operacja tworzy obiekt blob, jeśli nie została wcześniej istnieje, lub go zastąpić, jeśli istnieje.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Wyświetlanie listy obiektów blob w kontenerze

Aby wyświetlić listę obiektów blob w kontenerze, należy najpierw pobrać odwołanie do kontenera. Następnie można użyć kontenera `ListBlobs` metodę, aby pobrać obiekty BLOB i/lub zawarte w nim katalogi. Aby uzyskać dostęp z bogatego zestawu właściwości i metod zwróconego do `IListBlobItem`, należy rzutować go na `CloudBlockBlob`, `CloudPageBlob`, lub `CloudBlobDirectory` obiektu. Jeśli typ jest nieznany, umożliwia sprawdzanie typu określić, do którego obiektu rzutować. Poniższy kod przedstawia sposób pobierania i zwracania identyfikatora URI poszczególnych elementów w `mydata` kontenera:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Można również nazwy obiektów blob, zawierające informacje o ścieżce w nazwach. Spowoduje to utworzenie wirtualnej struktury katalogów, którą można organizować i przechodzić przez, tak jak w przypadku tradycyjnego systemu plików. Należy pamiętać, że struktura katalogów jest wyłącznie wirtualna — jedyne zasoby dostępne w usłudze Blob storage to kontenery i obiekty BLOB. Jednak biblioteka klienta magazynu zapewnia `CloudBlobDirectory` obiekt, aby odwoływać się do katalogu wirtualnego i uprościć proces Praca z obiektami blob zorganizowanymi w ten sposób.

Na przykład rozważmy następujący zestaw blokowych obiektów blob w kontenerze o nazwie `photos`:

*photo1.jpg*\
*2015/Architecture/Description.txt*\
*2015/Architecture/photo3.jpg*\
*2015/architecture/photo4.jpg*\
*2016/architecture/photo5.jpg*\
*2016/Architecture/photo6.jpg*\
*2016/Architecture/Description.txt*\
*2016/photo7.jpg*\

Gdy wywołujesz `ListBlobs` na kontenerze (jak w powyższym przykładzie) zwrócenie listy hierarchicznej. Jeśli zawiera jednocześnie `CloudBlobDirectory` i `CloudBlockBlob` obiektów reprezentujących katalogi i obiekty BLOB w kontenerze, odpowiednio, a następnie wynikowe dane wyjściowe wyglądają podobnie do poniższego:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Opcjonalnie możesz ustawić `UseFlatBlobListing` parametru `ListBlobs` metody `true`. W takim przypadku każdy obiekt blob w kontenerze jest zwracana jako `CloudBlockBlob` obiektu. Wywołanie `ListBlobs` do zwrócenia listy niezhierarchizowanej wygląda następująco:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

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

## <a name="download-blobs"></a>Pobieranie obiektów blob

Aby pobrać obiekty BLOB, należy najpierw pobrać odwołanie do obiektu blob, a następnie wywołać `DownloadToStream` metody. W poniższym przykładzie użyto `DownloadToStream` metodę, aby przesłać zawartość obiektu blob do obiektu strumienia, który można następnie zachować w pliku lokalnym.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Można również użyć `DownloadToStream` metody do pobierania zawartości obiektu blob jako ciąg tekstowy.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Usuwanie obiektów blob

Aby usunąć obiekt blob, najpierw pobrać odwołanie do obiektu blob, a następnie wywołać `Delete` metody na nim.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Wyświetlanie listy obiektów blob na stronach, asynchronicznie

Jeśli chcesz wyświetlić dużą liczbę obiektów blob lub chcesz kontrolować liczbę wyników zwracanych przez jedną operację wyświetlania listy, możesz wyświetlić listę obiektów blob na stronach wyników. Ten przykład przedstawia sposób zwracania wyników na stronach asynchronicznie, dzięki czemu wykonanie nie jest blokowane podczas oczekiwania na zwrócenie dużych zestawów wyników.

W tym przykładzie przedstawiono niezhierarchizowaną listę obiektów blob, ale można również wykonać listę hierarchiczną, ustawiając `useFlatBlobListing` parametru `ListBlobsSegmentedAsync` metody `false`.

Przykładowa aplikacja definiuje metodę asynchroniczną, za pomocą `async` bloku. ``let!`` — Słowo kluczowe wstrzymuje wykonywanie przykładowej metody do momentu ukończenia zadania wyświetlania listy.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Firma Microsoft może teraz używać tej procedury asynchroniczne w następujący sposób. Najpierw należy przekazać fikcyjne dane (przy użyciu lokalnego pliku utworzone wcześniej w tym samouczku).

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Teraz wywoła procedurę. Możesz użyć `Async.RunSynchronously` do wymuszenia wykonanie operacji asynchronicznej.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Zapisywanie do uzupełnialnego obiektu blob

Uzupełnialny obiekt blob jest zoptymalizowany pod kątem operacji dołączania, takich jak rejestrowanie. Podobnie jak blokowy obiekt blob uzupełnialny obiekt blob jest złożony z bloków, ale po dodaniu nowego bloku do uzupełnialnego obiektu blob jest zawsze dołączany na końcu obiektu blob. Nie można zaktualizować ani usunąć istniejącego bloku w uzupełnialnym obiekcie blob. Identyfikatory bloków w uzupełnialnym obiekcie blob nie są widoczne, ponieważ są one dla blokowych obiektów blob.

Każdy blok w uzupełnialnym obiekcie blob może być inny rozmiar, maksymalnie do 4 MB, a uzupełnialny obiekt blob może zawierać maksymalnie 50 000 bloków. Maksymalny rozmiar uzupełnialnego obiektu blob w związku z tym jest nieco przekraczać 195 GB (4 MB X 50 000 bloków).

Poniższy przykład tworzy nowy uzupełnialny obiekt blob i dołącza dane, symulując prostą operację rejestrowania.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Zobacz [omówienie blokowych obiektów blob, stronicowe obiekty BLOB i Uzupełnialnych obiektów blob](https://msdn.microsoft.com/library/azure/ee691964.aspx) Aby uzyskać więcej informacji na temat różnic między trzy typy obiektów blob.

## <a name="concurrent-access"></a>Równoczesny dostęp

Aby zapewnić obsługę równoczesny dostęp do obiektu blob z wielu klientów lub wielu wystąpień procesu, można użyć **elementów etag** lub **dzierżawy**.

* **Element etag** — zapewnia sposób, aby wykryć, że obiekt blob lub kontenera została zmodyfikowana przez inny proces

* **Dzierżawy** — zapewnia sposób uzyskania wyłącznego, odnawialnych, zapisu i usuwania dostępu do obiektu blob przez pewien czas

Aby uzyskać więcej informacji, zobacz [Zarządzanie współbieżnością w Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Nazewnictwa kontenerów

Każdy obiekt blob w usłudze Azure storage musi znajdować się w kontenerze. Kontener jest częścią nazwy obiektu blob. Na przykład `mydata` to nazwa kontenera w tych przykładowych identyfikatorami URI obiektów blob:

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Nazwa kontenera musi być prawidłową nazwą DNS zgodną z następującymi zasadami nazewnictwa:

1. Nazwa kontenera musi zaczynać się literą lub cyfrą i może zawierać tylko litery, cyfry i znak kreski (-).
1. Każdy znak kreski (-) musi być natychmiast poprzedzony i następuje litera lub cyfra; następujące po sobie kreski są niedozwolone w nazwach kontenerów.
1. Wszystkie litery w nazwie kontenera muszą być małe.
1. Nazwy kontenerów muszą być od 3 do 63 znaków.

Należy pamiętać, że nazwa kontenera musi być zawsze małe litery. Jeśli zawierają wielkie litery w nazwie kontenera lub inny sposób naruszać zasady nazewnictwa dotyczące kontenerów zostaną, może wystąpić błąd 400 (nieprawidłowe żądanie).

## <a name="managing-security-for-blobs"></a>Zarządzanie zabezpieczeniami obiektów blob

Domyślnie usługi Azure Storage zapewnia bezpieczeństwo danych przez ograniczenie dostępu do właściciela konta, która jest w posiadaniu kluczy dostępu do konta. Gdy zachodzi potrzeba udostępnienia danych obiektów blob na koncie magazynu, należy to zrobić bez uszczerbku dla bezpieczeństwa kluczy dostępu do Twojego konta. Dodatkowo można zaszyfrować dane obiektu blob, aby zapewnić bezpieczeństwo podczas przesyłania przez sieć oraz w usłudze Azure Storage.

### <a name="controlling-access-to-blob-data"></a>Kontrolowanie dostępu do danych obiektów blob

Domyślnie dane obiektów blob na koncie magazynu jest dostępny tylko dla właściciela konta magazynu. Uwierzytelnianie żądań dotyczących magazynu obiektów Blob wymaga klucza dostępu do konta, domyślnie. Można jednak udostępnić określone dane obiektów blob innym użytkownikom.

### <a name="encrypting-blob-data"></a>Szyfrowanie danych obiektów blob

Usługa Azure Storage obsługuje szyfrowanie danych obiektów blob, zarówno na kliencie, jak i na serwerze.

## <a name="next-steps"></a>Następne kroki

Teraz, kiedy znasz już podstawy usługi Blob storage, skorzystaj z poniższych linków, aby dowiedzieć się więcej.

### <a name="tools"></a>Narzędzia

- [F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
F# Dostawcy typu, który może służyć do zapoznaj się z zasobami obiektów Blob, tabel i kolejek usługi Azure Storage i z łatwością zastosować operacji CRUD na nich.

- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
F# Interfejs API przy użyciu usługi Microsoft Azure Table Storage

- [Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Bezpłatną, autonomiczną aplikacją oferowaną przez firmę Microsoft, która umożliwia wizualną pracę z danymi usługi Azure Storage w Windows, OS X i Linux.

### <a name="blob-storage-reference"></a>Odwołanie do obiektu blob magazynu

- [Interfejsy API usługi Azure Storage dla platformy .NET](/dotnet/api/overview/azure/storage)
- [Dokumentacja interfejsu API REST usługi Azure Storage](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>Powiązane przewodniki

- [Wprowadzenie do usługi Azure Blob Storage w języku C#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Transferowanie danych za pomocą narzędzia wiersza polecenia AzCopy w Windows](/azure/storage/common/storage-use-azcopy)
- [Transferowanie danych za pomocą narzędzia wiersza polecenia AzCopy w systemie Linux](/azure/storage/common/storage-use-azcopy-linux)
- [Konfigurowanie parametrów połączenia usługi Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Blog zespołu usługi Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Szybki start: Tworzenie obiektu blob w magazynie obiektów przy użyciu .NET](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
