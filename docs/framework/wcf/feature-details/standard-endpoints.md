---
title: Standardowe punkty końcowe
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 395d910ddabc553cca47dcdd038f44b1470b3455
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="standard-endpoints"></a><span data-ttu-id="19875-102">Standardowe punkty końcowe</span><span class="sxs-lookup"><span data-stu-id="19875-102">Standard Endpoints</span></span>
<span data-ttu-id="19875-103">Punkty końcowe są definiowane przez określenie adresu, powiązania i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="19875-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="19875-104">Inne parametry, które mogą zostać ustawione dla punktu końcowego obejmują konfigurację zachowania, nagłówki oraz identyfikatorów URI nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="19875-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="19875-105">Dla niektórych typów punktów końcowych, które nie należy zmieniać tych wartości.</span><span class="sxs-lookup"><span data-stu-id="19875-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="19875-106">Na przykład zawsze używać punktów końcowych wymiany metadanych <xref:System.ServiceModel.Description.IMetadataExchange> kontraktu.</span><span class="sxs-lookup"><span data-stu-id="19875-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="19875-107">Inne punkty końcowe, takich jak <xref:System.ServiceModel.Description.WebHttpEndpoint> zawsze wymagane jest zachowanie określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="19875-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="19875-108">Konfigurując punkty końcowe z wartościami domyślnymi dla często używanych punktu końcowego właściwości można zwiększyć użyteczność punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="19875-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="19875-109">Standardowe punkty końcowe umożliwiają deweloperowi zdefiniuj punktu końcowego, który zawiera wartości domyślne lub gdy nie zmienia właściwości co najmniej jednego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="19875-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="19875-110">Te punkty końcowe umożliwiają używanie punktu końcowego bez konieczności określania informacji o charakterze statycznych.</span><span class="sxs-lookup"><span data-stu-id="19875-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="19875-111">Standardowe punkty końcowe może służyć do punktów końcowych infrastruktury i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19875-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="19875-112">Punkty końcowe infrastruktury</span><span class="sxs-lookup"><span data-stu-id="19875-112">Infrastructure Endpoints</span></span>  
 <span data-ttu-id="19875-113">Usługa może narazić punktów końcowych z niektórych właściwości nie jawnie implementowane przez autora usługi.</span><span class="sxs-lookup"><span data-stu-id="19875-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="19875-114">Na przykład punkt końcowy wymiany metadanych przedstawia <xref:System.ServiceModel.Description.IMetadataExchange> kontraktu, ale jako usługa autora, możesz nie implementuje interfejsu, jest zaimplementowana przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="19875-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="19875-115">Takie punkty końcowe infrastruktury ma domyślne wartości dla właściwości punktu końcowego, z których część może być aspektów.</span><span class="sxs-lookup"><span data-stu-id="19875-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="19875-116"><xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> Właściwość punkt końcowy wymiany metadanych musi być <xref:System.ServiceModel.Description.IMetadataExchange>, podczas gdy inne właściwości, takie jak powiązania mogą być dostarczane przez dewelopera.</span><span class="sxs-lookup"><span data-stu-id="19875-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="19875-117">Punkty końcowe infrastruktury są identyfikowane przez ustawienie <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="19875-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="19875-118">Punkty końcowe aplikacji</span><span class="sxs-lookup"><span data-stu-id="19875-118">Application Endpoints</span></span>  
 <span data-ttu-id="19875-119">Deweloperzy aplikacji można definiować własnych standardowych punktów końcowych, które określanie wartości domyślnych dla adresu, powiązanie lub kontrakt.</span><span class="sxs-lookup"><span data-stu-id="19875-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="19875-120">Zdefiniuj standardowy punkt końcowy przez wyprowadzanie klasy z <xref:System.ServiceModel.Description.ServiceEndpoint> i ustawienie właściwości odpowiednich punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="19875-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="19875-121">Można podać wartości domyślnej dla właściwości, które można zmienić.</span><span class="sxs-lookup"><span data-stu-id="19875-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="19875-122">Niektóre inne właściwości będą miały statyczne wartości, których nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="19875-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="19875-123">Poniższy przykład pokazuje, jak do implementowania standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="19875-123">The following example shows how to implement a standard endpoint.</span></span>  
  
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
  
 <span data-ttu-id="19875-124">Do użycia niestandardowego punktu końcowego zdefiniowana przez użytkownika w pliku konfiguracji musi pochodzić z klasy <xref:System.ServiceModel.Configuration.StandardEndpointElement>, klasa wyprowadzona z <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>i Zarejestruj nowy standardowy punkt końcowy w sekcji rozszerzeń w pliku machine.config lub w pliku app.config.  <xref:System.ServiceModel.Configuration.StandardEndpointElement> Zapewnia obsługę konfiguracji dla standardowego punktu końcowego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="19875-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="19875-125"><xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> Zawiera zapasowy typ kolekcji, który jest wyświetlany w obszarze <`standardEndpoints`> sekcji konfiguracji dla standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="19875-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="19875-126">Poniższy przykład przedstawia sposób implementowania tej klasy.</span><span class="sxs-lookup"><span data-stu-id="19875-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="19875-127">Poniższy przykład pokazuje, jak zarejestrować standardowy punkt końcowy w sekcji rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="19875-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="19875-128">Konfigurowanie standardowego punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="19875-128">Configuring a Standard Endpoint</span></span>  
 <span data-ttu-id="19875-129">Standardowe punkty końcowe można dodać w kodzie, lub w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="19875-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="19875-130">Aby dodać standardowy punkt końcowy w kodzie po prostu utworzyć wystąpienia typu odpowiedniego standardowego punktu końcowego i dodaj go do usługi hosta, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="19875-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="19875-131">Aby dodać standardowy punkt końcowy w konfiguracji, Dodaj <`endpoint`> elementu <`service`> element i wszystkie wymagane ustawienia konfiguracji w <`standardEndpoints`> elementu.</span><span class="sxs-lookup"><span data-stu-id="19875-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="19875-132">Poniższy przykład przedstawia sposób dodawania <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jeden standardowych punktów końcowych, które jest dostarczany z [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="19875-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
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
  
 <span data-ttu-id="19875-133">Typ standardowy punkt końcowy zostanie określona przy użyciu rodzaju atrybutu w <`endpoint`> elementu.</span><span class="sxs-lookup"><span data-stu-id="19875-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="19875-134">Punkt końcowy jest skonfigurowana w <`standardEndpoints`> elementu.</span><span class="sxs-lookup"><span data-stu-id="19875-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="19875-135">W powyższym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punkt końcowy zostanie dodany i skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="19875-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="19875-136"><`udpDiscoveryEndpoint`> Zawiera element <`standardEndpoint`> stanowiąca <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> właściwość <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="19875-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="19875-137">Standardowe punkty końcowe zostały wydane z programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="19875-137">Standard Endpoints Shipped with the .NET Framework</span></span>  
 <span data-ttu-id="19875-138">W poniższej tabeli wymieniono standardowe punkty końcowe zostały wydane z [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="19875-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="19875-139">Standardowy punkt końcowy, który jest używany do udostępnienia metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="19875-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="19875-140">Standardowy punkt końcowy, który jest używany przez usługi do wysyłania wiadomości powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="19875-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="19875-141">Standardowy punkt końcowy, który jest używany przez usługi do wysyłania wiadomości odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="19875-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="19875-142">Standardowy punkt końcowy, który jest wstępnie skonfigurowana dla operacji odnajdowania za pośrednictwem protokołu UDP multiemisji powiązania.</span><span class="sxs-lookup"><span data-stu-id="19875-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="19875-143">Standardowy punkt końcowy, który jest używany przez usługi do wysłania komunikatów Anons powiązania protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="19875-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="19875-144">Standardowy punkt końcowy, który używa protokołu WS Discovery, aby znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="19875-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="19875-145">Standardowy punkt końcowy wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="19875-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="19875-146">Standardowy punkt końcowy z <xref:System.ServiceModel.WebHttpBinding> powiązania, które automatycznie dodaje <xref:System.ServiceModel.Description.WebHttpBehavior> zachowanie</span><span class="sxs-lookup"><span data-stu-id="19875-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="19875-147">Standardowy punkt końcowy z <xref:System.ServiceModel.WebHttpBinding> powiązania, które automatycznie dodaje <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> zachowanie.</span><span class="sxs-lookup"><span data-stu-id="19875-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="19875-148">Standardowy punkt końcowy z <xref:System.ServiceModel.WebHttpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="19875-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="19875-149">Standardowy punkt końcowy, który umożliwia wywołanie operacji kontroli na wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="19875-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="19875-150">Standardowy punkt końcowy, który obsługuje wznowienie przepływu pracy tworzenia i zakładki.</span><span class="sxs-lookup"><span data-stu-id="19875-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
