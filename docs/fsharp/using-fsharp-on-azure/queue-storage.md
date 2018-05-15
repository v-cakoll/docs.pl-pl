---
title: 'Rozpoczynanie pracy z magazynem kolejek Azure przy użyciu języka F #'
description: Kolejek platformy Azure zapewniają niezawodne, asynchronicznego wysyłanie komunikatów między składnikami aplikacji. Chmury obsługi komunikatów włącza składniki aplikacji można skalować niezależnie.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 14bbc657f965fc262d2a83b1fdf982fe5e75d55e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="f4134-104">Rozpoczynanie pracy z magazynem kolejek Azure przy użyciu języka F #</span><span class="sxs-lookup"><span data-stu-id="f4134-104">Get started with Azure Queue storage using F#</span></span> #

<span data-ttu-id="f4134-105">Magazyn kolejek Azure udostępnia chmury wysyłanie komunikatów między składnikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4134-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="f4134-106">Podczas projektowania aplikacji pod kątem skalowania, składniki aplikacji są często rozłączane, dzięki czemu można skalować niezależnie.</span><span class="sxs-lookup"><span data-stu-id="f4134-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="f4134-107">Magazyn kolejek zapewnia asynchroniczną obsługę wiadomości do komunikacji między składnikami aplikacji, czy działają w chmurze, na komputerze, na serwerze lokalnym lub na urządzeniu przenośnym.</span><span class="sxs-lookup"><span data-stu-id="f4134-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="f4134-108">Magazyn kolejek obsługuje również zarządzanie asynchronicznymi zadaniami oraz przepływy pracy procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f4134-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="f4134-109">Informacje o tym samouczku</span><span class="sxs-lookup"><span data-stu-id="f4134-109">About this tutorial</span></span>

<span data-ttu-id="f4134-110">Ten samouczek pokazuje, jak napisać kod F # dla niektórych typowych zadań przy użyciu magazynu kolejek Azure.</span><span class="sxs-lookup"><span data-stu-id="f4134-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="f4134-111">Zadań obejmują tworzenie i usuwanie kolejek i dodawanie, odczytywanie i usuwanie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f4134-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="f4134-112">Omówienie pojęć dotyczących magazynu kolejek, zobacz [przewodnik .NET dla magazynu kolejek](/azure/storage/storage-dotnet-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="f4134-112">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f4134-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f4134-113">Prerequisites</span></span>

<span data-ttu-id="f4134-114">Aby użyć tego przewodnika, należy najpierw [utworzyć konto magazynu Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="f4134-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="f4134-115">Należy również klucz dostępu do magazynu dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="f4134-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="f4134-116">Tworzenie skryptu języka F # i rozpocząć F # Interactive</span><span class="sxs-lookup"><span data-stu-id="f4134-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="f4134-117">Przykłady w tym artykule można używać w F # aplikacji lub skryptu języka F #.</span><span class="sxs-lookup"><span data-stu-id="f4134-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="f4134-118">Aby utworzyć skrypt F #, Utwórz plik o `.fsx` rozszerzenie, na przykład `queues.fsx`, w środowiska deweloperskiego F #.</span><span class="sxs-lookup"><span data-stu-id="f4134-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="f4134-119">Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) do zainstalowania `WindowsAzure.Storage` odwołanie do pakietu i `WindowsAzure.Storage.dll` skryptu za pomocą `#r`dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="f4134-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="f4134-120">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="f4134-120">Add namespace declarations</span></span>

<span data-ttu-id="f4134-121">Dodaj następujące `open` instrukcje na początku `queues.fsx` pliku:</span><span class="sxs-lookup"><span data-stu-id="f4134-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="f4134-122">Pobierz ciąg połączenia</span><span class="sxs-lookup"><span data-stu-id="f4134-122">Get your connection string</span></span>

<span data-ttu-id="f4134-123">Parametry połączenia magazynu Azure należy w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="f4134-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="f4134-124">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="f4134-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="f4134-125">Samouczek będzie wprowadź parametry połączenia za pomocą skryptu, jak to:</span><span class="sxs-lookup"><span data-stu-id="f4134-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="f4134-126">Jest to jednak **niezalecane** rzeczywiste projektów.</span><span class="sxs-lookup"><span data-stu-id="f4134-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="f4134-127">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="f4134-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="f4134-128">Zawsze starannie Chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="f4134-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="f4134-129">Unikaj udostępniaj go innym użytkownikom, kodować je lub zapisać go w pliku jako zwykły tekst, który jest dostępny do innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="f4134-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="f4134-130">Można ponownie wygenerować klucz przy użyciu portalu Azure, jeśli uważasz, że mogą zostać naruszone.</span><span class="sxs-lookup"><span data-stu-id="f4134-130">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="f4134-131">Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f4134-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="f4134-132">Aby pobrać parametry połączenia w pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="f4134-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="f4134-133">Przy użyciu programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f4134-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="f4134-134">Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="f4134-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="f4134-135">Przeanalizować parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="f4134-135">Parse the connection string</span></span>

<span data-ttu-id="f4134-136">Aby przeanalizować parametrów połączenia, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="f4134-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="f4134-137">Spowoduje to zwrócenie `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="f4134-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="f4134-138">Tworzenie klienta usługi kolejki</span><span class="sxs-lookup"><span data-stu-id="f4134-138">Create the Queue service client</span></span>

<span data-ttu-id="f4134-139">`CloudQueueClient` Klasa umożliwia pobieranie kolejek przechowywanych w magazynie kolejek.</span><span class="sxs-lookup"><span data-stu-id="f4134-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="f4134-140">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="f4134-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="f4134-141">Teraz można przystąpić do pisania kodu, która odczytuje i zapisuje dane do magazynu kolejek.</span><span class="sxs-lookup"><span data-stu-id="f4134-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="f4134-142">Tworzenie kolejki</span><span class="sxs-lookup"><span data-stu-id="f4134-142">Create a queue</span></span>

<span data-ttu-id="f4134-143">W tym przykładzie pokazano, jak utworzyć kolejkę, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="f4134-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="f4134-144">Wstawianie komunikatu do kolejki</span><span class="sxs-lookup"><span data-stu-id="f4134-144">Insert a message into a queue</span></span>

<span data-ttu-id="f4134-145">Aby wstawić komunikat do istniejącej kolejki, najpierw utwórz nową `CloudQueueMessage`.</span><span class="sxs-lookup"><span data-stu-id="f4134-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="f4134-146">Następnie wywołaj `AddMessage` metody.</span><span class="sxs-lookup"><span data-stu-id="f4134-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="f4134-147">A `CloudQueueMessage` można tworzyć przy użyciu dowolnego ciągu (w formacie UTF-8) lub `byte` tablicy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f4134-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="f4134-148">Podgląd kolejnego komunikatu</span><span class="sxs-lookup"><span data-stu-id="f4134-148">Peek at the next message</span></span>

<span data-ttu-id="f4134-149">Możesz uzyskać wgląd w komunikat z przodu kolejki, bez jego usuwania z kolejki, wywołując `PeekMessage` metody.</span><span class="sxs-lookup"><span data-stu-id="f4134-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="f4134-150">Następny komunikat do przetworzenia</span><span class="sxs-lookup"><span data-stu-id="f4134-150">Get the next message for processing</span></span>

<span data-ttu-id="f4134-151">Komunikat z przodu kolejki przetwarzania można pobrać przez wywołanie metody `GetMessage` metody.</span><span class="sxs-lookup"><span data-stu-id="f4134-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="f4134-152">Później wskazywać pomyślne przetwarzania komunikatu za pomocą `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="f4134-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="f4134-153">Zmiana zawartości komunikatu w kolejce</span><span class="sxs-lookup"><span data-stu-id="f4134-153">Change the contents of a queued message</span></span>

<span data-ttu-id="f4134-154">Można zmienić zawartość komunikatu pobrane w miejscu w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f4134-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="f4134-155">Jeśli komunikat reprezentuje zadanie robocze, można Użyj tej funkcji, aby zaktualizować stan zadania.</span><span class="sxs-lookup"><span data-stu-id="f4134-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="f4134-156">Poniższy kod aktualizuje komunikat kolejki o nową zawartość i Ustawia rozszerzenie limitu czasu widoczności kolejne 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="f4134-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="f4134-157">Zapisuje stan pracy powiązanej z komunikatem i daje klientowi kolejną minutę na kontynuowanie pracy nad wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f4134-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="f4134-158">Można użyć tej metody do śledzenia wieloetapowych przepływów pracy związanych z komunikatami kolejek, bez konieczności rozpoczynania od początku, jeśli dany etap nie powiedzie się z powodu awarii sprzętu lub oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="f4134-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="f4134-159">Zazwyczaj zachowa również liczbę ponownych prób, a jeśli komunikat zostanie ponowiony więcej niż pewną liczbę razy, zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="f4134-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="f4134-160">Jest to zabezpieczenie przed komunikatami, które wyzwalają błąd aplikacji zawsze, gdy jest przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="f4134-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="f4134-161">Do następnego komunikatu z kolejki</span><span class="sxs-lookup"><span data-stu-id="f4134-161">De-queue the next message</span></span>

<span data-ttu-id="f4134-162">Kod do kolejki wiadomości z kolejki w dwóch krokach.</span><span class="sxs-lookup"><span data-stu-id="f4134-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="f4134-163">Podczas wywoływania `GetMessage`, Pobierz następnej wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f4134-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="f4134-164">Komunikat zwrócony z `GetMessage` staje się niewidoczny dla innego kodu odczytującego komunikaty z tej kolejki.</span><span class="sxs-lookup"><span data-stu-id="f4134-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="f4134-165">Domyślnie komunikat pozostanie niewidoczny przez 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="f4134-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="f4134-166">Aby zakończyć usuwanie komunikatu z kolejki, musisz również wywołać `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="f4134-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="f4134-167">Ten dwuetapowy proces usuwania komunikatów gwarantuje, że jeśli kod nie może przetworzyć komunikatu z powodu awarii sprzętu lub oprogramowania, inne wystąpienie kodu można uzyskać ten sam komunikat i spróbuj ponownie.</span><span class="sxs-lookup"><span data-stu-id="f4134-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="f4134-168">Twój kod wywołuje `DeleteMessage` natychmiast po przetworzeniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f4134-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="f4134-169">Asynchroniczne przepływy pracy za pomocą wspólnych interfejsów API magazynu kolejek</span><span class="sxs-lookup"><span data-stu-id="f4134-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="f4134-170">W tym przykładzie przedstawiono sposób asynchronicznego przepływu pracy za pomocą wspólnych interfejsów API magazynu kolejek.</span><span class="sxs-lookup"><span data-stu-id="f4134-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="f4134-171">Dodatkowe opcje usuwania komunikatów z kolejek</span><span class="sxs-lookup"><span data-stu-id="f4134-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="f4134-172">Istnieją dwa sposoby dostosowania pobierania komunikatów z kolejki.</span><span class="sxs-lookup"><span data-stu-id="f4134-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="f4134-173">Po pierwsze można uzyskać partii wiadomości (do 32).</span><span class="sxs-lookup"><span data-stu-id="f4134-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="f4134-174">Po drugie można ustawić limit czasu niewidoczności dłuższy lub krótszy, dzięki czemu kod będzie bardziej lub mniej czasu na pełne przetworzenie każdego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f4134-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="f4134-175">Poniższy przykład kodu wykorzystuje `GetMessages` można pobrać 20 komunikatów w jednym wywołań, a następnie przetwarza każdy komunikat.</span><span class="sxs-lookup"><span data-stu-id="f4134-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="f4134-176">Ustawia również limitu czasu niewidoczności na pięć minut dla każdego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f4134-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="f4134-177">Należy pamiętać, że 5 minut rozpoczyna się dla wszystkich wiadomości w tym samym czasie, więc po 5 minut przekazany od czasu wywołania `GetMessages`, wszystkie komunikaty, które nie zostały usunięte, będą widoczne ponownie.</span><span class="sxs-lookup"><span data-stu-id="f4134-177">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="f4134-178">Pobieranie długości kolejki</span><span class="sxs-lookup"><span data-stu-id="f4134-178">Get the queue length</span></span>

<span data-ttu-id="f4134-179">Możesz uzyskać szacunkową liczbę wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f4134-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="f4134-180">`FetchAttributes` Metody prosi usługę kolejki o pobranie atrybutów kolejki, w tym liczby komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f4134-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="f4134-181">`ApproximateMessageCount` Właściwość zwraca ostatnią wartość pobraną przez `FetchAttributes` bez wywoływania usługi kolejki.</span><span class="sxs-lookup"><span data-stu-id="f4134-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="f4134-182">Usuwanie kolejki</span><span class="sxs-lookup"><span data-stu-id="f4134-182">Delete a queue</span></span>

<span data-ttu-id="f4134-183">Aby usunąć kolejkę i wszystkie zawarte w niej komunikaty, wywołaj `Delete` metody dla obiekt kolejki.</span><span class="sxs-lookup"><span data-stu-id="f4134-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="f4134-184">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f4134-184">Next steps</span></span>

<span data-ttu-id="f4134-185">Teraz, kiedy znasz już podstawy magazynu kolejek, skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu.</span><span class="sxs-lookup"><span data-stu-id="f4134-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="f4134-186">Interfejsy API usługi Azure Storage dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="f4134-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="f4134-187">Dostawca typów magazynu Azure</span><span class="sxs-lookup"><span data-stu-id="f4134-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="f4134-188">Blog zespołu usługi Magazyn Azure</span><span class="sxs-lookup"><span data-stu-id="f4134-188">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="f4134-189">Konfigurowanie parametrów połączenia usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="f4134-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="f4134-190">Dokumentacja interfejsu API REST usług magazynu Azure</span><span class="sxs-lookup"><span data-stu-id="f4134-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
