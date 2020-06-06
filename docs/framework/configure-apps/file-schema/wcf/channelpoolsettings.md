---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 26537980a6be5c0fe12661d93a6ba5fe862ceb4e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398158"
---
# \<channelPoolSettings>
Określa ustawienia puli kanałów dla niestandardowego powiązania.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**  
  
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
|[\<oneWay>](oneway.md)|Włącza routing pakietów dla niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Przydziały są używane jako mechanizm zasad, aby zapobiec zużyciu nadmiernych zasobów. Uniemożliwiają one ataki typu "odmowa usługi" (DOS), które są złośliwe lub niezamierzone. Użyj tego elementu, gdy ustawiasz limity przydziału kanałów w niestandardowym kanale.  
  
 `ChannelPoolSettings`określa trzy przydziały:  
  
- `idleTimeout`Przydział służy do zapobiegania atakom typu "odmowa usługi" (DOS) na serwerze, który polega na rozdzieleniu zasobów przez dłuższy czas. Ustawienie poprawnej wartości na kliencie może zwiększyć niezawodność połączenia z usługą. Wartość domyślna jest oparta na nieumiarkowanie niedostatecznej alokacji zasobów. Jest to odpowiednie dla środowiska programistycznego i małych scenariuszy instalacji. Administratorzy usługi powinni sprawdzić wartość w przypadku braku zasobów w ramach instalacji lub w przypadku ograniczonej liczby połączeń poza dostępnością dodatkowych zasobów.  
  
- `leaseTimeout`Przydział służy do integracji z usługami równoważenia obciążenia i zwiększania niezawodności. Wartość domyślna jest określana na podstawie ostrożnej alokacji zasobów. Jest to odpowiednie dla środowiska programistycznego i małych scenariuszy instalacji. Administratorzy usługi powinni sprawdzić wartość w przypadku braku zasobów w ramach instalacji lub w przypadku ograniczonej liczby połączeń poza dostępnością dodatkowych zasobów.  
  
- `maxOutboundChannelsPerEndpoint`Limity przydziału są ustawiane w pamięci podręcznej zarówno na serwerze, jak i na kliencie i są używane w celu zwiększenia niezawodności. Wartość domyślna jest oparta na niewielkiej ilości alokacji zasobów, która jest odpowiednia dla środowiska programistycznego i małych scenariuszy instalacji. Administratorzy usługi powinni sprawdzić wartość w przypadku braku zasobów w ramach instalacji lub w przypadku ograniczonej liczby połączeń poza dostępnością dodatkowych zasobów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
