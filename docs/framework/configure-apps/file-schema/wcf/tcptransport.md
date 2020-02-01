---
title: <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 7101719f77a03909d9a38dca93100ec90c1add13
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921389"
---
# <a name="tcptransport"></a>\<tcpTransport>
Definiuje transport TCP, który może być używany przez kanał do przesyłania komunikatów dla niestandardowego powiązania.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tcpTransport >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<tcpTransport channelInitializationTimeout="TimeSpan"
              connectionBufferSize="Integer"
              hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
              listenBacklog="Integer"
              manualAddressing="Boolean"
              maxBufferPoolSize="Integer"
              maxBufferSize="Integer"
              maxOutputDelay="TimeSpan"
              maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              maxReceivedMessageSize="Integer"
              portSharingEnabled="Boolean"
              teredoEnabled="Boolean"
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse" >
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          leaseTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</tcpTransport>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|channelInitializationTimeout|Pobiera lub ustawia limit czasu inicjowania kanału, który ma zostać zaakceptowany.  Maksymalny czas, w którym kanał może być w stanie inicjowania przed rozłączeniem w sekundach. Ten limit przydziału obejmuje czas, przez jaki połączenie TCP może być wykonywane w celu samodzielnego uwierzytelnienia przy użyciu protokołu ramki komunikatów .NET. Klient musi wysłać pewne dane początkowe, zanim serwer będzie miał wystarczającą ilość informacji do przeprowadzenia uwierzytelniania. Wartość domyślna to 30 sekund.|  
|connectionBufferSize|Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentu serializowanego komunikatu w locie z klienta lub usługi.|  
|hostNameComparisonMode|Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.|  
|listenBacklog|Maksymalna liczba żądań połączeń umieszczonych w kolejce, które mogą być oczekujące dla usługi sieci Web. Atrybut `connectionLeaseTimeout` ogranicza czas, przez jaki klient będzie oczekiwał na połączenie przed wygenerowaniem wyjątku połączenia. Jest to właściwość poziomu gniazda, która kontroluje maksymalną liczbę oczekujących żądań połączeń w usłudze sieci Web. Gdy ListenBacklog jest zbyt niska, usługa WCF nie akceptuje żądań i w związku z tym porzuca nowe połączenia, dopóki serwer nie potwierdzi niektórych istniejących połączeń umieszczonych w kolejce. Wartość domyślna to 16 * liczba procesorów.|  
|Opcję ManualAddressing|Pobiera lub ustawia wartość wskazującą, czy ręczne adresowanie wiadomości jest wymagane.|  
|maxBufferPoolSize|Pobiera lub ustawia maksymalny rozmiar wszystkich pul buforów używanych przez transport.|  
|maxBufferSize|Pobiera lub ustawia maksymalny rozmiar buforu do użycia. W przypadku komunikatów przesyłanych strumieniowo ta wartość powinna mieć co najmniej maksymalny możliwy rozmiar nagłówków komunikatów, które są odczytywane w trybie buforowanym.|  
|maxOutputDelay|Pobiera lub ustawia maksymalny przedział czasu, przez który fragment komunikatu lub pełny komunikat może pozostawać w pamięci przed wysłaniem.|  
|maxPendingAccepts|Pobiera lub ustawia maksymalną liczbę oczekujących asynchronicznych operacji akceptujących, które są dostępne do przetwarzania przychodzących połączeń do usługi.|  
|maxPendingConnections|Pobiera lub ustawia maksymalną liczbę połączeń oczekujących na wysłanie usługi.|  
|maxReceivedMessageSize|Pobiera i ustawia maksymalny dopuszczalny rozmiar komunikatu, który można odbierać.|  
|portSharingEnabled|Wartość logiczna określająca, czy włączone jest Udostępnianie portów TCP dla tego połączenia. Jeśli jest to `false`, każde powiązanie będzie używać własnego portu wyłącznego. Wartość domyślna to `false`.<br /><br /> To ustawienie dotyczy tylko usług. Nie dotyczy to klientów.<br /><br /> Użycie tego ustawienia wymaga włączenia usługi udostępniania portów TCP Windows Communication Foundation (WCF), zmieniając jej typ uruchamiania na ręczny lub automatyczny.|  
|teredoEnabled|Wartość logiczna określająca, czy jest włączona funkcja Teredo (technologia do adresowania klientów znajdujących się za zaporą). Wartość domyślna to `false`.<br /><br /> Ta właściwość włącza protokół Teredo dla bazowego gniazda TCP. Aby uzyskać więcej informacji, zobacz [Omówienie protokołu Teredo](https://go.microsoft.com/fwlink/?LinkId=95339).<br /><br /> Ta właściwość ma zastosowanie tylko w systemach Windows XP z dodatkiem SP2 i Windows Server 2003. W systemie Windows Vista jest używana opcja konfiguracji całego komputera dla protokołu Teredo, więc w przypadku korzystania z systemu Vista Ta właściwość jest ignorowana. Protokół Teredo wymaga, aby komputery klienckie i usługi miały zainstalowany stos IPv6 firmy Microsoft i prawidłowo skonfigurowany do użycia w protokole Teredo. Aby uzyskać więcej informacji na temat konfigurowania protokołu Teredo, zobacz [Omówienie protokołu Teredo](https://go.microsoft.com/fwlink/?LinkId=95339). Aby uzyskać więcej informacji, zobacz [centra technologiczne systemu Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=49888).|  
|transferMode|Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy przesyłane strumieniowo przy użyciu transportu zorientowanego na połączenia.|  
|connectionPoolSettings|Określa dodatkowe ustawienia puli połączeń dla powiązania nazwanego potoku.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[> powiązań \<](bindings.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten transport używa identyfikatorów URI w postaci "net. TCP://NazwaHosta: Port/Path". Inne składniki URI są opcjonalne.  
  
 Element `tcpTransport` jest punktem początkowym do tworzenia niestandardowego powiązania, które implementuje protokół transportowy TCP. Ten transport jest zoptymalizowany pod kątem komunikacji między WCF i WCF.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.TcpTransportElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transporty](../../../wcf/feature-details/transports.md)
- [Wybieranie transportu](../../../wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
