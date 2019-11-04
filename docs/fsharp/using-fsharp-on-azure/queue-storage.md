---
title: Rozpoczynanie pracy z usługą Azure Queue Storage przy użyciu języka F#
description: Kolejki platformy Azure zapewniają niezawodne, asynchroniczne komunikaty między składnikami aplikacji. Obsługa komunikatów w chmurze umożliwia niezależne skalowanie składników aplikacji.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: a09cbdd4b995e34177c110ce91b02162bb19dfa8
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423843"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Rozpoczynanie pracy z usługą Azure queue storage przy użyciu programu F\#

Usługa Azure queue storage udostępnia komunikaty w chmurze między składnikami aplikacji. Podczas projektowania aplikacji do skalowania składniki aplikacji są często rozłączane, dzięki czemu mogą być skalowane niezależnie. Usługa queue storage zapewnia asynchroniczne przesyłanie komunikatów na potrzeby komunikacji między składnikami aplikacji, niezależnie od tego, czy działają w chmurze, na komputerze, na serwerze lokalnym, czy na urządzeniu przenośnym. Magazyn kolejek obsługuje również zarządzanie zadaniami asynchronicznymi i przepływami pracy procesu kompilacji.

### <a name="about-this-tutorial"></a>Informacje o tym samouczku

W tym samouczku pokazano, F# jak napisać kod dla niektórych typowych zadań za pomocą usługi Azure queue storage. Objęte zadaniami obejmują tworzenie i usuwanie kolejek oraz dodawanie, odczytywanie i usuwanie komunikatów w kolejce.

Omówienie pojęć dotyczących usługi queue storage można znaleźć [w przewodniku .NET dla usługi queue storage](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Wymagania wstępne

Aby skorzystać z tego przewodnika, musisz najpierw [utworzyć konto usługi Azure Storage](/azure/storage/storage-create-storage-account).
Wymagany jest również klucz dostępu do magazynu dla tego konta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Utwórz F# skrypt i uruchom F# interaktywny

Przykłady w tym artykule mogą być używane w F# aplikacji lub F# skrypcie. Aby utworzyć F# skrypt, Utwórz plik z rozszerzeniem `.fsx`, na przykład `queues.fsx`, w środowisku F# deweloperskim.

Następnie należy użyć [Menedżera pakietów](package-management.md) , takiego jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) , aby zainstalować pakiet `WindowsAzure.Storage` i odwołanie `WindowsAzure.Storage.dll` w skrypcie przy użyciu dyrektywy `#r`.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujące instrukcje `open` na początku pliku `queues.fsx`:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Pobierz parametry połączenia

W tym samouczku będą potrzebne parametry połączenia usługi Azure Storage. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [Konfigurowanie parametrów połączenia magazynu](/azure/storage/storage-configure-connection-string).

Na potrzeby samouczka wprowadzisz w skrypcie parametry połączenia, takie jak:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Nie jest to jednak **zalecane** w przypadku rzeczywistych projektów. Klucz konta magazynu jest podobny do hasła głównego dla konta magazynu. Zawsze należy zachować ostrożność, aby chronić klucz konta magazynu. Należy unikać dystrybuowania go do innych użytkowników, ich trwałego kodowania lub zapisywania w pliku w formacie zwykłego tekstu, który jest dostępny dla innych. Możesz ponownie wygenerować klucz za pomocą witryny Azure Portal, jeśli uważasz, że jego zabezpieczenia mogły zostać naruszone.

W przypadku prawdziwych aplikacji najlepszym sposobem obsługi parametrów połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Korzystanie z usługi Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takiego jak typ `ConfigurationManager` .NET Framework.

### <a name="parse-the-connection-string"></a>Analizowanie parametrów połączenia

Aby przeanalizować parametry połączenia, użyj:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Spowoduje to zwrócenie `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Tworzenie klienta usługa kolejki

Klasa `CloudQueueClient` umożliwia pobieranie kolejek przechowywanych w usłudze queue storage. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Teraz możesz przystąpić do pisania kodu, który odczytuje dane z usługi queue storage i zapisuje dane.

## <a name="create-a-queue"></a>Tworzenie kolejki

Ten przykład pokazuje, jak utworzyć kolejkę, jeśli jeszcze nie istnieje:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Wstawianie komunikatu do kolejki

Aby wstawić komunikat do istniejącej kolejki, najpierw utwórz nowy `CloudQueueMessage`. Następnie Wywołaj metodę `AddMessage`. `CloudQueueMessage` można utworzyć na podstawie ciągu (w formacie UTF-8) lub tablicy `byte`, tak jak to:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Wgląd w następny komunikat

Możesz uzyskać wgląd w komunikat z przodu kolejki, bez usuwania go z kolejki, wywołując metodę `PeekMessage`.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Pobierz następny komunikat do przetworzenia

Możesz pobrać komunikat z przodu kolejki do przetworzenia, wywołując metodę `GetMessage`.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Możesz później wskazać pomyślne przetwarzanie komunikatu przy użyciu `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Zmiana zawartości komunikatu w kolejce

Można zmienić zawartość pobranego komunikatu w miejscu w kolejce. Jeśli komunikat reprezentuje zadanie służbowe, można użyć tej funkcji do zaktualizowania stanu zadania pracy. Poniższy kod aktualizuje komunikat kolejki z nową zawartością i ustawia limit czasu widoczności, aby zwiększyć kolejny 60 sekund. Spowoduje to zapisanie stanu pracy skojarzonej z wiadomością i nadaje klientowi kolejną minutę na kontynuowanie pracy nad komunikatem. Ta technika służy do śledzenia wieloetapowych przepływów pracy dla komunikatów w kolejce, bez konieczności rozpoczynania od początku, jeśli etap przetwarzania zakończy się niepowodzeniem z powodu awarii sprzętu lub oprogramowania. Zwykle należy również zachować liczbę ponownych prób, a jeśli komunikat zostanie ponowiony więcej niż jakiś czas, należy go usunąć. Chroni to przed komunikatem, który wyzwala błąd aplikacji przy każdym przetwarzaniu.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Usuń następny komunikat z kolejki

Twój kod usuwa komunikat z kolejki w dwóch krokach. Po wywołaniu `GetMessage`otrzymujesz następny komunikat w kolejce. Komunikat zwrócony z `GetMessage` jest niewidoczny dla każdego innego kodu odczytującego komunikaty z tej kolejki. Domyślnie ten komunikat pozostaje niewidoczny przez 30 sekund. Aby zakończyć usuwanie komunikatu z kolejki, należy również wywołać `DeleteMessage`. Ten dwuetapowy proces usuwania komunikatu gwarantuje, że jeśli kod nie może przetworzyć komunikatu z powodu awarii sprzętu lub oprogramowania, inne wystąpienie kodu może uzyskać ten sam komunikat i spróbować ponownie. Kod wywołuje `DeleteMessage` bezpośrednio po przetworzeniu komunikatu.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Używanie asynchronicznych przepływów pracy ze wspólnymi interfejsami API magazynu kolejki

Ten przykład pokazuje, jak używać asynchronicznego przepływu pracy ze wspólnymi interfejsami API magazynu kolejki.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Dodatkowe opcje do usuwania komunikatów z kolejkowania

Istnieją dwa sposoby dostosowania pobierania komunikatów z kolejki.
Najpierw można pobrać partię komunikatów (do 32). Następnie można ustawić dłuższy lub krótszy limit czasu niewglądu, co pozwala na zwiększenie lub skrócenie czasu w celu pełnego przetworzenia poszczególnych komunikatów. Poniższy przykład kodu używa `GetMessages`, aby pobrać 20 komunikatów w jednym wywołaniu, a następnie przetwarza każdy komunikat. Ustawia również limit czasu niewidoczności na pięć minut dla każdego komunikatu. Należy zauważyć, że 5 minut rozpoczyna się dla wszystkich komunikatów w tym samym czasie, więc po upływie 5 minut od wywołania do `GetMessages`wszystkie komunikaty, które nie zostały usunięte, staną się znów widoczne.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Pobieranie długości kolejki

Możesz uzyskać szacunkową liczbę komunikatów w kolejce. Metoda `FetchAttributes` prosi usługa kolejki o pobranie atrybutów kolejki, łącznie z liczbą komunikatów. Właściwość `ApproximateMessageCount` zwraca ostatnią wartość pobraną przez metodę `FetchAttributes`, bez wywoływania usługa kolejki.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Usuwanie kolejki

Aby usunąć kolejkę i wszystkie znajdujące się w niej komunikaty, wywołaj metodę `Delete` w obiekcie Queue.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Następne kroki

Teraz, gdy znasz już podstawy magazynu kolejek, Skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu.

- [Interfejsy API usługi Azure Storage dla platformy .NET](/dotnet/api/overview/azure/storage)
- [Dostawca typów usługi Azure Storage](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog zespołu usługi Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Konfigurowanie parametrów połączenia usługi Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Dokumentacja interfejsu API REST usług Azure Storage](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
