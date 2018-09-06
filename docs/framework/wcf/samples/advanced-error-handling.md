---
title: Zaawansowana obsługa błędów
ms.date: 03/30/2017
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
ms.openlocfilehash: 72fb9885408759f5781501b548f81625d258d13c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745261"
---
# <a name="advanced-error-handling"></a><span data-ttu-id="469f3-102">Zaawansowana obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="469f3-102">Advanced Error Handling</span></span>
<span data-ttu-id="469f3-103">Niniejszy przykład pokazuje usługi routingu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="469f3-103">This sample demonstrates the Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="469f3-104">Usługa routingu jest składnikiem usługi WCF, który ułatwia to dołączenie routerem na podstawie zawartości do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="469f3-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="469f3-105">Niniejszy przykład pokazuje, jak usługa routingu inteligentnie odzyskiwania sprawności błędów, za pomocą transakcji i inne bardziej złożonych koncepcji obsługi komunikatów, takich jak multiemisji.</span><span class="sxs-lookup"><span data-stu-id="469f3-105">This sample shows how the routing service intelligently recovers from errors, using transactions and other more complex messaging concepts such as multicasting.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="469f3-106">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="469f3-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="469f3-107">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="469f3-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="469f3-108">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="469f3-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="469f3-109">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="469f3-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a><span data-ttu-id="469f3-110">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="469f3-110">Sample Details</span></span>  
 <span data-ttu-id="469f3-111">W tym przykładzie usługa routingu skonfigurowano odczytywać komunikaty z kolejki usługi MSMQ i multiemisji ten komunikat do list dwóch kolejek.</span><span class="sxs-lookup"><span data-stu-id="469f3-111">In this sample, the routing service is configured to read a message from an MSMQ queue and multicast this message to two lists of queues.</span></span> <span data-ttu-id="469f3-112">Jedną listę służy do kolejek usługi service i inny jest używana do rejestrowania kolejek.</span><span class="sxs-lookup"><span data-stu-id="469f3-112">One list is used for service queues and another is used for logging queues.</span></span>  
  
 <span data-ttu-id="469f3-113">Ponieważ domyślnie powiązanie usługi MSMQ usługa routingu jest skonfigurowany do użycia obsługuje transakcje, usługa routingu sprawia, że się, że wiadomości transakcyjne i odebranych przez co najmniej jedną kolejką na wszystkich listach przed zgłoszeniem do (kolejki dla ruchu przychodzącego `InQ`) który komunikat został pomyślnie kierowany.</span><span class="sxs-lookup"><span data-stu-id="469f3-113">Because, by default, the MSMQ binding that the routing service is configured to use supports the use of transactions, the routing service makes sure that the message is transactional and received by at least one queue in each list before reporting to the Inbound Queue (`InQ`) that the message was successfully routed.</span></span> <span data-ttu-id="469f3-114">W związku z tym w przypadku, gdy obie z kolejek usługi i / lub kolejek rejestrowania są niedostępne, usługa routingu zgłasza, że komunikat nie może być kierowany i kolejki elementów przychodzących powinno zająć określonej akcji.</span><span class="sxs-lookup"><span data-stu-id="469f3-114">Thus, in the case where both of the service queues or both of the logging queues are unavailable, the routing service reports that the message could not be routed and the inbound queue should take some action.</span></span> <span data-ttu-id="469f3-115">Ta akcja składa się z przenoszenie wiadomości do kolejki utraconych wiadomości systemu.</span><span class="sxs-lookup"><span data-stu-id="469f3-115">This action consists of moving the message to the system dead letter queue.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="469f3-116">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="469f3-116">To use this sample</span></span>  
  
1.  > [!IMPORTANT]
    >  <span data-ttu-id="469f3-117">Przed uruchomieniem tego przykładu, należy zainstalować usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="469f3-117">Install MSMQ before running this sample.</span></span> <span data-ttu-id="469f3-118">Jeśli usługa MSMQ nie jest zainstalowany, zwracany jest komunikat o wyjątku, podczas uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="469f3-118">If MSMQ is not installed, an exception message is returned when running the sample.</span></span> <span data-ttu-id="469f3-119">Instrukcje dotyczące instalowania usługi MSMQ znajduje się w temacie [instalowanie komunikatów usługi kolejkowania wiadomości (MSMQ)](https://go.microsoft.com/fwlink/?LinkId=166437).</span><span class="sxs-lookup"><span data-stu-id="469f3-119">Instructions for installing MSMQ can be found at [Installing Message Queuing (MSMQ)](https://go.microsoft.com/fwlink/?LinkId=166437).</span></span>  
  
     <span data-ttu-id="469f3-120">Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz AdvancedErrorHandling.sln.</span><span class="sxs-lookup"><span data-stu-id="469f3-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedErrorHandling.sln.</span></span>  
  
2.  <span data-ttu-id="469f3-121">Naciśnij klawisz **F5** lub **CTRL + SHIFT + B** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="469f3-121">Press **F5** or **CTRL+SHIFT+B** in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="469f3-122">Jeśli tworzysz aplikację za pomocą klawiszy CTRL + SHIFT + B, należy uruchomić tę aplikację u. / RoutingService/bin/debug/RoutingService.exe.</span><span class="sxs-lookup"><span data-stu-id="469f3-122">If you build the application with CTRL+SHIFT+B, you must start the application at ./RoutingService/bin/debug/RoutingService.exe.</span></span>  
  
3.  <span data-ttu-id="469f3-123">W oknie konsoli naciśnij klawisz ENTER, aby uruchomić klienta.</span><span class="sxs-lookup"><span data-stu-id="469f3-123">In the console window, press ENTER to start the client.</span></span>  
  
4.  <span data-ttu-id="469f3-124">Różne statystyki dotyczące kolejki w każdym przypadku zwracane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="469f3-124">The client returns different statistics about the queues for each case.</span></span>  
  
    1.  <span data-ttu-id="469f3-125">Poniżej znajduje się dane wyjściowe zwracane w przypadku 1 (Brak błędów).</span><span class="sxs-lookup"><span data-stu-id="469f3-125">The following is the output returned for case 1 (no failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  <span data-ttu-id="469f3-126">Poniżej znajduje się dane wyjściowe zwracane w przypadku 3 (podstawowej usługi i rejestrowania błędów kolejki).</span><span class="sxs-lookup"><span data-stu-id="469f3-126">The following is the output returned for case 3 (primary service and logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  <span data-ttu-id="469f3-127">Poniżej znajduje się dane wyjściowe zwracane w przypadku 4 (podstawowa usługa kolejki i rejestrowanie podstawowych i zapasowych kolejki błędów).</span><span class="sxs-lookup"><span data-stu-id="469f3-127">The following is the output returned for case 4 (primary service queue and primary and backup logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  <span data-ttu-id="469f3-128">Poniżej znajduje się dane wyjściowe zwracane w przypadku 2 (niepowodzenie kolejki głównej usługi).</span><span class="sxs-lookup"><span data-stu-id="469f3-128">The following is the output returned for case 2 (primary service queue failure).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="469f3-129">Można konfigurować za pomocą kodu lub pliku App.config</span><span class="sxs-lookup"><span data-stu-id="469f3-129">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="469f3-130">Dostarczany próbki, skonfigurowany do używania pliku App.config do definiowania zachowania routera.</span><span class="sxs-lookup"><span data-stu-id="469f3-130">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="469f3-131">Możesz również zmienić nazwę pliku RoutingService\App.config się czymś innym, tak, aby nie został rozpoznany i zmień wartość właściwości `configDriven` pole RoutingService\Program.cs do `false` do korzystania z konfiguracji zdefiniowana w kodzie.</span><span class="sxs-lookup"><span data-stu-id="469f3-131">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and change the value of the `configDriven` field in RoutingService\Program.cs to `false` to use the configuration defined in the code.</span></span> <span data-ttu-id="469f3-132">Każda z tych metod powoduje takie samo zachowanie z routera.</span><span class="sxs-lookup"><span data-stu-id="469f3-132">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="469f3-133">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="469f3-133">Scenario</span></span>  
 <span data-ttu-id="469f3-134">Niniejszy przykład pokazuje, że usługa routingu mogą obsługiwać zaawansowane funkcje obsługi komunikatów, takie jak transakcje i odbierania kontekstu i użyć tych funkcji w ramach poprawnie Obsługa scenariuszy błąd.</span><span class="sxs-lookup"><span data-stu-id="469f3-134">This sample demonstrates that the routing service can handle advanced messaging capabilities, such as transactions and receive context, and that it can utilize these capabilities as a part of correctly handling error scenarios.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="469f3-135">Scenariusz rzeczywistych</span><span class="sxs-lookup"><span data-stu-id="469f3-135">Real World Scenario</span></span>  
 <span data-ttu-id="469f3-136">Contoso chce korzystać transakcyjnych odbiera za pośrednictwem usługi routingu, aby upewnić się, że wszystkie niezbędne usługi otrzymywanie informacji, nawet w trakcie warunków błędów.</span><span class="sxs-lookup"><span data-stu-id="469f3-136">Contoso wants to utilize transactional receives through the routing service to ensure that all necessary services receive information even during error conditions.</span></span> <span data-ttu-id="469f3-137">Ponadto chciałby, błędy, które mają być obsługiwane poprawnie i automatycznie i błędów, należy podać w przypadku, że komunikat nie można dostarczyć nawet wtedy, gdy logika obsługi błędów jest wykorzystywany.</span><span class="sxs-lookup"><span data-stu-id="469f3-137">Furthermore, they would like errors to be handled correctly and automatically and failures to be reported in the case that a message is undeliverable even when error handling logic is utilized.</span></span> <span data-ttu-id="469f3-138">W tym celu skonfigurowana usługa routingu do trybu failover do określonych punktów końcowych, zgodnie z oczekiwaniami, a usługa routingu obsługuje sytuacje, w tym tworzenie, uzupełnianie i wycofania/Przerywanie transakcji i odbierania kontekstów jako wymagane.</span><span class="sxs-lookup"><span data-stu-id="469f3-138">For this purpose, they configure the routing service to fail over to specific endpoints as expected and the routing service handles the error situations, which includes the creation, completion, and rollback/aborting of transactions/receive contexts as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="469f3-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="469f3-139">See Also</span></span>  
 [<span data-ttu-id="469f3-140">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="469f3-140">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
