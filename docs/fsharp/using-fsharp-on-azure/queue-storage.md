---
title: Rozpoczynanie pracy z usługą Azure Queue storage przy użyciuF#
description: Usługa Azure Queues zapewnia niezawodne, asynchroniczne przesyłanie komunikatów między składnikami aplikacji. Chmura komunikatów umożliwia składnikom aplikacji niezależne skalowanie obu elementów.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 58a46dfe905a32be77a13d11df8f0544546ea0ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756380"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="5552e-104">Rozpoczynanie pracy z usługą Azure Queue storage przy użyciu F\#</span><span class="sxs-lookup"><span data-stu-id="5552e-104">Get started with Azure Queue storage using F\#</span></span>

<span data-ttu-id="5552e-105">Usługa Azure Queue storage umożliwia przesyłanie komunikatów między składnikami aplikacji w chmurze.</span><span class="sxs-lookup"><span data-stu-id="5552e-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="5552e-106">Projektowanie aplikacji do skalowania, składniki aplikacji są często odłączane, tak aby mogły być skalowane niezależnie.</span><span class="sxs-lookup"><span data-stu-id="5552e-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="5552e-107">Usługa queue storage zapewnia asynchroniczne przesyłanie komunikatów do komunikacji między składnikami aplikacji, czy działają w chmurze, na komputerze, na serwerze lokalnym lub na urządzeniu przenośnym.</span><span class="sxs-lookup"><span data-stu-id="5552e-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="5552e-108">Usługa queue storage obsługuje również zarządzanie asynchronicznymi zadaniami oraz przepływy pracy procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5552e-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="5552e-109">Informacje o tym samouczku</span><span class="sxs-lookup"><span data-stu-id="5552e-109">About this tutorial</span></span>

<span data-ttu-id="5552e-110">Ten samouczek przedstawia sposób zapisania F# kodu dla niektórych typowych zadań przy użyciu usługi Azure Queue storage.</span><span class="sxs-lookup"><span data-stu-id="5552e-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="5552e-111">Objęte zadania obejmują tworzenie i usuwanie kolejek oraz dodawanie, odczytywanie i usuwanie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="5552e-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="5552e-112">Omówienie pojęć usługi queue storage, zobacz [przewodnik platformy .NET dla usługi queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="5552e-112">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5552e-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5552e-113">Prerequisites</span></span>

<span data-ttu-id="5552e-114">Aby użyć tego przewodnika, należy najpierw [Tworzenie konta usługi Azure storage](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="5552e-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="5552e-115">Należy także klucz dostępu do magazynu dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="5552e-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="5552e-116">Tworzenie F# skrypt i uruchomić F# interaktywne</span><span class="sxs-lookup"><span data-stu-id="5552e-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="5552e-117">Przykłady w tym artykule mogą być używane w jednej F# aplikacji lub F# skryptu.</span><span class="sxs-lookup"><span data-stu-id="5552e-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="5552e-118">Aby utworzyć F# skrypt, Utwórz plik o `.fsx` rozszerzenia, na przykład `queues.fsx`w usługi F# środowiska deweloperskiego.</span><span class="sxs-lookup"><span data-stu-id="5552e-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="5552e-119">Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) zainstalował `WindowsAzure.Storage` pakietów i odwołań `WindowsAzure.Storage.dll` w skrypcie za pomocą `#r`dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="5552e-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="5552e-120">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="5552e-120">Add namespace declarations</span></span>

<span data-ttu-id="5552e-121">Dodaj następujący kod `open` instrukcji na górze `queues.fsx` pliku:</span><span class="sxs-lookup"><span data-stu-id="5552e-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="5552e-122">Pobieranie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="5552e-122">Get your connection string</span></span>

<span data-ttu-id="5552e-123">Na potrzeby tego samouczka konieczne będzie parametrów połączenia usługi Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="5552e-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="5552e-124">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="5552e-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="5552e-125">Samouczek wprowadzisz parametrów połączenia w skrypcie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5552e-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="5552e-126">Jest to jednak **niezalecane** rzeczywiste projektów.</span><span class="sxs-lookup"><span data-stu-id="5552e-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="5552e-127">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="5552e-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="5552e-128">Zawsze starannie Chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="5552e-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="5552e-129">Należy unikać, ich dystrybucję w innym użytkownikom, kodować je lub zapisanie go w pliku tekstowego, który jest dostępny dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="5552e-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="5552e-130">Można ponownie wygenerować klucz za pośrednictwem witryny Azure Portal, jeśli uważasz, że mogą zostać przejęte.</span><span class="sxs-lookup"><span data-stu-id="5552e-130">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="5552e-131">Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5552e-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="5552e-132">Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="5552e-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="5552e-133">Użycie programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="5552e-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="5552e-134">Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="5552e-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="5552e-135">Przeanalizować parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="5552e-135">Parse the connection string</span></span>

<span data-ttu-id="5552e-136">Aby przeanalizować parametrów połączenia, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="5552e-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="5552e-137">Spowoduje to zwrócenie `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="5552e-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="5552e-138">Tworzenie klienta usługi kolejki</span><span class="sxs-lookup"><span data-stu-id="5552e-138">Create the Queue service client</span></span>

<span data-ttu-id="5552e-139">`CloudQueueClient` Klasy umożliwia pobieranie kolejek przechowywanych w usłudze Queue storage.</span><span class="sxs-lookup"><span data-stu-id="5552e-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="5552e-140">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="5552e-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="5552e-141">Teraz możesz przystąpić do pisania kodu, który odczytuje i zapisuje dane do usługi Queue storage.</span><span class="sxs-lookup"><span data-stu-id="5552e-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="5552e-142">Tworzenie kolejki</span><span class="sxs-lookup"><span data-stu-id="5552e-142">Create a queue</span></span>

<span data-ttu-id="5552e-143">Ten przykład pokazuje, jak utworzyć kolejkę, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="5552e-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="5552e-144">Wstawianie komunikatu do kolejki</span><span class="sxs-lookup"><span data-stu-id="5552e-144">Insert a message into a queue</span></span>

<span data-ttu-id="5552e-145">Aby wstawić komunikat do istniejącej kolejki, najpierw utwórz nowe `CloudQueueMessage`.</span><span class="sxs-lookup"><span data-stu-id="5552e-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="5552e-146">Następnie wywołaj `AddMessage` metody.</span><span class="sxs-lookup"><span data-stu-id="5552e-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="5552e-147">A `CloudQueueMessage` można utworzyć przy użyciu dowolnego ciągu (w formacie UTF-8) lub `byte` tablicy, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5552e-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="5552e-148">Podgląd kolejnego komunikatu</span><span class="sxs-lookup"><span data-stu-id="5552e-148">Peek at the next message</span></span>

<span data-ttu-id="5552e-149">Użytkownik może wglądu do wiadomości uzyskać kolejki, bez usuwania go z kolejki, wywołując `PeekMessage` metody.</span><span class="sxs-lookup"><span data-stu-id="5552e-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="5552e-150">Następny komunikat do przetworzenia</span><span class="sxs-lookup"><span data-stu-id="5552e-150">Get the next message for processing</span></span>

<span data-ttu-id="5552e-151">Możesz pobrać komunikat z przodu kolejki do przetworzenia przez wywołanie metody `GetMessage` metody.</span><span class="sxs-lookup"><span data-stu-id="5552e-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="5552e-152">Później wskazują pomyślnego przetwarzania komunikatu przy użyciu `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="5552e-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="5552e-153">Zmień zawartość komunikatu w kolejce</span><span class="sxs-lookup"><span data-stu-id="5552e-153">Change the contents of a queued message</span></span>

<span data-ttu-id="5552e-154">Możesz zmienić zawartość komunikatu pobrane w miejscu w kolejce.</span><span class="sxs-lookup"><span data-stu-id="5552e-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="5552e-155">Jeśli komunikat reprezentuje zadanie robocze, można użyć tej funkcji można zaktualizować stanu zadania.</span><span class="sxs-lookup"><span data-stu-id="5552e-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="5552e-156">Poniższy kod aktualizuje komunikat kolejki o nową zawartość i Ustawia rozszerzenie limitu czasu widoczności o kolejne 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="5552e-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="5552e-157">Zapisuje stan pracy powiązanej z komunikatem i daje klientowi kolejną minutę na kontynuowanie pracy w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="5552e-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="5552e-158">Tej techniki można używać do śledzenia wieloetapowe przepływy pracy na wiadomości w kolejce bez konieczności uruchamiania za pośrednictwem od samego początku, jeśli krok przetwarzania zakończy się niepowodzeniem z powodu awarii sprzętu lub oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="5552e-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="5552e-159">Zazwyczaj zachowa również liczbę ponownych prób, a jeśli komunikat zostanie ponowiony więcej niż pewną liczbę razy, zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="5552e-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="5552e-160">Chroni to przed komunikatami, które wyzwalają błąd aplikacji za każdym razem, gdy jest on przetwarzany.</span><span class="sxs-lookup"><span data-stu-id="5552e-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="5552e-161">Usuń zaznaczenie pola następnego komunikatu z kolejki</span><span class="sxs-lookup"><span data-stu-id="5552e-161">De-queue the next message</span></span>

<span data-ttu-id="5552e-162">Twój kod cofnąć umieszcza w kolejce komunikatu z kolejki w dwóch etapach.</span><span class="sxs-lookup"><span data-stu-id="5552e-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="5552e-163">Gdy wywołujesz `GetMessage`, uzyskasz następny komunikat w kolejce.</span><span class="sxs-lookup"><span data-stu-id="5552e-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="5552e-164">Komunikat zwrócony z `GetMessage` staje się niewidoczny dla innego kodu odczytującego komunikaty z tej kolejki.</span><span class="sxs-lookup"><span data-stu-id="5552e-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="5552e-165">Domyślnie komunikat pozostanie niewidoczny przez 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="5552e-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="5552e-166">Aby zakończyć usuwanie komunikatu z kolejki, musisz również wywołać `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="5552e-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="5552e-167">Ten dwuetapowy proces usuwania komunikatów gwarantuje, że jeśli Twój kod nie może przetworzyć komunikatu z powodu awarii sprzętu lub oprogramowania, inne wystąpienie kodu można uzyskać ten sam komunikat i spróbuj ponownie.</span><span class="sxs-lookup"><span data-stu-id="5552e-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="5552e-168">Twój kod wywołuje `DeleteMessage` natychmiast po przetworzeniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="5552e-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="5552e-169">Asynchroniczne przepływy pracy za pomocą wspólnego kolejki magazynu interfejsów API</span><span class="sxs-lookup"><span data-stu-id="5552e-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="5552e-170">W tym przykładzie przedstawiono sposób asynchronicznego przepływu pracy za pomocą wspólnego kolejki magazynu interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="5552e-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="5552e-171">Dodatkowe opcje usuwania komunikatów z kolejek</span><span class="sxs-lookup"><span data-stu-id="5552e-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="5552e-172">Istnieją dwa sposoby, które można dostosować odebrania komunikatu z kolejki.</span><span class="sxs-lookup"><span data-stu-id="5552e-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="5552e-173">Po pierwsze można uzyskać partię komunikatów (maksymalnie 32).</span><span class="sxs-lookup"><span data-stu-id="5552e-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="5552e-174">Po drugie można ustawić limitu czasu niewidoczności dłuższy lub krótszy, dzięki czemu kod więcej lub mniej czasu na pełne przetworzenie każdego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="5552e-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="5552e-175">Poniższy przykład kodu wykorzystuje `GetMessages` można pobrać 20 komunikatów w jednym wywołań, a następnie przetwarza każdy komunikat.</span><span class="sxs-lookup"><span data-stu-id="5552e-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="5552e-176">Ustawia również limitu czasu niewidoczności na pięć minut dla każdego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="5552e-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="5552e-177">Należy zauważyć, że 5 minut rozpoczyna się dla wszystkich komunikatów w tym samym czasie, dlatego po 5 minut ma minęło od wywołania `GetMessages`, wszystkie komunikaty, które nie zostały usunięte, będą widoczne ponownie.</span><span class="sxs-lookup"><span data-stu-id="5552e-177">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="5552e-178">Pobieranie długości kolejki</span><span class="sxs-lookup"><span data-stu-id="5552e-178">Get the queue length</span></span>

<span data-ttu-id="5552e-179">Możesz uzyskać szacunkową liczbę komunikatów w kolejce.</span><span class="sxs-lookup"><span data-stu-id="5552e-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="5552e-180">`FetchAttributes` Metoda prosi usługę kolejki o pobranie atrybutów kolejki, w tym liczby komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5552e-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="5552e-181">`ApproximateMessageCount` Właściwość zwraca ostatnią wartość pobraną przez `FetchAttributes` metody bez wywoływania usługi kolejki.</span><span class="sxs-lookup"><span data-stu-id="5552e-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="5552e-182">Usuwanie kolejki</span><span class="sxs-lookup"><span data-stu-id="5552e-182">Delete a queue</span></span>

<span data-ttu-id="5552e-183">Aby usunąć kolejkę i wszystkie zawarte w niej komunikaty, wywołaj `Delete` metody na obiekcie kolejki.</span><span class="sxs-lookup"><span data-stu-id="5552e-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="5552e-184">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5552e-184">Next steps</span></span>

<span data-ttu-id="5552e-185">Teraz, kiedy znasz już podstawy usługi Queue storage, skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu.</span><span class="sxs-lookup"><span data-stu-id="5552e-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="5552e-186">Interfejsy API usługi Azure Storage dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="5552e-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="5552e-187">Dostawcy typów usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="5552e-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="5552e-188">Blog zespołu usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="5552e-188">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="5552e-189">Konfigurowanie parametrów połączenia usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="5552e-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="5552e-190">Dokumentacja interfejsu API REST usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="5552e-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
