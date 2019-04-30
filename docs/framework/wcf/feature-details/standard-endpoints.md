---
title: Standardowe punkty końcowe
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 395d910ddabc553cca47dcdd038f44b1470b3455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747774"
---
# <a name="standard-endpoints"></a>Standardowe punkty końcowe
Punkty końcowe są definiowane przez określenie adresu, powiązanie i kontrakt. Inne parametry, które mogą zostać ustawione dla punktu końcowego obejmują konfigurację zachowania, nagłówki i analizują identyfikatorów URI.  W przypadku niektórych typów punktów końcowych, których nie należy zmieniać te wartości. Na przykład punkty końcowe wymiany metadanych zawsze używaj <xref:System.ServiceModel.Description.IMetadataExchange> kontraktu. Inne punkty końcowe, takich jak <xref:System.ServiceModel.Description.WebHttpEndpoint> zawsze należy wymagać zachowania w określonym punkcie końcowym. Przez punkty końcowe z wartościami domyślnymi dla punktu końcowego często używanych właściwości można zwiększyć użyteczność punktu końcowego. Standardowe punkty końcowe umożliwiają deweloperowi zdefiniować punkt końcowy, który zawiera wartości domyślne lub gdzie właściwości przynajmniej jednego punktu końcowego nie zmienia się.  Te punkty końcowe umożliwiają używanie punktu końcowego bez konieczności określania informacji o charakterze statyczne. Standardowe punkty końcowe może służyć do punktów końcowych infrastruktury i aplikacji.  
  
## <a name="infrastructure-endpoints"></a>Punkty końcowe infrastruktury  
 Usługa może ujawnić punkty końcowe z niektórych właściwości nie są jawnie implementowane przez autora usługi. Na przykład udostępnia punkt końcowy wymiany metadanych <xref:System.ServiceModel.Description.IMetadataExchange> kontraktu, ale jako usługa autora, możesz nie implementuje interfejsu, jest implementowany przez architekturę WCF. Takie punkty końcowe infrastruktury mają wartości domyślnych dla właściwości punktu końcowego, z których część może być aspektów. <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> Właściwość punkt końcowy wymiany metadanych musi być <xref:System.ServiceModel.Description.IMetadataExchange>, podczas gdy inne właściwości, takie jak powiązania mogą być dostarczane przez dewelopera. Infrastruktura punktów końcowych są identyfikowane przez ustawienie <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> właściwość `true`.  
  
## <a name="application-endpoints"></a>Punkty końcowe aplikacji  
 Deweloperzy aplikacji mogą definiować własne standardowe punkty końcowe, które określanie wartości domyślnych dla adresu, powiązanie lub umowy. Standardowy punkt końcowy jest definiowane za wyprowadzanie klasy z <xref:System.ServiceModel.Description.ServiceEndpoint> i ustawienie właściwości odpowiednich punktów końcowych. Możesz podać wartości domyślne dla właściwości, które mogą być zmieniane. Niektóre inne właściwości mają wartości statyczne, których nie można zmienić. Poniższy przykład pokazuje, jak wdrożyć standardowy punkt końcowy.  
  
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
  
 Aby użyć niestandardowego punktu końcowego zdefiniowana przez użytkownika w pliku konfiguracji należy wyprowadzić klasę z <xref:System.ServiceModel.Configuration.StandardEndpointElement>, wyprowadzić klasę z <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>i Zarejestruj nowy standardowy punkt końcowy w sekcji rozszerzeń w pliku machine.config lub w pliku app.config.  <xref:System.ServiceModel.Configuration.StandardEndpointElement> Zapewnia obsługę Konfiguracja standardowego punktu końcowego, jak pokazano w poniższym przykładzie.  
  
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
  
 <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> Zapewnia zapasowy typ kolekcji, która pojawia się w obszarze <`standardEndpoints`> sekcji w konfiguracji dla standardowego punktu końcowego.  Poniższy przykład przedstawia sposób implementowania tej klasy.  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

Poniższy przykład pokazuje, jak zarejestrować standardowy punkt końcowy w sekcji rozszerzeń.

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a>Konfigurowanie standardowy punkt końcowy  
 Standardowe punkty końcowe można dodać w kodzie lub w konfiguracji.  Aby dodać standardowy punkt końcowy w kodzie po prostu utworzenie wystąpienia typu odpowiedniego standardowego punktu końcowego i dodaj go do hosta usługi, jak pokazano w poniższym przykładzie:  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 Aby dodać standardowy punkt końcowy w konfiguracji <`endpoint`> elementu <`service`> element i wszystkie wymagane ustawienia konfiguracji w <`standardEndpoints`> element. Poniższy przykład pokazuje, jak dodać <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jeden standardowe punkty końcowe, które jest dostarczany z [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
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
  
 Typ standardowy punkt końcowy jest określony, przy użyciu atrybutu kind w <`endpoint`> element. Punkt końcowy jest konfigurowany w <`standardEndpoints`> element. W powyższym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> dodawania i konfigurowania punktu końcowego. <`udpDiscoveryEndpoint`> Zawiera element <`standardEndpoint`> określająca <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> właściwość <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>Standardowe punkty końcowe dostarczane z programem .NET Framework  
 W poniższej tabeli wymieniono standardowe punkty końcowe są dostarczane z [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
 `Mex Endpoint`  
 Standardowy punkt końcowy, który jest używany do udostępnienia metadanych usługi.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Standardowy punkt końcowy, który jest używany przez usługi, aby wysyłać komunikaty anonsów.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Standardowy punkt końcowy, który jest używany przez usługi do wysyłania wiadomości odnajdywania.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 Standardowy punkt końcowy, który jest wstępnie skonfigurowana dla operacji odnajdowania za pośrednictwem protokołu UDP multiemisji powiązania.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 Standardowy punkt końcowy, który jest używany przez usługi do wysłania komunikatów Anons z powiązania protokołu UDP.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 Standardowy punkt końcowy, który używa protokołu WS Discovery, aby znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Standardowy punkt końcowy wymiany metadanych.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 Standardowy punkt końcowy ze <xref:System.ServiceModel.WebHttpBinding> powiązania, który automatycznie dodaje <xref:System.ServiceModel.Description.WebHttpBehavior> zachowanie  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 Standardowy punkt końcowy ze <xref:System.ServiceModel.WebHttpBinding> powiązania, który automatycznie dodaje <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> zachowanie.  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Standardowy punkt końcowy ze <xref:System.ServiceModel.WebHttpBinding> powiązania.  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 Standardowy punkt końcowy, który umożliwia wywoływanie operacji kontroli na wystąpienia przepływu pracy.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 Standardowy punkt końcowy, który obsługuje wznowienie przepływu pracy tworzenia i zakładki.
