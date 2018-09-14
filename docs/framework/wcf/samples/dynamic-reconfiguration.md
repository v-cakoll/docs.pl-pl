---
title: Dynamiczna ponowna konfiguracja
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: a147a1d6cf61001832661376363ecc850ecad309
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45508210"
---
# <a name="dynamic-reconfiguration"></a><span data-ttu-id="890f9-102">Dynamiczna ponowna konfiguracja</span><span class="sxs-lookup"><span data-stu-id="890f9-102">Dynamic Reconfiguration</span></span>
<span data-ttu-id="890f9-103">Niniejszy przykład pokazuje usługi routingu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="890f9-103">This sample demonstrates the Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="890f9-104">Usługa routingu jest składnikiem usługi WCF, który ułatwia to dołączenie routerem na podstawie zawartości do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="890f9-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="890f9-105">W tym przykładzie dostosowuje się standardowa przykładowe Kalkulator WCF do komunikowania się za pomocą usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="890f9-105">This sample adapts the standard WCF Calculator Sample to communicate using the routing service.</span></span> <span data-ttu-id="890f9-106">Niniejszy przykład pokazuje, jak usługa routingu można dynamicznie tak skonfigurować, podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="890f9-106">This sample shows how the routing service can be dynamically reconfigured during runtime.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="890f9-107">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="890f9-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="890f9-108">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="890f9-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="890f9-109">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="890f9-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="890f9-110">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="890f9-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a><span data-ttu-id="890f9-111">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="890f9-111">Sample Details</span></span>  
 <span data-ttu-id="890f9-112">Można dynamicznie zmieniać swoją usługą routingu w czasie wykonywania, w tym przykładzie uruchamia czasomierz co pięć sekund, która tworzy nową <xref:System.ServiceModel.Routing.RoutingConfiguration> obiektu i stosuje je.</span><span class="sxs-lookup"><span data-stu-id="890f9-112">To dynamically reconfigure the routing service during runtime, this sample fires a timer every five seconds that creates a new <xref:System.ServiceModel.Routing.RoutingConfiguration> object and applies it.</span></span> <span data-ttu-id="890f9-113">Ta konfiguracja odwołuje się standardowym punktem końcowym kalkulatora lub punkt końcowy Kalkulator zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="890f9-113">This configuration references either the regular Calculator endpoint or the Rounding Calculator endpoint.</span></span> <span data-ttu-id="890f9-114">Aplikacja kliencka Kalkulator ma swoje wiadomości zwrócony z jednej usługi lub innych, w zależności od tego, co jest skonfigurowana usługa routingu w przypadku kierowania do w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="890f9-114">The Calculator Client application has its messages returned from one service or the other, depending on which one the routing service is configured to route to at that time.</span></span>  
  
 <span data-ttu-id="890f9-115">Usługa routingu capabilitiy dla dynamiczna ponowna konfiguracja poprzez niestandardowe zachowanie jest używany.</span><span class="sxs-lookup"><span data-stu-id="890f9-115">The routing service’s capabilitiy for dynamic reconfiguration through a custom behavior is used.</span></span> <span data-ttu-id="890f9-116">To zachowanie niestandardowe dołącza rozszerzenie usługi, który zawiera proste wątku czasomierz, który jest uruchamiany co pięć sekund, co powoduje wywołanie zwrotne w celu `UpdateRules` metody.</span><span class="sxs-lookup"><span data-stu-id="890f9-116">This custom behavior attaches a service extension, which contains a simple thread timer that fires every five seconds, which results in a callback to the `UpdateRules` method.</span></span> <span data-ttu-id="890f9-117">To wywołanie zwrotne tworzy i stosuje nową konfigurację routingu.</span><span class="sxs-lookup"><span data-stu-id="890f9-117">This callback creates and applies the new routing configuration.</span></span> <span data-ttu-id="890f9-118">W rzeczywiste wdrożenie to wywołanie zwrotne prawdopodobnie będzie realizowane w wyniku innego typu zdarzenia, takiego jak powiadomienie zdarzenie SQL lub anonsu protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="890f9-118">In an actual deployment, this callback would likely be accomplished as a result of some other type of event, such as a SQL-Event notification, or a WS-Discovery announcement.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="890f9-119">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="890f9-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="890f9-120">Za pomocą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz DynamicReconfiguration.sln.</span><span class="sxs-lookup"><span data-stu-id="890f9-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open DynamicReconfiguration.sln.</span></span>  
  
2.  <span data-ttu-id="890f9-121">Aby otworzyć **Eksploratora rozwiązań**, wybierz opcję **Eksploratora rozwiązań** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="890f9-121">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="890f9-122">Naciśnij klawisz **F5** lub **CTRL + SHIFT + B** w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="890f9-122">Press **F5** or **CTRL+SHIFT+B** in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="890f9-123">Jeśli chcesz automatycznie uruchomić projektów konieczne po naciśnięciu klawisza **F5**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="890f9-123">If you would like to auto-launch the necessary projects when you press **F5**, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="890f9-124">Wybierz **projekt startowy** węźle **wspólne właściwości** w okienku po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="890f9-124">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="890f9-125">Wybierz **wiele projektów startowych** przycisk radiowy, a następnie ustaw wszystkie projekty, które mają **Start** akcji.</span><span class="sxs-lookup"><span data-stu-id="890f9-125">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="890f9-126">Jeśli tworzysz projekt za pomocą **CTRL + SHIFT + B**, należy uruchomić następujące aplikacje:</span><span class="sxs-lookup"><span data-stu-id="890f9-126">If you build the project with **CTRL+SHIFT+B**, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="890f9-127">Kalkulator klienta (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="890f9-127">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="890f9-128">Kalkulator usługi (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="890f9-128">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="890f9-129">Usługa routingu Kalkulator (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="890f9-129">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="890f9-130">RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="890f9-130">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="890f9-131">W oknie konsoli klienta Kalkulator naciśnij klawisz ENTER, aby uruchomić klienta i wywoływanie operacji usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="890f9-131">In the console window of the Calculator Client, press ENTER to start the client and to call the Calculator service operations.</span></span>  
  
     <span data-ttu-id="890f9-132">Usługa routingu kieruje komunikaty do Kalkulatora zaokrąglania i kalkulatora regularne też jako zmiany konfiguracji routingu dynamicznie co pięć sekund.</span><span class="sxs-lookup"><span data-stu-id="890f9-132">The routing service routes messages to the Rounding Calculator and to the regular Calculator alternately as the routing configuration changes dynamically every five seconds.</span></span> <span data-ttu-id="890f9-133">W zależności od punktu końcowego, które usługa routingu jest skonfigurowana do wysyłania komunikatów do istnieją różne wyniki w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="890f9-133">Depending on which endpoint the routing service is configured to send messages to there are different outputs in the client console window.</span></span>  
  
5.  <span data-ttu-id="890f9-134">Nadal, naciskając klawisz ENTER w więcej niż pięć sekund, a następnie obserwować zmiany w wynikach z usługi.</span><span class="sxs-lookup"><span data-stu-id="890f9-134">Continue pressing ENTER repeatedly over more than five seconds and observe the change in the results from the service.</span></span>  
  
    1.  <span data-ttu-id="890f9-135">Poniżej przedstawiono, że dane wyjściowe zwrócone, jeśli Usługa routera jest skonfigurowana do przesyłania wiadomości w usłudze zaokrąglania Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="890f9-135">The following is the output returned if the Router Service is configured to route messages to the Rounding Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="890f9-136">Poniżej przedstawiono, że dane wyjściowe zwrócone, jeśli usługa routingu jest skonfigurowana do przesyłania wiadomości w usłudze kalkulatora regularne.</span><span class="sxs-lookup"><span data-stu-id="890f9-136">The following is the output returned if the routing service is configured to route messages to the regular Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  <span data-ttu-id="890f9-137">Kalkulator usługi i zaokrąglania Kalkulator również wydrukować dziennika operacji wywoływane w celu ich odpowiedniej konsoli systemu windows.</span><span class="sxs-lookup"><span data-stu-id="890f9-137">The Calculator Service and the Rounding Calculator Service also print out a log of the operations invoked to their respective console windows.</span></span>  
  
7.  <span data-ttu-id="890f9-138">W oknie konsoli klienta wpisz "Zamknij", a następnie naciśnij klawisz ENTER, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="890f9-138">In the client console window, type "quit" and press ENTER to exit.</span></span>  
  
8.  <span data-ttu-id="890f9-139">Naciśnij klawisz ENTER w oknach konsoli usług do zakończenia usługi.</span><span class="sxs-lookup"><span data-stu-id="890f9-139">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="890f9-140">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="890f9-140">Scenario</span></span>  
 <span data-ttu-id="890f9-141">Niniejszy przykład demonstruje routerze działającego jako router opartego na zawartości, dzięki czemu wielu typów lub implementacji usług są dostępne za pośrednictwem punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="890f9-141">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="890f9-142">Scenariusz rzeczywistych</span><span class="sxs-lookup"><span data-stu-id="890f9-142">Real World Scenario</span></span>  
 <span data-ttu-id="890f9-143">Firma Contoso chce wszystkich swoich usług, aby uwidocznić tylko jeden punkt końcowy publicznie za pomocą którego oferują dostęp do wielu różnych typów usług wirtualizacji.</span><span class="sxs-lookup"><span data-stu-id="890f9-143">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="890f9-144">W tym przypadku skorzystają z usługą routingu opartego na zawartości możliwości routingu w celu określenia, gdzie mają być wysyłane żądania przychodzące.</span><span class="sxs-lookup"><span data-stu-id="890f9-144">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="890f9-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="890f9-145">See Also</span></span>  
 [<span data-ttu-id="890f9-146">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="890f9-146">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
