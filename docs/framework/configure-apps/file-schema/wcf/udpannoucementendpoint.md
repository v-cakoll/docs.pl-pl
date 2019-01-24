---
title: '&lt;udpAnnoucementEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: ab0e786ec4b21f25682c52fb7609d24e901f6eac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582438"
---
# <a name="ltudpannoucementendpointgt"></a>&lt;udpAnnoucementEndpoint&gt;
Ten element konfiguracji definiuje standardowy punkt końcowy, który jest używany przez usługi do wysłania komunikatów Anons z powiązania protokołu UDP. Ma stały kontraktu i obsługuje dwie wersje odnajdywania. Ponadto ma stałym powiązaniem UDP oraz domyślną wartość adresu określonych w specyfikacji WS-Discovery (WS-Discovery kwietnia 2005 lub w wersji 1.1 protokołu WS-Discovery). Możesz określić adres multiemisji na potrzeby wysyłania i odbierania wiadomości anonsów.  
  
\<system.ServiceModel>  
\<standardEndpoints>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|DiscoveryVersion|Ciąg, który określa jedno z dwóch wersji protokołu WS Discovery. Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005. Ta wartość jest typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.|  
|maxAnnouncementDelay|Wartość przedziału czasu, która określa maksymalną wartość opóźnienia protokołu odnajdowania będzie czekać przed wysłaniem wiadomości powitania. Przed wysłaniem wiadomości będą oczekiwać czasu losowego wartość z zakresu od 0 i wartość tego atrybutu. Ten atrybut służy do ustawiania małe, losowego opóźnienia, aby zapobiec nadmiarem sieci, gdy trafia do sieci i wszystkich usług pochodzą wróci do trybu online w tym samym czasie.|  
|multicastAddress|Identyfikator URI, który określa adres multiemisji służące do wysyłania i odbierania komunikatów odnajdywania. Wartość domyślna to adres multiemisji jako zgodna ze specyfikacją protokołu.|  
|nazwa|Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy. Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<udpTransportSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|Kolekcja ustawień, które umożliwiają skonfigurowanie transportu UDP dla punktu końcowego protokołu UDP.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano klienta nasłuchiwanie anonsu za pośrednictwem protokołu UDP transportu multiemisji za pomocą domyślny adres multiemisji i UDP transportu multiemisji przy użyciu określonego adresu multiemisji.  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="udpAnnouncementEndpointStandard"
              kind="udpAnnouncementEndpoint"
              bindingConfiguration="..." />
    <endpoint name="udpAnnouncementEndpoint2"
              kind="udpAnnouncementEndpoint"
              endpointConfiguration="AnnouncementConfiguration3702"
              bindingConfiguration="..." />
    ...
  </service>
</services>
<standardEndpoints>
  <udpAnnouncementEndpoint>
    <standardEndpoint name="AnnouncementConfiguration2"
                      version="WSDiscoveryApril2005"
                      multicastAddress="soap.udp://239.255.255.250:3703"/>
  </udpAnnouncementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
