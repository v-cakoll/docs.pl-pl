---
title: Konfiguracja — przykład
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: eb02b5d01b3f95ef741aa689cc66616fd598577b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741959"
---
# <a name="configuration-sample"></a><span data-ttu-id="3534d-102">Konfiguracja — przykład</span><span class="sxs-lookup"><span data-stu-id="3534d-102">Configuration Sample</span></span>
<span data-ttu-id="3534d-103">Ten przykład ilustruje użycie pliku konfiguracji w celu odnalezienia usługi.</span><span class="sxs-lookup"><span data-stu-id="3534d-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3534d-104">Ten przykład implementuje odnajdywanie w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3534d-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="3534d-105">Przykład, który implementuje odnajdywanie w kodzie, znajduje się w temacie [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3534d-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3534d-106">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3534d-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3534d-107">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="3534d-107">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="3534d-108">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3534d-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3534d-109">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3534d-109">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="3534d-110">Konfiguracja usługi</span><span class="sxs-lookup"><span data-stu-id="3534d-110">Service Configuration</span></span>  
 <span data-ttu-id="3534d-111">Plik konfiguracji w tym przykładzie ilustruje dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="3534d-111">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="3534d-112">Umożliwienie odnajdywania usługi w standardowym <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="3534d-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="3534d-113">Dostosowanie informacji dotyczących odnajdywania dla punktu końcowego aplikacji usługi i dostosowanie niektórych ustawień związanych z odnajdywaniem w standardowym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="3534d-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="3534d-114">Aby włączyć odnajdywanie, należy wprowadzić kilka zmian w pliku konfiguracyjnym aplikacji dla usługi:</span><span class="sxs-lookup"><span data-stu-id="3534d-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="3534d-115">Do elementu `<service>` należy dodać punkt końcowy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="3534d-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="3534d-116">Jest to standardowy punkt końcowy <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="3534d-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="3534d-117">Jest to systemowy punkt końcowy, który jest skojarzony ze środowiskiem uruchomieniowym z usługą odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="3534d-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="3534d-118">Usługa odnajdywania nasłuchuje komunikatów w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="3534d-118">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="3534d-119">Do sekcji `<serviceBehaviors>` zostanie dodane zachowanie `<serviceDiscovery>`.</span><span class="sxs-lookup"><span data-stu-id="3534d-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="3534d-120">Pozwala to na odnalezienie usługi w czasie wykonywania i użycie punktu końcowego odnajdywania wspomnianego wcześniej do nasłuchiwania `Probe` i `Resolve` komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3534d-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="3534d-121">Za pomocą tych dwóch dodatków usługa jest wykrywalna w określonym punkcie końcowym odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="3534d-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="3534d-122">Poniższy fragment konfiguracji przedstawia usługę z punktem końcowym aplikacji oraz zdefiniowanym punktem końcowym odnajdywania:</span><span class="sxs-lookup"><span data-stu-id="3534d-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"   
                    kind="udpDiscoveryEndpoint"   
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 <span data-ttu-id="3534d-123">Aby skorzystać z anonsów, musisz dodać punkt końcowy anonsu.</span><span class="sxs-lookup"><span data-stu-id="3534d-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="3534d-124">W tym celu należy zmodyfikować plik konfiguracji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="3534d-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="3534d-125">Dodanie punktu końcowego anonsu do zachowania usługi odnajdywania powoduje utworzenie domyślnego klienta anonsu dla usługi.</span><span class="sxs-lookup"><span data-stu-id="3534d-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="3534d-126">Gwarantuje to, że usługa wyśle powiadomienie online i offline, gdy usługa zostanie odpowiednio otwarta i ZAMKNIĘTA.</span><span class="sxs-lookup"><span data-stu-id="3534d-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="3534d-127">Ten plik konfiguracji wykracza poza tylko te proste kroki poprzez modyfikację dodatkowych zachowań.</span><span class="sxs-lookup"><span data-stu-id="3534d-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="3534d-128">Można kontrolować informacje związane z odnajdywaniem za pomocą określonych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="3534d-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="3534d-129">Oznacza to, że użytkownik może kontrolować, czy można odnaleźć punkt końcowy, a użytkownik może również oznaczyć ten punkt końcowy przy użyciu <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> i niestandardowych metadanych XML.</span><span class="sxs-lookup"><span data-stu-id="3534d-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="3534d-130">W tym celu użytkownik musi dodać właściwość `behaviorConfiguration` do punktu końcowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3534d-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="3534d-131">W takim przypadku następująca właściwość jest dodawana do punktu końcowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3534d-131">In this case, the following property is added to the application endpoint.</span></span>  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 <span data-ttu-id="3534d-132">Teraz za pomocą elementu konfiguracja zachowania można kontrolować atrybuty związane z odnajdywaniem.</span><span class="sxs-lookup"><span data-stu-id="3534d-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="3534d-133">W takim przypadku dwa zakresy są dodawane do punktu końcowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3534d-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
```  
  
 <span data-ttu-id="3534d-134">Aby uzyskać więcej informacji na temat zakresów, zobacz [odnajdywanie Znajdź i kryteria znajdowania](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="3534d-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="3534d-135">Można również kontrolować konkretne szczegóły punktu końcowego odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="3534d-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="3534d-136">Odbywa się to za pomocą <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span><span class="sxs-lookup"><span data-stu-id="3534d-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="3534d-137">W tym przykładzie użyta wersja protokołu jest modyfikowana, a także dodawanie `maxResponseDelay` atrybutu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="3534d-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="3534d-138">Poniżej znajduje się kompletny plik konfiguracji, który jest używany w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3534d-138">The following is the complete configuration file used in this example:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->            
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a><span data-ttu-id="3534d-139">Konfiguracja klienta</span><span class="sxs-lookup"><span data-stu-id="3534d-139">Client Configuration</span></span>  
 <span data-ttu-id="3534d-140">W pliku konfiguracyjnym aplikacji dla klienta `standardEndpoint` typu `dynamicEndpoint` służy do korzystania z odnajdywania, jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="3534d-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 <span data-ttu-id="3534d-141">Gdy klient używa `dynamicEndpoint`, środowisko uruchomieniowe automatycznie wykonuje odnajdywanie.</span><span class="sxs-lookup"><span data-stu-id="3534d-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="3534d-142">Podczas odnajdywania są używane różne ustawienia, takie jak te zdefiniowane w sekcji `discoveryClientSettings`, która określa typ punktu końcowego odnajdywania do użycia:</span><span class="sxs-lookup"><span data-stu-id="3534d-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="3534d-143">Kryteria wyszukiwania używane do wyszukiwania usług:</span><span class="sxs-lookup"><span data-stu-id="3534d-143">The find criteria used to search for services:</span></span>  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 <span data-ttu-id="3534d-144">Ten przykład rozszerza tę funkcję i modyfikuje <xref:System.ServiceModel.Discovery.FindCriteria> używany przez klienta, a także kilka właściwości standardowego `updDiscoveryEndpoint` używany do odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="3534d-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="3534d-145"><xref:System.ServiceModel.Discovery.FindCriteria> są modyfikowane w celu korzystania z zakresu i określonego algorytmu `scopeMatchBy`, a także niestandardowych kryteriów zakończenia.</span><span class="sxs-lookup"><span data-stu-id="3534d-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="3534d-146">Ponadto przykład pokazuje również, jak klient może wysyłać elementy XML przy użyciu komunikatów `Probe`.</span><span class="sxs-lookup"><span data-stu-id="3534d-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="3534d-147">Na koniec niektóre zmiany są wprowadzane do <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, takich jak wersja używanego protokołu i ustawienia specyficzne dla UDP, jak pokazano w następującym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="3534d-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
```xml  
<udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
```  
  
 <span data-ttu-id="3534d-148">Poniżej znajduje się kompletna konfiguracja klienta użyta w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3534d-148">The following is the complete client configuration used in the sample.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>        
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>     
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="3534d-149">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="3534d-149">To use this sample</span></span>  
  
1. <span data-ttu-id="3534d-150">Ten przykład korzysta z punktów końcowych HTTP i do uruchomienia tego przykładu należy dodać prawidłowe listy ACL adresów URL.</span><span class="sxs-lookup"><span data-stu-id="3534d-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="3534d-151">Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i https](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="3534d-151">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="3534d-152">Wykonanie następującego polecenia z podwyższonym poziomem uprawnień powinno spowodować dodanie odpowiednich list ACL.</span><span class="sxs-lookup"><span data-stu-id="3534d-152">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="3534d-153">Można zastąpić domenę i nazwę użytkownika dla następujących argumentów, jeśli polecenie nie działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="3534d-153">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="3534d-154">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="3534d-154">Build the solution.</span></span>  
  
3. <span data-ttu-id="3534d-155">Uruchom plik wykonywalny usługi z katalogu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3534d-155">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="3534d-156">Uruchom plik wykonywalny klienta.</span><span class="sxs-lookup"><span data-stu-id="3534d-156">Run the client executable.</span></span> <span data-ttu-id="3534d-157">Należy pamiętać, że klient może zlokalizować usługę.</span><span class="sxs-lookup"><span data-stu-id="3534d-157">Note that the client is able to locate the service.</span></span>  
