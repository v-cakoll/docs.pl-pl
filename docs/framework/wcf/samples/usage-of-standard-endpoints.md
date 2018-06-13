---
title: Użycie standardowych punktów końcowych
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 10f7280383a7fe381b36db76b72f7d67ba39eb40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506496"
---
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="ff25b-102">Użycie standardowych punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="ff25b-102">Usage of Standard Endpoints</span></span>
<span data-ttu-id="ff25b-103">W tym przykładzie przedstawiono sposób użycia standardowych punktów końcowych w plikach konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="ff25b-103">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="ff25b-104">Standardowy punkt końcowy umożliwia użytkownikowi uprościć definicje punktu końcowego za pomocą jednej właściwości do opisywania address, binding i contract kombinacji z dodatkowe właściwości skojarzone z nim.</span><span class="sxs-lookup"><span data-stu-id="ff25b-104">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="ff25b-105">W tym przykładzie przedstawiono sposób definiowania i implementować niestandardowe standardowy punkt końcowy oraz do definiowania właściwości specyficzne dla punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ff25b-105">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="ff25b-106">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="ff25b-106">Sample Details</span></span>  
 <span data-ttu-id="ff25b-107">Punkty końcowe usługi można określić podając trzy parametry: adres i powiązanie i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ff25b-107">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="ff25b-108">Inne parametry, które mogą być dostarczane obejmują konfigurację zachowania, nagłówki, identyfikatora URI nasłuchiwania i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ff25b-108">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="ff25b-109">W niektórych przypadkach, dowolne lub wszystkie adresy powiązania i kontrakty mają wartości, których nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="ff25b-109">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="ff25b-110">Z tego powodu jest możliwe użycie standardowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ff25b-110">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="ff25b-111">Niektóre z tych punktów końcowych przykładami punkty końcowe wymiany metadanych i odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ff25b-111">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="ff25b-112">Standardowe punkty końcowe także zwiększają jego użyteczność, zezwalając konfiguracji punktów końcowych usługi bez konieczności zawierają informacje o charakterze stałym lub utworzyć własne standardowych punktów końcowych, na przykład aby poprawić użyteczność, podając uzasadnione zestaw domyślnych wartości i w związku z tym zmniejszenie szczegółowości plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ff25b-112">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>  
  
 <span data-ttu-id="ff25b-113">Ten przykład zawiera dwa projekty: usługi, który definiuje dwa standardowe punkty końcowe i klienta, który komunikuje się z usługą.</span><span class="sxs-lookup"><span data-stu-id="ff25b-113">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="ff25b-114">Sposób standardowych punktów końcowych zdefiniowanych w pliku konfiguracji usługi jest Pokaż w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ff25b-114">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <endpointExtensions>  
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">  
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />  
        <endpoint kind="mexEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <standardEndpoints>  
      <customEndpoint>  
        <standardEndpoint property="True" />  
      </customEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ff25b-115">Pierwszy punkt końcowy zdefiniowany dla usługi jest rodzaju `customEndpoint`, którego definicja będzie widoczne w `<standardEndpoints>` sekcji, w którym właściwość `property` znajduje się wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="ff25b-115">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="ff25b-116">Jest to punkt końcowy dostosować za pomocą nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="ff25b-116">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="ff25b-117">Odpowiada drugiego punktu końcowego na punkt końcowy metadanych, w którym są ustalone wartości address, binding i contract.</span><span class="sxs-lookup"><span data-stu-id="ff25b-117">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>  
  
 <span data-ttu-id="ff25b-118">Aby zdefiniować element standardowego punktu końcowego, klasy, która jest pochodną `StandardEndpointElement` musi zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="ff25b-118">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="ff25b-119">W przypadku tej próbki `CustomEndpointElement` zdefiniowano klasy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ff25b-119">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>  
  
```csharp  
public class CustomEndpointElement : StandardEndpointElement  
{  
    public bool Property  
    {  
        get { return (bool)base["property"]; }  
        set { base["property"] = value; }  
    }  
  
    protected override ConfigurationPropertyCollection Properties  
    {  
        get  
        {  
            ConfigurationPropertyCollection properties = base.Properties;  
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));  
            return properties;  
        }  
    }  
  
    protected override Type EndpointType  
    {  
        get { return typeof(CustomEndpoint); }  
    }  
  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)  
    {  
        return new CustomEndpoint();  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;  
        customEndpoint.Property = this.Property;  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;  
        customEndpoint.Property = this.Property;  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
}  
```  
  
 <span data-ttu-id="ff25b-120">W `CreateServiceEndpoint` funkcji `CustomEndpoint` tworzony jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="ff25b-120">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="ff25b-121">W poniższym przykładzie przedstawiono definicję.</span><span class="sxs-lookup"><span data-stu-id="ff25b-121">Its definition is shown in the following example.</span></span>  
  
```  
public class CustomEndpoint : ServiceEndpoint  
    {  
        public CustomEndpoint()  
            : this(string.Empty)  
        {  
        }  
  
        public CustomEndpoint(string address)  
            : this(address, ContractDescription.GetContract(typeof(ICalculator)))  
        {  
        }  
  
        public CustomEndpoint(string address, ContractDescription contract)  
            : base(contract)  
        {  
            this.Binding = new BasicHttpBinding();  
            this.IsSystemEndpoint = false;  
        }  
  
        public bool Property  
        {  
            get;  
            set;  
        }  
    }  
```  
  
 <span data-ttu-id="ff25b-122">Aby wykonać komunikacji między usługą i klienta, odwołania do usługi jest tworzony w klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="ff25b-122">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="ff25b-123">Gdy próbki jest wbudowana i wykonywane, wykonuje usługa i klient komunikuje się z nim.</span><span class="sxs-lookup"><span data-stu-id="ff25b-123">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="ff25b-124">Należy pamiętać, że odwołania do usługi powinien być aktualizowane za każdym razem, gdy niektóre zmiany w usłudze.</span><span class="sxs-lookup"><span data-stu-id="ff25b-124">Note that the service reference should be updated every time there is some change in the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="ff25b-125">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="ff25b-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="ff25b-126">Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik StandardEndpoints.sln.</span><span class="sxs-lookup"><span data-stu-id="ff25b-126">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the StandardEndpoints.sln file.</span></span>  
  
2.  <span data-ttu-id="ff25b-127">Włącz wiele projektów mogła się uruchomić.</span><span class="sxs-lookup"><span data-stu-id="ff25b-127">Enable multiple projects to start up.</span></span>  
  
    1.  <span data-ttu-id="ff25b-128">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie standardowych punktów końcowych, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ff25b-128">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="ff25b-129">W **wspólne właściwości**, wybierz pozycję **projekt startowy**, a następnie kliknij przycisk **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="ff25b-129">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>  
  
    3.  <span data-ttu-id="ff25b-130">Projekt usługi na początku listy, są przenoszone wraz z **akcji** ustawioną **Start**.</span><span class="sxs-lookup"><span data-stu-id="ff25b-130">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>  
  
    4.  <span data-ttu-id="ff25b-131">Przenieś projektu klienta po projektu usługi również z **akcji** ustawioną **Start**.</span><span class="sxs-lookup"><span data-stu-id="ff25b-131">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>  
  
         <span data-ttu-id="ff25b-132">To ustawienie określa, że projekt klienta jest wykonywane po projektu usługi.</span><span class="sxs-lookup"><span data-stu-id="ff25b-132">This specifies that the Client project is executed after the Service project.</span></span>  
  
3.  <span data-ttu-id="ff25b-133">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="ff25b-133">To run the solution, press F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff25b-134">Jeśli te kroki nie działają, następnie upewnij się, że środowiska nie został prawidłowo skonfigurowany, wykonując następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="ff25b-134">If these steps do not work, then make sure that your environment has been properly set up, using the following steps.</span></span>  
>   
>  1.  <span data-ttu-id="ff25b-135">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ff25b-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="ff25b-136">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ff25b-136">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="ff25b-137">Aby uruchomić przykład w jednym lub wielu konfiguracji komputera, postępuj zgodnie z instrukcjami [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ff25b-137">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff25b-138">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ff25b-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ff25b-139">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ff25b-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ff25b-140">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="ff25b-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff25b-141">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ff25b-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`  
  
## <a name="see-also"></a><span data-ttu-id="ff25b-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff25b-142">See Also</span></span>
