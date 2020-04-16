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
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="55f6a-102">Konfigurowanie odnajdywania w pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="55f6a-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="55f6a-103">Istnieją cztery główne grupy ustawień konfiguracji używane w odnajdowaniu.</span><span class="sxs-lookup"><span data-stu-id="55f6a-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="55f6a-104">W tym temacie pokrótce opisano każdy z nich i pokazano przykłady sposobu ich konfigurowania.</span><span class="sxs-lookup"><span data-stu-id="55f6a-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="55f6a-105">Po każdej sekcji będzie link do bardziej szczegółowej dokumentacji na temat każdego obszaru.</span><span class="sxs-lookup"><span data-stu-id="55f6a-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="55f6a-106">Konfiguracja zachowania</span><span class="sxs-lookup"><span data-stu-id="55f6a-106">Behavior Configuration</span></span>  
 <span data-ttu-id="55f6a-107">Odnajdowanie używa zachowań usługi i zachowań punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="55f6a-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="55f6a-108">Zachowanie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> umożliwia odnajdowanie dla wszystkich punktów końcowych usługi i umożliwia określenie punktów końcowych anonsu.</span><span class="sxs-lookup"><span data-stu-id="55f6a-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="55f6a-109">W poniższym przykładzie <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> pokazano, jak dodać i określić punkt końcowy anonsu.</span><span class="sxs-lookup"><span data-stu-id="55f6a-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
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
  
 <span data-ttu-id="55f6a-110">Po określeniu zachowania, odwołaj się `service` do niego z <> elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="55f6a-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="55f6a-111">Aby usługa była wykrywalna, należy również dodać punkt końcowy odnajdywania, powyższy przykład dodaje standardowy <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="55f6a-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="55f6a-112">Po dodaniu punktów końcowych anonsu należy również dodać usługę odbiornika anonsu do <`services`> element, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="55f6a-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="55f6a-113">Zachowanie <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> jest używane do włączania lub wyłączania odnajdowania określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="55f6a-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="55f6a-114">Poniższy przykład konfiguruje usługę z dwoma punktami końcowymi aplikacji, jeden z włączoną odnajdą i jeden z wyłączonym odnajdywaniem.</span><span class="sxs-lookup"><span data-stu-id="55f6a-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="55f6a-115">Dla każdego punktu <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> końcowego jest dodawane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="55f6a-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
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
  
 <span data-ttu-id="55f6a-116">Zachowanie <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> może również służyć do dodawania niestandardowych metadanych do metadanych punktu końcowego zwracanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="55f6a-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="55f6a-117">W przykładzie poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="55f6a-117">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="55f6a-118">Zachowanie <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> może również służyć do dodawania zakresów i typów, które klienci używają do wyszukiwania usług.</span><span class="sxs-lookup"><span data-stu-id="55f6a-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="55f6a-119">W poniższym przykładzie pokazano, jak to zrobić w pliku konfiguracji po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="55f6a-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
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
  
 <span data-ttu-id="55f6a-120">Aby uzyskać <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> więcej <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> informacji na temat i zobacz [Przegląd odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="55f6a-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="55f6a-121">Konfiguracja elementu wiązania</span><span class="sxs-lookup"><span data-stu-id="55f6a-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="55f6a-122">Konfiguracja elementu wiązania jest najbardziej interesująca po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="55f6a-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="55f6a-123">Można użyć konfiguracji, aby określić kryteria znajdowania używane do odnajdowania usług z aplikacji klienckiej WCF.</span><span class="sxs-lookup"><span data-stu-id="55f6a-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="55f6a-124">Poniższy przykład tworzy niestandardowe <xref:System.ServiceModel.Discovery.DiscoveryClient> powiązanie z kanałem i określa znajdź kryteria, które zawiera typ i zakres.</span><span class="sxs-lookup"><span data-stu-id="55f6a-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="55f6a-125">Ponadto określa wartości i <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="55f6a-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
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
  
 <span data-ttu-id="55f6a-126">Ta niestandardowa konfiguracja powiązania musi się odwoływać za pomocą punktu końcowego klienta:</span><span class="sxs-lookup"><span data-stu-id="55f6a-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 <span data-ttu-id="55f6a-127">Aby uzyskać więcej informacji na temat znajdowania kryteriów, zobacz [Odnajdowanie i Znajdźkryterię](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="55f6a-127">For more information about find criteria see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="55f6a-128">Aby uzyskać więcej informacji na temat odnajdywania i elementów wiązania zobacz [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="55f6a-128">For more information about discovery and binding elements see, [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="55f6a-129">Konfiguracja standardowego punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="55f6a-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="55f6a-130">Standardowe punkty końcowe są wstępnie zdefiniowanymi punktami końcowymi, które mają wartości domyślne dla jednej lub więcej właściwości (adres, powiązanie lub kontrakt) lub jedną lub więcej wartości właściwości, których nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="55f6a-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="55f6a-131">.NET 4 jest dostarczany z 3 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>standardowymi punktami końcowymi powiązanymi z odnajdywaniem: , <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>i <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="55f6a-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="55f6a-132">Jest <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to standardowy punkt końcowy, który jest wstępnie skonfigurowany do operacji odnajdywania za pociągnięte do wiązania multiemisji UDP.</span><span class="sxs-lookup"><span data-stu-id="55f6a-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="55f6a-133">Jest <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> to standardowy punkt końcowy, który jest wstępnie skonfigurowany do wysyłania komunikatów anonsu za poczęsk 1/ powiązania UDP.</span><span class="sxs-lookup"><span data-stu-id="55f6a-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="55f6a-134">Jest <xref:System.ServiceModel.Discovery.DynamicEndpoint> to standardowy punkt końcowy, który używa odnajdywania, aby dynamicznie znaleźć adres punktu końcowego odnalezionej usługi w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="55f6a-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="55f6a-135">Standardowe powiązania są określone za pomocą `endpoint` <> element, który zawiera atrybut rodzaju, który określa typ standardowego punktu końcowego do dodania.</span><span class="sxs-lookup"><span data-stu-id="55f6a-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="55f6a-136">W poniższym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> pokazano, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>jak dodać a i a .</span><span class="sxs-lookup"><span data-stu-id="55f6a-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="55f6a-137">Standardowe punkty końcowe są konfigurowane `standardEndpoints` w <> element.</span><span class="sxs-lookup"><span data-stu-id="55f6a-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="55f6a-138">W poniższym przykładzie pokazano, jak skonfigurować <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="55f6a-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="55f6a-139">Po dodaniu konfiguracji standardowego punktu końcowego odwołaj się `endpoint` do konfiguracji w <> element dla każdego punktu końcowego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="55f6a-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="55f6a-140">W przeciwieństwie do innych standardowych punktów końcowych używanych w <xref:System.ServiceModel.Discovery.DynamicEndpoint>odnajdowaniu, należy określić powiązanie i kontrakt dla .</span><span class="sxs-lookup"><span data-stu-id="55f6a-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="55f6a-141">W poniższym przykładzie pokazano, <xref:System.ServiceModel.Discovery.DynamicEndpoint>jak dodać i skonfigurować plik .</span><span class="sxs-lookup"><span data-stu-id="55f6a-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="55f6a-142">Aby uzyskać więcej informacji o standardowych punktach końcowych, zobacz [Standardowe punkty końcowe](standard-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="55f6a-142">For more information about standard endpoints see [Standard Endpoints](standard-endpoints.md).</span></span>
