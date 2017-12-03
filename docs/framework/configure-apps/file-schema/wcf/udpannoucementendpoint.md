---
title: '&lt;udpAnnoucementEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8dad3ac58b92c70f32b8a0e6a81f8ebb2b23f25c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltudpannoucementendpointgt"></a>&lt;udpAnnoucementEndpoint&gt;
Ten element konfiguracji definiuje standardowy punkt końcowy jest używany przez usługi do wysłania komunikatów Anons powiązania protokołu UDP. Ma stały kontraktu i obsługuje dwie wersje odnajdywania. Ponadto ma stałym powiązaniem UDP oraz domyślną wartość adresu zgodnie ze specyfikacją WS-Discovery (WS-Discovery kwietnia 2005 lub WS-Discovery w wersji 1.1). Można określić adres multiemisji do użycia na potrzeby wysyłania i odbierania wiadomości powiadomienia.  
  
\<System. ServiceModel >  
\<standardEndpoints >  
  
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
|discoveryVersion|Ciąg, który określa jeden z dwóch wersji protokołu WS-Discovery. Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005. Ta wartość jest typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.|  
|maxAnnouncementDelay|Wartość Timespan określający maksymalną wartość opóźnienia protokołu Discovery będzie czekać przed wysłaniem wiadomości powitania. Przed wysłaniem wiadomości będą oczekiwać losowo wartość z zakresu od 0 i wartość tego atrybutu. Ten atrybut służy do ustawiania małe, losowe opóźnienie do uniknięcia sieci "burz", gdy sieć trafia i wszystkich usług powróci w tym samym czasie.|  
|multicastAddress|Identyfikator URI, który określa adres multiemisji do użycia na potrzeby wysyłania i odbierania wiadomości odnajdywania. Wartość domyślna to adres multiemisji jako zgodna ze specyfikacją protokołu.|  
|nazwa|Ciąg określający nazwę Konfiguracja standardowego punktu końcowego. Nazwa jest używana w `endpointConfiguration` atrybutu punktu końcowego usługi, aby połączyć standardowy punkt końcowy do konfiguracji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<udpTransportSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|Kolekcja ustawień, które pozwalają na skonfigurowanie transportu UDP dla punktu końcowego protokołu UDP.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano klienta nasłuchiwanie powiadomienia za pośrednictwem protokołu UDP multiemisji transportu z domyślny adres multiemisji i UDP multiemisji transportu z określonym adresem multiemisji.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
