---
title: Konfigurowanie odnajdywania w pliku konfiguracji
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 934b04b51b9954cf943f57f33250951048e5671b
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464206"
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Konfigurowanie odnajdywania w pliku konfiguracji
Istnieją cztery główne grupy ustawień konfiguracji używane w odnajdowaniu. W tym temacie pokrótce opisano każdy z nich i pokazano przykłady sposobu ich konfigurowania. Po każdej sekcji będzie link do bardziej szczegółowej dokumentacji na temat każdego obszaru.  
  
## <a name="behavior-configuration"></a>Konfiguracja zachowania  
 Odnajdowanie używa zachowań usługi i zachowań punktu końcowego. Zachowanie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> umożliwia odnajdowanie dla wszystkich punktów końcowych usługi i umożliwia określenie punktów końcowych anonsu.  W poniższym przykładzie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> pokazano, jak dodać i określić punkt końcowy anonsu.  
  
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
</behaviors>  
```  
  
 Po określeniu zachowania, odwołaj się `service` do niego z <> elementu, jak pokazano w poniższym przykładzie.  
  
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
    </services>  
</system.serviceModel>  
```  
  
 Aby usługa była wykrywalna, należy również dodać punkt końcowy odnajdywania, powyższy przykład dodaje standardowy <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punkt końcowy.  
  
 Po dodaniu punktów końcowych anonsu należy również dodać usługę odbiornika anonsu do <`services`> element, jak pokazano w poniższym przykładzie.  
  
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
</services>
```  
  
 Zachowanie <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> jest używane do włączania lub wyłączania odnajdowania określonego punktu końcowego.  Poniższy przykład konfiguruje usługę z dwoma punktami końcowymi aplikacji, jeden z włączoną odnajdą i jeden z wyłączonym odnajdywaniem. Dla każdego punktu <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> końcowego jest dodawane zachowanie.  
  
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
</system.serviceModel>  
```  
  
 Zachowanie <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> może również służyć do dodawania niestandardowych metadanych do metadanych punktu końcowego zwracanych przez usługę. W przykładzie poniżej pokazano, jak to zrobić.  
  
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
  
 Zachowanie <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> może również służyć do dodawania zakresów i typów, które klienci używają do wyszukiwania usług. W poniższym przykładzie pokazano, jak to zrobić w pliku konfiguracji po stronie klienta.  
  
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
  
 Aby uzyskać <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> więcej <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> informacji na temat i zobacz [Przegląd odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Konfiguracja elementu wiązania  
 Konfiguracja elementu wiązania jest najbardziej interesująca po stronie klienta. Można użyć konfiguracji, aby określić kryteria znajdowania używane do odnajdowania usług z aplikacji klienckiej WCF.  Poniższy przykład tworzy niestandardowe <xref:System.ServiceModel.Discovery.DiscoveryClient> powiązanie z kanałem i określa znajdź kryteria, które zawiera typ i zakres. Ponadto określa wartości i <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> właściwości.  
  
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
   </customBinding>
</bindings>  
```  
  
 Ta niestandardowa konfiguracja powiązania musi się odwoływać za pomocą punktu końcowego klienta:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 Aby uzyskać więcej informacji na temat znajdowania kryteriów, zobacz [Odnajdowanie i Znajdźkryterię](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). Aby uzyskać więcej informacji na temat odnajdywania i elementów wiązania zobacz [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Konfiguracja standardowego punktu końcowego  
 Standardowe punkty końcowe są wstępnie zdefiniowanymi punktami końcowymi, które mają wartości domyślne dla jednej lub więcej właściwości (adres, powiązanie lub kontrakt) lub jedną lub więcej wartości właściwości, których nie można zmienić. .NET 4 jest dostarczany z 3 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>standardowymi punktami końcowymi powiązanymi z odnajdywaniem: , <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>i <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  Jest <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to standardowy punkt końcowy, który jest wstępnie skonfigurowany do operacji odnajdywania za pociągnięte do wiązania multiemisji UDP. Jest <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> to standardowy punkt końcowy, który jest wstępnie skonfigurowany do wysyłania komunikatów anonsu za poczęsk 1/ powiązania UDP. Jest <xref:System.ServiceModel.Discovery.DynamicEndpoint> to standardowy punkt końcowy, który używa odnajdywania, aby dynamicznie znaleźć adres punktu końcowego odnalezionej usługi w czasie wykonywania.  Standardowe powiązania są określone za pomocą `endpoint` <> element, który zawiera atrybut rodzaju, który określa typ standardowego punktu końcowego do dodania. W poniższym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> pokazano, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>jak dodać a i a .  
  
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
  
 Standardowe punkty końcowe są konfigurowane `standardEndpoints` w <> element. W poniższym przykładzie pokazano, jak skonfigurować <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
</standardEndpoints>
```  
  
 Po dodaniu konfiguracji standardowego punktu końcowego odwołaj się `endpoint` do konfiguracji w <> element dla każdego punktu końcowego, jak pokazano w poniższym przykładzie.  
  
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
  
 W przeciwieństwie do innych standardowych punktów końcowych używanych w <xref:System.ServiceModel.Discovery.DynamicEndpoint>odnajdowaniu, należy określić powiązanie i kontrakt dla . W poniższym przykładzie pokazano, <xref:System.ServiceModel.Discovery.DynamicEndpoint>jak dodać i skonfigurować plik .  
  
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
  
 Aby uzyskać więcej informacji o standardowych punktach końcowych, zobacz [Standardowe punkty końcowe](standard-endpoints.md).
