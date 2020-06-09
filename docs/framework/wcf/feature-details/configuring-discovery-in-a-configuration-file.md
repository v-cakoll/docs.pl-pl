---
title: Konfigurowanie odnajdywania w pliku konfiguracji
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 59eaecb7e34b9105bc694f444d98c13c036d552f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597556"
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Konfigurowanie odnajdywania w pliku konfiguracji
Odnajdywanie obejmuje cztery główne grupy ustawień konfiguracji. W tym temacie krótko opisano poszczególne i przedstawiono przykłady sposobu ich konfigurowania. Poniższe sekcje będą linkiem do bardziej szczegółowej dokumentacji dotyczącej każdego obszaru.  
  
## <a name="behavior-configuration"></a>Konfiguracja zachowania  
 Funkcja odnajdywania używa zachowań usługi i zachowań punktów końcowych. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Zachowanie umożliwia odnajdywanie dla wszystkich punktów końcowych usługi i pozwala określić punkty końcowe anonsu.  Poniższy przykład pokazuje, jak dodać <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> i określić punkt końcowy anonsu.  
  
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
  
 Po określeniu zachowania należy odwołać się do niego za pomocą <`service`> elementu, jak pokazano w poniższym przykładzie.  
  
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
  
 Aby można było odnaleźć usługę, należy również dodać punkt końcowy odnajdywania, tym jak powyżej, dodaje <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Standardowy punkt końcowy.  
  
 Po dodaniu punktów końcowych anonsów należy również dodać usługę odbiornika anonsu do <`services`> elementu, jak pokazano w poniższym przykładzie.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Zachowanie służy do włączania lub wyłączania odnajdywania określonego punktu końcowego.  Poniższy przykład konfiguruje usługę z dwoma punktami końcowymi aplikacji, jedną z włączonym odnajdywaniem i z wyłączonym odnajdywaniem. Dla każdego punktu końcowego <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> dodawane jest zachowanie.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Zachowanie może również służyć do dodawania niestandardowych metadanych do metadanych punktu końcowego zwróconego przez usługę. W przykładzie poniżej pokazano, jak to zrobić.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Zachowanie może również służyć do dodawania zakresów i typów używanych przez klientów do wyszukiwania usług. Poniższy przykład pokazuje, jak to zrobić w pliku konfiguracji po stronie klienta.  
  
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
  
 Aby uzyskać więcej informacji na temat usługi <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> [WCF Discovery — Omówienie](wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Konfiguracja elementu powiązania  
 Konfiguracja elementu powiązania jest najbardziej interesująca po stronie klienta. Za pomocą konfiguracji można określić kryteria wyszukiwania używane do odnajdywania usług z aplikacji klienckiej programu WCF.  Poniższy przykład tworzy powiązanie niestandardowe z <xref:System.ServiceModel.Discovery.DiscoveryClient> kanałem i określa kryteria wyszukiwania, które zawierają typ i zakres. Oprócz tego określa wartości <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> właściwości i.  
  
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
  
 Ta konfiguracja powiązania niestandardowego musi być przywoływana przez punkt końcowy klienta:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 Aby uzyskać więcej informacji na temat kryteriów wyszukiwania [, zobacz odnajdywanie Znajdź i kryteria znajdowania](discovery-find-and-findcriteria.md). Aby uzyskać więcej informacji na temat odnajdywania i elementów powiązań, zobacz [Omówienie odnajdywania WCF](wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Standardowa konfiguracja punktu końcowego  
 Standardowe punkty końcowe są wstępnie zdefiniowanymi punktami końcowymi, które mają wartości domyślne dla jednej lub wielu właściwości (adresu, powiązania lub kontraktu) lub jednej lub więcej wartości właściwości, których nie można zmienić. Platforma .NET 4 jest dostarczana z 3 punktami końcowymi związanymi z odnajdywaniem: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> , <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> i <xref:System.ServiceModel.Discovery.DynamicEndpoint> .  <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>Jest standardowym punktem końcowym, który jest wstępnie skonfigurowany dla operacji odnajdywania za pośrednictwem powiązania MULTIEMISJI UDP. <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>Jest standardowym punktem końcowym, który jest wstępnie skonfigurowany do wysyłania komunikatów anonsu za pośrednictwem powiązania UDP. <xref:System.ServiceModel.Discovery.DynamicEndpoint>Jest standardowym punktem końcowym, który używa odnajdywania do dynamicznego znajdowania adresu punktu końcowego wykrytej usługi w czasie wykonywania.  Standardowe powiązania są określane za pomocą `endpoint` elementu> <, który zawiera atrybut Kind, który określa typ standardowego punktu końcowego do dodania. Poniższy przykład pokazuje, jak dodać <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> .  
  
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
  
 Standardowe punkty końcowe są konfigurowane w <`standardEndpoints`> elementu. Poniższy przykład pokazuje, jak skonfigurować <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> .  
  
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
  
 Po dodaniu standardowej konfiguracji punktu końcowego odwołując się do konfiguracji w <`endpoint`> elementu dla każdego punktu końcowego, jak pokazano w poniższym przykładzie.  
  
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
  
 W przeciwieństwie do innych standardowych punktów końcowych używanych podczas odnajdywania, należy określić powiązanie i kontrakt dla <xref:System.ServiceModel.Discovery.DynamicEndpoint> . Poniższy przykład pokazuje, jak dodać i skonfigurować <xref:System.ServiceModel.Discovery.DynamicEndpoint> .  
  
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
  
 Aby uzyskać więcej informacji na temat standardowych punktów końcowych, zobacz [standardowe punkty końcowe](standard-endpoints.md).
