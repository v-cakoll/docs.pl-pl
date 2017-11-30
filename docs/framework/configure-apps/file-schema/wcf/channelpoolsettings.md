---
title: '&lt;channelPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 44e79c7af470cefead8bcfb0ef96606ecde30383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltchannelpoolsettingsgt"></a>&lt;channelPoolSettings&gt;
Określa ustawienia puli kanału dla niestandardowego powiązania.  
  
 \<system.serviceModel >  
\<powiązania >  
\<customBinding >  
\<Powiązanie >  
\<oneWay >  
\<channelPoolSettings >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<channelPoolSettings  
    idleTimeout"TimeSpan"  
        leaseTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`idleTimeout`|Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas kanałów w puli może być bezczynne, zanim zostanie rozłączone. Wartość domyślna to 00:02:00.|  
|`leaseTimeout`|A <xref:System.TimeSpan> , który określa przedział czasu, po którym kanał, gdy zwrócony do puli, jest zamknięty. Wartość domyślna to 00:10:00.|  
|`maxOutboundChannelsPerEndpoint`|Dodatnia liczba całkowita, która określa maksymalną liczbę kanałów, które mogą być przechowywane w puli dla każdego zdalnego punktu końcowego. Wartość domyślna to 10.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<oneWay >](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|Włącza pakiet rutingu dla niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Przydziały są używane jako mechanizm zasad zapobiegających zużycie zasobów nadmierne. Zapobiegają one przez ataków typu odmowa usługi (DOS), które są złośliwe lub przypadkowe. Użyj tego elementu, ustawiając przydziały kanału w niestandardowym kanale.  
  
 `ChannelPoolSettings`Określa trzy przydziały:  
  
-   `idleTimeout` Przydziału służy do ograniczenie liczby ataków typu odmowa usługi (DOS) na serwerze, które są oparte na zajmowania zasobów przez dłuższy czas. Na komputerze klienckim ustawienie poprawną wartość może zwiększyć niezawodność nawiązywać połączenia z usługą. Wartość domyślna jest oparta na konserwatywnie niewielkie alokacji zasobów. Jest ona odpowiednia dla Środowisko deweloperskie i scenariusze małych instalacji. Administratorzy usługi powinni sprawdzić wartość, jeśli instalacja kończy się zasoby lub połączeń są ograniczeni niezależnie od dostępności dodatkowych zasobów.  
  
-   `leaseTimeout` Przydziału służy do integracji z usługą równoważenia obciążenia i poprawa niezawodności. Wartość domyślna jest oparta na zachowawcze alokacji zasobów. Jest ona odpowiednia dla Środowisko deweloperskie i scenariusze małych instalacji. Administratorzy usługi powinni sprawdzić wartość, jeśli instalacja kończy się zasoby lub połączeń są ograniczeni niezależnie od dostępności dodatkowych zasobów.  
  
-   `maxOutboundChannelsPerEndpoint` Przydziału Ustawia limity pamięci podręcznej na serwerze i kliencie i jest używany do poprawy niezawodności. Wartość domyślna jest oparta na konserwatywnie niewielkie alokacji zasobów, które jest odpowiednie dla środowiska programowania i scenariusze instalacji małych. Administratorzy usługi powinni sprawdzić wartość, jeśli instalacja kończy się zasoby lub połączeń są ograniczeni niezależnie od dostępności dodatkowych zasobów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [\<oneWay >](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
