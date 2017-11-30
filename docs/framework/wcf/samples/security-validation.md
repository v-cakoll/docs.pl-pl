---
title: "Walidacja zabezpieczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
caps.latest.revision: "35"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 4e8e8ff9a99c362fb5e2a6f5ef1161f48df86ceb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security-validation"></a><span data-ttu-id="9029f-102">Walidacja zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9029f-102">Security Validation</span></span>
<span data-ttu-id="9029f-103">W tym przykładzie przedstawiono sposób użycia niestandardowego zachowania do sprawdzania poprawności usług na komputerze, aby upewnić się, że spełniają określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="9029f-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="9029f-104">W tym przykładzie usług są weryfikowane przez niestandardowe działanie przez skanowanie za pomocą każdego punktu końcowego w usłudze i sprawdzanie, czy zawierają one elementy bezpiecznego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9029f-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="9029f-105">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9029f-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9029f-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="9029f-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="9029f-107">Niestandardowe zachowanie weryfikacji punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="9029f-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="9029f-108">Dodając kod użytkownika do `Validate` metody zawarte w <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu, niestandardowe zachowanie można przydzielić do usługi lub punkt końcowy do wykonania akcji zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9029f-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="9029f-109">Poniższy kod służy do pętli każdego punktu końcowego objętych usługą, które wyszukiwania za pomocą ich kolekcji powiązanie dla bezpiecznego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9029f-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```  
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually gathering their    
       binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =   
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any   
        // secure binding elements. Transport, Asymmetric, and Symmetric      
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 <span data-ttu-id="9029f-110">Dodawanie następujący kod do pliku Web.config dodaje `serviceValidate` rozszerzenia zachowania usługi do rozpoznania.</span><span class="sxs-lookup"><span data-stu-id="9029f-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="9029f-111">Po dodaniu rozszerzenia zachowania do usługi jest teraz można dodać `endpointValidate` zachowania do listy zachowania w pliku Web.config i w związku z tym do usługi.</span><span class="sxs-lookup"><span data-stu-id="9029f-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="9029f-112">Zachowania i ich rozszerzeń, które są dodawane do pliku Web.config dotyczą zachowania poszczególnych usług, podczas gdy dodany do pliku Machine.config zastosować zachowanie do każdej usługi, które są aktywne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="9029f-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9029f-113">Podczas dodawania zachowania do wszystkich usług, zalecane jest aby utworzyć kopię zapasową pliku Machine.config przed wprowadzeniem zmian.</span><span class="sxs-lookup"><span data-stu-id="9029f-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="9029f-114">Teraz z klientem w katalogu client\bin tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="9029f-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="9029f-115">Wyjątek ma występuje następujący komunikat o błędzie: "żądanej usługi nie można aktywować"http://localhost/servicemodelsamples/service.svc"."</span><span class="sxs-lookup"><span data-stu-id="9029f-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="9029f-116">Oczekuje się, ponieważ przyjęto, że punkt końcowy jest niebezpieczne przez punkt końcowy, sprawdzanie poprawności zachowania i uniemożliwia uruchomienie usługi.</span><span class="sxs-lookup"><span data-stu-id="9029f-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="9029f-117">Zachowanie również zgłasza wyjątek wewnętrzny, który opisano, który punkt końcowy jest niebezpieczne i zapisuje komunikat do systemu Podglądu zdarzeń w źródle "System.ServiceModel 4.0.0.0" oraz kategorii "WebHost".</span><span class="sxs-lookup"><span data-stu-id="9029f-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="9029f-118">Użytkownik może również włączyć śledzenie usługi, w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9029f-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="9029f-119">Dzięki temu użytkownikowi na wyświetlanie wyjątki wyrzucane przez działanie sprawdzania poprawności punktu końcowego, otwierając wynikowy ślady usługi za pomocą narzędzia podglądu śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="9029f-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="9029f-120">Aby wyświetlić nie powiodło się komunikaty o wyjątku weryfikacji punktu końcowego w Podglądzie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="9029f-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1.  <span data-ttu-id="9029f-121">Kliknij przycisk **Start** menu i wybierz **Uruchom...** .</span><span class="sxs-lookup"><span data-stu-id="9029f-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2.  <span data-ttu-id="9029f-122">Typ `eventvwr` i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9029f-122">Type `eventvwr` and click **OK**.</span></span>  
  
3.  <span data-ttu-id="9029f-123">W oknie Podgląd zdarzeń, kliknij przycisk **aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="9029f-123">In the Event Viewer window, click **Application**.</span></span>  
  
4.  <span data-ttu-id="9029f-124">Kliknij dwukrotnie zdarzenie ostatnio dodane "System.ServiceModel 4.0.0.0" w kategorii "WebHost" w **aplikacji** okna, aby wyświetlić komunikaty niezabezpieczonych punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9029f-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9029f-125">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="9029f-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9029f-126">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9029f-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9029f-127">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9029f-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9029f-128">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9029f-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9029f-129">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9029f-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9029f-130">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="9029f-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9029f-131">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="9029f-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9029f-132">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9029f-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="9029f-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9029f-133">See Also</span></span>  
 [<span data-ttu-id="9029f-134">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="9029f-134">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
