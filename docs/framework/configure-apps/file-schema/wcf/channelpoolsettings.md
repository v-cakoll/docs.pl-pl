---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 70f7452a22ae08d6eccd7d3644bdc8df45087ae0
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423187"
---
# <a name="channelpoolsettings"></a>\<channelPoolSettings>
Określa ustawienia puli kanału dla niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<oneWay>  
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
|`idleTimeout`|Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas kanałów w puli może być bezczynne, zanim zostanie rozłączone. Wartość domyślna to 00:02:00.|  
|`leaseTimeout`|Element <xref:System.TimeSpan> , który określa przedział czasu, po którym kanał, gdy zwrócony do puli, jest zamknięty. Wartość domyślna to 00:10:00.|  
|`maxOutboundChannelsPerEndpoint`|Dodatnia liczba całkowita, określająca maksymalną liczbę kanałów, które mogą być przechowywane w puli dla każdego zdalnego punktu końcowego. Wartość domyślna wynosi 10.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<oneWay>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|Umożliwia routing pakietów dla niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Przydziały są używane jako mechanizm zasady zapobiegające zużycia zasobów. Mogą zapobiegać atakom typu odmowa usługi (DOS), które są złośliwe lub przypadkowe. Podczas ustawiania przydziałów kanału w niestandardowym kanale, użyj tego elementu.  
  
 `ChannelPoolSettings` Określa trzy przydziały:  
  
- `idleTimeout` Przydziału służy do ograniczenie liczby ataków typu odmowa usługi (DOS) na serwerze, które zależą od zajmowania zasobów przez dłuższy czas. Na komputerze klienckim ustawienie poprawną wartość może zwiększyć niezawodność nawiązywania połączenia z usługą. Wartość domyślna jest oparta na konserwatywnie skromną alokacji zasobów. Nadaje się do środowiska deweloperskiego i scenariusze małych instalacji. Administratorzy usług należy przejrzeć wartość, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.  
  
- `leaseTimeout` Przydziału służy do integracji z modułami równoważenia obciążenia i zwiększając niezawodność. Wartość domyślna jest oparta na zachowawcze alokacji zasobów. Nadaje się do środowiska deweloperskiego i scenariusze małych instalacji. Administratorzy usług należy przejrzeć wartość, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.  
  
- `maxOutboundChannelsPerEndpoint` Przydziału Ustawia limity pamięci podręcznej serwera i klienta i jest używana w celu zwiększenia niezawodności. Wartość domyślna jest oparta na konserwatywnie skromną alokacji zasobów, który nadaje się do środowiska deweloperskiego i scenariusze instalacji małych. Administratorzy usług należy przejrzeć wartość, czy instalacja zaczyna brakować zasobów, czy połączenia są ograniczeni pomimo dostępność dodatkowych zasobów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
