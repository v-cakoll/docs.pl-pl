---
title: Rozpoczynanie pracy z usługą Azure Queue Storage przy użyciu języka F#
description: Kolejki platformy Azure zapewniają niezawodne, asynchroniczne komunikaty między składnikami aplikacji. Obsługa komunikatów w chmurze umożliwia niezależne skalowanie składników aplikacji.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 65af98fb88e91d709eb0e35907cbc2dc097634d0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630483"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="8c246-104">Rozpoczynanie pracy z usługą Azure queue storage przy użyciu języka F\#</span><span class="sxs-lookup"><span data-stu-id="8c246-104">Get started with Azure Queue storage using F\#</span></span>

<span data-ttu-id="8c246-105">Usługa Azure queue storage udostępnia komunikaty w chmurze między składnikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c246-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="8c246-106">Podczas projektowania aplikacji do skalowania składniki aplikacji są często rozłączane, dzięki czemu mogą być skalowane niezależnie.</span><span class="sxs-lookup"><span data-stu-id="8c246-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="8c246-107">Usługa queue storage zapewnia asynchroniczne przesyłanie komunikatów na potrzeby komunikacji między składnikami aplikacji, niezależnie od tego, czy działają w chmurze, na komputerze, na serwerze lokalnym, czy na urządzeniu przenośnym.</span><span class="sxs-lookup"><span data-stu-id="8c246-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="8c246-108">Magazyn kolejek obsługuje również zarządzanie zadaniami asynchronicznymi i przepływami pracy procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c246-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="8c246-109">Informacje o tym samouczku</span><span class="sxs-lookup"><span data-stu-id="8c246-109">About this tutorial</span></span>

<span data-ttu-id="8c246-110">W tym samouczku pokazano, F# jak napisać kod dla niektórych typowych zadań za pomocą usługi Azure queue storage.</span><span class="sxs-lookup"><span data-stu-id="8c246-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="8c246-111">Objęte zadaniami obejmują tworzenie i usuwanie kolejek oraz dodawanie, odczytywanie i usuwanie komunikatów w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8c246-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="8c246-112">Omówienie pojęć dotyczących usługi queue storage można znaleźć [w przewodniku .NET dla usługi queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="8c246-112">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8c246-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8c246-113">Prerequisites</span></span>

<span data-ttu-id="8c246-114">Aby skorzystać z tego przewodnika, musisz najpierw [utworzyć konto usługi Azure Storage](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="8c246-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="8c246-115">Wymagany jest również klucz dostępu do magazynu dla tego konta.</span><span class="sxs-lookup"><span data-stu-id="8c246-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="8c246-116">Utwórz F# skrypt i uruchom F# interaktywny</span><span class="sxs-lookup"><span data-stu-id="8c246-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="8c246-117">Przykłady w tym artykule mogą być używane w F# aplikacji lub F# skrypcie.</span><span class="sxs-lookup"><span data-stu-id="8c246-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="8c246-118">Aby utworzyć F# skrypt, Utwórz plik z `.fsx` rozszerzeniem, na przykład `queues.fsx`w środowisku F# deweloperskim.</span><span class="sxs-lookup"><span data-stu-id="8c246-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="8c246-119">Następnie należy użyć [Menedżera pakietów](package-management.md) , takiego jak [Paket](https://fsprojects.github.io/Paket/) lub [](https://www.nuget.org/) `WindowsAzure.Storage` NuGet, aby zainstalować `#r` pakiet i odwołanie `WindowsAzure.Storage.dll` w skrypcie przy użyciu dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="8c246-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="8c246-120">Dodawanie deklaracji przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="8c246-120">Add namespace declarations</span></span>

<span data-ttu-id="8c246-121">Dodaj następujące `open` instrukcje na początku `queues.fsx` pliku:</span><span class="sxs-lookup"><span data-stu-id="8c246-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="8c246-122">Pobierz parametry połączenia</span><span class="sxs-lookup"><span data-stu-id="8c246-122">Get your connection string</span></span>

<span data-ttu-id="8c246-123">W tym samouczku będą potrzebne parametry połączenia usługi Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="8c246-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="8c246-124">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [Konfigurowanie parametrów połączenia magazynu](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="8c246-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="8c246-125">Na potrzeby samouczka wprowadzisz w skrypcie parametry połączenia, takie jak:</span><span class="sxs-lookup"><span data-stu-id="8c246-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="8c246-126">Nie jest to jednak **zalecane** w przypadku rzeczywistych projektów.</span><span class="sxs-lookup"><span data-stu-id="8c246-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="8c246-127">Klucz konta magazynu jest podobny do hasła głównego dla konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="8c246-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="8c246-128">Zawsze należy zachować ostrożność, aby chronić klucz konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="8c246-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="8c246-129">Należy unikać dystrybuowania go do innych użytkowników, ich trwałego kodowania lub zapisywania w pliku w formacie zwykłego tekstu, który jest dostępny dla innych.</span><span class="sxs-lookup"><span data-stu-id="8c246-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="8c246-130">Możesz ponownie wygenerować klucz za pomocą witryny Azure Portal, jeśli uważasz, że jego zabezpieczenia mogły zostać naruszone.</span><span class="sxs-lookup"><span data-stu-id="8c246-130">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="8c246-131">W przypadku prawdziwych aplikacji najlepszym sposobem obsługi parametrów połączenia magazynu jest w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8c246-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="8c246-132">Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:</span><span class="sxs-lookup"><span data-stu-id="8c246-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="8c246-133">Korzystanie z usługi Azure Configuration Manager jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="8c246-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="8c246-134">Można również użyć interfejsu API, takiego jak `ConfigurationManager` typ .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c246-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="8c246-135">Analizowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="8c246-135">Parse the connection string</span></span>

<span data-ttu-id="8c246-136">Aby przeanalizować parametry połączenia, użyj:</span><span class="sxs-lookup"><span data-stu-id="8c246-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="8c246-137">Spowoduje to zwrócenie elementu `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="8c246-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="8c246-138">Tworzenie klienta usługa kolejki</span><span class="sxs-lookup"><span data-stu-id="8c246-138">Create the Queue service client</span></span>

<span data-ttu-id="8c246-139">`CloudQueueClient` Klasa umożliwia pobieranie kolejek przechowywanych w usłudze queue storage.</span><span class="sxs-lookup"><span data-stu-id="8c246-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="8c246-140">Oto jeden ze sposobów tworzenia klienta usługi:</span><span class="sxs-lookup"><span data-stu-id="8c246-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="8c246-141">Teraz możesz przystąpić do pisania kodu, który odczytuje dane z usługi queue storage i zapisuje dane.</span><span class="sxs-lookup"><span data-stu-id="8c246-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="8c246-142">Tworzenie kolejki</span><span class="sxs-lookup"><span data-stu-id="8c246-142">Create a queue</span></span>

<span data-ttu-id="8c246-143">Ten przykład pokazuje, jak utworzyć kolejkę, jeśli jeszcze nie istnieje:</span><span class="sxs-lookup"><span data-stu-id="8c246-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="8c246-144">Wstawianie komunikatu do kolejki</span><span class="sxs-lookup"><span data-stu-id="8c246-144">Insert a message into a queue</span></span>

<span data-ttu-id="8c246-145">Aby wstawić komunikat do istniejącej kolejki, najpierw utwórz nowy `CloudQueueMessage`.</span><span class="sxs-lookup"><span data-stu-id="8c246-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="8c246-146">Następnie Wywołaj `AddMessage` metodę.</span><span class="sxs-lookup"><span data-stu-id="8c246-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="8c246-147">Element `CloudQueueMessage` można utworzyć na podstawie ciągu (w formacie UTF-8) `byte` lub tablicy, tak jak to:</span><span class="sxs-lookup"><span data-stu-id="8c246-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="8c246-148">Wgląd w następny komunikat</span><span class="sxs-lookup"><span data-stu-id="8c246-148">Peek at the next message</span></span>

<span data-ttu-id="8c246-149">Możesz uzyskać wgląd w komunikat z przodu kolejki, bez usuwania go z kolejki, wywołując `PeekMessage` metodę.</span><span class="sxs-lookup"><span data-stu-id="8c246-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="8c246-150">Pobierz następny komunikat do przetworzenia</span><span class="sxs-lookup"><span data-stu-id="8c246-150">Get the next message for processing</span></span>

<span data-ttu-id="8c246-151">Możesz pobrać komunikat z przodu kolejki do przetworzenia, wywołując `GetMessage` metodę.</span><span class="sxs-lookup"><span data-stu-id="8c246-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="8c246-152">Później wskazujemy pomyślne przetwarzanie komunikatu przy użyciu `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="8c246-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="8c246-153">Zmiana zawartości komunikatu w kolejce</span><span class="sxs-lookup"><span data-stu-id="8c246-153">Change the contents of a queued message</span></span>

<span data-ttu-id="8c246-154">Można zmienić zawartość pobranego komunikatu w miejscu w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8c246-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="8c246-155">Jeśli komunikat reprezentuje zadanie służbowe, można użyć tej funkcji do zaktualizowania stanu zadania pracy.</span><span class="sxs-lookup"><span data-stu-id="8c246-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="8c246-156">Poniższy kod aktualizuje komunikat kolejki z nową zawartością i ustawia limit czasu widoczności, aby zwiększyć kolejny 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="8c246-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="8c246-157">Spowoduje to zapisanie stanu pracy skojarzonej z wiadomością i nadaje klientowi kolejną minutę na kontynuowanie pracy nad komunikatem.</span><span class="sxs-lookup"><span data-stu-id="8c246-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="8c246-158">Ta technika służy do śledzenia wieloetapowych przepływów pracy dla komunikatów w kolejce, bez konieczności rozpoczynania od początku, jeśli etap przetwarzania zakończy się niepowodzeniem z powodu awarii sprzętu lub oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="8c246-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="8c246-159">Zwykle należy również zachować liczbę ponownych prób, a jeśli komunikat zostanie ponowiony więcej niż jakiś czas, należy go usunąć.</span><span class="sxs-lookup"><span data-stu-id="8c246-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="8c246-160">Chroni to przed komunikatem, który wyzwala błąd aplikacji przy każdym przetwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="8c246-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="8c246-161">Usuń następny komunikat z kolejki</span><span class="sxs-lookup"><span data-stu-id="8c246-161">De-queue the next message</span></span>

<span data-ttu-id="8c246-162">Twój kod usuwa komunikat z kolejki w dwóch krokach.</span><span class="sxs-lookup"><span data-stu-id="8c246-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="8c246-163">Po wywołaniu `GetMessage`otrzymujesz następną wiadomość w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8c246-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="8c246-164">Komunikat zwrócony z programu `GetMessage` stał się niewidoczny dla każdego innego kodu odczytującego komunikaty z tej kolejki.</span><span class="sxs-lookup"><span data-stu-id="8c246-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="8c246-165">Domyślnie ten komunikat pozostaje niewidoczny przez 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="8c246-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="8c246-166">Aby zakończyć usuwanie komunikatu z kolejki, należy również wywołać metodę `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="8c246-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="8c246-167">Ten dwuetapowy proces usuwania komunikatu gwarantuje, że jeśli kod nie może przetworzyć komunikatu z powodu awarii sprzętu lub oprogramowania, inne wystąpienie kodu może uzyskać ten sam komunikat i spróbować ponownie.</span><span class="sxs-lookup"><span data-stu-id="8c246-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="8c246-168">Kod wywołuje `DeleteMessage` się bezpośrednio po przetworzeniu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8c246-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="8c246-169">Używanie asynchronicznych przepływów pracy ze wspólnymi interfejsami API magazynu kolejki</span><span class="sxs-lookup"><span data-stu-id="8c246-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="8c246-170">Ten przykład pokazuje, jak używać asynchronicznego przepływu pracy ze wspólnymi interfejsami API magazynu kolejki.</span><span class="sxs-lookup"><span data-stu-id="8c246-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="8c246-171">Dodatkowe opcje do usuwania komunikatów z kolejkowania</span><span class="sxs-lookup"><span data-stu-id="8c246-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="8c246-172">Istnieją dwa sposoby dostosowania pobierania komunikatów z kolejki.</span><span class="sxs-lookup"><span data-stu-id="8c246-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="8c246-173">Najpierw można pobrać partię komunikatów (do 32).</span><span class="sxs-lookup"><span data-stu-id="8c246-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="8c246-174">Następnie można ustawić dłuższy lub krótszy limit czasu niewglądu, co pozwala na zwiększenie lub skrócenie czasu w celu pełnego przetworzenia poszczególnych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8c246-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="8c246-175">Poniższy przykład kodu używa `GetMessages` do uzyskania 20 komunikatów w jednym wywołaniu, a następnie przetwarza każdy komunikat.</span><span class="sxs-lookup"><span data-stu-id="8c246-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="8c246-176">Ustawia również limit czasu niewidoczności na pięć minut dla każdego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8c246-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="8c246-177">Należy zauważyć, że 5 minut rozpoczyna się dla wszystkich komunikatów w tym samym czasie, więc po upływie 5 minut od wywołania `GetMessages`do, wszystkie komunikaty, które nie zostały usunięte, staną się znów widoczne.</span><span class="sxs-lookup"><span data-stu-id="8c246-177">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="8c246-178">Pobieranie długości kolejki</span><span class="sxs-lookup"><span data-stu-id="8c246-178">Get the queue length</span></span>

<span data-ttu-id="8c246-179">Możesz uzyskać szacunkową liczbę komunikatów w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8c246-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="8c246-180">`FetchAttributes` Metoda prosi usługa kolejki o pobranie atrybutów kolejki, łącznie z liczbą komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8c246-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="8c246-181">Właściwość zwraca ostatnią wartość pobraną `FetchAttributes` przez metodę bez wywoływania usługa kolejki. `ApproximateMessageCount`</span><span class="sxs-lookup"><span data-stu-id="8c246-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="8c246-182">Usuwanie kolejki</span><span class="sxs-lookup"><span data-stu-id="8c246-182">Delete a queue</span></span>

<span data-ttu-id="8c246-183">Aby usunąć kolejkę i wszystkie znajdujące się w niej komunikaty, wywołaj `Delete` metodę w obiekcie Queue.</span><span class="sxs-lookup"><span data-stu-id="8c246-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="8c246-184">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="8c246-184">Next steps</span></span>

<span data-ttu-id="8c246-185">Teraz, gdy znasz już podstawy magazynu kolejek, Skorzystaj z poniższych linków, aby dowiedzieć się więcej o bardziej skomplikowanych zadaniach magazynu.</span><span class="sxs-lookup"><span data-stu-id="8c246-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="8c246-186">Interfejsy API usługi Azure Storage dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="8c246-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="8c246-187">Dostawca typów usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="8c246-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="8c246-188">Blog zespołu usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="8c246-188">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="8c246-189">Konfigurowanie parametrów połączenia usługi Azure Storage</span><span class="sxs-lookup"><span data-stu-id="8c246-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="8c246-190">Dokumentacja interfejsu API REST usług Azure Storage</span><span class="sxs-lookup"><span data-stu-id="8c246-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
