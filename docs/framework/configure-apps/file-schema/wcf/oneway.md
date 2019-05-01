---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: bfda2b9d7b3aa5219a3e4c344347d3b10419a7bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783490"
---
# <a name="oneway"></a>\<oneWay>
Włącza pakiet rutingu i metod jednokierunkowych dla niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<oneWay>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpopint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`packetRoutable`|Wartość logiczna określająca, czy jest włączony pakiet routingu. Wartość domyślna to `false`.|  
|`MaxAcceptedChannels`|Liczba całkowita określająca maksymalną liczbę kanałów, które mogą być akceptowane.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<channelPoolSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> obiekt, który zawiera właściwości puli kanału na kanał bieżący.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Aby włączyć routing pakietów, warstwy jednokierunkowe konwersji jest wymagany, który zawiera ten element. Użytkownik może utworzyć niestandardowego powiązania, które warstw tego powiązania za pośrednictwem obsługujących sesji lub "żądanie-odpowiedź" transportu ułatwiają pakietów obsługi routingu. Ten element jest również przydatne, gdy chcesz udostępnić metody jednokierunkowe w sposób bardziej natywnych. Kolejnych przekształceń można stosować w tej warstwie, takie jak złożone dwukierunkowego i niezawodną obsługę komunikatów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
