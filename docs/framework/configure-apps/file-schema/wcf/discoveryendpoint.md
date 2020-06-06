---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32b14f8fb3235040a51455f2099a403c8312c699
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855392"
---
# \<discoveryEndpoint>

Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem odnajdowania. Po dodaniu do konfiguracji usługi określa miejsce nasłuchiwania komunikatów odnajdowania. Po dodaniu do konfiguracji klienta określa, gdzie mają być wysyłane zapytania odnajdywania.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**  
  
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
| Odnajdywanie    | Ciąg określający tryb protokołu odnajdywania. Prawidłowe wartości to "AdHoc" i "Managed". W trybie zarządzanym protokół polega na serwerze proxy odnajdywania, który działa jako repozytorium usług, które można odnaleźć. Tryb ad hoc wymaga, aby protokół używał mechanizmu multiemisji UDP do znajdowania dostępnych usług. Aby uzyskać więcej informacji na temat właściwości, zobacz <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A> . |  
| discoveryVersion | Ciąg określający jedną z dwóch wersji protokołu WS-Discovery. Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005. Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>. |  
| maxResponseDelay | Wartość TimeSpan określająca maksymalną wartość opóźnienia, przez którą Protokół odnajdywania będzie oczekiwać przed wysłaniem pewnych komunikatów, takich jak dopasowanie sondy lub rozpoznanie dopasowania.<br /><br /> Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może to być burza sieci. Aby temu zapobiec, ProbeMatches są wysyłane z losowym opóźnieniem między poszczególnymi ProbeMatch. Opóźnienie losowe jest z zakresu od 0 do wartości ustawionej przez ten atrybut. Jeśli ten atrybut ma wartość 0, komunikaty ProbeMatches są wysyłane w ścisłej pętli bez opóźnień. W przeciwnym razie komunikaty ProbeMatches są wysyłane z przypadkowym opóźnieniem, w którym łączny czas wysłania wszystkich komunikatów ProbeMatches nie przekracza maxResponseDelay. Ta wartość dotyczy tylko usług, ale nie jest używana przez klientów. |  
| `name`           | Ciąg określający nazwę konfiguracji standardowego punktu końcowego. Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją. |  
  
### <a name="child-elements"></a>Elementy podrzędne

Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |  
| ------- | ----------- |  
| [\<standardEndpoints>](standardendpoints.md) | Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt). |  
  
## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak usługa nasłuchuje komunikatów odnajdywania za pośrednictwem transportowego ruchu multiemisji sieci równorzędnej. Przykład jawnie określa wersję WS-Discovery z kwietnia 2005.  
  
Standardowa konfiguracja punktu końcowego jest definiowana na usługę i nie może być współużytkowana przez usługę. Jeśli inna usługa chce mieć ten sam punkt końcowy odnajdywania, należy dodać tę samą konfigurację do sekcji tej usługi.  
  
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
