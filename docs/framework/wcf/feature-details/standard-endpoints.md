---
title: Standardowe punkty końcowe
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 48924e06457cf9f91ce4f900bb38de4d22bfc550
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463773"
---
# <a name="standard-endpoints"></a>Standardowe punkty końcowe
Punkty końcowe są definiowane przez określenie adresu, powiązania i umowy. Inne parametry, które mogą być ustawione w punkcie końcowym obejmują konfigurację zachowania, nagłówki i identyfikatory URI nasłuchi.  W przypadku niektórych typów punktów końcowych te wartości nie zmieniają się. Na przykład punkty końcowe wymiany metadanych zawsze używają <xref:System.ServiceModel.Description.IMetadataExchange> umowy. Inne punkty końcowe, <xref:System.ServiceModel.Description.WebHttpEndpoint> takie jak zawsze wymagają określonego zachowania punktu końcowego. Użyteczność punktu końcowego można poprawić, mając punkty końcowe z wartościami domyślnymi dla powszechnie używanych właściwości punktu końcowego. Standardowe punkty końcowe umożliwiają deweloperowi zdefiniowanie punktu końcowego, który ma wartości domyślne lub gdy co najmniej jedna z właściwości punktu końcowego nie ulegnie zmianie.  Te punkty końcowe umożliwiają korzystanie z takiego punktu końcowego bez konieczności określania informacji o charakterze statycznym. Standardowe punkty końcowe mogą być używane dla infrastruktury i punktów końcowych aplikacji.  
  
## <a name="infrastructure-endpoints"></a>Punkty końcowe infrastruktury  
 Usługa może udostępnić punkty końcowe z niektórych właściwości nie jawnie zaimplementowane przez autora usługi. Na przykład punkt końcowy wymiany metadanych udostępnia <xref:System.ServiceModel.Description.IMetadataExchange> umowy, ale jako autor usługi nie implementujesz tego interfejsu, jest implementowany przez WCF. Takie punkty końcowe infrastruktury mają wartości domyślne dla jednej lub więcej właściwości punktu końcowego, z których niektóre mogą być niezmienne. Właściwość <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> punktu końcowego wymiany metadanych musi być <xref:System.ServiceModel.Description.IMetadataExchange>, podczas gdy inne właściwości, takie jak powiązanie mogą być dostarczane przez dewelopera. Punkty końcowe infrastruktury są identyfikowane przez ustawienie <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> właściwości na `true`.  
  
## <a name="application-endpoints"></a>Punkty końcowe aplikacji  
 Deweloperzy aplikacji można zdefiniować własne standardowe punkty końcowe, które określają wartości domyślne dla adresu, powiązania lub umowy. Standardowy punkt końcowy definiuje się przez <xref:System.ServiceModel.Description.ServiceEndpoint> wyprowadzanie klasy z i ustawienie odpowiednich właściwości punktu końcowego. Można podać wartości domyślne dla właściwości, które można zmienić. Niektóre inne właściwości będą miały wartości statyczne, których nie można zmienić. W poniższym przykładzie pokazano, jak zaimplementować standardowy punkt końcowy.  
  
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
  
 Aby użyć niestandardowego punktu końcowego zdefiniowanego przez użytkownika w <xref:System.ServiceModel.Configuration.StandardEndpointElement>pliku konfiguracyjnym, należy wyprowadzić klasę z , wyprowadzić klasę z <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>programu i zarejestrować nowy standardowy punkt końcowy w sekcji rozszerzenia w pliku app.config lub machine.config.  Zapewnia <xref:System.ServiceModel.Configuration.StandardEndpointElement> obsługę konfiguracji dla standardowego punktu końcowego, jak pokazano w poniższym przykładzie.  
  
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
  
 Zapewnia <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> typ kopii kolekcji, który pojawia się `standardEndpoints` w sekcji <> w konfiguracji dla standardowego punktu końcowego.  W poniższym przykładzie pokazano, jak zaimplementować tę klasę.  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

W poniższym przykładzie pokazano, jak zarejestrować standardowy punkt końcowy w sekcji rozszerzeń.

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
      </standardEndpointExtensions>
</extensions>  
```  
  
## <a name="configuring-a-standard-endpoint"></a>Konfigurowanie standardowego punktu końcowego  
 Standardowe punkty końcowe można dodać w kodzie lub w konfiguracji.  Aby dodać standardowy punkt końcowy w kodzie, po prostu smówić wystąpienie odpowiedniego standardowego typu punktu końcowego i dodać go do hosta usługi, jak pokazano w poniższym przykładzie:  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 Aby dodać standardowy punkt końcowy w konfiguracji, `endpoint` dodaj element> <do `service` <> element i wszelkie potrzebne ustawienia `standardEndpoints` konfiguracji w <> element. W poniższym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>pokazano, jak dodać jeden ze [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]standardowych punktów końcowych dostarczanych z programem .  
  
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
  
 Typ standardowego punktu końcowego jest określony przy użyciu atrybutu rodzaju w <`endpoint`> element. Punkt końcowy jest konfigurowany w `standardEndpoints` <> element. W powyższym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punkt końcowy jest dodawany i konfigurowany. Element> `udpDiscoveryEndpoint` <zawiera `standardEndpoint`> <, który ustawia <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> właściwość . <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>Standardowe punkty końcowe dostarczane z platformą .NET Framework  
 W poniższej tabeli wymieniono standardowe [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]punkty końcowe dostarczane z programem .  
  
 `Mex Endpoint`  
 Standardowy punkt końcowy, który jest używany do udostępnienia metadanych usługi.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Standardowy punkt końcowy, który jest używany przez usługi do wysyłania komunikatów anonsu.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Standardowy punkt końcowy, który jest używany przez usługi do wysyłania komunikatów odnajdywania.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 Standardowy punkt końcowy, który jest wstępnie skonfigurowany do operacji odnajdywania za pociągnięte do wiązania multiemisji UDP.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 Standardowy punkt końcowy, który jest używany przez usługi do wysyłania komunikatów anonsu za pomocą powiązania UDP.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 Standardowy punkt końcowy, który używa WS-Discovery, aby dynamicznie znaleźć adres punktu końcowego w czasie wykonywania.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Standardowy punkt końcowy wymiany metadanych.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 Standardowy punkt końcowy <xref:System.ServiceModel.WebHttpBinding> z powiązaniem, <xref:System.ServiceModel.Description.WebHttpBehavior> które automatycznie dodaje zachowanie  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 Standardowy punkt końcowy <xref:System.ServiceModel.WebHttpBinding> z powiązaniem, <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> które automatycznie dodaje zachowanie.  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Standardowy punkt końcowy <xref:System.ServiceModel.WebHttpBinding> z powiązaniem.  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 Standardowy punkt końcowy, który umożliwia wywoływanie operacji kontroli w wystąpieniach przepływu pracy.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 Standardowy punkt końcowy, który obsługuje tworzenie przepływu pracy i wznowienie zakładek.
