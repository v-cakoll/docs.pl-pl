---
title: Program Hello World z usługą routingu
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: b84d4dc17db5bb422ba86fbab9c25d3348be7488
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120162"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="b1bfc-102">Program Hello World z usługą routingu</span><span class="sxs-lookup"><span data-stu-id="b1bfc-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="b1bfc-103">Niniejszy przykład pokazuje usługi routingu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b1bfc-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="b1bfc-104">Usługa routingu jest składnikiem usługi WCF, który ułatwia to dołączenie routerem na podstawie zawartości do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="b1bfc-105">W tym przykładzie dostosowuje się standardowej próbki Kalkulator WCF do komunikowania się za pomocą usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="b1bfc-106">W tym przykładzie klient Kalkulator jest skonfigurowany do wysyłania wiadomości do punktu końcowego uwidocznionego przez router.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="b1bfc-107">Usługa routingu jest skonfigurowana do akceptowania wszystkie komunikaty wysyłane do niej i przekazują je do punktu końcowego, który odnosi się do usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="b1bfc-108">Ten sposób wiadomości wysłanych z klienta są odebrany przez router i ponownie kierowane do rzeczywistej usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="b1bfc-109">Komunikaty z Kalkulatora usługi są wysyłane do routera, który z kolei przekazuje je do klienta kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="b1bfc-110">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="b1bfc-110">To use this sample</span></span>

1.  <span data-ttu-id="b1bfc-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2.  <span data-ttu-id="b1bfc-112">Naciśnij klawisz F5 lub CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-112">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="b1bfc-113">Jeśli użytkownik naciśnie klawisz F5, rozpoczyna się automatycznie klienta Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="b1bfc-114">Jeśli użytkownik naciśnie klawisz CTRL + SHIFT + B (Kompilacja), należy uruchomić następujące aplikacje samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1.  <span data-ttu-id="b1bfc-115">Kalkulator klienta (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="b1bfc-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2.  <span data-ttu-id="b1bfc-116">Kalkulator usługi (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="b1bfc-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3.  <span data-ttu-id="b1bfc-117">Usługa routingu (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="b1bfc-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3.  <span data-ttu-id="b1bfc-118">Naciśnij klawisz ENTER, aby uruchomić klienta.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-118">Press ENTER to start the client.</span></span>

     <span data-ttu-id="b1bfc-119">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b1bfc-119">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="b1bfc-120">Można konfigurować za pomocą kodu lub pliku App.Config</span><span class="sxs-lookup"><span data-stu-id="b1bfc-120">Configurable via Code or App.Config</span></span>
 <span data-ttu-id="b1bfc-121">Dostarczany próbki, skonfigurowany do używania pliku App.config do definiowania zachowania routera.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-121">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="b1bfc-122">Można również zmienić nazwę pliku App.config się czymś innym, tak aby nie został rozpoznany i usuń znaczniki komentarza wywołania metody, które ma ConfigureRouterViaCode().</span><span class="sxs-lookup"><span data-stu-id="b1bfc-122">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="b1bfc-123">Każda z tych metod powoduje takie samo zachowanie z routera.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-123">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="b1bfc-124">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="b1bfc-124">Scenario</span></span>
 <span data-ttu-id="b1bfc-125">Niniejszy przykład pokazuje routera będącego pompa podstawowe wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-125">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="b1bfc-126">Usługa routingu działa jako węzeł przezroczystym serwerem proxy skonfigurowane do przekazywania wiadomości bezpośrednio do wstępnie skonfigurowanego zestawu docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-126">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="b1bfc-127">Scenariusz rzeczywistych</span><span class="sxs-lookup"><span data-stu-id="b1bfc-127">Real World Scenario</span></span>
 <span data-ttu-id="b1bfc-128">Firma Contoso chce zwiększyć elastyczność, który ma w nazewnictwa, adresowania, konfiguracji i zabezpieczeń swoich usług.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-128">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="b1bfc-129">Aby to zrobić, mogą umieścić pompy komunikatów podstawowe przed ich usługom, aby pełnić rolę publiczny punkt końcowy umożliwiający dostęp do Internetu.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-129">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="b1bfc-130">Umożliwi to umieszczenie dodatkową ochronę przed ich rzeczywiste usługi i ułatwić do zaimplementowania Skalowanie rozwiązań lub przechowywanie wersji usługi w późniejszym terminie.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-130">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="b1bfc-131">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-131">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b1bfc-132">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b1bfc-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b1bfc-133">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b1bfc-134">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b1bfc-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="b1bfc-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1bfc-135">See also</span></span>

- [<span data-ttu-id="b1bfc-136">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="b1bfc-136">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
