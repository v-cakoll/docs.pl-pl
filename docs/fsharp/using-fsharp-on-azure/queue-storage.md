---
title: "Rozpoczynanie pracy z magazynem kolejek Azure przy użyciu języka F #"
description: "Kolejek platformy Azure zapewniają niezawodne, asynchronicznego wysyłanie komunikatów między składnikami aplikacji. Chmury obsługi komunikatów włącza składniki aplikacji można skalować niezależnie."
keywords: "Visual f #, f #, funkcjonalności programowania .NET, .NET Core Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 70dc554c-8f4d-42a7-8e2a-6438657d012a
ms.openlocfilehash: f5ebdb3f3b50996a397c8420b773178493744d70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="fa3c2-105">Rozpoczynanie pracy z magazynem kolejek Azure przy użyciu języka F #</span><span class="sxs-lookup"><span data-stu-id="fa3c2-105">Get started with Azure Queue storage using F#</span></span> #

<span data-ttu-id="fa3c2-106">Magazyn kolejek Azure udostępnia chmury wysyłanie komunikatów między składnikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-106">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="fa3c2-107">Podczas projektowania aplikacji pod kątem skalowania, składniki aplikacji są często rozłączane, dzięki czemu można skalować niezależnie.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-107">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="fa3c2-108">Magazyn kolejek zapewnia asynchroniczną obsługę wiadomości do komunikacji między składnikami aplikacji, czy działają w chmurze, na komputerze, na serwerze lokalnym lub na urządzeniu przenośnym.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-108">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="fa3c2-109">Magazyn kolejek obsługuje również zarządzanie asynchronicznymi zadaniami oraz przepływy pracy procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-109">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="fa3c2-110">Informacje o tym samouczku</span><span class="sxs-lookup"><span data-stu-id="fa3c2-110">About this tutorial</span></span>

<span data-ttu-id="fa3c2-111">Ten samouczek pokazuje, jak napisać kod F # dla niektórych typowych zadań przy użyciu magazynu kolejek Azure.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-111">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="fa3c2-112">Zadań obejmują tworzenie i usuwanie kolejek i dodawanie, odczytywanie i usuwanie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-112">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="fa3c2-113">Omówienie pojęć dotyczących magazynu kolejek, zobacz [przewodnik .NET dla magazynu kolejek](/azure/storage/storage-dotnet-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="fa3c2-113">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fa3c2-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fa3c2-114">Prerequisites</span></span>

<span data-ttu-id="fa3c2-115">Aby użyć tego przewodnika, należy najpierw [utworzyć konto magazynu Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="fa3c2-115">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="fa3c2-116">Należy również klucz dostępu do magazynu dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-116">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="fa3c2-117">Tworzenie skryptu języka F # i rozpocząć F # Interactive</span><span class="sxs-lookup"><span data-stu-id="fa3c2-117">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="fa3c2-118">Przykłady w tym artykule można używać w F # aplikacji lub skryptu języka F #.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-118">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="fa3c2-119">Aby utworzyć skrypt F #, Utwórz plik o `.fsx` rozszerzenie, na przykład `queues.fsx`, w środowiska deweloperskiego F #.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-119">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="fa3c2-120">Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) do zainstalowania `WindowsAzure.Storage` odwołanie do pakietu i `WindowsAzure.Storage.dll` skryptu za pomocą `#r`dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-120">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="fa3c2-121">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="fa3c2-121">Add namespace declarations</span></span>

<span data-ttu-id="fa3c2-122">Dodaj następujące `open` instrukcje na początku `queues.fsx` pliku:</span><span class="sxs-lookup"><span data-stu-id="fa3c2-122">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="fa3c2-123">Pobierz ciąg połączenia</span><span class="sxs-lookup"><span data-stu-id="fa3c2-123">Get your connection string</span></span>

<span data-ttu-id="fa3c2-124">Parametry połączenia magazynu Azure należy w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-124">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="fa3c2-125">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="fa3c2-125">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="fa3c2-126">Samouczek będzie wprowadź parametry połączenia za pomocą skryptu, jak to:</span><span class="sxs-lookup"><span data-stu-id="fa3c2-126">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="fa3c2-127">Jest to jednak **niezalecane** rzeczywiste projektów.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-127">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="fa3c2-128">Klucz konta magazynu jest podobny do hasła głównego konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-128">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="fa3c2-129">Zawsze starannie Chroń klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-129">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="fa3c2-130">Unikaj udostępniaj go innym użytkownikom, kodować je lub zapisać go w pliku jako zwykły tekst, który jest dostępny do innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-130">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="fa3c2-131">Można ponownie wygenerować klucz przy użyciu portalu Azure, jeśli uważasz, że mogą zostać naruszone.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-131">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="fa3c2-132">Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-132">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="fa3c2-133">Aby pobrać parametry połączenia w pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="fa3c2-133">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="fa3c2-134">Przy użyciu programu Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-134">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="fa3c2-135">Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-135">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="fa3c2-136">Przeanalizować parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="fa3c2-136">Parse the connection string</span></span>

<span data-ttu-id="fa3c2-137">Aby przeanalizować parametrów połączenia, należy użyć:</span><span class="sxs-lookup"><span data-stu-id="fa3c2-137">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="fa3c2-138">Spowoduje to zwrócenie `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-138">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="fa3c2-139">Tworzenie klienta usługi kolejki</span><span class="sxs-lookup"><span data-stu-id="fa3c2-139">Create the Queue service client</span></span>

<span data-ttu-id="fa3c2-140">`CloudQueueClient` Klasa umożliwia pobieranie kolejek przechowywanych w magazynie kolejek.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-140">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="fa3c2-141">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="fa3c2-141">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="fa3c2-142">Teraz można przystąpić do pisania kodu, która odczytuje i zapisuje dane do magazynu kolejek.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-142">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="fa3c2-143">Tworzenie kolejki</span><span class="sxs-lookup"><span data-stu-id="fa3c2-143">Create a queue</span></span>

<span data-ttu-id="fa3c2-144">W tym przykładzie pokazano, jak utworzyć kolejkę, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="fa3c2-144">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="fa3c2-145">Wstawianie komunikatu do kolejki</span><span class="sxs-lookup"><span data-stu-id="fa3c2-145">Insert a message into a queue</span></span>

<span data-ttu-id="fa3c2-146">Aby wstawić komunikat do istniejącej kolejki, najpierw utwórz nową `CloudQueueMessage`.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-146">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="fa3c2-147">Następnie wywołaj `AddMessage` metody.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-147">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="fa3c2-148">A `CloudQueueMessage` można tworzyć przy użyciu dowolnego ciągu (w formacie UTF-8) lub `byte` tablicy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="fa3c2-148">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="fa3c2-149">Podgląd kolejnego komunikatu</span><span class="sxs-lookup"><span data-stu-id="fa3c2-149">Peek at the next message</span></span>

<span data-ttu-id="fa3c2-150">Możesz uzyskać wgląd w komunikat z przodu kolejki, bez jego usuwania z kolejki, wywołując `PeekMessage` metody.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-150">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="fa3c2-151">Następny komunikat do przetworzenia</span><span class="sxs-lookup"><span data-stu-id="fa3c2-151">Get the next message for processing</span></span>

<span data-ttu-id="fa3c2-152">Komunikat z przodu kolejki przetwarzania można pobrać przez wywołanie metody `GetMessage` metody.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-152">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="fa3c2-153">Później wskazywać pomyślne przetwarzania komunikatu za pomocą `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-153">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="fa3c2-154">Zmiana zawartości komunikatu w kolejce</span><span class="sxs-lookup"><span data-stu-id="fa3c2-154">Change the contents of a queued message</span></span>

<span data-ttu-id="fa3c2-155">Można zmienić zawartość komunikatu pobrane w miejscu w kolejce.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-155">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="fa3c2-156">Jeśli komunikat reprezentuje zadanie robocze, można Użyj tej funkcji, aby zaktualizować stan zadania.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-156">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="fa3c2-157">Poniższy kod aktualizuje komunikat kolejki o nową zawartość i Ustawia rozszerzenie limitu czasu widoczności kolejne 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-157">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="fa3c2-158">Zapisuje stan pracy powiązanej z komunikatem i daje klientowi kolejną minutę na kontynuowanie pracy nad wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-158">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="fa3c2-159">Można użyć tej metody do śledzenia wieloetapowych przepływów pracy związanych z komunikatami kolejek, bez konieczności rozpoczynania od początku, jeśli dany etap nie powiedzie się z powodu awarii sprzętu lub oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-159">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="fa3c2-160">Zazwyczaj zachowa również liczbę ponownych prób, a jeśli komunikat zostanie ponowiony więcej niż pewną liczbę razy, zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-160">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="fa3c2-161">Jest to zabezpieczenie przed komunikatami, które wyzwalają błąd aplikacji zawsze, gdy jest przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-161">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="fa3c2-162">Do następnego komunikatu z kolejki</span><span class="sxs-lookup"><span data-stu-id="fa3c2-162">De-queue the next message</span></span>

<span data-ttu-id="fa3c2-163">Kod do kolejki wiadomości z kolejki w dwóch krokach.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-163">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="fa3c2-164">Podczas wywoływania `GetMessage`, Pobierz następnej wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-164">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="fa3c2-165">Komunikat zwrócony z `GetMessage` staje się niewidoczny dla innego kodu odczytującego komunikaty z tej kolejki.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-165">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="fa3c2-166">Domyślnie komunikat pozostanie niewidoczny przez 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-166">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="fa3c2-167">Aby zakończyć usuwanie komunikatu z kolejki, musisz również wywołać `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-167">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="fa3c2-168">Ten dwuetapowy proces usuwania komunikatów gwarantuje, że jeśli kod nie może przetworzyć komunikatu z powodu awarii sprzętu lub oprogramowania, inne wystąpienie kodu można uzyskać ten sam komunikat i spróbuj ponownie.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-168">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="fa3c2-169">Twój kod wywołuje `DeleteMessage` natychmiast po przetworzeniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-169">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="fa3c2-170">Asynchroniczne przepływy pracy za pomocą wspólnych interfejsów API magazynu kolejek</span><span class="sxs-lookup"><span data-stu-id="fa3c2-170">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="fa3c2-171">W tym przykładzie przedstawiono sposób asynchronicznego przepływu pracy za pomocą wspólnych interfejsów API magazynu kolejek.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-171">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="fa3c2-172">Dodatkowe opcje usuwania komunikatów z kolejek</span><span class="sxs-lookup"><span data-stu-id="fa3c2-172">Additional options for de-queuing messages</span></span>

<span data-ttu-id="fa3c2-173">Istnieją dwa sposoby dostosowania pobierania komunikatów z kolejki.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-173">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="fa3c2-174">Po pierwsze można uzyskać partii wiadomości (do 32).</span><span class="sxs-lookup"><span data-stu-id="fa3c2-174">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="fa3c2-175">Po drugie można ustawić limit czasu niewidoczności dłuższy lub krótszy, dzięki czemu kod będzie bardziej lub mniej czasu na pełne przetworzenie każdego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-175">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="fa3c2-176">Poniższy przykład kodu wykorzystuje `GetMessages` można pobrać 20 komunikatów w jednym wywołań, a następnie przetwarza każdy komunikat.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-176">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="fa3c2-177">Ustawia również limitu czasu niewidoczności na pięć minut dla każdego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-177">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="fa3c2-178">Należy pamiętać, że 5 minut rozpoczyna się dla wszystkich wiadomości w tym samym czasie, więc po 5 minut przekazany od czasu wywołania `GetMessages`, wszystkie komunikaty, które nie zostały usunięte, będą widoczne ponownie.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-178">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="fa3c2-179">Pobieranie długości kolejki</span><span class="sxs-lookup"><span data-stu-id="fa3c2-179">Get the queue length</span></span>

<span data-ttu-id="fa3c2-180">Możesz uzyskać szacunkową liczbę wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-180">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="fa3c2-181">`FetchAttributes` Metody prosi usługę kolejki o pobranie atrybutów kolejki, w tym liczby komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-181">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="fa3c2-182">`ApproximateMessageCount` Właściwość zwraca ostatnią wartość pobraną przez `FetchAttributes` bez wywoływania usługi kolejki.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-182">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="fa3c2-183">Usuwanie kolejki</span><span class="sxs-lookup"><span data-stu-id="fa3c2-183">Delete a queue</span></span>

<span data-ttu-id="fa3c2-184">Aby usunąć kolejkę i wszystkie zawarte w niej komunikaty, wywołaj `Delete` metody dla obiekt kolejki.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-184">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="fa3c2-185">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="fa3c2-185">Next steps</span></span>

<span data-ttu-id="fa3c2-186">Teraz, kiedy znasz już podstawy magazynu kolejek, skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu.</span><span class="sxs-lookup"><span data-stu-id="fa3c2-186">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="fa3c2-187">Biblioteka klienta usługi Storage dla platformy .NET odwołania</span><span class="sxs-lookup"><span data-stu-id="fa3c2-187">Storage Client Library for .NET reference</span></span>](http://go.microsoft.com/fwlink/?LinkID=390731&clcid=0x409)
- [<span data-ttu-id="fa3c2-188">Dostawca typów magazynu Azure</span><span class="sxs-lookup"><span data-stu-id="fa3c2-188">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="fa3c2-189">Blog zespołu usługi Magazyn Azure</span><span class="sxs-lookup"><span data-stu-id="fa3c2-189">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="fa3c2-190">Konfigurowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="fa3c2-190">Configuring Connection Strings</span></span>](http://msdn.microsoft.com/library/azure/ee758697.aspx)
- [<span data-ttu-id="fa3c2-191">Dokumentacja interfejsu API REST</span><span class="sxs-lookup"><span data-stu-id="fa3c2-191">REST API reference</span></span>](http://msdn.microsoft.com/library/azure/dd179355)
