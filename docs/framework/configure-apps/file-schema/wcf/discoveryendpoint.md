---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: d1a3371872f5587a682b8242c29b71808508ca3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704059"
---
# <a name="discoveryendpoint"></a>\<discoveryEndpoint>

Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem odkrywania. Po dodaniu do konfiguracji usługi, określa, gdzie nasłuchiwać komunikatów odnajdywania. Po dodaniu do konfiguracji klienta określa, gdzie wysyłać zapytania odnajdywania.  
  
\<system.serviceModel>  
\<standardEndpoints>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty

| Atrybut        | Opis |  
| ---------------- | ----------- |  
| discoveryMode    | Ciąg, który określa tryb protokół RDP. Prawidłowe wartości to "Ad hoc" i "Zarządzane". W trybie zarządzanym protokołu zależy od serwera Proxy odnajdywania, który działa jako repozytorium wykrywalny usług. W trybie ad hoc wymagane używany protokół UDP mechanizm multiemisji, aby znaleźć dostępne usługi. Aby uzyskać więcej informacji na temat właściwości, zobacz <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>. |  
| DiscoveryVersion | Ciąg, który określa jedno z dwóch wersji protokołu WS Discovery. Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005. Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>. |  
| maxResponseDelay | Wartość przedziału czasu, która określa maksymalną wartość opóźnienia protokołu odnajdowania będzie czekać przed wysłaniem niektóre komunikaty, takie jak dopasowanie sondowania lub rozwiązać dopasowania.<br /><br /> Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może spowodować storm sieci. Aby temu zapobiec, ProbeMatches są wysyłane z losowo wybranym opóźnieniem między każdym ProbeMatch. Opóźnienie losowe jest z zakresu od 0 do wartość ustawioną przy użyciu tego atrybutu. Jeśli ten atrybut jest ustawiony na wartość 0, ProbeMatches komunikaty są wysyłane w pętli bez żadnego opóźnienia. W przeciwnym razie wiadomości ProbeMatches są wysyłane z pewne opóźnienie losowe w taki sposób, że całkowity czas wykonywania, aby wysłać wszystkie wiadomości ProbeMatches nie przekracza maxResponseDelay. Ta wartość ma zastosowanie tylko dla usług, nie jest używany przez klientów. |  
| `name`           | Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy. Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji. |  
  
### <a name="child-elements"></a>Elementy podrzędne

Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |  
| ------- | ----------- |  
| [\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe. |  
  
## <a name="example"></a>Przykład

Poniższy przykład pokazuje usługi nasłuchiwać komunikatów odnajdywania za pośrednictwem elementu równorzędnego netto transportu multiemisji. Przykład jawnie określa WS-Discovery w wersji 2005 kwietnia.  
  
Konfiguracja standardowego punktu końcowego jest zdefiniowana na usługę i nie może być współużytkowane przez usługę. Jeśli inna usługa chce mieć ten sam punkt końcowy odnajdywania, tę samą konfigurację musi można dodawać do sekcji tej usługi.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="peerNetDiscovery"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              kind="discoveryEndpoint"
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  </service>
</services>
<standardEndpoints>
  <discoveryEndpoint>
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"
                      version="WSDiscoveryApril2005" />
  </discoveryEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
