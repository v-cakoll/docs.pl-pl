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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7771b9a4d5a6c0fb4349894afd348e9dece27fd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-error-handling"></a><span data-ttu-id="14850-102">Zaawansowana obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="14850-102">Advanced Error Handling</span></span>
<span data-ttu-id="14850-103">W przykładzie pokazano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="14850-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="14850-104">Usługa routingu jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składnik, który ułatwia obejmują routerem na podstawie zawartości w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="14850-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="14850-105">W tym przykładzie pokazano, jak usługa routingu inteligentnie odzyskiwania z błędów przy użyciu transakcji i innych bardziej złożonych pojęć obsługi wiadomości, takie jak multiemisji.</span><span class="sxs-lookup"><span data-stu-id="14850-105">This sample shows how the routing service intelligently recovers from errors, using transactions and other more complex messaging concepts such as multicasting.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="14850-106">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="14850-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="14850-107">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="14850-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="14850-108">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="14850-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="14850-109">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="14850-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a><span data-ttu-id="14850-110">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="14850-110">Sample Details</span></span>  
 <span data-ttu-id="14850-111">W tym przykładzie usługi routingu skonfigurowano odczytywać komunikaty z kolejki usługi MSMQ i multiemisji tej wiadomości do dwóch list z kolejki.</span><span class="sxs-lookup"><span data-stu-id="14850-111">In this sample, the routing service is configured to read a message from an MSMQ queue and multicast this message to two lists of queues.</span></span> <span data-ttu-id="14850-112">Jedna lista służy do kolejek usługi service i inny służy do rejestrowania kolejek.</span><span class="sxs-lookup"><span data-stu-id="14850-112">One list is used for service queues and another is used for logging queues.</span></span>  
  
 <span data-ttu-id="14850-113">Ponieważ domyślnie MSMQ powiązanie usługi routingu skonfigurowano Użyj obsługuje transakcje, usługa routingu upewnia się, że wiadomość jest transakcyjna i odebranych przez co najmniej jedna kolejka na wszystkich listach przed zgłoszeniem do (kolejki ruchu przychodzącego `InQ`), że komunikat został pomyślnie skierowany.</span><span class="sxs-lookup"><span data-stu-id="14850-113">Because, by default, the MSMQ binding that the routing service is configured to use supports the use of transactions, the routing service makes sure that the message is transactional and received by at least one queue in each list before reporting to the Inbound Queue (`InQ`) that the message was successfully routed.</span></span> <span data-ttu-id="14850-114">W związku z tym w przypadku, gdy oba kolejek usługi lub oba kolejek rejestrowania są niedostępne, usługa routingu zgłasza, że nie być kierowane wiadomości i kolejki przychodzącej powinien podjąć inną akcję.</span><span class="sxs-lookup"><span data-stu-id="14850-114">Thus, in the case where both of the service queues or both of the logging queues are unavailable, the routing service reports that the message could not be routed and the inbound queue should take some action.</span></span> <span data-ttu-id="14850-115">Ta akcja składa się z przenoszenie wiadomości do kolejki utraconych wiadomości systemu.</span><span class="sxs-lookup"><span data-stu-id="14850-115">This action consists of moving the message to the system dead letter queue.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="14850-116">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="14850-116">To use this sample</span></span>  
  
1.  > [!IMPORTANT]
    >  <span data-ttu-id="14850-117">Zainstaluj usługę MSMQ przed uruchomieniem tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="14850-117">Install MSMQ before running this sample.</span></span> <span data-ttu-id="14850-118">Jeśli usługa MSMQ nie jest zainstalowana, zwracany jest komunikat o wyjątku, podczas uruchamiania próbki.</span><span class="sxs-lookup"><span data-stu-id="14850-118">If MSMQ is not installed, an exception message is returned when running the sample.</span></span> <span data-ttu-id="14850-119">Instrukcje dotyczące instalowania usługi MSMQ można znaleźć w folderze [usługi kolejkowania komunikatów instalowanie (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).</span><span class="sxs-lookup"><span data-stu-id="14850-119">Instructions for installing MSMQ can be found at [Installing Message Queuing (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).</span></span>  
  
     <span data-ttu-id="14850-120">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz AdvancedErrorHandling.sln.</span><span class="sxs-lookup"><span data-stu-id="14850-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedErrorHandling.sln.</span></span>  
  
2.  <span data-ttu-id="14850-121">Naciśnij klawisz **F5** lub **CTRL + SHIFT + B** w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14850-121">Press **F5** or **CTRL+SHIFT+B** in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="14850-122">W przypadku tworzenia aplikacji z klawiszy CTRL + SHIFT + B, należy uruchomić aplikację w. / RoutingService/bin/debug/RoutingService.exe.</span><span class="sxs-lookup"><span data-stu-id="14850-122">If you build the application with CTRL+SHIFT+B, you must start the application at ./RoutingService/bin/debug/RoutingService.exe.</span></span>  
  
3.  <span data-ttu-id="14850-123">W oknie konsoli naciśnij klawisz ENTER, aby uruchomić klienta.</span><span class="sxs-lookup"><span data-stu-id="14850-123">In the console window, press ENTER to start the client.</span></span>  
  
4.  <span data-ttu-id="14850-124">Różne Statystyka kolejki dla każdego przypadku zwracane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="14850-124">The client returns different statistics about the queues for each case.</span></span>  
  
    1.  <span data-ttu-id="14850-125">Poniżej przedstawiono dane wyjściowe zwrócone w przypadku 1 (nie błędów).</span><span class="sxs-lookup"><span data-stu-id="14850-125">The following is the output returned for case 1 (no failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  <span data-ttu-id="14850-126">Poniżej przedstawiono dane wyjściowe zwrócone w przypadku 3 (podstawowej usługi i rejestrowania błędów kolejki).</span><span class="sxs-lookup"><span data-stu-id="14850-126">The following is the output returned for case 3 (primary service and logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  <span data-ttu-id="14850-127">Poniżej przedstawiono dane wyjściowe zwrócone w przypadku 4 (Rejestrowanie podstawowego i zapasowego kolejki błędy i kolejki głównej usługi).</span><span class="sxs-lookup"><span data-stu-id="14850-127">The following is the output returned for case 4 (primary service queue and primary and backup logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  <span data-ttu-id="14850-128">Poniżej przedstawiono dane wyjściowe zwrócone w przypadku 2 (niepowodzenie kolejki głównej usługi).</span><span class="sxs-lookup"><span data-stu-id="14850-128">The following is the output returned for case 2 (primary service queue failure).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="14850-129">Można konfigurować za pomocą kodu lub pliku App.config</span><span class="sxs-lookup"><span data-stu-id="14850-129">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="14850-130">Jest skonfigurowany do używania pliku App.config do definiowania zachowania routera dostarczany próbki.</span><span class="sxs-lookup"><span data-stu-id="14850-130">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="14850-131">Można również zmienić nazwę pliku RoutingService\App.config na inny tak, aby nie został rozpoznany i zmień wartość `configDriven` w RoutingService\Program.cs do `false` do korzystania z konfiguracji zdefiniowane w kodzie.</span><span class="sxs-lookup"><span data-stu-id="14850-131">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and change the value of the `configDriven` field in RoutingService\Program.cs to `false` to use the configuration defined in the code.</span></span> <span data-ttu-id="14850-132">Każda z tych metod powoduje takie samo zachowanie z routera.</span><span class="sxs-lookup"><span data-stu-id="14850-132">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="14850-133">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="14850-133">Scenario</span></span>  
 <span data-ttu-id="14850-134">W przykładzie pokazano, usługa routingu może obsłużyć zaawansowane możliwości obsługi komunikatów, takie jak transakcji i kontekstu odbierania i czy mogą wykorzystywać te możliwości w ramach poprawnie obsługiwać scenariusze błędu.</span><span class="sxs-lookup"><span data-stu-id="14850-134">This sample demonstrates that the routing service can handle advanced messaging capabilities, such as transactions and receive context, and that it can utilize these capabilities as a part of correctly handling error scenarios.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="14850-135">Scenariusz rzeczywistych</span><span class="sxs-lookup"><span data-stu-id="14850-135">Real World Scenario</span></span>  
 <span data-ttu-id="14850-136">Contoso chce korzystać z transakcyjnego odbiera za pośrednictwem usługi routingu, aby upewnić się, że wszystkie niezbędne usługi otrzymywanie informacji, nawet w przypadku błędów.</span><span class="sxs-lookup"><span data-stu-id="14850-136">Contoso wants to utilize transactional receives through the routing service to ensure that all necessary services receive information even during error conditions.</span></span> <span data-ttu-id="14850-137">Ponadto chciałby, błędów, które mają być obsługiwane poprawnie i automatycznie i błędów należy podać w przypadku czy wiadomość dostarczona nawet, gdy jest wykorzystywany logiki obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="14850-137">Furthermore, they would like errors to be handled correctly and automatically and failures to be reported in the case that a message is undeliverable even when error handling logic is utilized.</span></span> <span data-ttu-id="14850-138">W tym celu skonfigurowano usługę routingu, aby przełączyć się do określonych punktów końcowych, zgodnie z oczekiwaniami i usługa routingu obsługuje sytuacjach błędu w tym tworzenie, uzupełniania i wycofywania/Przerywanie transakcji/odebrać kontekstów jako niezbędne.</span><span class="sxs-lookup"><span data-stu-id="14850-138">For this purpose, they configure the routing service to fail over to specific endpoints as expected and the routing service handles the error situations, which includes the creation, completion, and rollback/aborting of transactions/receive contexts as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14850-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14850-139">See Also</span></span>  
 [<span data-ttu-id="14850-140">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="14850-140">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
