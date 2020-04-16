---
title: Konfiguracja — przykład
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 52747e6d964022d5028b0edb91dc8bc0ac0e82bc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463959"
---
# <a name="configuration-sample"></a>Konfiguracja — przykład
W tym przykładzie pokazano użycie pliku konfiguracji, aby usługa wykrywalne.  
  
> [!NOTE]
> Ten przykład implementuje odnajdowanie w konfiguracji. Aby uzyskać przykład implementujący odnajdowanie w kodzie, zobacz [Podstawowe](../../../../docs/framework/wcf/samples/basic-sample.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Konfiguracja usługi  
 Plik konfiguracyjny w tym przykładzie pokazuje dwie funkcje:  
  
- Uczynienie usługi wykrywalną w <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>standardzie.  
  
- Dostosowywanie informacji związanych z odnajdywaniem dla punktu końcowego aplikacji usługi i dostosowywanie niektórych ustawień związanych z odnajdywaniem w standardowym punkcie końcowym.  
  
 Aby włączyć odnajdowanie, należy wnieść kilka zmian w pliku konfiguracji aplikacji dla usługi:  
  
- Punkt końcowy odnajdywania musi zostać dodany do `<service>` elementu. Jest to <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standardowy punkt końcowy. Jest to punkt końcowy systemu, który środowisko wykonawcze kojarzy z usługą odnajdywania. Usługa odnajdowania nasłuchuje wiadomości w tym punkcie końcowym.  
  
- Zachowanie `<serviceDiscovery>` zostanie dodane `<serviceBehaviors>` do sekcji. Dzięki temu usługa ma zostać wykryta w czasie wykonywania i używa punktu końcowego odnajdywania wymienionych wcześniej do nasłuchiwania odnajdywania `Probe` i `Resolve` wiadomości. Z tych dwóch dodatków usługa jest wykrywalny w punkcie końcowym odnajdywania określonych.  
  
 Następujący fragment kodu konfiguracji przedstawia usługę z punktem końcowym aplikacji i zdefiniowanym punktem końcowym odnajdywania:  
  
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
  
 Aby skorzystać z anonsów, należy dodać punkt końcowy anonsu. Aby to zrobić, zmodyfikuj plik konfiguracyjny, jak pokazano w poniższym kodzie.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Dodanie punktu końcowego anonsu do zachowania usługi odnajdywania tworzy domyślnego klienta anonsu dla usługi. Gwarantuje to, że usługa wyśle ogłoszenie online i offline, gdy usługa zostanie otwarta i zamknięta odpowiednio.  
  
 Ten plik konfiguracyjny wykracza poza te proste kroki, modyfikując dodatkowe zachowania. Możliwe jest kontrolowanie informacji związanych z odnajdywania przy użyciu określonych punktów końcowych. Oznacza to, że użytkownik może kontrolować, czy punkt końcowy można odnajdować, a użytkownik może również oznaczyć ten punkt końcowy za pomocą <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> i niestandardowych metadanych XML. Aby to zrobić, użytkownik `behaviorConfiguration` musi dodać właściwość do punktu końcowego aplikacji. W takim przypadku następująca właściwość jest dodawana do punktu końcowego aplikacji.  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 Teraz za pośrednictwem elementu konfiguracji zachowania można kontrolować atrybuty związane z odnajdywania. W takim przypadku dwa zakresy są dodawane do punktu końcowego aplikacji.  
  
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
  
 Aby uzyskać więcej informacji na temat zakresów, zobacz [Odnajdowanie i Znajdźkryterię](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).  
  
 Można również kontrolować szczegółowe informacje o punkcie końcowym odnajdywania. Odbywa się to <xref:System.ServiceModel.Configuration.StandardEndpointsSection>za pośrednictwem . W tym przykładzie wersja używanego protokołu jest modyfikowana, a także dodawanie atrybutu, `maxResponseDelay` jak pokazano w poniższym przykładzie kodu.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 Poniżej przedstawiono kompletny plik konfiguracyjny użyty w tym przykładzie:  
  
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
 W pliku konfiguracji aplikacji dla `standardEndpoint` klienta `dynamicEndpoint` typu jest używany do wykorzystania odnajdywania, jak pokazano w poniższym fragmentie konfiguratu.  
  
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
  
 Gdy klient używa `dynamicEndpoint`, środowisko wykonawcze wykonuje odnajdowanie automatycznie. Podczas odnajdowania są używane różne `discoveryClientSettings` ustawienia, takie jak te zdefiniowane w sekcji, która określa typ punktu końcowego odnajdywania, którego należy użyć:  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Kryteria wyszukiwania używane do wyszukiwania usług:  
  
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
  
 Ten przykład rozszerza tę funkcję <xref:System.ServiceModel.Discovery.FindCriteria> i modyfikuje używane przez klienta, a `updDiscoveryEndpoint` także niektóre właściwości standardu używanego do odnajdowania. Są <xref:System.ServiceModel.Discovery.FindCriteria> modyfikowane w celu użycia `scopeMatchBy` zakresu i określonego algorytmu, a także kryteria zakończenia niestandardowego. Ponadto w przykładzie pokazano również, jak klient `Probe` może wysyłać elementy XML przy użyciu wiadomości. Wreszcie, niektóre zmiany są <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>wprowadzane do , takich jak wersja używanego protokołu i ustawienia specyficzne dla UDP, jak pokazano w poniższym pliku konfiguracyjnym.  
  
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
  
 Poniżej przedstawiono pełną konfigurację klienta używaną w przykładzie.  
  
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
</configuration>
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tej próbki  
  
1. W tym przykładzie użyto punktów końcowych HTTP i do uruchomienia tego przykładu należy dodać odpowiednie listy ACL adresów URL. Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołu HTTP i HTTPS](../feature-details/configuring-http-and-https.md). Wykonywanie następującego polecenia z podwyższonym poziomem uprawnień należy dodać odpowiednie listy ACL. Jeśli polecenie nie działa zgodnie z oczekiwaniami, można zastąpić domenę i nazwę użytkownika następującymi argumentami. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Skompiluj rozwiązanie.  
  
3. Uruchom plik wykonywalny usługi z katalogu kompilacji.  
  
4. Uruchom plik wykonywalny klienta. Należy zauważyć, że klient jest w stanie zlokalizować usługę.  
