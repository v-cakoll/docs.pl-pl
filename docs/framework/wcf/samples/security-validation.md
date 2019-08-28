---
title: Weryfikacja zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: b2af9f8b93737700531e3e8c0fbe739b03469923
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038902"
---
# <a name="security-validation"></a><span data-ttu-id="a913c-102">Weryfikacja zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a913c-102">Security Validation</span></span>
<span data-ttu-id="a913c-103">W tym przykładzie pokazano, jak za pomocą niestandardowego zachowania sprawdzić poprawność usług na komputerze, aby upewnić się, że spełniają one określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="a913c-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="a913c-104">W tym przykładzie usługi są weryfikowane przez zachowanie niestandardowe przez skanowanie poszczególnych punktów końcowych usługi i sprawdzanie, czy zawierają one bezpieczne elementy powiązania.</span><span class="sxs-lookup"><span data-stu-id="a913c-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="a913c-105">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a913c-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a913c-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a913c-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="a913c-107">Niestandardowe zachowanie walidacji punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="a913c-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="a913c-108">Dodając kod użytkownika do `Validate` metody zawartej <xref:System.ServiceModel.Description.IServiceBehavior> w interfejsie, do usługi lub punktu końcowego można przymieścić niestandardowe zachowanie w celu wykonania akcji zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a913c-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="a913c-109">Poniższy kod służy do zapętlenia między punktami końcowymi zawartymi w usłudze, które przeszukują kolekcje powiązań dla bezpiecznych powiązań.</span><span class="sxs-lookup"><span data-stu-id="a913c-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```csharp
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their    
    // binding elements.  
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
  
 <span data-ttu-id="a913c-110">Dodanie poniższego kodu do pliku Web. config dodaje `serviceValidate` rozszerzenie zachowania dla usługi do rozpoznania.</span><span class="sxs-lookup"><span data-stu-id="a913c-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="a913c-111">Po dodaniu rozszerzenia zachowania do usługi można teraz dodać `endpointValidate` zachowanie do listy zachowań w pliku Web. config i w ten sposób do usługi.</span><span class="sxs-lookup"><span data-stu-id="a913c-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
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
  
 <span data-ttu-id="a913c-112">Zachowania i ich rozszerzenia, które są dodawane do pliku Web. config, mają zastosowanie do poszczególnych usług, natomiast w przypadku dodania do pliku Machine. config należy zastosować zachowanie dla każdej usługi aktywnej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a913c-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a913c-113">Podczas dodawania zachowania do wszystkich usług zaleca się wykonanie kopii zapasowej pliku Machine. config przed wprowadzeniem jakichkolwiek zmian.</span><span class="sxs-lookup"><span data-stu-id="a913c-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="a913c-114">Teraz uruchom klienta dostarczonego w katalogu client\bin tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="a913c-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="a913c-115">Wystąpił wyjątek z następującym komunikatem: "Nie można aktywować żądanej http://localhost/servicemodelsamples/service.svc usługi" ".</span><span class="sxs-lookup"><span data-stu-id="a913c-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="a913c-116">Jest to oczekiwane, ponieważ punkt końcowy jest traktowany jako niezabezpieczony przez sprawdzanie poprawności zachowania punktu końcowego i uniemożliwia uruchomienie usługi.</span><span class="sxs-lookup"><span data-stu-id="a913c-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="a913c-117">Zachowanie generuje również wyjątek wewnętrzny, który opisuje, który punkt końcowy jest niezabezpieczony i zapisuje komunikat do Podgląd zdarzeń systemu w ramach źródła "System. ServiceModel 4.0.0.0" i kategorii "WebHost".</span><span class="sxs-lookup"><span data-stu-id="a913c-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="a913c-118">Możliwe jest również włączenie śledzenia usługi w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a913c-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="a913c-119">Dzięki temu użytkownik może wyświetlić wyjątki zgłoszone przez sprawdzanie poprawności przez punkt końcowy, otwierając wynikowe ślady usługi za pomocą narzędzia Podgląd śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="a913c-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="a913c-120">Aby wyświetlić komunikaty o wyjątkach sprawdzania poprawności punktu końcowego zakończone niepowodzeniem w Podgląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a913c-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="a913c-121">Kliknij menu **Start** i wybierz polecenie **Uruchom...** .</span><span class="sxs-lookup"><span data-stu-id="a913c-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="a913c-122">Wpisz `eventvwr` , a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a913c-122">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="a913c-123">W oknie Podgląd zdarzeń kliknij pozycję **aplikacja**.</span><span class="sxs-lookup"><span data-stu-id="a913c-123">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="a913c-124">Kliknij dwukrotnie ostatnio dodane zdarzenie "System. ServiceModel 4.0.0.0" w kategorii "WebHost" w oknie **aplikacji** , aby wyświetlić komunikaty o niezabezpieczonym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="a913c-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a913c-125">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="a913c-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a913c-126">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a913c-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a913c-127">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a913c-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a913c-128">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a913c-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a913c-129">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a913c-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a913c-130">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="a913c-130">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="a913c-131">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="a913c-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a913c-132">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a913c-132">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="a913c-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a913c-133">See also</span></span>

- [<span data-ttu-id="a913c-134">Przykłady monitorowania oprogramowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="a913c-134">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
