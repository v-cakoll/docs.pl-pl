---
title: Zaawansowane filtry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 988c41bb691d27e819710bbc2cd48bc1c844e7c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="advanced-filters"></a><span data-ttu-id="982d1-102">Zaawansowane filtry</span><span class="sxs-lookup"><span data-stu-id="982d1-102">Advanced Filters</span></span>
<span data-ttu-id="982d1-103">W przykładzie pokazano [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="982d1-103">This sample demonstrates a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="982d1-104">Usługa routingu jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składnik, który ułatwia obejmują routerem na podstawie zawartości w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="982d1-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="982d1-105">W tym przykładzie dostosowuje standardowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] próbki Kalkulator do komunikowania się przy użyciu usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="982d1-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator sample to communicate using the routing service.</span></span> <span data-ttu-id="982d1-106">W tym przykładzie pokazano sposób definiowania opartej na zawartości logiki routingu przy użyciu filtrów wiadomości i tabele filtr komunikatu.</span><span class="sxs-lookup"><span data-stu-id="982d1-106">This sample shows how to define content-based routing logic through the use of message filters and message filter tables.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="982d1-107">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="982d1-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="982d1-108">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="982d1-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="982d1-109">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="982d1-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="982d1-110">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="982d1-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a><span data-ttu-id="982d1-111">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="982d1-111">Sample Details</span></span>  
 <span data-ttu-id="982d1-112">W poniższej tabeli przedstawiono filtry komunikatów, które są dodawane do tabeli filtru komunikat usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="982d1-112">The following table shows the message filters that are added to the message filter table of the routing service.</span></span>  
  
|<span data-ttu-id="982d1-113">Filtr</span><span class="sxs-lookup"><span data-stu-id="982d1-113">Filter</span></span>|<span data-ttu-id="982d1-114">Reguła</span><span class="sxs-lookup"><span data-stu-id="982d1-114">Rule</span></span>|<span data-ttu-id="982d1-115">Priorytet</span><span class="sxs-lookup"><span data-stu-id="982d1-115">Priority</span></span>|  
|------------|----------|--------------|  
|<span data-ttu-id="982d1-116">Jeśli (ma nagłówka)</span><span class="sxs-lookup"><span data-stu-id="982d1-116">If (has header)</span></span>|<span data-ttu-id="982d1-117">Zaokrąglanie</span><span class="sxs-lookup"><span data-stu-id="982d1-117">Rounding</span></span>|<span data-ttu-id="982d1-118">2</span><span class="sxs-lookup"><span data-stu-id="982d1-118">2</span></span>|  
|<span data-ttu-id="982d1-119">Jeśli (wykazało na Ep2)</span><span class="sxs-lookup"><span data-stu-id="982d1-119">If (showed up on Ep2)</span></span>|<span data-ttu-id="982d1-120">Regularne</span><span class="sxs-lookup"><span data-stu-id="982d1-120">Regular</span></span>|<span data-ttu-id="982d1-121">1</span><span class="sxs-lookup"><span data-stu-id="982d1-121">1</span></span>|  
|<span data-ttu-id="982d1-122">Jeśli (wykazało z 2)</span><span class="sxs-lookup"><span data-stu-id="982d1-122">If (showed up with Address2)</span></span>|<span data-ttu-id="982d1-123">Zaokrąglanie</span><span class="sxs-lookup"><span data-stu-id="982d1-123">Rounding</span></span>|<span data-ttu-id="982d1-124">1</span><span class="sxs-lookup"><span data-stu-id="982d1-124">1</span></span>|  
|<span data-ttu-id="982d1-125">Jeśli (RoundRobin1)</span><span class="sxs-lookup"><span data-stu-id="982d1-125">If (RoundRobin1)</span></span>|<span data-ttu-id="982d1-126">Regularne</span><span class="sxs-lookup"><span data-stu-id="982d1-126">Regular</span></span>|<span data-ttu-id="982d1-127">0</span><span class="sxs-lookup"><span data-stu-id="982d1-127">0</span></span>|  
|<span data-ttu-id="982d1-128">Jeśli (RoundRobin2)</span><span class="sxs-lookup"><span data-stu-id="982d1-128">If (RoundRobin2)</span></span>|<span data-ttu-id="982d1-129">Zaokrąglanie</span><span class="sxs-lookup"><span data-stu-id="982d1-129">Rounding</span></span>|<span data-ttu-id="982d1-130">0</span><span class="sxs-lookup"><span data-stu-id="982d1-130">0</span></span>|  
  
 <span data-ttu-id="982d1-131">Filtry komunikatów i tabele filtr komunikatu można tworzyć i skonfigurowany za pomocą kodu lub w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="982d1-131">The message filters and message filter tables can be created and configured either through code or in the application configuration file.</span></span> <span data-ttu-id="982d1-132">Dla tego przykładu można znaleźć filtry komunikatów i tabele filtru komunikat zdefiniowany przez kod w pliku RoutingService\routing.cs lub zdefiniowane w pliku konfiguracyjnym aplikacji w pliku RoutingService\App.config.</span><span class="sxs-lookup"><span data-stu-id="982d1-132">For this sample, you can find the message filters and message filter tables defined through code in the RoutingService\routing.cs file, or defined in the application configuration file in the RoutingService\App.config file.</span></span> <span data-ttu-id="982d1-133">Następuje opisano sposób tworzenia filtry komunikatów i tabele filtr komunikatu dla tego przykładu za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="982d1-133">The following paragraphs describe how the message filters and message filter tables are created for this sample through code.</span></span>  
  
 <span data-ttu-id="982d1-134">Najpierw <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> szuka nagłówek niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="982d1-134">First, an <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> looks for the custom header.</span></span> <span data-ttu-id="982d1-135">Należy pamiętać, że <xref:System.ServiceModel.WSHttpBinding> powoduje wersja schematu envelope przy użyciu protokołu SOAP 1.2, co instrukcji XPath jest zdefiniowany w celu używania przestrzeni nazw protokołu SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="982d1-135">Note that <xref:System.ServiceModel.WSHttpBinding> results in an envelope version using SOAP 1.2, so the XPath statement is defined to use the SOAP 1.2 namespace.</span></span> <span data-ttu-id="982d1-136">Domyślnego menedżera przestrzeń nazw dla <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s już definiuje prefiksu dla przestrzeni nazw protokołu SOAP 1.2 /s12, którego można użyć.</span><span class="sxs-lookup"><span data-stu-id="982d1-136">The default namespace manager for <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s already defines a prefix for the SOAP 1.2 namespace, /s12, which can be used.</span></span> <span data-ttu-id="982d1-137">Jednak domyślnego menedżera przestrzeni nazw nie ma niestandardowej przestrzeni nazw, do którego klient używa do definiowania rzeczywistej wartości nagłówka, więc musi być zdefiniowana tego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="982d1-137">However, the default namespace manager does not have the custom namespace that the client uses to define the actual header value, so that prefix must be defined.</span></span> <span data-ttu-id="982d1-138">Wiadomości, które zostaną wyświetlone z tym nagłówkiem spełni warunki tego filtru.</span><span class="sxs-lookup"><span data-stu-id="982d1-138">Any message that shows up with this header matches this filter.</span></span>  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 <span data-ttu-id="982d1-139">Drugi filtr <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, który dopasowuje dowolny komunikat, który został odebrany w `calculatorEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="982d1-139">The second filter is an <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, which matches any message that was received on the `calculatorEndpoint`.</span></span> <span data-ttu-id="982d1-140">Nazwa punktu końcowego jest definiowany podczas tworzenia obiektu punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="982d1-140">The endpoint name is defined when a service endpoint object is created.</span></span>  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 <span data-ttu-id="982d1-141">Trzeci filtr jest <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="982d1-141">The third filter is a <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span></span> <span data-ttu-id="982d1-142">To dopasowuje dowolny komunikat, który na punkt końcowy z adresu, który odpowiada prefiks adresu (lub przedniej części) pod warunkiem.</span><span class="sxs-lookup"><span data-stu-id="982d1-142">This matches any message that showed up on an endpoint with an address that matches the address prefix (or the front portion) provided.</span></span> <span data-ttu-id="982d1-143">W tym przykładzie prefiks adresu jest zdefiniowany jako "http://localhost/routingservice/router/rounding/".</span><span class="sxs-lookup"><span data-stu-id="982d1-143">In this example the address prefix is defined as "http://localhost/routingservice/router/rounding/".</span></span> <span data-ttu-id="982d1-144">Oznacza to, że komunikaty przychodzące, które są opisane na "http://localhost/routingservice/router/rounding/ *" równoważona tego filtru.</span><span class="sxs-lookup"><span data-stu-id="982d1-144">This means that any incoming messages that are addressed to "http://localhost/routingservice/router/rounding/*" are matched by this filter.</span></span> <span data-ttu-id="982d1-145">W takim przypadku jest komunikatów wyświetlanych w punkcie końcowym zaokrąglania Kalkulator, której adres "http://localhost/routingservice/router/rounding/calculator".</span><span class="sxs-lookup"><span data-stu-id="982d1-145">In this case, it is messages that show up on the Rounding Calculator endpoint, which has the address of "http://localhost/routingservice/router/rounding/calculator".</span></span>  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 <span data-ttu-id="982d1-146">Ostatnie dwa filtry komunikatów są niestandardowe <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span><span class="sxs-lookup"><span data-stu-id="982d1-146">The last two message filters are custom <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span></span> <span data-ttu-id="982d1-147">W tym przykładzie jest używany filtr komunikatu "RoundRobin".</span><span class="sxs-lookup"><span data-stu-id="982d1-147">In this example, a "RoundRobin" message filter is used.</span></span> <span data-ttu-id="982d1-148">Ten filtr komunikatu jest tworzony w wybrany plik RoutingService\RoundRobinMessageFilter.cs.</span><span class="sxs-lookup"><span data-stu-id="982d1-148">This message filter is created in the provided RoutingService\RoundRobinMessageFilter.cs file.</span></span> <span data-ttu-id="982d1-149">Te filtry, gdy ustawiono na tej samej grupie przemian raportowania są zgodne wiadomości i czy nie, w taki sposób, że odpowiada tylko jeden z nich `true` naraz.</span><span class="sxs-lookup"><span data-stu-id="982d1-149">These filters, when set to the same group, alternate between reporting that they match the message and that they do not, such that only one of them responds `true` at a time.</span></span>  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 <span data-ttu-id="982d1-150">Następnie wszystkie te wiadomości są dodawane do <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span><span class="sxs-lookup"><span data-stu-id="982d1-150">Next, all of those messages are added to a <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span></span> <span data-ttu-id="982d1-151">W ten sposób priorytety podano do wywierania wpływu na kolejność, w którym tabeli filtru komunikatów wykonuje filtrów.</span><span class="sxs-lookup"><span data-stu-id="982d1-151">In doing so, priorities are specified to influence the order in which the message filter table executes the filters.</span></span> <span data-ttu-id="982d1-152">Wyższy priorytet, tym szybciej filtr jest wykonywane; tym niższy priorytet, później filtr jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="982d1-152">The higher the priority, the sooner the filter is executed; the lower the priority, the later a filter is executed.</span></span> <span data-ttu-id="982d1-153">W związku z tym filtrze priorytetem 2 jest uruchamiany przed filtrem priorytetem 1.</span><span class="sxs-lookup"><span data-stu-id="982d1-153">Thus a filter at priority 2 runs before a filter at priority 1.</span></span> <span data-ttu-id="982d1-154">Domyślny poziom priorytetu, jeśli nie zostanie określona, to 0.</span><span class="sxs-lookup"><span data-stu-id="982d1-154">The default priority level if none is specified is 0.</span></span> <span data-ttu-id="982d1-155">Tabela Filtr komunikatu wykonuje wszystkie filtry na poziomie podana wartość priorytetu przed przejściem do następnego najniższy poziom priorytetu.</span><span class="sxs-lookup"><span data-stu-id="982d1-155">A message filter table executes all of the filters at a given priority level before moving to the next lowest priority level.</span></span> <span data-ttu-id="982d1-156">Jeśli dopasowanie znajduje się na określony priorytet, Tabela Filtr komunikatu nie Kontynuuj próby znalezienia dopasowania niższym priorytetem dalej.</span><span class="sxs-lookup"><span data-stu-id="982d1-156">If a match is found at a particular priority, then the message filter table does not continue trying to find matches at the next lower priority.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="982d1-157">Gdy w tym przykładzie pokazano, jak korzystać z priorytetów filtr komunikatu, ogólnie jest więcej wydajności i lepsze projektu do projektu i skonfigurować filtry w taki sposób, że nie wymagają priorytetyzacji do poprawnego działania.</span><span class="sxs-lookup"><span data-stu-id="982d1-157">While this example shows how to use message filter priorities, in general it is more performant and better design to design and configure your filters such that they do not require prioritization to function correctly.</span></span>  
  
 <span data-ttu-id="982d1-158">Filtr XPath jest pierwszy filtr w celu dodania i jego priorytetu jest równa 2.</span><span class="sxs-lookup"><span data-stu-id="982d1-158">The first filter to be added is the XPath filter and its priority is set to 2.</span></span> <span data-ttu-id="982d1-159">Jest to pierwszy filtr komunikatu, która wykonuje.</span><span class="sxs-lookup"><span data-stu-id="982d1-159">This is the first message filter that executes.</span></span> <span data-ttu-id="982d1-160">W przypadku odnalezienia niestandardowego nagłówka, niezależnie od tego, co może być wyniki inne filtry: wiadomość jest przesyłana do punktu końcowego Kalkulator zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="982d1-160">If it finds the custom header, regardless of what the results of the other filters would be, the message is routed to the Rounding Calculator endpoint.</span></span>  
  
 <span data-ttu-id="982d1-161">Priorytetem 1 zostaną dodane dwa filtry.</span><span class="sxs-lookup"><span data-stu-id="982d1-161">At priority 1, two filters are added.</span></span> <span data-ttu-id="982d1-162">Ponownie je uruchomić tylko filtr XPath priorytetem 2 jest niezgodna z komunikatu.</span><span class="sxs-lookup"><span data-stu-id="982d1-162">Again, these only run if the XPath filter at priority 2 does not match the message.</span></span> <span data-ttu-id="982d1-163">Te dwa filtry zawierają dwa różne sposoby, aby określić, gdzie komunikat został skierowany po potem.</span><span class="sxs-lookup"><span data-stu-id="982d1-163">These two filters show two different ways to determine where the message was addressed when it showed up.</span></span> <span data-ttu-id="982d1-164">Ponieważ dwa filtry skutecznie Sprawdź, czy wiadomość dotarła do jednego z dwoma punktami końcowymi, mogły być uruchamiane na tym samym poziomie priorytetu ponieważ są one zwracane nie obie `true` w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="982d1-164">Because the two filters effectively check to see whether the message arrived at one of the two endpoints, they can be run at the same priority level because they do not both return `true` at the same time.</span></span>  
  
 <span data-ttu-id="982d1-165">Na koniec priorytetem 0 (najniższy priorytet) uruchom RoundRobin komunikatów filtrów.</span><span class="sxs-lookup"><span data-stu-id="982d1-165">Finally, at Priority 0 (the lowest priority) run the RoundRobin message filters.</span></span> <span data-ttu-id="982d1-166">Filtry są skonfigurowane z tej samej nazwie, odpowiada tylko jeden z nich w czasie.</span><span class="sxs-lookup"><span data-stu-id="982d1-166">Because the filters are configured with the same group name, only one of them matches at a time.</span></span> <span data-ttu-id="982d1-167">Ponieważ trasowanych wszystkie komunikaty z niestandardowego nagłówka i wszystkie osoby skierowane do określonych zwirtualizowanych punktów końcowych, komunikaty obsługiwane przez filtry komunikatów RoundRobin są tylko komunikaty, które zostały skierowane do routera domyślny punkt końcowy bez niestandardowego Nagłówek.</span><span class="sxs-lookup"><span data-stu-id="982d1-167">Because all messages with the custom header have been routed and all those addressed to the specific virtualized endpoints, messages handled by the RoundRobin message filters are only messages that were addressed to the default router endpoint without the custom header.</span></span> <span data-ttu-id="982d1-168">Ponieważ te komunikaty, Włącz komunikat dla każdego wywołania, połowy Operacje przejdź do punktu końcowego regularne Kalkulator i drugą przejdź do punktu końcowego Kalkulator zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="982d1-168">Because these messages switch on a message for each call, half of the operations go to the Regular Calculator endpoint and the other half go to the Rounding Calculator endpoint.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="982d1-169">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="982d1-169">To use this sample</span></span>  
  
1.  <span data-ttu-id="982d1-170">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz AdvancedFilters.sln.</span><span class="sxs-lookup"><span data-stu-id="982d1-170">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedFilters.sln.</span></span>  
  
2.  <span data-ttu-id="982d1-171">Aby otworzyć **Eksploratora rozwiązań**, wybierz pozycję **Eksploratora rozwiązań** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="982d1-171">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="982d1-172">Naciśnij klawisz F5 lub CTRL + SHIFT + B w [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="982d1-172">Press F5 or CTRL+SHIFT+B in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="982d1-173">Jeśli chcesz automatyczne uruchamianie niezbędne projektów po naciśnięciu klawisza F5 kliknij rozwiązanie prawym przyciskiem myszy i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="982d1-173">If you would like to auto-launch the necessary projects when you press F5, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="982d1-174">Wybierz **projekt startowy** węźle **wspólne właściwości** w okienku po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="982d1-174">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="982d1-175">Wybierz **wiele projektów startowych** przycisk radiowy i ustaw wszystkie projekty, które mają **Start** akcji.</span><span class="sxs-lookup"><span data-stu-id="982d1-175">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="982d1-176">W przypadku tworzenia projektu z klawiszy CTRL + SHIFT + B, należy uruchomić następujące aplikacje:</span><span class="sxs-lookup"><span data-stu-id="982d1-176">If you build the project with CTRL+SHIFT+B, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="982d1-177">Kalkulator klienta (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="982d1-177">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="982d1-178">Usługa kalkulatora (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="982d1-178">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="982d1-179">Usługa routingu kalkulatora (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="982d1-179">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="982d1-180">Obiektu RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="982d1-180">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="982d1-181">W oknie konsoli klienta Kalkulator naciśnij klawisz ENTER, aby uruchomić klienta.</span><span class="sxs-lookup"><span data-stu-id="982d1-181">In the console window of the Calculator client, press ENTER to start the client.</span></span> <span data-ttu-id="982d1-182">Klient zwraca listę punktów końcowych docelowego do wyboru.</span><span class="sxs-lookup"><span data-stu-id="982d1-182">The client returns a list of destination endpoints to choose from.</span></span>  
  
5.  <span data-ttu-id="982d1-183">Wybierz docelowy punkt końcowy, wpisując jego odpowiednich list, a następnie naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="982d1-183">Choose a destination endpoint by typing its corresponding letter and press ENTER.</span></span>  
  
6.  <span data-ttu-id="982d1-184">Następnie klient pyta, jeśli chcesz dodać niestandardowy nagłówek.</span><span class="sxs-lookup"><span data-stu-id="982d1-184">Next, the client asks you if you want to add a custom header.</span></span> <span data-ttu-id="982d1-185">Naciśnij t dla tak lub N nie, naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="982d1-185">Press Y for Yes or N for No, then press ENTER.</span></span>  
  
7.  <span data-ttu-id="982d1-186">W zależności od wyborów dokonanych powinny zostać wyświetlone różne wyniki.</span><span class="sxs-lookup"><span data-stu-id="982d1-186">Depending on the selections you made, you should see different outputs.</span></span>  
  
    1.  <span data-ttu-id="982d1-187">Poniżej przedstawiono dane wyjściowe zwracane, jeśli niestandardowy nagłówek został dodany do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="982d1-187">The following is the output returned if you added a custom header to the messages.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="982d1-188">Poniżej przedstawiono dane wyjściowe zwracane, jeśli została wybrana opcja punkt końcowy zaokrąglania Kalkulator bez niestandardowego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="982d1-188">The following is the output returned if you chose the Rounding Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  <span data-ttu-id="982d1-189">Poniżej przedstawiono dane wyjściowe zwracane, jeśli została wybrana opcja punkt końcowy regularne Kalkulator bez niestandardowego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="982d1-189">The following is the output returned if you chose the Regular Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  <span data-ttu-id="982d1-190">Poniżej przedstawiono dane wyjściowe zwracane, jeśli została wybrana opcja Router domyślny punkt końcowy bez niestandardowego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="982d1-190">The following is the output returned if you chose the Default Router endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  <span data-ttu-id="982d1-191">Kalkulator usługi oraz zaokrąglania Kalkulator również drukowania dziennika operacji wywoływane w celu ich odpowiednich konsoli systemu windows.</span><span class="sxs-lookup"><span data-stu-id="982d1-191">The Calculator Service and the Rounding Calculator Service also prints out a log of the operations invoked to their respective console windows.</span></span>  
  
9. <span data-ttu-id="982d1-192">W oknie konsoli klienta wpisz `quit` i naciśnij klawisz ENTER, aby wyjść.</span><span class="sxs-lookup"><span data-stu-id="982d1-192">In the client console window, type `quit` and press ENTER to exit.</span></span>  
  
10. <span data-ttu-id="982d1-193">Naciśnij klawisz ENTER w oknach konsoli usług zakończenie usług.</span><span class="sxs-lookup"><span data-stu-id="982d1-193">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="982d1-194">Można konfigurować za pomocą kodu lub pliku App.config</span><span class="sxs-lookup"><span data-stu-id="982d1-194">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="982d1-195">Jest skonfigurowany do używania pliku App.config do definiowania zachowania routera dostarczany próbki.</span><span class="sxs-lookup"><span data-stu-id="982d1-195">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="982d1-196">Można również zmienić nazwę pliku RoutingService\App.config na inny tak, aby nie został rozpoznany i Usuń komentarz wywołanie metody `ConfigureRouterViaCode()` w RoutingService\routing.cs.</span><span class="sxs-lookup"><span data-stu-id="982d1-196">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and uncomment the method call to `ConfigureRouterViaCode()` in RoutingService\routing.cs.</span></span> <span data-ttu-id="982d1-197">Każda z tych metod powoduje takie samo zachowanie z routera.</span><span class="sxs-lookup"><span data-stu-id="982d1-197">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="982d1-198">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="982d1-198">Scenario</span></span>  
 <span data-ttu-id="982d1-199">W tym przykładzie przedstawiono router działająca jako router na podstawie zawartości stosowanie wielu typów lub implementacji usług są dostępne za pośrednictwem jeden punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="982d1-199">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="982d1-200">Scenariusz rzeczywistych</span><span class="sxs-lookup"><span data-stu-id="982d1-200">Real World Scenario</span></span>  
 <span data-ttu-id="982d1-201">Firma Contoso chce wszystkie ich usługi do udostępnienia tylko jeden punkt końcowy publicznie za pośrednictwem której zapewniają dostęp do wielu różnych typów usług wirtualizacji.</span><span class="sxs-lookup"><span data-stu-id="982d1-201">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="982d1-202">W takim przypadku wykorzystania usługi routingu na podstawie zawartości możliwości routingu ustalenie wysyłania żądań przychodzących.</span><span class="sxs-lookup"><span data-stu-id="982d1-202">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="982d1-203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="982d1-203">See Also</span></span>  
 [<span data-ttu-id="982d1-204">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="982d1-204">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
