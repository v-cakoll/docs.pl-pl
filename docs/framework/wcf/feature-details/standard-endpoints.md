---
title: "Standardowe punkty końcowe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 869861ce1e2ba4456c8e8fbd06f9ff590fb3576a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="standard-endpoints"></a>Standardowe punkty końcowe
Punkty końcowe są definiowane przez określenie adresu, powiązania i kontrakt. Inne parametry, które mogą zostać ustawione dla punktu końcowego obejmują konfigurację zachowania, nagłówki oraz identyfikatorów URI nasłuchiwania.  Dla niektórych typów punktów końcowych, które nie należy zmieniać tych wartości. Na przykład zawsze używać punktów końcowych wymiany metadanych <xref:System.ServiceModel.Description.IMetadataExchange> kontraktu. Inne punkty końcowe, takich jak <xref:System.ServiceModel.Description.WebHttpEndpoint> zawsze wymagane jest zachowanie określonego punktu końcowego. Konfigurując punkty końcowe z wartościami domyślnymi dla często używanych punktu końcowego właściwości można zwiększyć użyteczność punktu końcowego. Standardowe punkty końcowe umożliwiają deweloperowi zdefiniuj punktu końcowego, który zawiera wartości domyślne lub gdy nie zmienia właściwości co najmniej jednego punktu końcowego.  Te punkty końcowe umożliwiają używanie punktu końcowego bez konieczności określania informacji o charakterze statycznych. Standardowe punkty końcowe może służyć do punktów końcowych infrastruktury i aplikacji.  
  
## <a name="infrastructure-endpoints"></a>Punkty końcowe infrastruktury  
 Usługa może narazić punktów końcowych z niektórych właściwości nie jawnie implementowane przez autora usługi. Na przykład punkt końcowy wymiany metadanych przedstawia <xref:System.ServiceModel.Description.IMetadataExchange> kontraktu, ale jako usługa autora, możesz nie implementuje interfejsu, jest zaimplementowana przez usługę WCF. Takie punkty końcowe infrastruktury ma domyślne wartości dla właściwości punktu końcowego, z których część może być aspektów. <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> Właściwość punkt końcowy wymiany metadanych musi być <xref:System.ServiceModel.Description.IMetadataExchange>, podczas gdy inne właściwości, takie jak powiązania mogą być dostarczane przez dewelopera. Punkty końcowe infrastruktury są identyfikowane przez ustawienie <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> właściwości `true`.  
  
## <a name="application-endpoints"></a>Punkty końcowe aplikacji  
 Deweloperzy aplikacji można definiować własnych standardowych punktów końcowych, które określanie wartości domyślnych dla adresu, powiązanie lub kontrakt. Zdefiniuj standardowy punkt końcowy przez wyprowadzanie klasy z <xref:System.ServiceModel.Description.ServiceEndpoint> i ustawienie właściwości odpowiednich punktów końcowych. Można podać wartości domyślnej dla właściwości, które można zmienić. Niektóre inne właściwości będą miały statyczne wartości, których nie można zmienić. Poniższy przykład pokazuje, jak do implementowania standardowego punktu końcowego.  
  
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
  
 Do użycia niestandardowego punktu końcowego zdefiniowana przez użytkownika w pliku konfiguracji musi pochodzić z klasy <xref:System.ServiceModel.Configuration.StandardEndpointElement>, klasa wyprowadzona z <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>i Zarejestruj nowy standardowy punkt końcowy w sekcji rozszerzeń w pliku machine.config lub w pliku app.config.  <xref:System.ServiceModel.Configuration.StandardEndpointElement> Zapewnia obsługę konfiguracji dla standardowego punktu końcowego, jak pokazano w poniższym przykładzie.  
  
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
  
 <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> Zawiera zapasowy typ kolekcji, który jest wyświetlany w obszarze <`standardEndpoints`> sekcji konfiguracji dla standardowego punktu końcowego.  Poniższy przykład przedstawia sposób implementowania tej klasy.  
  
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
  
## <a name="configuring-a-standard-endpoint"></a>Konfigurowanie standardowego punktu końcowego  
 Standardowe punkty końcowe można dodać w kodzie, lub w konfiguracji.  Aby dodać standardowy punkt końcowy w kodzie po prostu utworzyć wystąpienia typu odpowiedniego standardowego punktu końcowego i dodaj go do usługi hosta, jak pokazano w poniższym przykładzie:  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 Aby dodać standardowy punkt końcowy w konfiguracji, Dodaj <`endpoint`> elementu <`service`> element i wszystkie wymagane ustawienia konfiguracji w <`standardEndpoints`> elementu. Poniższy przykład przedstawia sposób dodawania <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, jeden standardowych punktów końcowych, które jest dostarczany z [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
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
  
 Typ standardowy punkt końcowy zostanie określona przy użyciu rodzaju atrybutu w <`endpoint`> elementu. Punkt końcowy jest skonfigurowana w <`standardEndpoints`> elementu. W powyższym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punkt końcowy zostanie dodany i skonfigurowany. <`udpDiscoveryEndpoint`> Zawiera element <`standardEndpoint`> stanowiąca <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> właściwość <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>Standardowe punkty końcowe zostały wydane z programu .NET Framework  
 W poniższej tabeli wymieniono standardowe punkty końcowe zostały wydane z [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
 `Mex Endpoint`  
 Standardowy punkt końcowy, który jest używany do udostępnienia metadanych usługi.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Standardowy punkt końcowy, który jest używany przez usługi do wysyłania wiadomości powiadomienia.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Standardowy punkt końcowy, który jest używany przez usługi do wysyłania wiadomości odnajdywania.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 Standardowy punkt końcowy, który jest wstępnie skonfigurowana dla operacji odnajdowania za pośrednictwem protokołu UDP multiemisji powiązania.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 Standardowy punkt końcowy, który jest używany przez usługi do wysłania komunikatów Anons powiązania protokołu UDP.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 Standardowy punkt końcowy, który używa protokołu WS Discovery, aby znaleźć adres punktu końcowego dynamicznie w czasie wykonywania.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Standardowy punkt końcowy wymiany metadanych.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 Standardowy punkt końcowy z <xref:System.ServiceModel.WebHttpBinding> powiązania, które automatycznie dodaje <xref:System.ServiceModel.Description.WebHttpBehavior> zachowanie  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 Standardowy punkt końcowy z <xref:System.ServiceModel.WebHttpBinding> powiązania, które automatycznie dodaje <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> zachowanie.  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Standardowy punkt końcowy z <xref:System.ServiceModel.WebHttpBinding> powiązania.  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 Standardowy punkt końcowy, który umożliwia wywołanie operacji kontroli na wystąpienia przepływu pracy.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 Standardowy punkt końcowy, który obsługuje wznowienie przepływu pracy tworzenia i zakładki.
