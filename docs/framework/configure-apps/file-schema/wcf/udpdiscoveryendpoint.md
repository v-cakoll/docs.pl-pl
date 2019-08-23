---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: e6e567e8a657b4c1683ae4abfb14f96a0f272e4a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934582"
---
# <a name="udpdiscoveryendpoint"></a>\<udpDiscoveryEndpoint >
Ten element konfiguracji definiuje standardowy punkt końcowy, który jest wstępnie skonfigurowany dla operacji odnajdywania za pośrednictwem powiązania multiemisji UDP. Ten punkt końcowy ma stały kontrakt i obsługuje dwie wersje protokołu WS-Discovery. Ponadto ma stałe powiązanie UDP i domyślny adres określony w specyfikacjach WS-Discovery (WS-Discovery Kwiecień 2005 lub WS-Discovery V 1.1).  
  
 \<system.ServiceModel>  
\<standardEndpoints >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|discoveryMode|Ciąg określający tryb protokołu odnajdywania. Prawidłowe wartości to "AdHoc" i "Managed". W trybie zarządzanym protokół polega na serwerze proxy odnajdywania, który działa jako repozytorium usług, które można odnaleźć. Tryb ad hoc wymaga, aby protokół używał mechanizmu multiemisji UDP do znajdowania dostępnych usług. Ta wartość jest typu <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.|  
|discoveryVersion|Ciąg określający jedną z dwóch wersji protokołu WS-Discovery. Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005. Ta wartość jest typu <xref:System.ServiceModel.Discovery.DiscoveryVersion>.|  
|maxResponseDelay|Wartość TimeSpan określająca maksymalną wartość opóźnienia, przez którą Protokół odnajdywania będzie oczekiwać przed wysłaniem pewnych komunikatów, takich jak dopasowanie sondy lub rozpoznanie dopasowania.<br /><br /> Jeśli wszystkie ProbeMatches są wysyłane w tym samym czasie, może to być burza sieci. Aby temu zapobiec, ProbeMatches są wysyłane z losowym opóźnieniem między poszczególnymi ProbeMatch. Opóźnienie losowe jest z zakresu od 0 do wartości ustawionej przez ten atrybut. Jeśli ten atrybut ma wartość 0, komunikaty ProbeMatches są wysyłane w ścisłej pętli bez opóźnień. W przeciwnym razie komunikaty ProbeMatches są wysyłane z przypadkowym opóźnieniem, w którym łączny czas wysłania wszystkich komunikatów ProbeMatches nie przekracza maxResponseDelay. Ta wartość dotyczy tylko usług, ale nie jest używana przez klientów.|  
|multicastAddress|Identyfikator URI, który określa adres multiemisji używany do wysyłania i otrzymywania komunikatów odnajdowania. Wartość domyślna to adres multiemisji zgodny ze specyfikacją protokołu.|  
|`name`|Ciąg określający nazwę konfiguracji standardowego punktu końcowego. Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|Kolekcja ustawień, które umożliwiają skonfigurowanie transportu UDP dla punktu końcowego UDP.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints >](standardendpoints.md)|Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak usługa nasłuchuje komunikatów odnajdywania za pośrednictwem transportu multiemisji UDP.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="DiscoveryEndpoint"
              kind="udpDiscoveryEndpoint" />
  </service>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="DiscoveryEndpoint"
                        version="WSDiscoveryApril2005" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
