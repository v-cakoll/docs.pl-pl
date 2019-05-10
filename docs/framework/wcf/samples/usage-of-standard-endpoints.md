---
title: Użycie standardowych punktów końcowych
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: a2af1ae793166d1ed3742782b911ded30d0b9d35
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662390"
---
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="edceb-102">Użycie standardowych punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="edceb-102">Usage of Standard Endpoints</span></span>

<span data-ttu-id="edceb-103">W tym przykładzie pokazano, jak używać standardowych punktów końcowych w plikach konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="edceb-103">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="edceb-104">Standardowy punkt końcowy umożliwia użytkownikowi Uprość definicji punktów końcowych przy użyciu pojedynczej właściwości do opisania za pomocą dodatkowych właściwości skojarzone z jego adres, powiązania i umowy.</span><span class="sxs-lookup"><span data-stu-id="edceb-104">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="edceb-105">Niniejszy przykład pokazuje, jak definiować ani implementować niestandardowe standardowy punkt końcowy oraz jak zdefiniować konkretne właściwości w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="edceb-105">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>

## <a name="sample-details"></a><span data-ttu-id="edceb-106">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="edceb-106">Sample Details</span></span>

<span data-ttu-id="edceb-107">Punkty końcowe usługi można określić, podając trzy parametry: adres i powiązanie i umowy.</span><span class="sxs-lookup"><span data-stu-id="edceb-107">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="edceb-108">Inne parametry, które mogą być dostarczane obejmują konfigurację zachowania, nagłówki, identyfikatora URI nasłuchiwania i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="edceb-108">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="edceb-109">W niektórych przypadkach, dowolne lub wszystkie adresy powiązania i kontrakty mają wartości, których nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="edceb-109">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="edceb-110">Z tego powodu jest możliwe użycie standardowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="edceb-110">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="edceb-111">Przykłady takich punktów końcowych to punkty końcowe wymiany metadanych i odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="edceb-111">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="edceb-112">Standardowe punkty końcowe również zwiększyć użyteczność, umożliwiając konfiguracji punktów końcowych usługi bez konieczności zawierają informacje o charakterze stałej lub utworzyć własne standardowych punktów końcowych, na przykład aby zwiększyć użyteczność, podając uzasadnione zestaw domyślnych wartości i zmniejszając w ten sposób poziom szczegółowości plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="edceb-112">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>

<span data-ttu-id="edceb-113">Ten przykład obejmuje dwa projekty: usługa, która definiuje dwa standardowe punkty końcowe i klienta, który komunikuje się z usługą.</span><span class="sxs-lookup"><span data-stu-id="edceb-113">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="edceb-114">Sposób zdefiniowanych standardowych punktów końcowych usługi w pliku konfiguracji jest show w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="edceb-114">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>

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

<span data-ttu-id="edceb-115">Pierwszy punkt końcowy zdefiniowany dla usługi jest rodzaju `customEndpoint`, którego definicja będzie widoczne w `<standardEndpoints>` sekcji, w którym właściwość `property` jest podana wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="edceb-115">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="edceb-116">Dotyczy to dostosować za pomocą nowej właściwości punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="edceb-116">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="edceb-117">Drugi punkt końcowy odnosi się do punktu końcowego metadanych, w którym są stałe wartości dla adresu, powiązania i umowy.</span><span class="sxs-lookup"><span data-stu-id="edceb-117">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>

<span data-ttu-id="edceb-118">Aby zdefiniować element standardowy punkt końcowy, klasa, która pochodzi od klasy `StandardEndpointElement` musi zostać utworzona.</span><span class="sxs-lookup"><span data-stu-id="edceb-118">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="edceb-119">W przypadku ten przykład `CustomEndpointElement` klasy została zdefiniowana, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="edceb-119">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>

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

<span data-ttu-id="edceb-120">W `CreateServiceEndpoint` funkcji `CustomEndpoint` obiekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="edceb-120">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="edceb-121">W poniższym przykładzie pokazano definicję:</span><span class="sxs-lookup"><span data-stu-id="edceb-121">Its definition is shown in the following example:</span></span>

```csharp
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

 <span data-ttu-id="edceb-122">Aby wykonać komunikacji między usługą i klienta, odwołanie do usługi jest tworzony w klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="edceb-122">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="edceb-123">Gdy próbki są kompilowane i wykonywany, usługa była wykonywana, a klient komunikuje się z nim.</span><span class="sxs-lookup"><span data-stu-id="edceb-123">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="edceb-124">Należy zauważyć, że odwołanie do usługi mają być aktualizowane za każdym razem, gdy niektóre zmiany w usłudze.</span><span class="sxs-lookup"><span data-stu-id="edceb-124">Note that the service reference should be updated every time there is some change in the service.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="edceb-125">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="edceb-125">To use this sample</span></span>

1. <span data-ttu-id="edceb-126">Za pomocą programu Visual Studio 2012, otwórz plik StandardEndpoints.sln.</span><span class="sxs-lookup"><span data-stu-id="edceb-126">Using Visual Studio 2012, open the StandardEndpoints.sln file.</span></span>

2. <span data-ttu-id="edceb-127">Włączanie wielu projektów do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="edceb-127">Enable multiple projects to start up.</span></span>

    1. <span data-ttu-id="edceb-128">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie standardowych punktów końcowych, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="edceb-128">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>

    2. <span data-ttu-id="edceb-129">W **wspólne właściwości**, wybierz opcję **projekt startowy**, a następnie kliknij przycisk **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="edceb-129">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>

    3. <span data-ttu-id="edceb-130">Przenieś projektu usługi na początku listy, za pomocą **akcji** równa **Start**.</span><span class="sxs-lookup"><span data-stu-id="edceb-130">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>

    4. <span data-ttu-id="edceb-131">Przejściem projekt klienta po projektu usługi również **akcji** równa **Start**.</span><span class="sxs-lookup"><span data-stu-id="edceb-131">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>

         <span data-ttu-id="edceb-132">To ustawienie określa, że projekt klienta jest wykonywane po projektu usługi.</span><span class="sxs-lookup"><span data-stu-id="edceb-132">This specifies that the Client project is executed after the Service project.</span></span>

3. <span data-ttu-id="edceb-133">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="edceb-133">To run the solution, press F5.</span></span>

> [!NOTE]
> <span data-ttu-id="edceb-134">Jeśli te kroki nie zadziałają, należy sprawdzić, czy środowiska prawidłowo skonfigurowano, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="edceb-134">If these steps don't work, then make sure that your environment has been properly set up, using the following steps:</span></span>
>
> 1. <span data-ttu-id="edceb-135">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="edceb-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>
> 2. <span data-ttu-id="edceb-136">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="edceb-136">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>
> 3. <span data-ttu-id="edceb-137">Do uruchomienia przykładu w jednej lub wielu konfiguracji komputera, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="edceb-137">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="edceb-138">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="edceb-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="edceb-139">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="edceb-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="edceb-140">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="edceb-140">If this directory doesn't exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="edceb-141">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="edceb-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
