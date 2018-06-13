---
title: Konfigurowanie odnajdywania w pliku konfiguracji
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: c282767e686ac8a6382268aee8b45eb2d1297f5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492290"
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Konfigurowanie odnajdywania w pliku konfiguracji
Istnieją cztery główne grupy ustawień konfiguracji używane podczas odnajdywania. W tym temacie zostaną krótko opisują każdą i przedstawiono przykłady sposobu ich konfiguracji. Po każdej sekcji będzie łącze do szczegółową dokumentację o każdym obszarze.  
  
## <a name="behavior-configuration"></a>Konfigurację zachowania  
 Odnajdywanie używa zachowania usługi i zachowania punktu końcowego. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Zachowanie umożliwia odnajdywania dla wszystkich punktów końcowych usługi i służy do określenia punktów końcowych powiadomienia.  Poniższy przykład przedstawia sposób dodawania <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> i określ punkt końcowy powiadomienia.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
```  
  
 Po określeniu zachowanie Odwołaj się z <`service`> element, jak pokazano w poniższym przykładzie.  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
         <!-- Application Endpoint -->  
         <endpoint address="endpoint0"  
                   binding="basicHttpBinding"  
                   contract="IHelloWorldService" />  
         <!-- Discovery Endpoints -->  
         <endpoint kind="udpDiscoveryEndpoint" />  
        </service>  
    </service>  
```  
  
 Aby usługa będzie wykrywalny, musisz również dodać punkt końcowy odnajdowania w powyższym przykładzie dodaje <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standardowego punktu końcowego.  
  
 Podczas dodawania punktów końcowych powiadomienia należy dodać usługi odbiornika anonsu do <`services`> element, jak pokazano w poniższym przykładzie.  
  
```xml  
<services>  
   <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
      <!-- Application Endpoint -->  
      <endpoint address="endpoint0"  
                binding="basicHttpBinding"  
                contract="IHelloWorldService" />  
      <!-- Discovery Endpoints -->  
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <!-- Announcement Listener Configuration -->  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
```  
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Zachowanie umożliwia włączanie lub wyłączanie odnajdowania określonego punktu końcowego.  Poniższy przykład umożliwia skonfigurowanie usługi za pomocą dwa punkty końcowe aplikacji, jeden z włączoną funkcję odnajdowania i jeden z odnajdywaniem wyłączone. Dla każdego punktu końcowego <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> zachowanie jest dodawany.  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService"  
               behaviorConfiguration="helloWorldServiceBehavior">  
  
        <!-- Application Endpoints -->  
        <endpoint address="endpoint0"  
                 binding="basicHttpBinding"  
                 contract="IHelloWorldService"   
                 behaviorConfiguration="ep0Behavior" />  
  
        <endpoint address="endpoint1"  
                  binding="basicHttpBinding"  
                  contract="IHelloWorldService"  
                  behaviorConfiguration="ep1Behavior" />  
  
        <!-- Discovery Endpoints -->  
        <endpoint kind="udpDiscoveryEndpoint" />  
      </service>  
   </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery />  
        </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="ep0Behavior">  
          <endpointDiscovery enabled="true"/>  
        </behavior>  
        <behavior name="ep1Behavior">  
          <endpointDiscovery enabled="false"/>  
        </behavior>  
     </endpointBehaviors>  
   </behaviors>  
```  
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Zachowanie można również dodać niestandardowe metadane do punktu końcowego metadane zwrócony przez usługę. W przykładzie poniżej pokazano, jak to zrobić.  
  
```xml  
<behavior name="ep4Behavior">  
   <endpointDiscovery enabled="true">  
      <extensions>  
         <CustomMetadata>This is custom metadata.</CustomMetadata>  
         <d:Types xmlns:d="http://schemas.xmlsoap.org/ws/2005/04/discovery" xmlns:i="http://printer.example.org/2003/imaging">i:PrintBasic</d:Types>  
         <CustomMetadata netsted="true">  
            <NestedMetadata>This is a nested custom metadata.</NestedMetadata>  
         </CustomMetadata>  
      </extensions>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Zachowanie można również dodać zakresy i typy używane przez klientów do wyszukiwania dla usług. Poniższy przykład pokazuje, jak to zrobić w pliku konfiguracji po stronie klienta.  
  
```xml  
<behavior name="ep2Behavior">  
   <endpointDiscovery enabled="true">  
      <scopes>  
         <add scope="http://www.microsoft.com/building42/floor1"/>  
         <add scope="ldap:///ou=engineeringo=examplecomc=us"/>  
      </scopes>  
      <types>  
         <add name="test" namespace="http://example.microsoft.com/" />  
         <add name="additionalContract" namespace="http://example.microsoft.com/" />  
      </types>  
   </endpointDiscovery>  
</behavior>  
```  
  
 Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> i <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> zobacz [omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Konfiguracja elementu powiązania  
 Konfiguracja elementu powiązania jest najbardziej interesujące po stronie klienta. Określ kryteria znajdowania używanej do odnajdywania usług z aplikacji klienta WCF umożliwia konfiguracji.  Poniższy przykład tworzy niestandardowego powiązania z <xref:System.ServiceModel.Discovery.DiscoveryClient> kanału i określa kryteria wyszukiwania, które obejmuje typie i zakresie. Ponadto określa wartości <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> i <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> właściwości.  
  
```xml  
<bindings>  
   <customBinding>  
      <!-- Binding Configuration for the Application Endpoint -->  
      <binding name="discoBindingConfiguration">  
         <discoveryClient>  
            <endpoint kind="discoveryEndpoint"  
                      address="http://localhost:8000/ConfigTest/Discovery"  
                      binding="customBinding"  
                      bindingConfiguration="httpSoap12WSAddressing10"/>  
            <findCriteria duration="00:00:10" maxResults="2">  
              <types>  
                <add name="IHelloWorldService"/>  
              </types>  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>              
            </findCriteria>  
          </discoveryClient>  
          <textMessageEncoding messageVersion="Soap11"/>  
          <httpTransport />  
        </binding>  
```  
  
 Ta konfiguracja niestandardowego powiązania musi odwoływać się punkt końcowy klienta:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 Aby uzyskać więcej informacji na temat kryteria znajdowania zobacz [odnajdywania Znajdowanie i kryteria znajdowania](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). Aby uzyskać więcej informacji na temat odnajdowania i powiązania elementów, zobacz temat [omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Konfiguracja standardowego punktu końcowego  
 Standardowe punkty końcowe są wstępnie zdefiniowanych punktów końcowych, które mają przypisane wartości domyślne dla co najmniej jednej właściwości (adres, powiązanie lub kontraktu) lub wartości właściwości, których nie można zmienić. .NET 4 jest dostarczany z 3 odnajdywania powiązane standardowych punktów końcowych: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, i <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Jest powiązanie standardowy punkt końcowy, który jest wstępnie skonfigurowane dla operacji odnajdowania za pośrednictwem multiemisji UDP. <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Jest standardowy punkt końcowy, który jest wstępnie skonfigurowana do wysyłania wiadomości powiadomienia za pośrednictwem powiązania protokołu UDP. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Jest standardowy punkt końcowy, który korzysta z odnajdywania można znaleźć adres punktu końcowego usługi odnalezionych dynamicznie w czasie wykonywania.  Standardowe powiązania są określane za pomocą <`endpoint`> element, który zawiera rodzaju atrybutu określającego typ Standardowy punkt końcowy do dodania. Poniższy przykład przedstawia sposób dodawania <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->          
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>  
```  
  
 Standardowe punkty końcowe zostały skonfigurowane w <`standardEndpoints`> elementu. Poniższy przykład przedstawia sposób konfigurowania <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
```xml  
<standardEndpoints>  
      <udpAnnouncementEndpoint>  
        <standardEndpoint   
            name="udpAnnouncementEndpointSettings"   
            multicastAddress="soap.udp://239.255.255.250:3703"    
            maxAnnouncementDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="1028"  
            maxPendingMessageCount="10"  
            maxMulticastRetransmitCount="3"  
            maxUnicastRetransmitCount="2"  
            socketReceiveBufferSize="131072"  
            timeToLive="2" />  
        </standardEndpoint>  
      </udpAnnouncementEndpoint>  
      <udpDiscoveryEndpoint>  
        <standardEndpoint  
            name="udpDiscoveryEndpointSettings"  
            multicastAddress="soap.udp://239.255.255.252:3704"  
            maxResponseDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="2048"  
            maxPendingMessageCount="5"  
            maxReceivedMessageSize="8192"  
            maxBufferPoolSize="262144"/>  
        </standardEndpoint>  
      </udpDiscoveryEndpoint>  
```  
  
 Po dodaniu Konfiguracja standardowego punktu końcowego odwołania konfiguracji w <`endpoint`> elementu dla każdego punktu końcowego, jak pokazano w poniższym przykładzie.  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->          
      <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="udpDiscoveryEndpointSettings"/>  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" endpointConfiguration="udpAnnouncementEndpointSettings" >  
   </service>  
</services>  
```  
  
 W przeciwieństwie do innych standardowych punktów końcowych używanych podczas odnajdywania, określić powiązanie i kontraktu dla <xref:System.ServiceModel.Discovery.DynamicEndpoint>. Poniższy przykład pokazuje, jak dodać i skonfigurować <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint kind="dynamicEndpoint" binding="basicHttpBinding" contract="IHelloWorldService" endpointConfiguration="dynamicEndpointConfiguration" />  
    </client>   
   <standardEndpoints>  
      <dynamicEndpoint>  
         <standardEndpoint name="dynamicEndpointConfiguration">  
             <discoveryClientSettings>  
              <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="2">  
                 <types>  
                   <add name="IHelloWorldService"/>  
                 </types>  
                 <scopes>  
                   <add scope="http://www.microsoft.com/building42/floor1"/>  
                 </scopes>  
                 <extensions>  
                   <CustomMetadata>This is custom metadata.</CustomMetadata>          
                 </extensions>  
               </findCriteria>  
             </discoveryClientSettings>  
           </standardEndpoint>  
         </dynamicEndpoint>  
   </standardEndpoints>  
</system.ServiceModel>  
```  
  
 Aby uzyskać więcej informacji na temat standardowych punktów końcowych zobacz [standardowych punktów końcowych](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
