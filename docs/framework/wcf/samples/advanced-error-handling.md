---
title: "Zaawansowana obsługa błędów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77034a1948b7fc6dd383c9bdb5456917c6082687
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="advanced-error-handling"></a><span data-ttu-id="e1d47-102">Zaawansowana obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="e1d47-102">Advanced Error Handling</span></span>
<span data-ttu-id="e1d47-103">W przykładzie pokazano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="e1d47-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="e1d47-104">Usługa routingu jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składnik, który ułatwia obejmują routerem na podstawie zawartości w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1d47-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="e1d47-105">W tym przykładzie pokazano, jak usługa routingu inteligentnie odzyskiwania z błędów przy użyciu transakcji i innych bardziej złożonych pojęć obsługi wiadomości, takie jak multiemisji.</span><span class="sxs-lookup"><span data-stu-id="e1d47-105">This sample shows how the routing service intelligently recovers from errors, using transactions and other more complex messaging concepts such as multicasting.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e1d47-106">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e1d47-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e1d47-107">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e1d47-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e1d47-108">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="e1d47-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1d47-109">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e1d47-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a><span data-ttu-id="e1d47-110">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="e1d47-110">Sample Details</span></span>  
 <span data-ttu-id="e1d47-111">W tym przykładzie usługi routingu skonfigurowano odczytywać komunikaty z kolejki usługi MSMQ i multiemisji tej wiadomości do dwóch list z kolejki.</span><span class="sxs-lookup"><span data-stu-id="e1d47-111">In this sample, the routing service is configured to read a message from an MSMQ queue and multicast this message to two lists of queues.</span></span> <span data-ttu-id="e1d47-112">Jedna lista służy do kolejek usługi service i inny służy do rejestrowania kolejek.</span><span class="sxs-lookup"><span data-stu-id="e1d47-112">One list is used for service queues and another is used for logging queues.</span></span>  
  
 <span data-ttu-id="e1d47-113">Ponieważ domyślnie MSMQ powiązanie usługi routingu skonfigurowano Użyj obsługuje transakcje, usługa routingu upewnia się, że wiadomość jest transakcyjna i odebranych przez co najmniej jedna kolejka na wszystkich listach przed zgłoszeniem do (kolejki ruchu przychodzącego `InQ`), że komunikat został pomyślnie skierowany.</span><span class="sxs-lookup"><span data-stu-id="e1d47-113">Because, by default, the MSMQ binding that the routing service is configured to use supports the use of transactions, the routing service makes sure that the message is transactional and received by at least one queue in each list before reporting to the Inbound Queue (`InQ`) that the message was successfully routed.</span></span> <span data-ttu-id="e1d47-114">W związku z tym w przypadku, gdy oba kolejek usługi lub oba kolejek rejestrowania są niedostępne, usługa routingu zgłasza, że nie być kierowane wiadomości i kolejki przychodzącej powinien podjąć inną akcję.</span><span class="sxs-lookup"><span data-stu-id="e1d47-114">Thus, in the case where both of the service queues or both of the logging queues are unavailable, the routing service reports that the message could not be routed and the inbound queue should take some action.</span></span> <span data-ttu-id="e1d47-115">Ta akcja składa się z przenoszenie wiadomości do kolejki utraconych wiadomości systemu.</span><span class="sxs-lookup"><span data-stu-id="e1d47-115">This action consists of moving the message to the system dead letter queue.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e1d47-116">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="e1d47-116">To use this sample</span></span>  
  
1.  > [!IMPORTANT]
    >  <span data-ttu-id="e1d47-117">Zainstaluj usługę MSMQ przed uruchomieniem tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="e1d47-117">Install MSMQ before running this sample.</span></span> <span data-ttu-id="e1d47-118">Jeśli usługa MSMQ nie jest zainstalowana, zwracany jest komunikat o wyjątku, podczas uruchamiania próbki.</span><span class="sxs-lookup"><span data-stu-id="e1d47-118">If MSMQ is not installed, an exception message is returned when running the sample.</span></span> <span data-ttu-id="e1d47-119">Instrukcje dotyczące instalowania usługi MSMQ można znaleźć w folderze [usługi kolejkowania komunikatów instalowanie (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).</span><span class="sxs-lookup"><span data-stu-id="e1d47-119">Instructions for installing MSMQ can be found at [Installing Message Queuing (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).</span></span>  
  
     <span data-ttu-id="e1d47-120">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz AdvancedErrorHandling.sln.</span><span class="sxs-lookup"><span data-stu-id="e1d47-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedErrorHandling.sln.</span></span>  
  
2.  <span data-ttu-id="e1d47-121">Naciśnij klawisz **F5** lub **CTRL + SHIFT + B** w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e1d47-121">Press **F5** or **CTRL+SHIFT+B** in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="e1d47-122">W przypadku tworzenia aplikacji z klawiszy CTRL + SHIFT + B, należy uruchomić aplikację w. / RoutingService/bin/debug/RoutingService.exe.</span><span class="sxs-lookup"><span data-stu-id="e1d47-122">If you build the application with CTRL+SHIFT+B, you must start the application at ./RoutingService/bin/debug/RoutingService.exe.</span></span>  
  
3.  <span data-ttu-id="e1d47-123">W oknie konsoli naciśnij klawisz ENTER, aby uruchomić klienta.</span><span class="sxs-lookup"><span data-stu-id="e1d47-123">In the console window, press ENTER to start the client.</span></span>  
  
4.  <span data-ttu-id="e1d47-124">Różne Statystyka kolejki dla każdego przypadku zwracane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="e1d47-124">The client returns different statistics about the queues for each case.</span></span>  
  
    1.  <span data-ttu-id="e1d47-125">Poniżej przedstawiono dane wyjściowe zwrócone w przypadku 1 (nie błędów).</span><span class="sxs-lookup"><span data-stu-id="e1d47-125">The following is the output returned for case 1 (no failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  <span data-ttu-id="e1d47-126">Poniżej przedstawiono dane wyjściowe zwrócone w przypadku 3 (podstawowej usługi i rejestrowania błędów kolejki).</span><span class="sxs-lookup"><span data-stu-id="e1d47-126">The following is the output returned for case 3 (primary service and logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  <span data-ttu-id="e1d47-127">Poniżej przedstawiono dane wyjściowe zwrócone w przypadku 4 (Rejestrowanie podstawowego i zapasowego kolejki błędy i kolejki głównej usługi).</span><span class="sxs-lookup"><span data-stu-id="e1d47-127">The following is the output returned for case 4 (primary service queue and primary and backup logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  <span data-ttu-id="e1d47-128">Poniżej przedstawiono dane wyjściowe zwrócone w przypadku 2 (niepowodzenie kolejki głównej usługi).</span><span class="sxs-lookup"><span data-stu-id="e1d47-128">The following is the output returned for case 2 (primary service queue failure).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="e1d47-129">Można konfigurować za pomocą kodu lub pliku App.config</span><span class="sxs-lookup"><span data-stu-id="e1d47-129">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="e1d47-130">Jest skonfigurowany do używania pliku App.config do definiowania zachowania routera dostarczany próbki.</span><span class="sxs-lookup"><span data-stu-id="e1d47-130">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="e1d47-131">Można również zmienić nazwę pliku RoutingService\App.config na inny tak, aby nie został rozpoznany i zmień wartość `configDriven` w RoutingService\Program.cs do `false` do korzystania z konfiguracji zdefiniowane w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e1d47-131">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and change the value of the `configDriven` field in RoutingService\Program.cs to `false` to use the configuration defined in the code.</span></span> <span data-ttu-id="e1d47-132">Każda z tych metod powoduje takie samo zachowanie z routera.</span><span class="sxs-lookup"><span data-stu-id="e1d47-132">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="e1d47-133">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="e1d47-133">Scenario</span></span>  
 <span data-ttu-id="e1d47-134">W przykładzie pokazano, usługa routingu może obsłużyć zaawansowane możliwości obsługi komunikatów, takie jak transakcji i kontekstu odbierania i czy mogą wykorzystywać te możliwości w ramach poprawnie obsługiwać scenariusze błędu.</span><span class="sxs-lookup"><span data-stu-id="e1d47-134">This sample demonstrates that the routing service can handle advanced messaging capabilities, such as transactions and receive context, and that it can utilize these capabilities as a part of correctly handling error scenarios.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="e1d47-135">Scenariusz rzeczywistych</span><span class="sxs-lookup"><span data-stu-id="e1d47-135">Real World Scenario</span></span>  
 <span data-ttu-id="e1d47-136">Contoso chce korzystać z transakcyjnego odbiera za pośrednictwem usługi routingu, aby upewnić się, że wszystkie niezbędne usługi otrzymywanie informacji, nawet w przypadku błędów.</span><span class="sxs-lookup"><span data-stu-id="e1d47-136">Contoso wants to utilize transactional receives through the routing service to ensure that all necessary services receive information even during error conditions.</span></span> <span data-ttu-id="e1d47-137">Ponadto chciałby, błędów, które mają być obsługiwane poprawnie i automatycznie i błędów należy podać w przypadku czy wiadomość dostarczona nawet, gdy jest wykorzystywany logiki obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="e1d47-137">Furthermore, they would like errors to be handled correctly and automatically and failures to be reported in the case that a message is undeliverable even when error handling logic is utilized.</span></span> <span data-ttu-id="e1d47-138">W tym celu skonfigurowano usługę routingu, aby przełączyć się do określonych punktów końcowych, zgodnie z oczekiwaniami i usługa routingu obsługuje sytuacjach błędu w tym tworzenie, uzupełniania i wycofywania/Przerywanie transakcji/odebrać kontekstów jako niezbędne.</span><span class="sxs-lookup"><span data-stu-id="e1d47-138">For this purpose, they configure the routing service to fail over to specific endpoints as expected and the routing service handles the error situations, which includes the creation, completion, and rollback/aborting of transactions/receive contexts as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d47-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1d47-139">See Also</span></span>  
 [<span data-ttu-id="e1d47-140">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="e1d47-140">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
