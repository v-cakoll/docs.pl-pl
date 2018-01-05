---
title: Konfigurowanie odnajdywania w pliku konfiguracji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43344fc5411236fbb7420fd4d58526b3e0351d4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="85d7d-102">Konfigurowanie odnajdywania w pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="85d7d-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="85d7d-103">Istnieją cztery główne grupy ustawień konfiguracji używane podczas odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="85d7d-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="85d7d-104">W tym temacie zostaną krótko opisują każdą i przedstawiono przykłady sposobu ich konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="85d7d-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="85d7d-105">Po każdej sekcji będzie łącze do szczegółową dokumentację o każdym obszarze.</span><span class="sxs-lookup"><span data-stu-id="85d7d-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="85d7d-106">Konfigurację zachowania</span><span class="sxs-lookup"><span data-stu-id="85d7d-106">Behavior Configuration</span></span>  
 <span data-ttu-id="85d7d-107">Odnajdywanie używa zachowania usługi i zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="85d7d-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="85d7d-108"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Zachowanie umożliwia odnajdywania dla wszystkich punktów końcowych usługi i służy do określenia punktów końcowych powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="85d7d-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="85d7d-109">Poniższy przykład przedstawia sposób dodawania <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> i określ punkt końcowy powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="85d7d-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
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
  
 <span data-ttu-id="85d7d-110">Po określeniu zachowanie Odwołaj się z <`service`> element, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="85d7d-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="85d7d-111">Aby usługa będzie wykrywalny, musisz również dodać punkt końcowy odnajdowania w powyższym przykładzie dodaje <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="85d7d-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="85d7d-112">Podczas dodawania punktów końcowych powiadomienia należy dodać usługi odbiornika anonsu do <`services`> element, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="85d7d-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="85d7d-113"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Zachowanie umożliwia włączanie lub wyłączanie odnajdowania określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="85d7d-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="85d7d-114">Poniższy przykład umożliwia skonfigurowanie usługi za pomocą dwa punkty końcowe aplikacji, jeden z włączoną funkcję odnajdowania i jeden z odnajdywaniem wyłączone.</span><span class="sxs-lookup"><span data-stu-id="85d7d-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="85d7d-115">Dla każdego punktu końcowego <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> zachowanie jest dodawany.</span><span class="sxs-lookup"><span data-stu-id="85d7d-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
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
  
 <span data-ttu-id="85d7d-116"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Zachowanie można również dodać niestandardowe metadane do punktu końcowego metadane zwrócony przez usługę.</span><span class="sxs-lookup"><span data-stu-id="85d7d-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="85d7d-117">W przykładzie poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="85d7d-117">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="85d7d-118"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Zachowanie można również dodać zakresy i typy używane przez klientów do wyszukiwania dla usług.</span><span class="sxs-lookup"><span data-stu-id="85d7d-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="85d7d-119">Poniższy przykład pokazuje, jak to zrobić w pliku konfiguracji po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="85d7d-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="85d7d-120"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> i <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> zobacz [omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="85d7d-120"> <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="85d7d-121">Konfiguracja elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="85d7d-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="85d7d-122">Konfiguracja elementu powiązania jest najbardziej interesujące po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="85d7d-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="85d7d-123">Określ kryteria znajdowania używanej do odnajdywania usług z aplikacji klienta WCF umożliwia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="85d7d-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="85d7d-124">Poniższy przykład tworzy niestandardowego powiązania z <xref:System.ServiceModel.Discovery.DiscoveryClient> kanału i określa kryteria wyszukiwania, które obejmuje typie i zakresie.</span><span class="sxs-lookup"><span data-stu-id="85d7d-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="85d7d-125">Ponadto określa wartości <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> i <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="85d7d-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
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
  
 <span data-ttu-id="85d7d-126">Ta konfiguracja niestandardowego powiązania musi odwoływać się punkt końcowy klienta:</span><span class="sxs-lookup"><span data-stu-id="85d7d-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="85d7d-127">Znajdź Zobacz kryteria [odnajdywania Znajdowanie i kryteria znajdowania](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="85d7d-127"> find criteria see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="85d7d-128">Odnajdywanie i powiązania elementów Zobacz, [omówienie odnajdywania WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="85d7d-128"> discovery and binding elements see, [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="85d7d-129">Konfiguracja standardowego punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="85d7d-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="85d7d-130">Standardowe punkty końcowe są wstępnie zdefiniowanych punktów końcowych, które mają przypisane wartości domyślne dla co najmniej jednej właściwości (adres, powiązanie lub kontraktu) lub wartości właściwości, których nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="85d7d-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="85d7d-131">.NET 4 jest dostarczany z 3 odnajdywania powiązane standardowych punktów końcowych: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, i <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="85d7d-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="85d7d-132"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Jest powiązanie standardowy punkt końcowy, który jest wstępnie skonfigurowane dla operacji odnajdowania za pośrednictwem multiemisji UDP.</span><span class="sxs-lookup"><span data-stu-id="85d7d-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="85d7d-133"><xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Jest standardowy punkt końcowy, który jest wstępnie skonfigurowana do wysyłania wiadomości powiadomienia za pośrednictwem powiązania protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="85d7d-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="85d7d-134"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Jest standardowy punkt końcowy, który korzysta z odnajdywania można znaleźć adres punktu końcowego usługi odnalezionych dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="85d7d-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="85d7d-135">Standardowe powiązania są określane za pomocą <`endpoint`> element, który zawiera rodzaju atrybutu określającego typ Standardowy punkt końcowy do dodania.</span><span class="sxs-lookup"><span data-stu-id="85d7d-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="85d7d-136">Poniższy przykład przedstawia sposób dodawania <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="85d7d-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="85d7d-137">Standardowe punkty końcowe zostały skonfigurowane w <`standardEndpoints`> elementu.</span><span class="sxs-lookup"><span data-stu-id="85d7d-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="85d7d-138">Poniższy przykład przedstawia sposób konfigurowania <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> i <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="85d7d-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="85d7d-139">Po dodaniu Konfiguracja standardowego punktu końcowego odwołania konfiguracji w <`endpoint`> elementu dla każdego punktu końcowego, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="85d7d-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="85d7d-140">W przeciwieństwie do innych standardowych punktów końcowych używanych podczas odnajdywania, określić powiązanie i kontraktu dla <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="85d7d-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="85d7d-141">Poniższy przykład pokazuje, jak dodać i skonfigurować <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="85d7d-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="85d7d-142">Zobacz standardowych punktów końcowych [standardowych punktów końcowych](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="85d7d-142"> standard endpoints see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)</span></span>
