---
title: Konfigurowanie odnajdywania w pliku konfiguracji
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: c282767e686ac8a6382268aee8b45eb2d1297f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857522"
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Konfigurowanie odnajdywania w pliku konfiguracji
Istnieją cztery główne grupy ustawienia konfiguracji używane podczas odnajdywania. W tym temacie zostaną krótko opisano każdą i wyświetlić przykłady sposobów ich konfigurowania. Po każdej sekcji będzie znajdował się link do dokumentację o każdy z tych obszarów.  
  
## <a name="behavior-configuration"></a>Konfigurację zachowania  
 Odnajdywanie używa zachowania usług i zachowań punktu końcowego. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Zachowanie umożliwia odnajdowanie dla wszystkich punktów końcowych usługi i umożliwia określenie ogłoszenie punktów końcowych.  Poniższy przykład pokazuje, jak dodać <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> i określania punktu końcowego anonsu.  
  
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
  
 Po określeniu zachowanie, odwołaj się do niego z <`service`> elementu, jak pokazano w następującym przykładzie.  
  
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
  
 Aby usługa być wykrywalny, musisz również dodać punkt końcowy odnajdywania w powyższym przykładzie dodaje <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standardowy punkt końcowy.  
  
 Po dodaniu punktów końcowych anons, należy także dodać usługi odbiornika anonsu do <`services`> elementu, jak pokazano w poniższym przykładzie.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Zachowanie jest używany, aby włączyć lub wyłączyć odnajdywanie określonego punktu końcowego.  Poniższy przykład umożliwia skonfigurowanie usługi za pomocą dwóch punktów końcowych w aplikacji z włączoną funkcję odnajdowania i jeden z odnajdywaniem wyłączone. Dla każdego punktu końcowego <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> zachowanie zostanie dodany.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Zachowanie można również dodać niestandardowych metadanych do punktu końcowego metadanych zwróconych przez usługę. W przykładzie poniżej pokazano, jak to zrobić.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Zachowanie można również dodać zakresy i typów używanych przez klientów do wyszukiwania dla usług. Poniższy przykład pokazuje, jak to zrobić w pliku konfiguracji po stronie klienta.  
  
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
 Konfiguracja elementu powiązania jest najbardziej interesujących po stronie klienta. Można użyć konfiguracji użytkownikowi określić kryteria wyszukiwania, używanej do odnajdywania usług od aplikacji klienckiej usługi WCF.  Poniższy przykład obejmuje tworzenie niestandardowego powiązania za pomocą <xref:System.ServiceModel.Discovery.DiscoveryClient> kanału i określa kryteria wyszukiwania, które zawiera, typie i zakresie. Ponadto określa wartości dla <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> i <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> właściwości.  
  
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
  
 Ta konfiguracja powiązania niestandardowego muszą być przywoływane przez punkt końcowy klienta:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 Aby uzyskać więcej informacji na temat kryteria znajdowania zobacz [odnajdywania Znajdowanie i kryteria znajdowania](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). Aby uzyskać więcej informacji na temat odnajdowania i Zobacz elementy powiązania [omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Konfiguracja standardowego punktu końcowego  
 Standardowe punkty końcowe są wstępnie zdefiniowanych punktów końcowych, które mają przypisane wartości domyślne dla co najmniej jednej właściwości (adres, powiązanie lub umowy) lub wartości właściwości, których nie można zmienić. .NET 4, który jest dostarczany z 3 odnajdywania powiązane standardowe punkty końcowe: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, i <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Wiąże standardowy punkt końcowy, który jest wstępnie skonfigurowana dla operacji odnajdowania za pośrednictwem multiemisji UDP. <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Jest standardowy punkt końcowy, który jest wstępnie skonfigurowana do wysyłania komunikatów Anons za pośrednictwem powiązania protokołu UDP. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Jest standardowy punkt końcowy, który używa odnajdywania można znaleźć adres punktu końcowego usługi odnalezionych dynamicznie w czasie wykonywania.  Standardowe powiązania są określane za pomocą <`endpoint`> element, który zawiera rodzaj atrybut, który określa typ Standardowy punkt końcowy, aby dodać. Poniższy przykład pokazuje, jak dodać <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Standardowe punkty końcowe są konfigurowane w <`standardEndpoints`> element. Poniższy przykład przedstawia sposób konfigurowania <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Po dodaniu konfiguracji standardowy punkt końcowy odwoływać się do konfiguracji w <`endpoint`>, element dla każdego punktu końcowego, jak pokazano w następującym przykładzie.  
  
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
  
 W przeciwieństwie do innych standardowych punktów końcowych używanych podczas odnajdywania, określanie wiązań i kontrakt dla <xref:System.ServiceModel.Discovery.DynamicEndpoint>. Poniższy przykład pokazuje, jak dodać i skonfigurować <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  
  
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
  
 Aby uzyskać więcej informacji na temat standardowych punktów końcowych zobacz [standardowe punkty końcowe](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
