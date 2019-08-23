---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: dd81821c74678cae8602458fe796a72bf5d379e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919558"
---
# <a name="channelpoolsettings"></a>\<channelPoolSettings>
Określa ustawienia puli kanałów dla niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<> oneWay  
\<channelPoolSettings>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`idleTimeout`|Wartość dodatnia <xref:System.TimeSpan> , która określa maksymalny czas bezczynności kanałów w puli przed rozłączeniem. Wartość domyślna to 00:02:00.|  
|`leaseTimeout`|A <xref:System.TimeSpan> , który określa przedział czasu, po którym kanał, gdy jest zwracany do puli, jest zamknięty. Wartość domyślna to 00:10:00.|  
|`maxOutboundChannelsPerEndpoint`|Dodatnia liczba całkowita, która określa maksymalną liczbę kanałów, które mogą być przechowywane w puli dla każdego zdalnego punktu końcowego. Wartość domyślna to 10.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> oneWay](oneway.md)|Włącza routing pakietów dla niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Przydziały są używane jako mechanizm zasad, aby zapobiec zużyciu nadmiernych zasobów. Uniemożliwiają one ataki typu "odmowa usługi" (DOS), które są złośliwe lub niezamierzone. Użyj tego elementu, gdy ustawiasz limity przydziału kanałów w niestandardowym kanale.  
  
 `ChannelPoolSettings`określa trzy przydziały:  
  
- `idleTimeout` Przydział służy do zapobiegania atakom typu "odmowa usługi" (DOS) na serwerze, który polega na rozdzieleniu zasobów przez dłuższy czas. Ustawienie poprawnej wartości na kliencie może zwiększyć niezawodność połączenia z usługą. Wartość domyślna jest oparta na nieumiarkowanie niedostatecznej alokacji zasobów. Jest to odpowiednie dla środowiska programistycznego i małych scenariuszy instalacji. Administratorzy usługi powinni sprawdzić wartość w przypadku braku zasobów w ramach instalacji lub w przypadku ograniczonej liczby połączeń poza dostępnością dodatkowych zasobów.  
  
- `leaseTimeout` Przydział służy do integracji z usługami równoważenia obciążenia i zwiększania niezawodności. Wartość domyślna jest określana na podstawie ostrożnej alokacji zasobów. Jest to odpowiednie dla środowiska programistycznego i małych scenariuszy instalacji. Administratorzy usługi powinni sprawdzić wartość w przypadku braku zasobów w ramach instalacji lub w przypadku ograniczonej liczby połączeń poza dostępnością dodatkowych zasobów.  
  
- Limity `maxOutboundChannelsPerEndpoint` przydziału są ustawiane w pamięci podręcznej zarówno na serwerze, jak i na kliencie i są używane w celu zwiększenia niezawodności. Wartość domyślna jest oparta na niewielkiej ilości alokacji zasobów, która jest odpowiednia dla środowiska programistycznego i małych scenariuszy instalacji. Administratorzy usługi powinni sprawdzić wartość w przypadku braku zasobów w ramach instalacji lub w przypadku ograniczonej liczby połączeń poza dostępnością dodatkowych zasobów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<> oneWay](oneway.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
