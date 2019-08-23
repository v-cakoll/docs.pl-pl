---
title: <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: b85f3b77ca42eaaae8eae261df6414b5f9378560
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938951"
---
# <a name="tcptransport"></a>\<tcpTransport>
Definiuje transport TCP, który może być używany przez kanał do przesyłania komunikatów dla niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<tcpTransport>  
  
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
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|channelInitializationTimeout|Pobiera lub ustawia limit czasu inicjowania kanału, który ma zostać zaakceptowany.  Maksymalny czas, w którym kanał może być w stanie inicjowania przed rozłączeniem w sekundach. Ten limit przydziału obejmuje czas, przez jaki połączenie TCP może być wykonywane w celu samodzielnego uwierzytelnienia przy użyciu protokołu ramki komunikatów .NET. Klient musi wysłać pewne dane początkowe, zanim serwer będzie miał wystarczającą ilość informacji do przeprowadzenia uwierzytelniania. Wartość domyślna to 30 sekund.|  
|connectionBufferSize|Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentu serializowanego komunikatu w locie z klienta lub usługi.|  
|hostNameComparisonMode|Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.|  
|listenBacklog|Maksymalna liczba żądań połączeń umieszczonych w kolejce, które mogą być oczekujące dla usługi sieci Web. Ten `connectionLeaseTimeout` atrybut ogranicza czas, przez jaki klient będzie oczekiwał na połączenie przed wygenerowaniem wyjątku połączenia. Jest to właściwość poziomu gniazda, która kontroluje maksymalną liczbę oczekujących żądań połączeń w usłudze sieci Web. Gdy ListenBacklog jest zbyt niska, usługa WCF nie akceptuje żądań i w związku z tym porzuca nowe połączenia, dopóki serwer nie potwierdzi niektórych istniejących połączeń umieszczonych w kolejce. Wartość domyślna to 16 * liczba procesorów.|  
|Opcję ManualAddressing|Pobiera lub ustawia wartość wskazującą, czy ręczne adresowanie wiadomości jest wymagane.|  
|maxBufferPoolSize|Pobiera lub ustawia maksymalny rozmiar wszystkich pul buforów używanych przez transport.|  
|maxBufferSize|Pobiera lub ustawia maksymalny rozmiar buforu do użycia. W przypadku komunikatów przesyłanych strumieniowo ta wartość powinna mieć co najmniej maksymalny możliwy rozmiar nagłówków komunikatów, które są odczytywane w trybie buforowanym.|  
|maxOutputDelay|Pobiera lub ustawia maksymalny przedział czasu, przez który fragment komunikatu lub pełny komunikat może pozostawać w pamięci przed wysłaniem.|  
|maxPendingAccepts|Pobiera lub ustawia maksymalną liczbę oczekujących asynchronicznych operacji akceptujących, które są dostępne do przetwarzania przychodzących połączeń do usługi.|  
|maxPendingConnections|Pobiera lub ustawia maksymalną liczbę połączeń oczekujących na wysłanie usługi.|  
|maxReceivedMessageSize|Pobiera i ustawia maksymalny dopuszczalny rozmiar komunikatu, który można odbierać.|  
|portSharingEnabled|Wartość logiczna określająca, czy włączone jest Udostępnianie portów TCP dla tego połączenia. `false`W takim przypadku każde powiązanie będzie używać własnego portu wyłącznego. Wartość domyślna to `false`.<br /><br /> To ustawienie dotyczy tylko usług. Nie dotyczy to klientów.<br /><br /> Użycie tego ustawienia wymaga włączenia usługi udostępniania portów TCP Windows Communication Foundation (WCF), zmieniając jej typ uruchamiania na ręczny lub automatyczny.|  
|teredoEnabled|Wartość logiczna określająca, czy jest włączona funkcja Teredo (technologia do adresowania klientów znajdujących się za zaporą). Wartość domyślna to `false`.<br /><br /> Ta właściwość włącza protokół Teredo dla bazowego gniazda TCP. Aby uzyskać więcej informacji, zobacz [Omówienie protokołu Teredo](https://go.microsoft.com/fwlink/?LinkId=95339).<br /><br /> Ta właściwość ma zastosowanie tylko w [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] systemach [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)]i. [!INCLUDE[wv](../../../../../includes/wv-md.md)]ma opcję konfiguracji całego komputera dla protokołu Teredo, więc w przypadku korzystania z systemu Vista Ta właściwość jest ignorowana. Protokół Teredo wymaga, aby komputery klienckie i usługi miały zainstalowany stos IPv6 firmy Microsoft i prawidłowo skonfigurowany do użycia w protokole Teredo. Aby uzyskać więcej informacji na temat konfigurowania protokołu Teredo, zobacz [Omówienie protokołu Teredo](https://go.microsoft.com/fwlink/?LinkId=95339). Aby uzyskać więcej informacji, zobacz [centra technologiczne systemu Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=49888).|  
|transferMode|Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy przesyłane strumieniowo przy użyciu transportu zorientowanego na połączenia.|  
|connectionPoolSettings|Określa dodatkowe ustawienia puli połączeń dla powiązania nazwanego potoku.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten transport używa identyfikatorów URI w postaci "net. TCP://NazwaHosta: Port/Path". Inne składniki URI są opcjonalne.  
  
 `tcpTransport` Element jest punktem początkowym do tworzenia niestandardowego powiązania, które implementuje protokół transportowy TCP. Ten transport jest zoptymalizowany pod kątem komunikacji między WCF i WCF.  
  
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
