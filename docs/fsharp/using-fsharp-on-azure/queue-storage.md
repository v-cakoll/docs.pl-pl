---
title: Rozpoczynanie pracy z usługą Azure Queue Storage przy użyciu języka F#
description: Usługa Azure Queues zapewnia niezawodne, asynchroniczne przesyłanie komunikatów między składnikami aplikacji. Przesyłanie komunikatów za pomocą chmury umożliwia składnikom aplikacji niezależne skalowanie.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 841068ac91aecc53811359e27d984907569a2c6d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935494"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Rozpoczynanie pracy z usługą Azure queue storage przy użyciu programu F\#

Usługa Azure Queue Storage umożliwia przesyłanie komunikatów za pomocą chmury między składnikami aplikacji. W przypadku projektowania aplikacji pod kątem skalowania składniki aplikacji są często rozłączane, dzięki czemu mogą być skalowane niezależnie. Usługa Queue Storage zapewnia asynchroniczne przesyłanie komunikatów na potrzeby komunikacji między składnikami aplikacji niezależnie od tego, czy działają w chmurze, na komputerze, serwerze lokalnym czy urządzeniu przenośnym. Magazyn kolejek obsługuje również zarządzanie asynchronicznymi zadaniami oraz przepływy pracy procesu kompilacji.

### <a name="about-this-tutorial"></a>Informacje o tym samouczku

W tym samouczku pokazano, F# jak napisać kod dla niektórych typowych zadań za pomocą usługi Azure queue storage. Objęte zadaniami obejmują tworzenie i usuwanie kolejek oraz dodawanie, odczytywanie i usuwanie komunikatów w kolejce.

Omówienie pojęć dotyczących usługi queue storage można znaleźć [w przewodniku .NET dla usługi queue storage](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Wymagania wstępne

Aby skorzystać z tego przewodnika, musisz najpierw [utworzyć konto usługi Azure Storage](/azure/storage/storage-create-storage-account).
Wymagany jest również klucz dostępu do magazynu dla tego konta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Utwórz F# skrypt i uruchom F# interaktywny

Przykłady w tym artykule mogą być używane w F# aplikacji lub F# skrypcie. Aby utworzyć F# skrypt, Utwórz plik z rozszerzeniem `.fsx`, na przykład `queues.fsx`, w środowisku F# deweloperskim.

Następnie należy użyć [Menedżera pakietów](package-management.md) , takiego jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) , aby zainstalować pakiet `WindowsAzure.Storage` i informacje referencyjne `WindowsAzure.Storage.dll` w skrypcie przy użyciu dyrektywy `#r`.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujące instrukcje `open` na początku pliku `queues.fsx`:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Uzyskiwanie parametrów połączenia

W tym samouczku będą potrzebne parametry połączenia usługi Azure Storage. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [Konfigurowanie parametrów połączenia magazynu](/azure/storage/storage-configure-connection-string).

Na potrzeby samouczka wprowadzisz w skrypcie parametry połączenia, takie jak:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Nie jest to jednak **zalecane** w przypadku rzeczywistych projektów. Klucz konta magazynu jest podobny do hasła głównego konta magazynu. Zawsze chroń klucz konta magazynu. Nie udostępniaj go innym użytkownikom, nie koduj go trwale ani nie zapisuj w zwykłym pliku tekstowym, do którego mają dostęp inne osoby. Możesz ponownie wygenerować klucz za pomocą witryny Azure Portal, jeśli uważasz, że jego zabezpieczenia mogły zostać naruszone.

W przypadku prawdziwych aplikacji najlepszym sposobem obsługi parametrów połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Użycie programu Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takiego jak typ `ConfigurationManager` .NET Framework.

### <a name="parse-the-connection-string"></a>Analizowanie parametrów połączenia

Aby przeanalizować parametry połączenia, użyj:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Spowoduje to zwrócenie `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Tworzenie klienta usługi kolejki

Klasa `CloudQueueClient` umożliwia pobieranie kolejek przechowywanych w usłudze queue storage. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Teraz możesz przystąpić do pisania kodu, który będzie odczytywać dane z usługi Queue Storage i zapisywać je w nim.

## <a name="create-a-queue"></a>Tworzenie kolejki

Ten przykład pokazuje, jak utworzyć kolejkę, jeśli jeszcze nie istnieje:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Wstawianie komunikatu do kolejki

Aby wstawić komunikat do istniejącej kolejki, najpierw utwórz nowy `CloudQueueMessage`. Następnie Wywołaj metodę `AddMessage`. `CloudQueueMessage` można utworzyć na podstawie ciągu (w formacie UTF-8) lub tablicy `byte`, tak jak to:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Podgląd kolejnego komunikatu

Możesz uzyskać wgląd w komunikat z przodu kolejki, bez usuwania go z kolejki, wywołując metodę `PeekMessage`.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Pobierz następny komunikat do przetworzenia

Możesz pobrać komunikat z przodu kolejki do przetworzenia, wywołując metodę `GetMessage`.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Możesz później wskazać pomyślne przetwarzanie komunikatu przy użyciu `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Zmiana zawartości komunikatu w kolejce

Można zmienić zawartość pobranego komunikatu w miejscu w kolejce. Jeśli komunikat reprezentuje zadanie robocze, możesz użyć tej funkcji, aby zaktualizować stan zadania. Poniższy kod aktualizuje komunikat kolejki o nową zawartość i ustawia rozszerzenie limitu czasu widoczności o kolejne 60 sekund. Operacja ta zapisuje stan pracy powiązanej z komunikatem i daje klientowi kolejną minutę na kontynuowanie pracy nad komunikatem. Możesz użyć tej metody do śledzenia wieloetapowych przepływów pracy związanych z komunikatami kolejek, bez konieczności rozpoczynania od nowa, gdy dany etap nie powiedzie się ze względu na awarię sprzętu lub oprogramowania. Zwykle należy również zachować liczbę ponownych prób, a jeśli komunikat zostanie ponowiony więcej niż jakiś czas, należy go usunąć. Jest to zabezpieczenie przed komunikatami, które wyzwalają błąd aplikacji zawsze, gdy są przetwarzane.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Usunięcie następnego komunikatu z kolejki

Twój kod usuwa komunikat z kolejki w dwóch etapach. Po wywołaniu `GetMessage`otrzymujesz następny komunikat w kolejce. Komunikat zwrócony z `GetMessage` jest niewidoczny dla każdego innego kodu odczytującego komunikaty z tej kolejki. Domyślnie komunikat pozostanie niewidoczny przez 30 sekund. Aby zakończyć usuwanie komunikatu z kolejki, należy również wywołać `DeleteMessage`. Ten dwuetapowy proces usuwania komunikatów gwarantuje, że jeśli kod nie będzie w stanie przetworzyć komunikatu z powodu awarii sprzętu lub oprogramowania, inne wystąpienie kodu będzie w stanie uzyskać ten sam komunikat i ponowić próbę. Kod wywołuje `DeleteMessage` bezpośrednio po przetworzeniu komunikatu.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Używanie asynchronicznych przepływów pracy ze wspólnymi interfejsami API magazynu kolejki

Ten przykład pokazuje, jak używać asynchronicznego przepływu pracy ze wspólnymi interfejsami API magazynu kolejki.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Dodatkowe opcje do usuwania komunikatów z kolejkowania

Istnieją dwa sposoby dostosowania pobierania komunikatów z kolejki.
Po pierwsze można uzyskać komunikaty zbiorczo (do 32). Po drugie można ustawić dłuższy lub krótszy limit czasu niewidoczności, dzięki czemu kod będzie mieć więcej lub mniej czasu na pełne przetworzenie każdego komunikatu. Poniższy przykład kodu używa `GetMessages`, aby pobrać 20 komunikatów w jednym wywołaniu, a następnie przetwarza każdy komunikat. Ustawia również limitu czasu niewidoczności na pięć minut dla każdego komunikatu. Należy zauważyć, że 5 minut rozpoczyna się dla wszystkich komunikatów w tym samym czasie, więc po upływie 5 minut od wywołania do `GetMessages`wszystkie komunikaty, które nie zostały usunięte, staną się znów widoczne.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Pobieranie długości kolejki

Możesz uzyskać szacunkową liczbę komunikatów w kolejce. Metoda `FetchAttributes` prosi usługa kolejki o pobranie atrybutów kolejki, łącznie z liczbą komunikatów. Właściwość `ApproximateMessageCount` zwraca ostatnią wartość pobraną przez metodę `FetchAttributes`, bez wywoływania usługa kolejki.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Usuwanie kolejki

Aby usunąć kolejkę i wszystkie znajdujące się w niej komunikaty, wywołaj metodę `Delete` w obiekcie Queue.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Następne kroki

Teraz, kiedy znasz już podstawy usługi Queue Storage, skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu.

- [Interfejsy API usługi Azure Storage dla platformy .NET](/dotnet/api/overview/azure/storage)
- [Dostawca typów usługi Azure Storage](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog zespołu odpowiedzialnego za usługę Azure Storage](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [Konfiguracja parametrów połączenia usługi Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Dokumentacja interfejsu API REST usługi Azure Storage](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
