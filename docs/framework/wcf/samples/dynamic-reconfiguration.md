---
title: Dynamiczna ponowna konfiguracja
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbf286891211da0e35274ff59f3bee69ebf3c9bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="dynamic-reconfiguration"></a><span data-ttu-id="1afc6-102">Dynamiczna ponowna konfiguracja</span><span class="sxs-lookup"><span data-stu-id="1afc6-102">Dynamic Reconfiguration</span></span>
<span data-ttu-id="1afc6-103">W przykładzie pokazano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="1afc6-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="1afc6-104">Usługa routingu jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składnik, który ułatwia obejmują routerem na podstawie zawartości w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1afc6-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="1afc6-105">W tym przykładzie dostosowuje standardowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] próbki Kalkulator do komunikowania się przy użyciu usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="1afc6-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator Sample to communicate using the routing service.</span></span> <span data-ttu-id="1afc6-106">W tym przykładzie pokazano, jak usługa routingu można dynamicznie tak skonfigurować, w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1afc6-106">This sample shows how the routing service can be dynamically reconfigured during runtime.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1afc6-107">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1afc6-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1afc6-108">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="1afc6-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1afc6-109">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="1afc6-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1afc6-110">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1afc6-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a><span data-ttu-id="1afc6-111">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="1afc6-111">Sample Details</span></span>  
 <span data-ttu-id="1afc6-112">Można dynamicznie zmieniać swoją usługę routingu w czasie wykonywania, w tym przykładzie generowane czasomierza co pięć sekund, która tworzy nowy <xref:System.ServiceModel.Routing.RoutingConfiguration> obiektu i stosuje je.</span><span class="sxs-lookup"><span data-stu-id="1afc6-112">To dynamically reconfigure the routing service during runtime, this sample fires a timer every five seconds that creates a new <xref:System.ServiceModel.Routing.RoutingConfiguration> object and applies it.</span></span> <span data-ttu-id="1afc6-113">Ta konfiguracja odwołuje się do regularnych punktu końcowego Kalkulator lub punkt końcowy Kalkulator zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="1afc6-113">This configuration references either the regular Calculator endpoint or the Rounding Calculator endpoint.</span></span> <span data-ttu-id="1afc6-114">Aplikacja kliencka Kalkulator ma jego komunikaty zwracane z jednej usługi lub inne, w zależności od tego, które z nich usługi routingu skonfigurowano do trasy, w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="1afc6-114">The Calculator Client application has its messages returned from one service or the other, depending on which one the routing service is configured to route to at that time.</span></span>  
  
 <span data-ttu-id="1afc6-115">Usługa routingu capabilitiy dynamicznej zmiany konfiguracji przy użyciu niestandardowych zachowanie jest używany.</span><span class="sxs-lookup"><span data-stu-id="1afc6-115">The routing service’s capabilitiy for dynamic reconfiguration through a custom behavior is used.</span></span> <span data-ttu-id="1afc6-116">To zachowanie niestandardowych dołącza rozszerzenie usługi zawiera proste wątku czasomierza generowane co pięć sekund, co powoduje wywołanie zwrotne do `UpdateRules` metody.</span><span class="sxs-lookup"><span data-stu-id="1afc6-116">This custom behavior attaches a service extension, which contains a simple thread timer that fires every five seconds, which results in a callback to the `UpdateRules` method.</span></span> <span data-ttu-id="1afc6-117">To wywołanie zwrotne tworzy i stosuje nową konfigurację routingu.</span><span class="sxs-lookup"><span data-stu-id="1afc6-117">This callback creates and applies the new routing configuration.</span></span> <span data-ttu-id="1afc6-118">We wdrożeniu rzeczywiste tego wywołania zwrotnego prawdopodobnie będzie wykonywać wyniku innego typu zdarzeń, takich jak powiadomienia zdarzenie SQL lub anonsu protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="1afc6-118">In an actual deployment, this callback would likely be accomplished as a result of some other type of event, such as a SQL-Event notification, or a WS-Discovery announcement.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1afc6-119">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="1afc6-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="1afc6-120">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz DynamicReconfiguration.sln.</span><span class="sxs-lookup"><span data-stu-id="1afc6-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open DynamicReconfiguration.sln.</span></span>  
  
2.  <span data-ttu-id="1afc6-121">Aby otworzyć **Eksploratora rozwiązań**, wybierz pozycję **Eksploratora rozwiązań** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="1afc6-121">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="1afc6-122">Naciśnij klawisz **F5** lub **CTRL + SHIFT + B** w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1afc6-122">Press **F5** or **CTRL+SHIFT+B** in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="1afc6-123">Jeśli chcesz automatyczne uruchamianie niezbędne projektów po naciśnięciu **F5**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1afc6-123">If you would like to auto-launch the necessary projects when you press **F5**, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="1afc6-124">Wybierz **projekt startowy** węźle **wspólne właściwości** w okienku po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="1afc6-124">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="1afc6-125">Wybierz **wiele projektów startowych** przycisk radiowy i ustaw wszystkie projekty, które mają **Start** akcji.</span><span class="sxs-lookup"><span data-stu-id="1afc6-125">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="1afc6-126">W przypadku tworzenia projektu z **CTRL + SHIFT + B**, należy uruchomić następujące aplikacje:</span><span class="sxs-lookup"><span data-stu-id="1afc6-126">If you build the project with **CTRL+SHIFT+B**, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="1afc6-127">Kalkulator klienta (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="1afc6-127">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="1afc6-128">Usługa kalkulatora (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="1afc6-128">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="1afc6-129">Usługa routingu kalkulatora (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="1afc6-129">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="1afc6-130">Obiektu RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="1afc6-130">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="1afc6-131">W oknie konsoli klienta Kalkulator naciśnij klawisz ENTER, aby uruchomić klienta i wywoływanie operacji usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="1afc6-131">In the console window of the Calculator Client, press ENTER to start the client and to call the Calculator service operations.</span></span>  
  
     <span data-ttu-id="1afc6-132">Usługa routingu kieruje komunikaty do Kalkulatora zaokrąglania i regularnego Kalkulator również jako routingu zmiany konfiguracji dynamicznie co pięć sekund.</span><span class="sxs-lookup"><span data-stu-id="1afc6-132">The routing service routes messages to the Rounding Calculator and to the regular Calculator alternately as the routing configuration changes dynamically every five seconds.</span></span> <span data-ttu-id="1afc6-133">W zależności od tego, który punkt końcowy, usługa routingu jest skonfigurowany do wysyłania komunikatów do istnieją różne wyniki w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="1afc6-133">Depending on which endpoint the routing service is configured to send messages to there are different outputs in the client console window.</span></span>  
  
5.  <span data-ttu-id="1afc6-134">Kontynuuj, naciskając klawisz ENTER w więcej niż pięciu sekund i Sprawdź zmiany wyników z usługi.</span><span class="sxs-lookup"><span data-stu-id="1afc6-134">Continue pressing ENTER repeatedly over more than five seconds and observe the change in the results from the service.</span></span>  
  
    1.  <span data-ttu-id="1afc6-135">Poniżej przedstawiono dane wyjściowe zwracane, jeśli Usługa routera jest skonfigurowana do przesyłania wiadomości z usługą Kalkulator zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="1afc6-135">The following is the output returned if the Router Service is configured to route messages to the Rounding Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="1afc6-136">Poniżej przedstawiono dane wyjściowe zwracane, jeśli skonfigurowano usługę routingu do wyznaczania tras wiadomościom regularne usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="1afc6-136">The following is the output returned if the routing service is configured to route messages to the regular Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  <span data-ttu-id="1afc6-137">Kalkulator usługi oraz zaokrąglania Kalkulator również wydrukować dziennik operacji wywoływane w celu ich odpowiednich konsoli systemu windows.</span><span class="sxs-lookup"><span data-stu-id="1afc6-137">The Calculator Service and the Rounding Calculator Service also print out a log of the operations invoked to their respective console windows.</span></span>  
  
7.  <span data-ttu-id="1afc6-138">W oknie konsoli klienta wpisz "Zamknij", a następnie naciśnij klawisz ENTER, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="1afc6-138">In the client console window, type "quit" and press ENTER to exit.</span></span>  
  
8.  <span data-ttu-id="1afc6-139">Naciśnij klawisz ENTER w oknach konsoli usług zakończenie usług.</span><span class="sxs-lookup"><span data-stu-id="1afc6-139">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="1afc6-140">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="1afc6-140">Scenario</span></span>  
 <span data-ttu-id="1afc6-141">W tym przykładzie przedstawiono router działająca jako router na podstawie zawartości stosowanie wielu typów lub implementacji usług są dostępne za pośrednictwem jeden punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="1afc6-141">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="1afc6-142">Scenariusz rzeczywistych</span><span class="sxs-lookup"><span data-stu-id="1afc6-142">Real World Scenario</span></span>  
 <span data-ttu-id="1afc6-143">Firma Contoso chce wszystkie ich usługi do udostępnienia tylko jeden punkt końcowy publicznie za pośrednictwem której zapewniają dostęp do wielu różnych typów usług wirtualizacji.</span><span class="sxs-lookup"><span data-stu-id="1afc6-143">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="1afc6-144">W takim przypadku wykorzystania usługi routingu na podstawie zawartości możliwości routingu ustalenie wysyłania żądań przychodzących.</span><span class="sxs-lookup"><span data-stu-id="1afc6-144">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1afc6-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1afc6-145">See Also</span></span>  
 [<span data-ttu-id="1afc6-146">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="1afc6-146">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
