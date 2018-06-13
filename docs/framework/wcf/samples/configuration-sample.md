---
title: Konfiguracja — przykład
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 26d8c0257f62079fefc8c6571774abf67506bbf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506153"
---
# <a name="configuration-sample"></a>Konfiguracja — przykład
W tym przykładzie przedstawiono korzystanie z pliku konfiguracji, aby stał się wykrywalny usługi.  
  
> [!NOTE]
>  W tym przykładzie implementuje odnajdywania w konfiguracji. Dla przykładu, który implementuje odnajdywania w kodzie, zobacz [podstawowe](../../../../docs/framework/wcf/samples/basic-sample.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Konfiguracja usługi  
 Plik konfiguracji w tym przykładzie przedstawiono dwie funkcje:  
  
-   Tworzenie usługi wykrywalny przez standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
-   Dostosowywanie informacji dotyczących odnajdywania, punkt końcowy aplikacji i dostosowanie niektórych ustawień związanych z odnajdywania standardowego punktu końcowego usługi.  
  
 Aby włączyć odnajdywanie, należy kilka zmian w pliku konfiguracyjnym aplikacji dla usługi:  
  
-   Punkt końcowy odnajdowania musi zostać dodany do `<service>` elementu. Jest to standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punktu końcowego. Jest to system punktu końcowego, który kojarzy środowiska uruchomieniowego usługi odnajdywania. Usługa odnajdywania nasłuchuje komunikatów na tym punkcie końcowym.  
  
-   A `<serviceDiscovery>` zachowanie jest dodawany do `<serviceBehaviors>` sekcji. To umożliwia usłudze odnaleziona w czasie wykonywania i używa już wspomniano w celu nasłuchiwania odnajdywania punkt końcowy odnajdowania `Probe` i `Resolve` wiadomości. Z tych dwóch dodatkami usługa jest łatwy w określonym punktem końcowym odnajdywania.  
  
 Poniższy fragment konfiguracji zawiera usługę z punktem końcowym aplikacji i punkt końcowy odnajdowania zdefiniowane:  
  
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
  
 Aby skorzystać z anonsów, należy dodać punktu końcowego powiadomienia. Aby to zrobić, należy zmodyfikować plik konfiguracji, jak pokazano w poniższym kodzie.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Dodawanie punktu końcowego powiadomienia do zachowania usługi odnajdywania tworzy domyślny klient anonsów dla usługi. Gwarantuje to, Usługa wyśle anons online i offline, gdy usługa jest otwarty i odpowiednio zamknięte.  
  
 Ten plik konfiguracji wykraczają poza tylko te prostych kroków, modyfikując dodatkowe zachowania. Istnieje możliwość kontrolowania informacji dotyczących odnajdywania przy użyciu określonych punktów końcowych. Oznacza to, użytkownik może kontrolować, czy można odnaleźć punktu końcowego i użytkownik może również oznaczać tego punktu końcowego z <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> i niestandardowych XML metadanych. Aby to zrobić, należy dodać użytkownika `behaviorConfiguration` właściwości do punktu końcowego aplikacji. W takim przypadku następujące właściwość została dodana do punktu końcowego aplikacji.  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 Teraz za pośrednictwem zachowanie elementu konfiguracji, można kontrolować atrybuty dotyczące odnajdywania. W takim przypadku dwa zakresy są dodawane do punktu końcowego aplikacji.  
  
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
  
 Można też kontrolować szczegółowe informacje dotyczące odnajdywania punktu końcowego. Jest to zrobić za pomocą <xref:System.ServiceModel.Configuration.StandardEndpointsSection>. W tym przykładzie wersję protokołu używany jest modyfikowany oraz dodawanie `maxResponseDelay` atrybutu, jak pokazano w poniższym przykładzie kodu.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 Poniżej znajduje się plik cała konfiguracja używana w tym przykładzie:  
  
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
 W pliku konfiguracyjnym aplikacji dla klienta `standardEndpoint` typu `dynamicEndpoint` służy do wykorzystywać odnajdywania, jak pokazano w poniższy fragment konfiguracji.  
  
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
  
 Gdy klient korzysta `dynamicEndpoint`, środowisko uruchomieniowe automatycznie wykonuje odnajdowanie. Różne ustawienia są używane podczas odnajdywania, takich jak te zdefiniowane `discoveryClientSettings` sekcji, która określa typ punktu końcowego odnajdywania do użycia:  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Znajdź kryteria wyszukiwania usług:  
  
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
  
 W tym przykładzie rozszerza tej funkcji i modyfikuje <xref:System.ServiceModel.Discovery.FindCriteria> używany przez klienta, a także niektóre właściwości standardowego `updDiscoveryEndpoint` używane do odnajdywania. <xref:System.ServiceModel.Discovery.FindCriteria> Są modyfikacji w celu użycia zakresu i określony `scopeMatchBy` algorytmu, jak również przerwanie niestandardowych kryteriów. Ponadto przykładzie przedstawiono również sposób klient może wysyłać elementów XML za pomocą `Probe` wiadomości. Ponadto niektóre zmiany zostały wprowadzone <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, takie jak wersja używanego protokołu i ustawienia specyficzne dla protokołu UDP, jak pokazano w następującym pliku konfiguracji.  
  
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
  
 Poniżej znajduje się konfiguracji klienta pełną użyty w próbce.  
  
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
  
1.  W przykładzie użyto punktów końcowych HTTP i do uruchomienia, to przykładowa, odpowiednich list ACL adresu URL muszą zostać dodane zobacz [Konfigurowanie protokołów HTTP i HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) szczegółowe informacje. Następujące polecenie w pełnych uprawnień do wykonania należy dodać odpowiednich list ACL. Można zastąpić użytkownika domena i nazwa użytkownika dla następujących argumentów, jeśli polecenie nie działa, ponieważ jest. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Skompiluj rozwiązanie.  
  
3.  Uruchom plik wykonywalny usługi z katalogu kompilacji.  
  
4.  Uruchom plik wykonywalny klienta. Należy pamiętać, że klient jest w stanie do lokalizowania usługi.  
  
## <a name="see-also"></a>Zobacz też
