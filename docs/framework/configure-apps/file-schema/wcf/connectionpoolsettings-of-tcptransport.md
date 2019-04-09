---
title: <connectionPoolSettings> z <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 93363c5ff1753ff02956404da7697780078c9839
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129977"
---
# <a name="connectionpoolsettings-of-tcptransport"></a>\<connectionPoolSettings> of \<tcpTransport>
Określa ustawienia puli dodatkowego połączenia dla transportu TCP.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<tcpTransport>  
\<connectionPoolSettings>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`groupName`|Ciąg, który definiuje nazwę puli połączeń dla wychodzących kanałów. W trybie przesyłane strumieniowo połączenia nie są udostępniane, co oznacza, że buforowanie połączeń jest wyłączona. Wartość domyślna to ciąg "default". Możesz zmodyfikować tę wartość, aby odizolować połączeń dla konkretnego klienta do osobnych grup.|  
|`idleTimeout`|Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas połączenia może być bezczynne, zanim zostanie rozłączone. Wartość domyślna to 00:02:00.|  
|`leaseTimeout`|Element <xref:System.TimeSpan> , który określa czas, po którym aktywne połączenie jest zamknięte. Wartość domyślna to 00:05:00.<br /><br /> Połączenie zostało zamknięte po został zwrócony z pamięcią podręczną w połączeń, a nie podczas transmisji active. Pamięć podręczna połączenia używane przez warstwy transportowej TCP tworzy nowe połączenia, zgodnie z wymaganiami dla każdego punktu końcowego do limitu pamięci podręcznej, która została ustawiona przez `maxOutboundConnectionsPerEndpoint.`|  
|`maxOutboundConnectionsPerEndpoint`|Dodatnia liczba całkowita, określająca maksymalną liczbę połączeń do zdalnego punktu końcowego, inicjowanego przez usługę. Połączeń poza limitem zostaną umieszczone w kolejce, dopóki miejsce poniżej limitu staje się dostępna. `idleTimeout` Ogranicza okres, w którym pozostają w kolejce zanim zostanie zgłoszony wyjątek. Wartość domyślna wynosi 10.<br /><br /> Ten atrybut ogranicza liczbę równoczesnych aktywnych połączeń z klienta do endpoint określonej usługi. Jeśli ta wartość zostanie przekroczony zlecając aktywnych połączeń klienta, usługa może pojawić się odpowiadać do klienta. W takim przypadku można dostosować tę wartość w przekracza maksymalną liczbę oczekiwanych równoczesnych połączeń klientów do określonego punktu końcowego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<namedPipeTransport>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transporty](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Wybieranie transportu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
