---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 3c8d905a04f8f6d7ecff9b0ef9e7d3c8afa727e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925976"
---
# <a name="connectionpoolsettings"></a>\<connectionPoolSettings>
Określa dodatkowe ustawienia puli połączeń dla powiązania nazwanego potoku.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<namePipeTransport>  
\<connectionPoolSettings>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`groupName`|Ciąg określający nazwę puli połączeń używanej dla kanałów wychodzących. W trybie przesyłania strumieniowego połączenia nie są udostępniane, co oznacza, że buforowanie połączeń jest wyłączone. Wartość domyślna to ciąg "default". Możesz zmodyfikować tę wartość, aby wyizolować połączenia dla określonego klienta w oddzielnych grupach.|  
|`idleTimeout`|Wartość dodatnia <xref:System.TimeSpan> , która określa maksymalny czas bezczynności połączenia przed jego rozłączeniem. Wartość domyślna to 00:02:00.|  
|`maxOutboundConnectionsPerEndpoint`|Dodatnia liczba całkowita, która określa maksymalną liczbę połączeń ze zdalnym punktem końcowym inicjowanym przez usługę. Połączenia przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu. `idleTimeout` Ogranicza czas, w którym połączenia pozostają w kolejce przed zgłoszeniem wyjątku. Wartość domyślna to 10.<br /><br /> Ten atrybut ogranicza liczbę jednoczesnych aktywnych połączeń z klienta do określonego punktu końcowego usługi. W przypadku przekroczenia tej wartości przy użyciu większej liczby aktywnych połączeń z klientem usługa może nie odpowiadać na klienta. W takim przypadku ta wartość powinna zostać zmieniona, aby przekroczyć maksymalną dozwoloną liczbę równoczesnych połączeń klienta do określonego punktu końcowego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|Definiuje transport, który powoduje, że kanał przesyła komunikaty przy użyciu nazwanych potoków.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transporty](../../../wcf/feature-details/transports.md)
- [Wybieranie transportu](../../../wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
