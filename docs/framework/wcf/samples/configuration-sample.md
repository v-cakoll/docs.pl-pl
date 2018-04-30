---
title: Konfiguracja — przykład
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 48f153a26181fa549973ec83e413b1294d7c8ce5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="configuration-sample"></a><span data-ttu-id="ecaf9-102">Konfiguracja — przykład</span><span class="sxs-lookup"><span data-stu-id="ecaf9-102">Configuration Sample</span></span>
<span data-ttu-id="ecaf9-103">W tym przykładzie przedstawiono korzystanie z pliku konfiguracji, aby stał się wykrywalny usługi.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecaf9-104">W tym przykładzie implementuje odnajdywania w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="ecaf9-105">Dla przykładu, który implementuje odnajdywania w kodzie, zobacz [podstawowe](../../../../docs/framework/wcf/samples/basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ecaf9-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ecaf9-106">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ecaf9-107">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ecaf9-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ecaf9-108">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ecaf9-109">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="ecaf9-110">Konfiguracja usługi</span><span class="sxs-lookup"><span data-stu-id="ecaf9-110">Service Configuration</span></span>  
 <span data-ttu-id="ecaf9-111">Plik konfiguracji w tym przykładzie przedstawiono dwie funkcje:</span><span class="sxs-lookup"><span data-stu-id="ecaf9-111">The configuration file in this sample demonstrates two features:</span></span>  
  
-   <span data-ttu-id="ecaf9-112">Tworzenie usługi wykrywalny przez standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
-   <span data-ttu-id="ecaf9-113">Dostosowywanie informacji dotyczących odnajdywania, punkt końcowy aplikacji i dostosowanie niektórych ustawień związanych z odnajdywania standardowego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="ecaf9-114">Aby włączyć odnajdywanie, należy kilka zmian w pliku konfiguracyjnym aplikacji dla usługi:</span><span class="sxs-lookup"><span data-stu-id="ecaf9-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
-   <span data-ttu-id="ecaf9-115">Punkt końcowy odnajdowania musi zostać dodany do `<service>` elementu.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="ecaf9-116">Jest to standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="ecaf9-117">Jest to system punktu końcowego, który kojarzy środowiska uruchomieniowego usługi odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="ecaf9-118">Usługa odnajdywania nasłuchuje komunikatów na tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-118">The discovery service listens for messages on this endpoint.</span></span>  
  
-   <span data-ttu-id="ecaf9-119">A `<serviceDiscovery>` zachowanie jest dodawany do `<serviceBehaviors>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="ecaf9-120">To umożliwia usłudze odnaleziona w czasie wykonywania i używa już wspomniano w celu nasłuchiwania odnajdywania punkt końcowy odnajdowania `Probe` i `Resolve` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="ecaf9-121">Z tych dwóch dodatkami usługa jest łatwy w określonym punktem końcowym odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="ecaf9-122">Poniższy fragment konfiguracji zawiera usługę z punktem końcowym aplikacji i punkt końcowy odnajdowania zdefiniowane:</span><span class="sxs-lookup"><span data-stu-id="ecaf9-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
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
  
 <span data-ttu-id="ecaf9-123">Aby skorzystać z anonsów, należy dodać punktu końcowego powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="ecaf9-124">Aby to zrobić, należy zmodyfikować plik konfiguracji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="ecaf9-125">Dodawanie punktu końcowego powiadomienia do zachowania usługi odnajdywania tworzy domyślny klient anonsów dla usługi.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="ecaf9-126">Gwarantuje to, Usługa wyśle anons online i offline, gdy usługa jest otwarty i odpowiednio zamknięte.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="ecaf9-127">Ten plik konfiguracji wykraczają poza tylko te prostych kroków, modyfikując dodatkowe zachowania.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="ecaf9-128">Istnieje możliwość kontrolowania informacji dotyczących odnajdywania przy użyciu określonych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="ecaf9-129">Oznacza to, użytkownik może kontrolować, czy można odnaleźć punktu końcowego i użytkownik może również oznaczać tego punktu końcowego z <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> i niestandardowych XML metadanych.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="ecaf9-130">Aby to zrobić, należy dodać użytkownika `behaviorConfiguration` właściwości do punktu końcowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="ecaf9-131">W takim przypadku następujące właściwość została dodana do punktu końcowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-131">In this case, the following property is added to the application endpoint.</span></span>  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 <span data-ttu-id="ecaf9-132">Teraz za pośrednictwem zachowanie elementu konfiguracji, można kontrolować atrybuty dotyczące odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="ecaf9-133">W takim przypadku dwa zakresy są dodawane do punktu końcowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
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
  
 <span data-ttu-id="ecaf9-134">Aby uzyskać więcej informacji na temat zakresów, zobacz [odnajdywania Znajdowanie i kryteria znajdowania](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="ecaf9-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="ecaf9-135">Można też kontrolować szczegółowe informacje dotyczące odnajdywania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="ecaf9-136">Jest to zrobić za pomocą <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="ecaf9-137">W tym przykładzie wersję protokołu używany jest modyfikowany oraz dodawanie `maxResponseDelay` atrybutu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="ecaf9-138">Poniżej znajduje się plik cała konfiguracja używana w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ecaf9-138">The following is the complete configuration file used in this example:</span></span>  
  
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
  
## <a name="client-configuration"></a><span data-ttu-id="ecaf9-139">Konfiguracja klienta</span><span class="sxs-lookup"><span data-stu-id="ecaf9-139">Client Configuration</span></span>  
 <span data-ttu-id="ecaf9-140">W pliku konfiguracyjnym aplikacji dla klienta `standardEndpoint` typu `dynamicEndpoint` służy do wykorzystywać odnajdywania, jak pokazano w poniższy fragment konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
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
  
 <span data-ttu-id="ecaf9-141">Gdy klient korzysta `dynamicEndpoint`, środowisko uruchomieniowe automatycznie wykonuje odnajdowanie.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="ecaf9-142">Różne ustawienia są używane podczas odnajdywania, takich jak te zdefiniowane `discoveryClientSettings` sekcji, która określa typ punktu końcowego odnajdywania do użycia:</span><span class="sxs-lookup"><span data-stu-id="ecaf9-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="ecaf9-143">Znajdź kryteria wyszukiwania usług:</span><span class="sxs-lookup"><span data-stu-id="ecaf9-143">The find criteria used to search for services:</span></span>  
  
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
  
 <span data-ttu-id="ecaf9-144">W tym przykładzie rozszerza tej funkcji i modyfikuje <xref:System.ServiceModel.Discovery.FindCriteria> używany przez klienta, a także niektóre właściwości standardowego `updDiscoveryEndpoint` używane do odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="ecaf9-145"><xref:System.ServiceModel.Discovery.FindCriteria> Są modyfikacji w celu użycia zakresu i określony `scopeMatchBy` algorytmu, jak również przerwanie niestandardowych kryteriów.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="ecaf9-146">Ponadto przykładzie przedstawiono również sposób klient może wysyłać elementów XML za pomocą `Probe` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="ecaf9-147">Ponadto niektóre zmiany zostały wprowadzone <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, takie jak wersja używanego protokołu i ustawienia specyficzne dla protokołu UDP, jak pokazano w następującym pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
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
  
 <span data-ttu-id="ecaf9-148">Poniżej znajduje się konfiguracji klienta pełną użyty w próbce.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-148">The following is the complete client configuration used in the sample.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="ecaf9-149">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="ecaf9-149">To use this sample</span></span>  
  
1.  <span data-ttu-id="ecaf9-150">W przykładzie użyto punktów końcowych HTTP i do uruchomienia, to przykładowa, odpowiednich list ACL adresu URL muszą zostać dodane zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="ecaf9-151">Następujące polecenie w pełnych uprawnień do wykonania należy dodać odpowiednich list ACL.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-151">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="ecaf9-152">Można zastąpić użytkownika domena i nazwa użytkownika dla następujących argumentów, jeśli polecenie nie działa, ponieważ jest.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-152">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="ecaf9-153">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-153">Build the solution.</span></span>  
  
3.  <span data-ttu-id="ecaf9-154">Uruchom plik wykonywalny usługi z katalogu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-154">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="ecaf9-155">Uruchom plik wykonywalny klienta.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-155">Run the client executable.</span></span> <span data-ttu-id="ecaf9-156">Należy pamiętać, że klient jest w stanie do lokalizowania usługi.</span><span class="sxs-lookup"><span data-stu-id="ecaf9-156">Note that the client is able to locate the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecaf9-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecaf9-157">See Also</span></span>
