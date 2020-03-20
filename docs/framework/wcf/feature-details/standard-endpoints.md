---
title: Standardowe punkty końcowe
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 880601664d7602e279c5d022fa37c44914a58772
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184403"
---
# <a name="standard-endpoints"></a><span data-ttu-id="0e6c2-102">Standardowe punkty końcowe</span><span class="sxs-lookup"><span data-stu-id="0e6c2-102">Standard Endpoints</span></span>
<span data-ttu-id="0e6c2-103">Punkty końcowe są definiowane przez określenie adresu, powiązania i umowy.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="0e6c2-104">Inne parametry, które mogą być ustawione w punkcie końcowym obejmują konfigurację zachowania, nagłówki i identyfikatory URI nasłuchi.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="0e6c2-105">W przypadku niektórych typów punktów końcowych te wartości nie zmieniają się.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="0e6c2-106">Na przykład punkty końcowe wymiany metadanych zawsze używają <xref:System.ServiceModel.Description.IMetadataExchange> umowy.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="0e6c2-107">Inne punkty końcowe, <xref:System.ServiceModel.Description.WebHttpEndpoint> takie jak zawsze wymagają określonego zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="0e6c2-108">Użyteczność punktu końcowego można poprawić, mając punkty końcowe z wartościami domyślnymi dla powszechnie używanych właściwości punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="0e6c2-109">Standardowe punkty końcowe umożliwiają deweloperowi zdefiniowanie punktu końcowego, który ma wartości domyślne lub gdy co najmniej jedna z właściwości punktu końcowego nie ulegnie zmianie.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="0e6c2-110">Te punkty końcowe umożliwiają korzystanie z takiego punktu końcowego bez konieczności określania informacji o charakterze statycznym.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="0e6c2-111">Standardowe punkty końcowe mogą być używane dla infrastruktury i punktów końcowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="0e6c2-112">Punkty końcowe infrastruktury</span><span class="sxs-lookup"><span data-stu-id="0e6c2-112">Infrastructure Endpoints</span></span>  
 <span data-ttu-id="0e6c2-113">Usługa może udostępnić punkty końcowe z niektórych właściwości nie jawnie zaimplementowane przez autora usługi.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="0e6c2-114">Na przykład punkt końcowy wymiany metadanych udostępnia <xref:System.ServiceModel.Description.IMetadataExchange> umowy, ale jako autor usługi nie implementujesz tego interfejsu, jest implementowany przez WCF.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="0e6c2-115">Takie punkty końcowe infrastruktury mają wartości domyślne dla jednej lub więcej właściwości punktu końcowego, z których niektóre mogą być niezmienne.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="0e6c2-116">Właściwość <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> punktu końcowego wymiany metadanych musi być <xref:System.ServiceModel.Description.IMetadataExchange>, podczas gdy inne właściwości, takie jak powiązanie mogą być dostarczane przez dewelopera.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="0e6c2-117">Punkty końcowe infrastruktury są identyfikowane przez ustawienie <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> właściwości na `true`.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="0e6c2-118">Punkty końcowe aplikacji</span><span class="sxs-lookup"><span data-stu-id="0e6c2-118">Application Endpoints</span></span>  
 <span data-ttu-id="0e6c2-119">Deweloperzy aplikacji można zdefiniować własne standardowe punkty końcowe, które określają wartości domyślne dla adresu, powiązania lub umowy.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="0e6c2-120">Standardowy punkt końcowy definiuje się przez <xref:System.ServiceModel.Description.ServiceEndpoint> wyprowadzanie klasy z i ustawienie odpowiednich właściwości punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="0e6c2-121">Można podać wartości domyślne dla właściwości, które można zmienić.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="0e6c2-122">Niektóre inne właściwości będą miały wartości statyczne, których nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="0e6c2-123">W poniższym przykładzie pokazano, jak zaimplementować standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-123">The following example shows how to implement a standard endpoint.</span></span>  
  
```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    { }  

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    { }  

    // Create the custom endpoint with a fixed binding
    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    // Definition of the additional property of this endpoint
    public bool Property { get; set; }
}
```
  
 <span data-ttu-id="0e6c2-124">Aby użyć niestandardowego punktu końcowego zdefiniowanego przez użytkownika w <xref:System.ServiceModel.Configuration.StandardEndpointElement>pliku konfiguracyjnym, należy wyprowadzić klasę z , wyprowadzić klasę z <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>programu i zarejestrować nowy standardowy punkt końcowy w sekcji rozszerzenia w pliku app.config lub machine.config.  Zapewnia <xref:System.ServiceModel.Configuration.StandardEndpointElement> obsługę konfiguracji dla standardowego punktu końcowego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    // Definition of the additional property for the standard endpoint element
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    // The additional property needs to be added to the properties of the standard endpoint element
    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    // Return the type of this standard endpoint
    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    // Create the custom service endpoint
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```  
  
 <span data-ttu-id="0e6c2-125">Zapewnia <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> typ kopii kolekcji, który pojawia się `standardEndpoints` w sekcji <> w konfiguracji dla standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="0e6c2-126">W poniższym przykładzie pokazano, jak zaimplementować tę klasę.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="0e6c2-127">W poniższym przykładzie pokazano, jak zarejestrować standardowy punkt końcowy w sekcji rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="0e6c2-128">Konfigurowanie standardowego punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="0e6c2-128">Configuring a Standard Endpoint</span></span>  
 <span data-ttu-id="0e6c2-129">Standardowe punkty końcowe można dodać w kodzie lub w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="0e6c2-130">Aby dodać standardowy punkt końcowy w kodzie, po prostu smówić wystąpienie odpowiedniego standardowego typu punktu końcowego i dodać go do hosta usługi, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0e6c2-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="0e6c2-131">Aby dodać standardowy punkt końcowy w konfiguracji, `endpoint` dodaj element> <do `service` <> element i wszelkie potrzebne ustawienia `standardEndpoints` konfiguracji w <> element.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="0e6c2-132">W poniższym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>pokazano, jak dodać jeden ze [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]standardowych punktów końcowych dostarczanych z programem .</span><span class="sxs-lookup"><span data-stu-id="0e6c2-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
```xml  
<services>  
  <service>  
    <endpoint isSystemEndpoint="true" kind="udpDiscoveryEndpoint" />  
  </service>  
</services>  
<standardEndpoints>
  <udpDiscoveryEndpoint>  
     <standardEndpoint multicastAddress="soap.udp://239.255.255.250:3702" />
  </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="0e6c2-133">Typ standardowego punktu końcowego jest określony przy użyciu atrybutu rodzaju w <`endpoint`> element.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="0e6c2-134">Punkt końcowy jest konfigurowany w `standardEndpoints` <> element.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="0e6c2-135">W powyższym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punkt końcowy jest dodawany i konfigurowany.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="0e6c2-136">Element> `udpDiscoveryEndpoint` <zawiera `standardEndpoint`> <, który ustawia <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> właściwość . <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="0e6c2-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="0e6c2-137">Standardowe punkty końcowe dostarczane z platformą .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0e6c2-137">Standard Endpoints Shipped with the .NET Framework</span></span>  
 <span data-ttu-id="0e6c2-138">W poniższej tabeli wymieniono standardowe [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]punkty końcowe dostarczane z programem .</span><span class="sxs-lookup"><span data-stu-id="0e6c2-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="0e6c2-139">Standardowy punkt końcowy, który jest używany do udostępnienia metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="0e6c2-140">Standardowy punkt końcowy, który jest używany przez usługi do wysyłania komunikatów anonsu.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="0e6c2-141">Standardowy punkt końcowy, który jest używany przez usługi do wysyłania komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="0e6c2-142">Standardowy punkt końcowy, który jest wstępnie skonfigurowany do operacji odnajdywania za pociągnięte do wiązania multiemisji UDP.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="0e6c2-143">Standardowy punkt końcowy, który jest używany przez usługi do wysyłania komunikatów anonsu za pomocą powiązania UDP.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="0e6c2-144">Standardowy punkt końcowy, który używa WS-Discovery, aby dynamicznie znaleźć adres punktu końcowego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="0e6c2-145">Standardowy punkt końcowy wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="0e6c2-146">Standardowy punkt końcowy <xref:System.ServiceModel.WebHttpBinding> z powiązaniem, <xref:System.ServiceModel.Description.WebHttpBehavior> które automatycznie dodaje zachowanie</span><span class="sxs-lookup"><span data-stu-id="0e6c2-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="0e6c2-147">Standardowy punkt końcowy <xref:System.ServiceModel.WebHttpBinding> z powiązaniem, <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> które automatycznie dodaje zachowanie.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="0e6c2-148">Standardowy punkt końcowy <xref:System.ServiceModel.WebHttpBinding> z powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="0e6c2-149">Standardowy punkt końcowy, który umożliwia wywoływanie operacji kontroli w wystąpieniach przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="0e6c2-150">Standardowy punkt końcowy, który obsługuje tworzenie przepływu pracy i wznowienie zakładek.</span><span class="sxs-lookup"><span data-stu-id="0e6c2-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
