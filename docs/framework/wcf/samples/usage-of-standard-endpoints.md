---
title: Użycie standardowych punktów końcowych
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 2b210bfe683669aeebf54a1701f07d492e6abdb4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715345"
---
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="31f6e-102">Użycie standardowych punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="31f6e-102">Usage of Standard Endpoints</span></span>

<span data-ttu-id="31f6e-103">Ten przykład pokazuje, jak używać standardowych punktów końcowych w plikach konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="31f6e-103">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="31f6e-104">Standardowy punkt końcowy umożliwia użytkownikowi uproszczenie definicji punktów końcowych przy użyciu pojedynczej właściwości do opisywania kombinacji adresu, powiązania i kontraktu z dodatkowymi skojarzonymi właściwościami.</span><span class="sxs-lookup"><span data-stu-id="31f6e-104">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="31f6e-105">Ten przykład ilustruje sposób definiowania i implementowania niestandardowego standardowego punktu końcowego oraz sposobu definiowania określonych właściwości w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="31f6e-105">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>

## <a name="sample-details"></a><span data-ttu-id="31f6e-106">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="31f6e-106">Sample Details</span></span>

<span data-ttu-id="31f6e-107">Punkty końcowe usługi można określić, dostarczając trzy parametry: Address, Binding i Contract.</span><span class="sxs-lookup"><span data-stu-id="31f6e-107">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="31f6e-108">Inne parametry, które można podać, obejmują konfigurację zachowań, nagłówki, identyfikator URI nasłuchiwania i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="31f6e-108">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="31f6e-109">W niektórych przypadkach wszystkie lub wszystkie adresy, powiązania i kontrakty mają wartości, których nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="31f6e-109">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="31f6e-110">Z tego powodu można używać standardowych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="31f6e-110">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="31f6e-111">Niektóre przykłady takich punktów końcowych obejmują punkty końcowe wymiany metadanych i punkty końcowe odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="31f6e-111">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="31f6e-112">Standardowe punkty końcowe również zwiększają użyteczność, umożliwiając Konfigurowanie punktów końcowych usługi bez konieczności dostarczania informacji o stałym charakterze lub do tworzenia własnych standardowych punktów końcowych, na przykład w celu poprawy użyteczności przez dostarczanie rozsądnego zestawu domyślnego wartości, co zmniejsza poziom szczegółowości plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="31f6e-112">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>

<span data-ttu-id="31f6e-113">Ten przykład składa się z dwóch projektów: usługi, która definiuje dwa standardowe punkty końcowe i klienta, który komunikuje się z usługą.</span><span class="sxs-lookup"><span data-stu-id="31f6e-113">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="31f6e-114">W poniższym przykładzie pokazano sposób definiowania standardowych punktów końcowych dla usługi w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="31f6e-114">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>

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

<span data-ttu-id="31f6e-115">Pierwszy punkt końcowy zdefiniowany dla usługi jest typu `customEndpoint`, którego definicja może być widoczna w sekcji `<standardEndpoints>`, w której Właściwość `property` ma daną wartość `true`.</span><span class="sxs-lookup"><span data-stu-id="31f6e-115">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="31f6e-116">Jest to przypadek punktu końcowego dostosowany do nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="31f6e-116">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="31f6e-117">Drugi punkt końcowy odpowiada punktowi końcowemu metadanych, w którym są naprawione wartości adresu, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="31f6e-117">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>

<span data-ttu-id="31f6e-118">Aby zdefiniować standardowy element punktu końcowego, należy utworzyć klasę, która dziedziczy z `StandardEndpointElement`.</span><span class="sxs-lookup"><span data-stu-id="31f6e-118">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="31f6e-119">W przypadku tego przykładu Klasa `CustomEndpointElement` została zdefiniowana, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="31f6e-119">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>

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

<span data-ttu-id="31f6e-120">W funkcji `CreateServiceEndpoint` tworzony jest obiekt `CustomEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="31f6e-120">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="31f6e-121">Jego definicja jest pokazana w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="31f6e-121">Its definition is shown in the following example:</span></span>

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

 <span data-ttu-id="31f6e-122">W celu przeprowadzenia komunikacji między usługą a klientem do usługi jest tworzone odwołanie do usługi.</span><span class="sxs-lookup"><span data-stu-id="31f6e-122">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="31f6e-123">Po skompilowaniu i wykonaniu przykładu usługa jest wykonywana i klient komunikuje się z nią.</span><span class="sxs-lookup"><span data-stu-id="31f6e-123">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="31f6e-124">Należy pamiętać, że odwołanie do usługi powinno być aktualizowane za każdym razem, gdy w usłudze wprowadzono pewne zmiany.</span><span class="sxs-lookup"><span data-stu-id="31f6e-124">Note that the service reference should be updated every time there is some change in the service.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="31f6e-125">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="31f6e-125">To use this sample</span></span>

1. <span data-ttu-id="31f6e-126">Za pomocą programu Visual Studio 2012 Otwórz plik StandardEndpoints. sln.</span><span class="sxs-lookup"><span data-stu-id="31f6e-126">Using Visual Studio 2012, open the StandardEndpoints.sln file.</span></span>

2. <span data-ttu-id="31f6e-127">Włącz uruchamianie wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="31f6e-127">Enable multiple projects to start up.</span></span>

    1. <span data-ttu-id="31f6e-128">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy standardowe rozwiązanie punktów końcowych, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="31f6e-128">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>

    2. <span data-ttu-id="31f6e-129">W obszarze **wspólne właściwości**wybierz pozycję **projekt startowy**, a następnie kliknij pozycję **wiele projektów startowych**.</span><span class="sxs-lookup"><span data-stu-id="31f6e-129">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>

    3. <span data-ttu-id="31f6e-130">Przenieś projekt usługi na początek listy z **akcją** ustawioną na wartość **Rozpocznij**.</span><span class="sxs-lookup"><span data-stu-id="31f6e-130">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>

    4. <span data-ttu-id="31f6e-131">Przenieś projekt klienta po projekcie usługi, również z **akcją** ustawioną na wartość **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="31f6e-131">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>

         <span data-ttu-id="31f6e-132">Oznacza to, że projekt klienta jest wykonywany po projekcie usługi.</span><span class="sxs-lookup"><span data-stu-id="31f6e-132">This specifies that the Client project is executed after the Service project.</span></span>

3. <span data-ttu-id="31f6e-133">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="31f6e-133">To run the solution, press F5.</span></span>

> [!NOTE]
> <span data-ttu-id="31f6e-134">Jeśli te kroki nie działają, upewnij się, że środowisko zostało prawidłowo skonfigurowane, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="31f6e-134">If these steps don't work, then make sure that your environment has been properly set up, using the following steps:</span></span>
>
> 1. <span data-ttu-id="31f6e-135">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="31f6e-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>
> 2. <span data-ttu-id="31f6e-136">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="31f6e-136">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>
> 3. <span data-ttu-id="31f6e-137">Aby uruchomić przykład w jednej lub wielu konfiguracjach komputera, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="31f6e-137">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31f6e-138">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="31f6e-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="31f6e-139">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="31f6e-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="31f6e-140">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="31f6e-140">If this directory doesn't exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="31f6e-141">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="31f6e-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
