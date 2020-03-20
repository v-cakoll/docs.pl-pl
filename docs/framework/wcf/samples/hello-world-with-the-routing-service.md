---
title: Program Hello World z usługą routingu
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 86a2981e8b861da9d5ccf0a34fe037f3ef419aab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183636"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="2078f-102">Program Hello World z usługą routingu</span><span class="sxs-lookup"><span data-stu-id="2078f-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="2078f-103">W tym przykładzie przedstawiono usługę routingu Programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2078f-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="2078f-104">Usługa routingu jest składnikiem WCF, który ułatwia dołączanie routera opartego na zawartości do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2078f-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="2078f-105">Ten przykład dostosowuje standardowy przykład kalkulatora WCF do komunikowania się za pomocą usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="2078f-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="2078f-106">W tym przykładzie klient kalkulatora jest skonfigurowany do wysyłania wiadomości do punktu końcowego udostępnianego przez router.</span><span class="sxs-lookup"><span data-stu-id="2078f-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="2078f-107">Usługa routingu jest skonfigurowana do akceptowania wszystkich wiadomości wysłanych do niej i przekazywania ich do punktu końcowego odpowiadającego usłudze Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="2078f-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="2078f-108">W ten sposób wiadomości wysyłane od klienta są odbierane przez router i ponownie kierowane do rzeczywistej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="2078f-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="2078f-109">Wiadomości z usługi Kalkulator są wysyłane z powrotem do routera, co z kolei przekazuje je z powrotem do klienta kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="2078f-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="2078f-110">Aby użyć tej próbki</span><span class="sxs-lookup"><span data-stu-id="2078f-110">To use this sample</span></span>

1. <span data-ttu-id="2078f-111">Za pomocą programu Visual Studio 2012, otwórz HelloRoutingService.sln.</span><span class="sxs-lookup"><span data-stu-id="2078f-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="2078f-112">Naciśnij klawisze F5 lub CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="2078f-112">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2078f-113">Po naciśnięciu klawisza F5 klient kalkulatora zostanie automatycznie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="2078f-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="2078f-114">Jeśli naciśniesz klawisze CTRL+SHIFT+B (kompilacja), należy rozpocząć obserwowanie aplikacji samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="2078f-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1. <span data-ttu-id="2078f-115">Klient kalkulatora (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="2078f-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2. <span data-ttu-id="2078f-116">Usługa kalkulatora (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="2078f-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3. <span data-ttu-id="2078f-117">Usługa routingu (./Usługa routingu/bin/usługa routingu.exe)</span><span class="sxs-lookup"><span data-stu-id="2078f-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="2078f-118">Naciśnij klawisz ENTER, aby uruchomić klienta.</span><span class="sxs-lookup"><span data-stu-id="2078f-118">Press ENTER to start the client.</span></span>

     <span data-ttu-id="2078f-119">Powinny zostać wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="2078f-119">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="2078f-120">Konfigurowalne za pomocą kodu lub app.config</span><span class="sxs-lookup"><span data-stu-id="2078f-120">Configurable via Code or App.Config</span></span>
 <span data-ttu-id="2078f-121">Przykładowe statki skonfigurowane do używania pliku App.config do definiowania zachowania routera.</span><span class="sxs-lookup"><span data-stu-id="2078f-121">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="2078f-122">Można również zmienić nazwę pliku App.config na coś innego, tak aby nie został rozpoznany i odkomentować wywołanie metody ConfigureRouterViaCode().</span><span class="sxs-lookup"><span data-stu-id="2078f-122">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="2078f-123">Każda z tych metod powoduje to samo zachowanie z routera.</span><span class="sxs-lookup"><span data-stu-id="2078f-123">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="2078f-124">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="2078f-124">Scenario</span></span>
 <span data-ttu-id="2078f-125">W tym przykładzie pokazano, że router działa jako podstawowa pompa wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2078f-125">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="2078f-126">Usługa routingu działa jako przezroczysty węzeł serwera proxy skonfigurowany do przekazywania wiadomości bezpośrednio do wstępnie skonfigurowanego zestawu docelowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="2078f-126">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="2078f-127">Scenariusz realny</span><span class="sxs-lookup"><span data-stu-id="2078f-127">Real World Scenario</span></span>
 <span data-ttu-id="2078f-128">Contoso chce zwiększyć elastyczność, która ma w nazewnictwie, adresowaniu, konfiguracji i bezpieczeństwie swoich usług.</span><span class="sxs-lookup"><span data-stu-id="2078f-128">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="2078f-129">Aby to zrobić, umieszczają podstawową pompę wiadomości przed swoimi usługami, aby działać jako publiczny punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="2078f-129">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="2078f-130">Dzięki temu można umieścić dodatkowe zabezpieczenia przed ich rzeczywistych usług i ułatwić implementowanie skalowane rozwiązania w poziomie lub wersji usługi w późniejszym terminie.</span><span class="sxs-lookup"><span data-stu-id="2078f-130">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2078f-131">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2078f-131">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2078f-132">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="2078f-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2078f-133">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="2078f-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2078f-134">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2078f-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="2078f-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2078f-135">See also</span></span>

- <span data-ttu-id="2078f-136">[AppFabric Hosting i trwałość przykłady](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2078f-136">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
