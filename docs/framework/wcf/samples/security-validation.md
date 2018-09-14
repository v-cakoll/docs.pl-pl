---
title: Walidacja zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0aaa88268959561cabe4613d51feb0f219275634
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45528211"
---
# <a name="security-validation"></a><span data-ttu-id="9b1d7-102">Walidacja zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9b1d7-102">Security Validation</span></span>
<span data-ttu-id="9b1d7-103">W tym przykładzie pokazano, jak umożliwia zachowanie niestandardowe sprawdzanie poprawności usługi na komputerze, aby upewnić się, że spełniają określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="9b1d7-104">W tym przykładzie usług są weryfikowane przez niestandardowe zachowanie przez skanowanie za pomocą każdego punktu końcowego w usłudze i sprawdzanie, czy zawierają one elementy bezpiecznego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="9b1d7-105">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9b1d7-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b1d7-106">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="9b1d7-107">Niestandardowe zachowanie weryfikacji punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="9b1d7-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="9b1d7-108">Dodając kod użytkownika do `Validate` metoda zawarte w <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu, niestandardowe zachowanie można nadać usługi lub punktu końcowego do wykonywania akcji zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="9b1d7-109">Poniższy kod umożliwia jednoczesne każdy punkt końcowy znajdujących się w usłudze wyszukiwania za pomocą ich kolekcji powiązania dla bezpiecznych powiązań.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
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
  
 <span data-ttu-id="9b1d7-110">Dodając następujący kod do pliku Web.config dodaje `serviceValidate` rozszerzenia zachowania dla usługi, rozpoznawał.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="9b1d7-111">Po dodaniu rozszerzenia zachowania do usługi jest teraz można dodać `endpointValidate` zachowanie na liście zachowań w pliku Web.config, a w związku z usługą.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
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
  
 <span data-ttu-id="9b1d7-112">Zachowania i ich rozszerzeń, które są dodawane do pliku Web.config, zachowanie mają zastosowanie do poszczególnych usług, podczas gdy po dodaniu do pliku Machine.config zastosować zachowanie do każdej usługi, które są aktywne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b1d7-113">Podczas dodawania zachowanie do wszystkich usług, zalecane jest aby utworzyć kopię zapasową pliku Machine.config przed wprowadzeniem zmiany.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="9b1d7-114">Teraz z klientem w katalogu client\bin tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="9b1d7-115">Wyjątek występuje z następującym komunikatem: "żądanej usługi"http://localhost/servicemodelsamples/service.svc"nie można aktywować."</span><span class="sxs-lookup"><span data-stu-id="9b1d7-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="9b1d7-116">Oczekuje się, ponieważ punkt końcowy jest uznawana za niebezpieczne przez punkt końcowy, sprawdzanie poprawności zachowanie i uniemożliwia uruchomienie usługi.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="9b1d7-117">Zachowanie zgłasza również wyjątek wewnętrzny, opisujący którym punktem końcowym jest niebezpieczne i zapisuje komunikat do systemu Podglądu zdarzeń w źródle "System.ServiceModel 4.0.0.0" oraz kategorii "Hostem sieci Web".</span><span class="sxs-lookup"><span data-stu-id="9b1d7-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="9b1d7-118">Użytkownik może również włączyć śledzenie usługi w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="9b1d7-119">Dzięki temu można wyświetlić wyjątki generowane przez działanie sprawdzania poprawności punktu końcowego, otwierając wynikowy śladów usługi za pomocą narzędzia przeglądarki danych śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="9b1d7-120">Aby wyświetlić nie powiodło się komunikaty o wyjątkach weryfikacji punktu końcowego w Podglądzie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="9b1d7-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1.  <span data-ttu-id="9b1d7-121">Kliknij przycisk **Start** menu, a następnie wybierz **uruchamianie...** .</span><span class="sxs-lookup"><span data-stu-id="9b1d7-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2.  <span data-ttu-id="9b1d7-122">Typ `eventvwr` i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-122">Type `eventvwr` and click **OK**.</span></span>  
  
3.  <span data-ttu-id="9b1d7-123">W oknie podglądu zdarzeń kliknij **aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-123">In the Event Viewer window, click **Application**.</span></span>  
  
4.  <span data-ttu-id="9b1d7-124">Kliknij dwukrotnie zdarzenie ostatnio dodane "System.ServiceModel 4.0.0.0" w kategorii "WebHost" w **aplikacji** okna, aby wyświetlić komunikaty niezabezpieczone punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9b1d7-125">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="9b1d7-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9b1d7-126">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9b1d7-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9b1d7-127">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9b1d7-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9b1d7-128">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9b1d7-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9b1d7-129">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9b1d7-130">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="9b1d7-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9b1d7-131">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9b1d7-132">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9b1d7-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="9b1d7-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b1d7-133">See Also</span></span>  
 [<span data-ttu-id="9b1d7-134">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="9b1d7-134">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
