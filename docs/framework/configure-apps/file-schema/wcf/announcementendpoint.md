---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: aa4cd8f4d7dcfa438ede71c394f1d0b0ac6faa50
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926550"
---
# <a name="announcementendpoint"></a>\<announcementEndpoint >
Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem anonsu. Usługa może opcjonalnie ogłaszać swoją dostępność, wysyłając wiadomość w trybie online i w trybie offline, gdy zostanie ona otwarta lub ZAMKNIĘTA odpowiednio. Usługa Windows Communication Foundation (WCF) określa punkty końcowe anonsu w [ \<elemencie servicediscovery >](servicediscovery.md) i używa AnnouncementClient do wykonywania anonsów. Klient, który chce nasłuchiwać anonsu z innej usługi, działa jako usługa WCF. w tym celu należy skonfigurować punkty końcowe anonsu dla tego klienta w [ \<sekcji > usług](services.md) .  
  
\<system.ServiceModel>  
\<standardEndpoints >  
  
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
|discoveryVersion|Ciąg określający jedną z dwóch wersji protokołu WS-Discovery. Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005. Ta wartość jest typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.|  
|maxAnnouncementDelay|Wartość TimeSpan określająca maksymalną wartość opóźnienia, przez którą Protokół odnajdywania będzie oczekiwać przed wysłaniem komunikatu powitania. Komunikaty będą oczekiwać na losową wartość czasu z przedziału od 0 do wartości tego atrybutu przed wysłaniem. Ten atrybut służy do ustawiania małego, losowego opóźnienia, aby zapobiec burzom sieci, gdy sieć przejdzie w tryb online, a wszystkie usługi są w tym samym czasie przywracane.|  
|nazwa|Ciąg określający nazwę konfiguracji standardowego punktu końcowego. Nazwa jest używana w `endpointConfiguration` atrybucie punktu końcowego usługi, aby połączyć standardowy punkt końcowy z jego konfiguracją.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints >](standardendpoints.md)|Kolekcja standardowych punktów końcowych, które są wstępnie zdefiniowanymi punktami końcowymi z co najmniej jedną z jej właściwości (adres, powiązanie, kontrakt).|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, że klient nasłuchuje komunikatów za pośrednictwem protokołów HTTP i PEERNET.  
  
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
