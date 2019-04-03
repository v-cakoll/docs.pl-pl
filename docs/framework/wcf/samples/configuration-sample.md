---
title: Konfiguracja — przykład
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: b999c84fc6fd4d1a367b4e1476de8376858008a2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814396"
---
# <a name="configuration-sample"></a>Konfiguracja — przykład
Niniejszy przykład pokazuje użycie pliku konfiguracji, aby stał się wykrywalny usługi.  
  
> [!NOTE]
>  W tym przykładzie implementuje odnajdywania w konfiguracji. Dla przykładu, który implementuje odnajdywania w kodzie, zobacz [podstawowe](../../../../docs/framework/wcf/samples/basic-sample.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Konfiguracja usługi  
 Plik konfiguracji, w tym przykładzie pokazano dwie funkcje:  
  
-   Dzięki czemu usługa stała się wykrywalna za pośrednictwem standardowego <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
-   Dostosowywanie informacje dotyczące odnajdywania dla punktu końcowego aplikacji i dostosowanie niektórych ustawień związanych z odnajdywania na standardowy punkt końcowy usługi.  
  
 Aby włączyć odnajdywanie, kilka zmian, musi nastąpić w pliku konfiguracji aplikacji dla usługi:  
  
-   Punkt końcowy odnajdywania musi zostać dodany do `<service>` elementu. Jest to standardowy <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punktu końcowego. Jest to punkt końcowy systemu kojarzące przez środowisko uruchomieniowe usługi odnajdywania. Usługa odnajdywania nasłuchuje komunikatów w tym punkcie końcowym.  
  
-   A `<serviceDiscovery>` zachowanie jest dodawany do `<serviceBehaviors>` sekcji. To pozwala usłudze, które mają zostać odnalezione w czasie wykonywania i używa punkt końcowy odnajdowania wymienionych wcześniej do nasłuchiwania pod kątem odnajdywania `Probe` i `Resolve` wiadomości. Z tych dwóch dodatki wykrywalny na punkt końcowy odnajdowania określony jest usługa.  
  
 Poniższy fragment konfiguracji przedstawia usługi z punktu końcowego aplikacji i punkt końcowy odnajdowania zdefiniowane:  
  
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
  
 Aby móc korzystać z anonsów, należy dodać punkt końcowy anonsu. Aby to zrobić, zmodyfikuj plik konfiguracji, jak pokazano w poniższym kodzie.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Dodawanie punktu końcowego anonsu do zachowania usługi odnajdywania tworzy domyślny klient anonsów, dla usługi. Gwarantuje to, usługa będzie wysyłać anonsu online i offline, gdy usługa jest otwarte i zamknięte odpowiednio.  
  
 Ten plik konfiguracyjny wykracza poza tylko te proste kroki, modyfikując zachowania dodatkowe. Istnieje możliwość kontrolowania informacje dotyczące odnajdowania przy użyciu określonych punktów końcowych. Oznacza to, czy można odnaleźć punktu końcowego i użytkownika można zaznaczyć tego punktu końcowego za pomocą można kontrolować użytkownika <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> i niestandardowych metadanych XML. Aby to zrobić, użytkownik musi dodać `behaviorConfiguration` właściwości punktu końcowego aplikacji. W tym przypadku poniższy właściwość została dodana do punktu końcowego aplikacji.  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 Teraz za pośrednictwem elementu konfiguracji zachowanie, możesz kontrolować atrybuty dotyczące odnajdywania. W takim przypadku dwa zakresy są dodawane do punktu końcowego aplikacji.  
  
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
  
 Aby uzyskać więcej informacji na temat zakresów, zobacz [odnajdywania Znajdowanie i kryteria znajdowania](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).  
  
 Można też sterować szczegóły dotyczące punktu końcowego odnajdywania. Jest to realizowane <xref:System.ServiceModel.Configuration.StandardEndpointsSection>. W tym przykładzie wersję protokół używany jest modyfikowany, a także dodawanie `maxResponseDelay` atrybutu, jak pokazano w poniższym przykładzie kodu.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 Poniżej znajduje się plik kompletna Konfiguracja użytego w tym przykładzie:  
  
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
  
## <a name="client-configuration"></a>Konfiguracja klienta  
 W pliku konfiguracji aplikacji dla klienta `standardEndpoint` typu `dynamicEndpoint` umożliwia korzystanie z odnajdywania, jak pokazano w poniższym fragmencie kodu konfiguracji.  
  
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
  
 Gdy klient korzysta `dynamicEndpoint`, środowisko uruchomieniowe wykonuje automatyczne odnajdowanie. Różne ustawienia są używane podczas odnajdywania, takie jak te zdefiniowane `discoveryClientSettings` sekcji, która określa typ punkt końcowy odnajdywania do użycia:  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Kryteria znajdowania umożliwia wyszukiwanie usług:  
  
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
  
 W tym przykładzie ta funkcja rozszerza i modyfikuje <xref:System.ServiceModel.Discovery.FindCriteria> używany przez klienta, a także niektóre właściwości standardowe `updDiscoveryEndpoint` używane na potrzeby odnajdywania. <xref:System.ServiceModel.Discovery.FindCriteria> Są modyfikowane w celu użycia zakres i określonego `scopeMatchBy` algorytm, a także kryteriów niestandardowych zakończenia. Ponadto próbka pokazuje również, jak klient może wysłać elementów XML przy użyciu `Probe` wiadomości. Ponadto niektóre zmiany zostały wprowadzone <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, takie jak wersja używanego protokołu i ustawienia specyficzne dla protokołu UDP, jak pokazano w następującym pliku konfiguracji.  
  
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
  
 Poniżej przedstawiono konfigurację klienta pełną użytemu w przykładzie.  
  
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
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  W tym przykładzie użyto punktów końcowych HTTP i przeprowadzić to przykład, odpowiednie listy ACL adresu URL muszą zostać dodane zobacz [Konfigurowanie protokołów HTTP i HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Aby uzyskać szczegółowe informacje. Wykonując następujące polecenie w podwyższonym poziomem uprawnień, należy dodać odpowiednie listy ACL. Można zastąpić Twoja domena i nazwa użytkownika o wprowadzenie następujących argumentów, jeśli polecenie nie działa, ponieważ jest. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Skompiluj rozwiązanie.  
  
3.  Uruchomić pliku wykonywalnego usługi z katalogu kompilacji.  
  
4.  Uruchom ten plik. Należy pamiętać, że klient jest w stanie do lokalizowania usługi.  
  
