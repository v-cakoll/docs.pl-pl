---
title: Program Hello World z usługą routingu
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 881636097cf342de09164804c6df6acfbcd97c45
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810255"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="dab47-102">Program Hello World z usługą routingu</span><span class="sxs-lookup"><span data-stu-id="dab47-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="dab47-103">W tym przykładzie pokazano, usługa routingu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dab47-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="dab47-104">Usługa routingu jest składnikiem usługi WCF, który ułatwia obejmują routerem na podstawie zawartości w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dab47-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="dab47-105">W tym przykładzie dostosowuje standardowej próbki Kalkulator WCF do komunikowania się przy użyciu usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="dab47-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="dab47-106">W tym przykładzie klient Kalkulator jest skonfigurowany do wysyłania komunikatów do punktu końcowego udostępnianych przez router.</span><span class="sxs-lookup"><span data-stu-id="dab47-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="dab47-107">Usługa routingu jest skonfigurowany do akceptowania wszystkich wiadomości wysłanych do niego i przekazują je do punktu końcowego, który odpowiada usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="dab47-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="dab47-108">W związku z tym komunikatów wysłanych z klienta są odbierane przez router i skierowane do rzeczywistego usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="dab47-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="dab47-109">Komunikaty z usługi Kalkulator są wysyłane do routera, który z kolei przekazuje je do Kalkulatora klienta.</span><span class="sxs-lookup"><span data-stu-id="dab47-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="dab47-110">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="dab47-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="dab47-111">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz HelloRoutingService.sln.</span><span class="sxs-lookup"><span data-stu-id="dab47-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open HelloRoutingService.sln.</span></span>  
  
2.  <span data-ttu-id="dab47-112">Naciśnij klawisz F5 lub CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="dab47-112">Press F5 or CTRL+SHIFT+B.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dab47-113">Jeśli zostanie naciśnięty klawisz F5, klient Kalkulator jest uruchamiana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="dab47-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="dab47-114">Po naciśnięciu klawiszy CTRL + SHIFT + B (Kompilacja), należy uruchomić następujące aplikacje samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="dab47-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>  
    >   
    >  1.  <span data-ttu-id="dab47-115">Kalkulator klienta (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="dab47-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>  
    > 2.  <span data-ttu-id="dab47-116">Usługa kalkulatora (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="dab47-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>  
    > 3.  <span data-ttu-id="dab47-117">Usługa routingu (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="dab47-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>  
  
3.  <span data-ttu-id="dab47-118">Naciśnij klawisz ENTER, aby uruchomić klienta.</span><span class="sxs-lookup"><span data-stu-id="dab47-118">Press ENTER to start the client.</span></span>  
  
     <span data-ttu-id="dab47-119">Powinny być widoczne następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="dab47-119">You should see the following output:</span></span>  
  
     <span data-ttu-id="dab47-120">Add(100,15.99) = 115.99</span><span class="sxs-lookup"><span data-stu-id="dab47-120">Add(100,15.99) = 115.99</span></span>  
  
     <span data-ttu-id="dab47-121">SUBTRACT(145,76.54) = 68.46</span><span class="sxs-lookup"><span data-stu-id="dab47-121">Subtract(145,76.54) = 68.46</span></span>  
  
     <span data-ttu-id="dab47-122">MULTIPLY(9,81.25) = 731.25</span><span class="sxs-lookup"><span data-stu-id="dab47-122">Multiply(9,81.25) = 731.25</span></span>  
  
     <span data-ttu-id="dab47-123">Divide(22,7) = 3.14285714285714</span><span class="sxs-lookup"><span data-stu-id="dab47-123">Divide(22,7) = 3.14285714285714</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="dab47-124">Można konfigurować za pomocą kodu lub pliku App.Config</span><span class="sxs-lookup"><span data-stu-id="dab47-124">Configurable via Code or App.Config</span></span>  
 <span data-ttu-id="dab47-125">Jest skonfigurowany do używania pliku App.config do definiowania zachowania routera dostarczany próbki.</span><span class="sxs-lookup"><span data-stu-id="dab47-125">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="dab47-126">Można również zmienić nazwę pliku App.config do innego elementu tak, aby nie został rozpoznany i Usuń komentarz wywołanie metody ConfigureRouterViaCode().</span><span class="sxs-lookup"><span data-stu-id="dab47-126">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="dab47-127">Każda z tych metod powoduje takie samo zachowanie z routera.</span><span class="sxs-lookup"><span data-stu-id="dab47-127">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="dab47-128">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="dab47-128">Scenario</span></span>  
 <span data-ttu-id="dab47-129">W przykładzie pokazano router działający jako pompa podstawowe wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dab47-129">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="dab47-130">Usługa routingu działa jako węzeł przezroczystego obiektu pośredniczącego skonfigurowane do przekazywania wiadomości bezpośrednio do zbioru wstępnie skonfigurowane miejsce docelowe punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="dab47-130">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="dab47-131">Scenariusz rzeczywistych</span><span class="sxs-lookup"><span data-stu-id="dab47-131">Real World Scenario</span></span>  
 <span data-ttu-id="dab47-132">Firma Contoso chce zwiększyć elastyczność, który ma w nazewnictwa, adresy, konfiguracji i zabezpieczeń w usługach.</span><span class="sxs-lookup"><span data-stu-id="dab47-132">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="dab47-133">Aby to zrobić, umieść one pompowania podstawowe komunikatów przed ich usług do działania jako publiczny punkt końcowy połączonej.</span><span class="sxs-lookup"><span data-stu-id="dab47-133">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="dab47-134">Pozwala na umieszczenie dodatkowe zabezpieczenia przed ich rzeczywiste usługi i ułatwić do zaimplementowania Skalowanie rozwiązań lub przechowywanie wersji usługi później.</span><span class="sxs-lookup"><span data-stu-id="dab47-134">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dab47-135">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="dab47-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="dab47-136">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="dab47-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dab47-137">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="dab47-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dab47-138">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="dab47-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="dab47-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dab47-139">See Also</span></span>  
 [<span data-ttu-id="dab47-140">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="dab47-140">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
