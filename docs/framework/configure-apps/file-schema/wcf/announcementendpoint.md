---
title: '&lt;announcementEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d49ea0b2dbabd5e747d912b76e493559b2a96ee7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltannouncementendpointgt"></a>&lt;announcementEndpoint&gt;
Ten element konfiguracji definiuje standardowy punkt końcowy ze stałym kontraktem zawiadomieniowym. Usługi można opcjonalnie ogłaszamy jego dostępność, wysyłając wiadomość online i offline powiadomienia, gdy jest otwarty lub zamknięty odpowiednio. A [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usługi określa punktów końcowych powiadomienia w [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element i używa AnnouncementClient przeprowadzić anonsów. Chcą nasłuchiwania dla anonsu z innej usługi rzeczywiście działa jako klient [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi; w związku z tym należy skonfigurować punktów końcowych powiadomienia dla tego klienta w [ \<usługi >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) sekcji.  
  
\<System. ServiceModel >  
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
|discoveryVersion|Ciąg, który określa jeden z dwóch wersji protokołu WS-Discovery. Prawidłowe wartości to WSDiscovery11 i WSDiscoveryApril2005. Ta wartość jest typu <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.|  
|maxAnnouncementDelay|Wartość Timespan określający maksymalną wartość opóźnienia protokołu Discovery będzie czekać przed wysłaniem wiadomości powitania. Przed wysłaniem wiadomości będą oczekiwać losowo wartość z zakresu od 0 i wartość tego atrybutu. Ten atrybut służy do ustawiania małe, losowe opóźnienie do uniknięcia sieci "burz", gdy sieć trafia i wszystkich usług powróci w tym samym czasie.|  
|nazwa|Ciąg określający nazwę Konfiguracja standardowego punktu końcowego. Nazwa jest używana w `endpointConfiguration` atrybutu punktu końcowego usługi, aby połączyć standardowy punkt końcowy do konfiguracji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Zbiór standardowych punktów końcowych, które są wstępnie zdefiniowanych punktów końcowych z jedną lub więcej z ich właściwości (adres, powiązanie, kontrakt) stałe.|  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
