---
title: '&lt;AnnouncementEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: 8e180d53260ccf3364ab3c8d7b076f78917526d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729882"
---
# <a name="ltannouncementendpointgt"></a>&lt;AnnouncementEndpoint&gt;
Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem zawiadomieniowym. Usługa może opcjonalnie ogłaszają jego dostępność, wysyłając anonse online i offline, po otwarciu lub zamknięciu odpowiednio. Usługa Windows Communication Foundation (WCF) określa punkty końcowe anonsu w [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elementu i używa AnnouncementClient przeprowadzić anonsów. Klient chcą nasłuchiwanie anonsu z innej usługi faktycznie działa jako usługa WCF; dlatego musisz skonfigurować punkty końcowe anonsu dla tego klienta w [ \<usługi >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) sekcji.  
  
\<system.ServiceModel>  
\<standardEndpoints>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
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
|nazwa|Ciąg, który określa nazwę konfiguracji standardowy punkt końcowy. Nazwa jest używana w `endpointConfiguration` atrybut punktu końcowego usługi do łączenia standardowy punkt końcowy do jego konfiguracji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowane punkty końcowe z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano nasłuchiwanie komunikaty anonsów za pośrednictwem protokołu http i peernet klienta.  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="httpAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="basicHttpBinding"
              address="announcements" />
    <endpoint name="peerNetAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  ...
  </service>
</services>

<standardEndpoints>
  <announcementEndpoint>
    <standardEndpoint name="httpAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
    <standardEndpoint name="peerNetAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
  </announcementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
