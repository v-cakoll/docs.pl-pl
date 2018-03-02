---
title: "Rozpoczynanie pracy z magazynem kolejek Azure przy użyciu języka F #"
description: "Kolejek platformy Azure zapewniają niezawodne, asynchronicznego wysyłanie komunikatów między składnikami aplikacji. Chmury obsługi komunikatów włącza składniki aplikacji można skalować niezależnie."
keywords: visual f#, f#, functional programming, .NET, .NET Core, Azure
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 70dc554c-8f4d-42a7-8e2a-6438657d012a
ms.openlocfilehash: 50b2d69a1753add688aa14c3314a0ca2df9f03a4
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Rozpoczynanie pracy z magazynem kolejek Azure przy użyciu języka F # #

Magazyn kolejek Azure udostępnia chmury wysyłanie komunikatów między składnikami aplikacji. Podczas projektowania aplikacji pod kątem skalowania, składniki aplikacji są często rozłączane, dzięki czemu można skalować niezależnie. Magazyn kolejek zapewnia asynchroniczną obsługę wiadomości do komunikacji między składnikami aplikacji, czy działają w chmurze, na komputerze, na serwerze lokalnym lub na urządzeniu przenośnym. Magazyn kolejek obsługuje również zarządzanie asynchronicznymi zadaniami oraz przepływy pracy procesu kompilacji.

### <a name="about-this-tutorial"></a>Informacje o tym samouczku

Ten samouczek pokazuje, jak napisać kod F # dla niektórych typowych zadań przy użyciu magazynu kolejek Azure. Zadań obejmują tworzenie i usuwanie kolejek i dodawanie, odczytywanie i usuwanie wiadomości w kolejce.

Omówienie pojęć dotyczących magazynu kolejek, zobacz [przewodnik .NET dla magazynu kolejek](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć tego przewodnika, należy najpierw [utworzyć konto magazynu Azure](/azure/storage/storage-create-storage-account).
Należy również klucz dostępu do magazynu dla tego konta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Tworzenie skryptu języka F # i rozpocząć F # Interactive

Przykłady w tym artykule można używać w F # aplikacji lub skryptu języka F #. Aby utworzyć skrypt F #, Utwórz plik o `.fsx` rozszerzenie, na przykład `queues.fsx`, w środowiska deweloperskiego F #.

Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) do zainstalowania `WindowsAzure.Storage` odwołanie do pakietu i `WindowsAzure.Storage.dll` skryptu za pomocą `#r`dyrektywy.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujące `open` instrukcje na początku `queues.fsx` pliku:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Pobierz ciąg połączenia

Parametry połączenia magazynu Azure należy w tym samouczku. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).

Samouczek będzie wprowadź parametry połączenia za pomocą skryptu, jak to:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Jest to jednak **niezalecane** rzeczywiste projektów. Klucz konta magazynu jest podobny do hasła głównego konta magazynu. Zawsze starannie Chroń klucz konta magazynu. Unikaj udostępniaj go innym użytkownikom, kodować je lub zapisać go w pliku jako zwykły tekst, który jest dostępny do innych użytkowników. Można ponownie wygenerować klucz przy użyciu portalu Azure, jeśli uważasz, że mogą zostać naruszone.

Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia w pliku konfiguracji, można to zrobić:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Przy użyciu programu Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Przeanalizować parametrów połączenia

Aby przeanalizować parametrów połączenia, należy użyć:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Spowoduje to zwrócenie `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Tworzenie klienta usługi kolejki

`CloudQueueClient` Klasa umożliwia pobieranie kolejek przechowywanych w magazynie kolejek. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Teraz można przystąpić do pisania kodu, która odczytuje i zapisuje dane do magazynu kolejek.

## <a name="create-a-queue"></a>Tworzenie kolejki

W tym przykładzie pokazano, jak utworzyć kolejkę, jeśli jeszcze nie istnieje:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Wstawianie komunikatu do kolejki

Aby wstawić komunikat do istniejącej kolejki, najpierw utwórz nową `CloudQueueMessage`. Następnie wywołaj `AddMessage` metody. A `CloudQueueMessage` można tworzyć przy użyciu dowolnego ciągu (w formacie UTF-8) lub `byte` tablicy w następujący sposób:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Podgląd kolejnego komunikatu

Możesz uzyskać wgląd w komunikat z przodu kolejki, bez jego usuwania z kolejki, wywołując `PeekMessage` metody.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Następny komunikat do przetworzenia

Komunikat z przodu kolejki przetwarzania można pobrać przez wywołanie metody `GetMessage` metody.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Później wskazywać pomyślne przetwarzania komunikatu za pomocą `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Zmiana zawartości komunikatu w kolejce

Można zmienić zawartość komunikatu pobrane w miejscu w kolejce. Jeśli komunikat reprezentuje zadanie robocze, można Użyj tej funkcji, aby zaktualizować stan zadania. Poniższy kod aktualizuje komunikat kolejki o nową zawartość i Ustawia rozszerzenie limitu czasu widoczności kolejne 60 sekund. Zapisuje stan pracy powiązanej z komunikatem i daje klientowi kolejną minutę na kontynuowanie pracy nad wiadomości. Można użyć tej metody do śledzenia wieloetapowych przepływów pracy związanych z komunikatami kolejek, bez konieczności rozpoczynania od początku, jeśli dany etap nie powiedzie się z powodu awarii sprzętu lub oprogramowania. Zazwyczaj zachowa również liczbę ponownych prób, a jeśli komunikat zostanie ponowiony więcej niż pewną liczbę razy, zostanie usunięty. Jest to zabezpieczenie przed komunikatami, które wyzwalają błąd aplikacji zawsze, gdy jest przetwarzane.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Do następnego komunikatu z kolejki

Kod do kolejki wiadomości z kolejki w dwóch krokach. Podczas wywoływania `GetMessage`, Pobierz następnej wiadomości w kolejce. Komunikat zwrócony z `GetMessage` staje się niewidoczny dla innego kodu odczytującego komunikaty z tej kolejki. Domyślnie komunikat pozostanie niewidoczny przez 30 sekund. Aby zakończyć usuwanie komunikatu z kolejki, musisz również wywołać `DeleteMessage`. Ten dwuetapowy proces usuwania komunikatów gwarantuje, że jeśli kod nie może przetworzyć komunikatu z powodu awarii sprzętu lub oprogramowania, inne wystąpienie kodu można uzyskać ten sam komunikat i spróbuj ponownie. Twój kod wywołuje `DeleteMessage` natychmiast po przetworzeniu komunikatu.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Asynchroniczne przepływy pracy za pomocą wspólnych interfejsów API magazynu kolejek

W tym przykładzie przedstawiono sposób asynchronicznego przepływu pracy za pomocą wspólnych interfejsów API magazynu kolejek.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Dodatkowe opcje usuwania komunikatów z kolejek

Istnieją dwa sposoby dostosowania pobierania komunikatów z kolejki.
Po pierwsze można uzyskać partii wiadomości (do 32). Po drugie można ustawić limit czasu niewidoczności dłuższy lub krótszy, dzięki czemu kod będzie bardziej lub mniej czasu na pełne przetworzenie każdego komunikatu. Poniższy przykład kodu wykorzystuje `GetMessages` można pobrać 20 komunikatów w jednym wywołań, a następnie przetwarza każdy komunikat. Ustawia również limitu czasu niewidoczności na pięć minut dla każdego komunikatu. Należy pamiętać, że 5 minut rozpoczyna się dla wszystkich wiadomości w tym samym czasie, więc po 5 minut przekazany od czasu wywołania `GetMessages`, wszystkie komunikaty, które nie zostały usunięte, będą widoczne ponownie.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Pobieranie długości kolejki

Możesz uzyskać szacunkową liczbę wiadomości w kolejce. `FetchAttributes` Metody prosi usługę kolejki o pobranie atrybutów kolejki, w tym liczby komunikatów. `ApproximateMessageCount` Właściwość zwraca ostatnią wartość pobraną przez `FetchAttributes` bez wywoływania usługi kolejki.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Usuwanie kolejki

Aby usunąć kolejkę i wszystkie zawarte w niej komunikaty, wywołaj `Delete` metody dla obiekt kolejki.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Następne kroki

Teraz, kiedy znasz już podstawy magazynu kolejek, skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu.

- [Interfejsy API usługi Azure Storage dla platformy .NET](/dotnet/api/overview/azure/storage)
- [Dostawca typów magazynu Azure](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure Storage Team Blog](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Konfigurowanie parametrów połączenia usługi Azure Storage](/azure/storage/common/storage-configure-connection-string)
- [Dokumentacja interfejsu API REST usług magazynu Azure](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
