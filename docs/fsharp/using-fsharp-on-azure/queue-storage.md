---
title: Rozpoczynanie pracy z usługą Azure Queue storage przy użyciu języka F#
description: Usługa Azure Queues zapewnia niezawodne, asynchroniczne przesyłanie komunikatów między składnikami aplikacji. Chmura komunikatów umożliwia składnikom aplikacji niezależne skalowanie obu elementów.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 14bbc657f965fc262d2a83b1fdf982fe5e75d55e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "33569421"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Rozpoczynanie pracy z usługą Azure Queue storage przy użyciu języka F# #

Usługa Azure Queue storage umożliwia przesyłanie komunikatów między składnikami aplikacji w chmurze. Projektowanie aplikacji do skalowania, składniki aplikacji są często odłączane, tak aby mogły być skalowane niezależnie. Usługa queue storage zapewnia asynchroniczne przesyłanie komunikatów do komunikacji między składnikami aplikacji, czy działają w chmurze, na komputerze, na serwerze lokalnym lub na urządzeniu przenośnym. Usługa queue storage obsługuje również zarządzanie asynchronicznymi zadaniami oraz przepływy pracy procesu kompilacji.

### <a name="about-this-tutorial"></a>Informacje o tym samouczku

Ten samouczek przedstawia sposób zapisania F# kodu dla niektórych typowych zadań przy użyciu usługi Azure Queue storage. Objęte zadania obejmują tworzenie i usuwanie kolejek oraz dodawanie, odczytywanie i usuwanie wiadomości w kolejce.

Omówienie pojęć usługi queue storage, zobacz [przewodnik platformy .NET dla usługi queue storage](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć tego przewodnika, należy najpierw [Tworzenie konta usługi Azure storage](/azure/storage/storage-create-storage-account).
Należy także klucz dostępu do magazynu dla tego konta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Utwórz skrypt F# i Rozpocznij języka F# Interactive

Przykłady w tym artykule może służyć w aplikacji F# lub skryptu F#. Aby utworzyć skrypt F#, Utwórz plik o `.fsx` rozszerzenia, na przykład `queues.fsx`, w środowisku projektowym F#.

Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) zainstalował `WindowsAzure.Storage` pakietów i odwołań `WindowsAzure.Storage.dll` w skrypcie za pomocą `#r`dyrektywy.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujący kod `open` instrukcji na górze `queues.fsx` pliku:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Pobieranie parametrów połączenia

Na potrzeby tego samouczka konieczne będzie parametrów połączenia usługi Azure Storage. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).

Samouczek wprowadzisz parametrów połączenia w skrypcie w następujący sposób:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Jest to jednak **niezalecane** rzeczywiste projektów. Klucz konta magazynu jest podobny do hasła głównego konta magazynu. Zawsze starannie Chroń klucz konta magazynu. Należy unikać, ich dystrybucję w innym użytkownikom, kodować je lub zapisanie go w pliku tekstowego, który jest dostępny dla innych użytkowników. Można ponownie wygenerować klucz za pośrednictwem witryny Azure Portal, jeśli uważasz, że mogą zostać przejęte.

Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Użycie programu Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Przeanalizować parametrów połączenia

Aby przeanalizować parametrów połączenia, należy użyć:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Spowoduje to zwrócenie `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Tworzenie klienta usługi kolejki

`CloudQueueClient` Klasy umożliwia pobieranie kolejek przechowywanych w usłudze Queue storage. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Teraz możesz przystąpić do pisania kodu, który odczytuje i zapisuje dane do usługi Queue storage.

## <a name="create-a-queue"></a>Tworzenie kolejki

Ten przykład pokazuje, jak utworzyć kolejkę, jeśli jeszcze nie istnieje:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Wstawianie komunikatu do kolejki

Aby wstawić komunikat do istniejącej kolejki, najpierw utwórz nowe `CloudQueueMessage`. Następnie wywołaj `AddMessage` metody. A `CloudQueueMessage` można utworzyć przy użyciu dowolnego ciągu (w formacie UTF-8) lub `byte` tablicy, w następujący sposób:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Podgląd kolejnego komunikatu

Użytkownik może wglądu do wiadomości uzyskać kolejki, bez usuwania go z kolejki, wywołując `PeekMessage` metody.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Następny komunikat do przetworzenia

Możesz pobrać komunikat z przodu kolejki do przetworzenia przez wywołanie metody `GetMessage` metody.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Później wskazują pomyślnego przetwarzania komunikatu przy użyciu `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Zmień zawartość komunikatu w kolejce

Możesz zmienić zawartość komunikatu pobrane w miejscu w kolejce. Jeśli komunikat reprezentuje zadanie robocze, można użyć tej funkcji można zaktualizować stanu zadania. Poniższy kod aktualizuje komunikat kolejki o nową zawartość i Ustawia rozszerzenie limitu czasu widoczności o kolejne 60 sekund. Zapisuje stan pracy powiązanej z komunikatem i daje klientowi kolejną minutę na kontynuowanie pracy w komunikacie. Tej techniki można używać do śledzenia wieloetapowe przepływy pracy na wiadomości w kolejce bez konieczności uruchamiania za pośrednictwem od samego początku, jeśli krok przetwarzania zakończy się niepowodzeniem z powodu awarii sprzętu lub oprogramowania. Zazwyczaj zachowa również liczbę ponownych prób, a jeśli komunikat zostanie ponowiony więcej niż pewną liczbę razy, zostanie usunięty. Chroni to przed komunikatami, które wyzwalają błąd aplikacji za każdym razem, gdy jest on przetwarzany.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Usuń zaznaczenie pola następnego komunikatu z kolejki

Twój kod cofnąć umieszcza w kolejce komunikatu z kolejki w dwóch etapach. Gdy wywołujesz `GetMessage`, uzyskasz następny komunikat w kolejce. Komunikat zwrócony z `GetMessage` staje się niewidoczny dla innego kodu odczytującego komunikaty z tej kolejki. Domyślnie komunikat pozostanie niewidoczny przez 30 sekund. Aby zakończyć usuwanie komunikatu z kolejki, musisz również wywołać `DeleteMessage`. Ten dwuetapowy proces usuwania komunikatów gwarantuje, że jeśli Twój kod nie może przetworzyć komunikatu z powodu awarii sprzętu lub oprogramowania, inne wystąpienie kodu można uzyskać ten sam komunikat i spróbuj ponownie. Twój kod wywołuje `DeleteMessage` natychmiast po przetworzeniu komunikatu.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Asynchroniczne przepływy pracy za pomocą wspólnego kolejki magazynu interfejsów API

W tym przykładzie przedstawiono sposób asynchronicznego przepływu pracy za pomocą wspólnego kolejki magazynu interfejsów API.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Dodatkowe opcje usuwania komunikatów z kolejek

Istnieją dwa sposoby, które można dostosować odebrania komunikatu z kolejki.
Po pierwsze można uzyskać partię komunikatów (maksymalnie 32). Po drugie można ustawić limitu czasu niewidoczności dłuższy lub krótszy, dzięki czemu kod więcej lub mniej czasu na pełne przetworzenie każdego komunikatu. Poniższy przykład kodu wykorzystuje `GetMessages` można pobrać 20 komunikatów w jednym wywołań, a następnie przetwarza każdy komunikat. Ustawia również limitu czasu niewidoczności na pięć minut dla każdego komunikatu. Należy zauważyć, że 5 minut rozpoczyna się dla wszystkich komunikatów w tym samym czasie, dlatego po 5 minut ma minęło od wywołania `GetMessages`, wszystkie komunikaty, które nie zostały usunięte, będą widoczne ponownie.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Pobieranie długości kolejki

Możesz uzyskać szacunkową liczbę komunikatów w kolejce. `FetchAttributes` Metoda prosi usługę kolejki o pobranie atrybutów kolejki, w tym liczby komunikatów. `ApproximateMessageCount` Właściwość zwraca ostatnią wartość pobraną przez `FetchAttributes` metody bez wywoływania usługi kolejki.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Usuwanie kolejki

Aby usunąć kolejkę i wszystkie zawarte w niej komunikaty, wywołaj `Delete` metody na obiekcie kolejki.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Następne kroki

Teraz, kiedy znasz już podstawy usługi Queue storage, skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu.

- [Interfejsy API usługi Azure Storage dla platformy .NET](/dotnet/api/overview/azure/storage)
- [Dostawcy typów usługi Azure Storage](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog zespołu usługi Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Konfigurowanie parametrów połączenia usługi Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Dokumentacja interfejsu API REST usługi Azure Storage](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
