---
title: Konfiguracja — przykład
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 6d84085d06da117ebf13fa4bb714513aacc3abd6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594728"
---
# <a name="configuration-sample"></a>Konfiguracja — przykład
Ten przykład ilustruje użycie pliku konfiguracji w celu odnalezienia usługi.  
  
> [!NOTE]
> Ten przykład implementuje odnajdywanie w konfiguracji. Przykład, który implementuje odnajdywanie w kodzie, znajduje się w temacie [Basic](basic-sample.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Konfiguracja usługi  
 Plik konfiguracji w tym przykładzie ilustruje dwie funkcje:  
  
- Umożliwienie odnajdywania usługi w warstwie Standardowa <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> .  
  
- Dostosowanie informacji dotyczących odnajdywania dla punktu końcowego aplikacji usługi i dostosowanie niektórych ustawień związanych z odnajdywaniem w standardowym punkcie końcowym.  
  
 Aby włączyć odnajdywanie, należy wprowadzić kilka zmian w pliku konfiguracyjnym aplikacji dla usługi:  
  
- Do elementu należy dodać punkt końcowy odnajdywania `<service>` . Jest to standardowy <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> punkt końcowy. Jest to systemowy punkt końcowy, który jest skojarzony ze środowiskiem uruchomieniowym z usługą odnajdywania. Usługa odnajdywania nasłuchuje komunikatów w tym punkcie końcowym.  
  
- `<serviceDiscovery>`Do sekcji dodano zachowanie `<serviceBehaviors>` . Pozwala to na odnalezienie usługi w czasie wykonywania i użycie punktu końcowego odnajdywania wspomnianego wcześniej do nasłuchiwania odnajdywania `Probe` i `Resolve` komunikatów. Za pomocą tych dwóch dodatków usługa jest wykrywalna w określonym punkcie końcowym odnajdywania.  
  
 Poniższy fragment konfiguracji przedstawia usługę z punktem końcowym aplikacji oraz zdefiniowanym punktem końcowym odnajdywania:  
  
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
  
 Aby skorzystać z anonsów, musisz dodać punkt końcowy anonsu. W tym celu należy zmodyfikować plik konfiguracji, jak pokazano w poniższym kodzie.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Dodanie punktu końcowego anonsu do zachowania usługi odnajdywania powoduje utworzenie domyślnego klienta anonsu dla usługi. Gwarantuje to, że usługa wyśle powiadomienie online i offline, gdy usługa zostanie odpowiednio otwarta i ZAMKNIĘTA.  
  
 Ten plik konfiguracji wykracza poza tylko te proste kroki poprzez modyfikację dodatkowych zachowań. Można kontrolować informacje związane z odnajdywaniem za pomocą określonych punktów końcowych. Oznacza to, że użytkownik może kontrolować, czy można odnaleźć punkt końcowy, a użytkownik może również oznaczyć ten punkt końcowy za pomocą <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> i niestandardowych metadanych XML. W tym celu użytkownik musi dodać `behaviorConfiguration` Właściwość do punktu końcowego aplikacji. W takim przypadku następująca właściwość jest dodawana do punktu końcowego aplikacji.  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 Teraz za pomocą elementu konfiguracja zachowania można kontrolować atrybuty związane z odnajdywaniem. W takim przypadku dwa zakresy są dodawane do punktu końcowego aplikacji.  
  
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
  
 Aby uzyskać więcej informacji na temat zakresów, zobacz [odnajdywanie Znajdź i kryteria znajdowania](../feature-details/discovery-find-and-findcriteria.md).  
  
 Można również kontrolować konkretne szczegóły punktu końcowego odnajdywania. Jest to realizowane za pomocą <xref:System.ServiceModel.Configuration.StandardEndpointsSection> . W tym przykładzie użyta wersja protokołu została zmodyfikowana, a także dodany `maxResponseDelay` atrybut, jak pokazano w poniższym przykładzie kodu.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 Poniżej znajduje się kompletny plik konfiguracji, który jest używany w tym przykładzie:  
  
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
 W pliku konfiguracyjnym aplikacji dla klienta programu `standardEndpoint` Typ `dynamicEndpoint` jest używany do korzystania z odnajdywania, jak pokazano w poniższym fragmencie kodu.  
  
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
  
 Gdy klient korzysta z programu `dynamicEndpoint` , środowisko uruchomieniowe automatycznie wykonuje odnajdywanie. Podczas odnajdywania są używane różne ustawienia, takie jak te zdefiniowane w `discoveryClientSettings` sekcji, które określają typ punktu końcowego odnajdywania do użycia:  
  
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
  
 Ten przykład rozszerza tę funkcję i modyfikuje <xref:System.ServiceModel.Discovery.FindCriteria> używane przez klienta, a także kilka właściwości standardu `updDiscoveryEndpoint` używanego do odnajdywania. <xref:System.ServiceModel.Discovery.FindCriteria>Są one modyfikowane w celu korzystania z zakresu i określonego `scopeMatchBy` algorytmu, a także niestandardowych kryteriów zakończenia. Ponadto przykład pokazuje również, jak klient może wysyłać elementy XML przy użyciu `Probe` komunikatów. Na koniec wprowadzono pewne zmiany w <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> programie, takie jak wersja używanego protokołu i ustawienia specyficzne dla UDP, jak pokazano w następującym pliku konfiguracyjnym.  
  
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
  
 Poniżej znajduje się kompletna konfiguracja klienta użyta w przykładzie.  
  
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
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1. Ten przykład korzysta z punktów końcowych HTTP i do uruchomienia tego przykładu należy dodać prawidłowe listy ACL adresów URL. Aby uzyskać więcej informacji, zobacz [Konfigurowanie protokołów HTTP i https](../feature-details/configuring-http-and-https.md). Wykonanie następującego polecenia z podwyższonym poziomem uprawnień powinno spowodować dodanie odpowiednich list ACL. Można zastąpić domenę i nazwę użytkownika dla następujących argumentów, jeśli polecenie nie działa zgodnie z oczekiwaniami. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Skompiluj rozwiązanie.  
  
3. Uruchom plik wykonywalny usługi z katalogu kompilacji.  
  
4. Uruchom plik wykonywalny klienta. Należy pamiętać, że klient może zlokalizować usługę.  
