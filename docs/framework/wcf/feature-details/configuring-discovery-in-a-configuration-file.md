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
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="bbc82-102">Konfigurowanie odnajdywania w pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bbc82-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="bbc82-103">Odnajdywanie obejmuje cztery główne grupy ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bbc82-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="bbc82-104">W tym temacie krótko opisano poszczególne i przedstawiono przykłady sposobu ich konfigurowania.</span><span class="sxs-lookup"><span data-stu-id="bbc82-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="bbc82-105">Poniższe sekcje będą linkiem do bardziej szczegółowej dokumentacji dotyczącej każdego obszaru.</span><span class="sxs-lookup"><span data-stu-id="bbc82-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="bbc82-106">Konfiguracja zachowania</span><span class="sxs-lookup"><span data-stu-id="bbc82-106">Behavior Configuration</span></span>  
 <span data-ttu-id="bbc82-107">Funkcja odnajdywania używa zachowań usługi i zachowań punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="bbc82-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="bbc82-108"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Zachowanie umożliwia odnajdywanie dla wszystkich punktów końcowych usługi i pozwala określić punkty końcowe anonsu.</span><span class="sxs-lookup"><span data-stu-id="bbc82-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="bbc82-109">Poniższy przykład pokazuje, jak dodać <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> i określić punkt końcowy anonsu.</span><span class="sxs-lookup"><span data-stu-id="bbc82-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
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
  
 <span data-ttu-id="bbc82-110">Po określeniu zachowania należy odwołać się do niego za pomocą <`service`> elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bbc82-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="bbc82-111">Aby można było odnaleźć usługę, należy również dodać punkt końcowy odnajdywania, tym jak powyżej, dodaje <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Standardowy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="bbc82-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="bbc82-112">Po dodaniu punktów końcowych anonsów należy również dodać usługę odbiornika anonsu do <`services`> elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bbc82-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="bbc82-113"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Zachowanie służy do włączania lub wyłączania odnajdywania określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="bbc82-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="bbc82-114">Poniższy przykład konfiguruje usługę z dwoma punktami końcowymi aplikacji, jedną z włączonym odnajdywaniem i z wyłączonym odnajdywaniem.</span><span class="sxs-lookup"><span data-stu-id="bbc82-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="bbc82-115">Dla każdego punktu końcowego <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> dodawane jest zachowanie.</span><span class="sxs-lookup"><span data-stu-id="bbc82-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
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
  
 <span data-ttu-id="bbc82-116"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Zachowanie może również służyć do dodawania niestandardowych metadanych do metadanych punktu końcowego zwróconego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="bbc82-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="bbc82-117">W przykładzie poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="bbc82-117">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="bbc82-118"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Zachowanie może również służyć do dodawania zakresów i typów używanych przez klientów do wyszukiwania usług.</span><span class="sxs-lookup"><span data-stu-id="bbc82-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="bbc82-119">Poniższy przykład pokazuje, jak to zrobić w pliku konfiguracji po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="bbc82-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
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
  
 <span data-ttu-id="bbc82-120">Aby uzyskać więcej informacji na temat usługi <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> [WCF Discovery — Omówienie](wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bbc82-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="bbc82-121">Konfiguracja elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="bbc82-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="bbc82-122">Konfiguracja elementu powiązania jest najbardziej interesująca po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="bbc82-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="bbc82-123">Za pomocą konfiguracji można określić kryteria wyszukiwania używane do odnajdywania usług z aplikacji klienckiej programu WCF.</span><span class="sxs-lookup"><span data-stu-id="bbc82-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="bbc82-124">Poniższy przykład tworzy powiązanie niestandardowe z <xref:System.ServiceModel.Discovery.DiscoveryClient> kanałem i określa kryteria wyszukiwania, które zawierają typ i zakres.</span><span class="sxs-lookup"><span data-stu-id="bbc82-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="bbc82-125">Oprócz tego określa wartości <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> właściwości i.</span><span class="sxs-lookup"><span data-stu-id="bbc82-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
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
  
 <span data-ttu-id="bbc82-126">Ta konfiguracja powiązania niestandardowego musi być przywoływana przez punkt końcowy klienta:</span><span class="sxs-lookup"><span data-stu-id="bbc82-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 <span data-ttu-id="bbc82-127">Aby uzyskać więcej informacji na temat kryteriów wyszukiwania [, zobacz odnajdywanie Znajdź i kryteria znajdowania](discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="bbc82-127">For more information about find criteria see [Discovery Find and FindCriteria](discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="bbc82-128">Aby uzyskać więcej informacji na temat odnajdywania i elementów powiązań, zobacz [Omówienie odnajdywania WCF](wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="bbc82-128">For more information about discovery and binding elements see, [WCF Discovery Overview](wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="bbc82-129">Standardowa konfiguracja punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="bbc82-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="bbc82-130">Standardowe punkty końcowe są wstępnie zdefiniowanymi punktami końcowymi, które mają wartości domyślne dla jednej lub wielu właściwości (adresu, powiązania lub kontraktu) lub jednej lub więcej wartości właściwości, których nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="bbc82-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="bbc82-131">Platforma .NET 4 jest dostarczana z 3 punktami końcowymi związanymi z odnajdywaniem: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> , <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> i <xref:System.ServiceModel.Discovery.DynamicEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="bbc82-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="bbc82-132"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>Jest standardowym punktem końcowym, który jest wstępnie skonfigurowany dla operacji odnajdywania za pośrednictwem powiązania MULTIEMISJI UDP.</span><span class="sxs-lookup"><span data-stu-id="bbc82-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="bbc82-133"><xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>Jest standardowym punktem końcowym, który jest wstępnie skonfigurowany do wysyłania komunikatów anonsu za pośrednictwem powiązania UDP.</span><span class="sxs-lookup"><span data-stu-id="bbc82-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="bbc82-134"><xref:System.ServiceModel.Discovery.DynamicEndpoint>Jest standardowym punktem końcowym, który używa odnajdywania do dynamicznego znajdowania adresu punktu końcowego wykrytej usługi w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bbc82-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="bbc82-135">Standardowe powiązania są określane za pomocą `endpoint` elementu> <, który zawiera atrybut Kind, który określa typ standardowego punktu końcowego do dodania.</span><span class="sxs-lookup"><span data-stu-id="bbc82-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="bbc82-136">Poniższy przykład pokazuje, jak dodać <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="bbc82-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="bbc82-137">Standardowe punkty końcowe są konfigurowane w <`standardEndpoints`> elementu.</span><span class="sxs-lookup"><span data-stu-id="bbc82-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="bbc82-138">Poniższy przykład pokazuje, jak skonfigurować <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="bbc82-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="bbc82-139">Po dodaniu standardowej konfiguracji punktu końcowego odwołując się do konfiguracji w <`endpoint`> elementu dla każdego punktu końcowego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bbc82-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="bbc82-140">W przeciwieństwie do innych standardowych punktów końcowych używanych podczas odnajdywania, należy określić powiązanie i kontrakt dla <xref:System.ServiceModel.Discovery.DynamicEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="bbc82-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="bbc82-141">Poniższy przykład pokazuje, jak dodać i skonfigurować <xref:System.ServiceModel.Discovery.DynamicEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="bbc82-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="bbc82-142">Aby uzyskać więcej informacji na temat standardowych punktów końcowych, zobacz [standardowe punkty końcowe](standard-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="bbc82-142">For more information about standard endpoints see [Standard Endpoints](standard-endpoints.md).</span></span>
