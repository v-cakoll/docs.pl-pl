---
title: '&lt;tcpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 4141b0f6493c51048ad60accdc1d5ee9bac01231
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751080"
---
# <a name="lttcptransportgt"></a>&lt;tcpTransport&gt;
Definiuje warstwę transportu TCP, które mogą być używane przez kanał do transferu wiadomości dla niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<tcpTransport>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<tcpTransport   
      channelInitializationTimeout="TimeSpan"   
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
      <connectionPoolSettings  
            groupName="String"  
            idleTimeout"TimeSpan"  
            leaseTimeout="TimeSpan"  
            maxOutboundConnectionsPerEndpopint="Integer" />  
</tcpTransport>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|channelInitializationTimeout|Pobiera lub ustawia limit czasu inicjowania kanału mają być akceptowane.  Maksymalny czas kanału może być w stanie inicjowania przed rozłączeniem w sekundach. Ten limit przydziału obejmuje czas połączenia TCP można wykonać w celu uwierzytelnienia przy użyciu programu .Net Framing komunikatu protokołu. Gdy klient musi wysłać niektórych początkowe dane, zanim serwer ma za mało informacji do uwierzytelniania. Wartość domyślna to 30 sekund.|  
|connectionBufferSize|Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentu szeregowanego komunikatu podczas transmisji od klienta lub usługi.|  
|hostNameComparisonMode|Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.|  
|ListenBacklog|Maksymalna liczba oczekujących żądań połączenia w kolejce dla usługi sieci Web. `connectionLeaseTimeout` Atrybut ogranicza czas trwania, klient będzie czekać do podłączenia przed zgłaszanie wyjątek połączenia. Jest to właściwość poziomu gniazda, która określa maksymalną liczbę oczekujących żądań połączenia w kolejce dla usługi sieci Web. Gdy ListenBacklog ma zbyt niską wartość, WCF spowoduje zatrzymanie, akceptując żądania i w związku z tym porzucić nowych połączeń, dopóki serwer uznaje, niektóre istniejące połączenia w kolejce. Wartość domyślna to 16 * liczba procesorów.|  
|Opcję ManualAddressing|Pobiera lub ustawia wartość wskazującą, czy ręcznego adresowania wiadomości jest wymagana.|  
|MaxBufferPoolSize|Pobiera lub ustawia maksymalny rozmiar pulami buforu, używany przez transport.|  
|wartość maxBufferSize|Pobiera lub ustawia maksymalny rozmiar buforu do użycia. Dla strumienia wiadomości wartość ta powinna być co najmniej maksymalna liczba nagłówków komunikatów, które są odczytywane w tryb buforowany.|  
|maxOutputDelay|Pobiera lub ustawia maksymalny interwał czasu, przez który fragment lub całość komunikatu może pozostawać buforowane w pamięci przed wysłaniem.|  
|maxPendingAccepts|Pobiera lub ustawia maksymalną liczbę oczekujących asynchronicznych zaakceptować operacje, które są dostępne do przetwarzania przychodzących połączeń z usługą.|  
|maxPendingConnections|Pobiera lub ustawia maksymalną liczbę połączeń oczekujących na wysyłania w usłudze.|  
|maxReceivedMessageSize|Pobiera i ustawia maksymalny dopuszczalny rozmiar wiadomości, który może zostać odebrany.|  
|PortSharingEnabled|Wartość logiczna określająca, czy włączone jest udostępnianie portów TCP dla tego połączenia. Jeśli jest to `false`, każdego powiązania użyje wyłącznego portu. Wartość domyślna to `false`.<br /><br /> To ustawienie ma zastosowanie tylko do usług. Nie dotyczy to klientów.<br /><br /> Za pomocą tej opcji wymaga włączenia usługę Udostępnianie portów TCP Windows Communication Foundation (WCF), zmieniając jej typ uruchamiania ręczny lub automatyczny|  
|TeredoEnabled|Wartość logiczna określająca czy włączona jest obsługa technologii Teredo (pozwalającej adresować klientów znajdujących się za zaporą). Wartość domyślna to `false`.<br /><br /> Ta właściwość umożliwia Teredo dla podstawowej gniazda TCP. Aby uzyskać więcej informacji, zobacz [omówienie Teredo](http://go.microsoft.com/fwlink/?LinkId=95339).<br /><br /> Ta właściwość ma zastosowanie tylko w [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] i [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)]. [!INCLUDE[wv](../../../../../includes/wv-md.md)] jest dostępna opcji konfiguracji komputera dla protokołu Teredo, dlatego podczas uruchamiania Vista, ta właściwość jest ignorowana. Teredo musi mieć maszyny klienta i usługi Microsoft IPv6 stosu zainstalowany i prawidłowo skonfigurowany w celu użycia protokołu Teredo. Aby uzyskać więcej informacji o konfigurowaniu protokołu Teredo, zobacz [omówienie Teredo](http://go.microsoft.com/fwlink/?LinkId=95339). Aby uzyskać więcej informacji, zobacz [systemu Windows Server 2003 technologii centrów](http://go.microsoft.com/fwlink/?LinkId=49888).|  
|Tryb transferu|Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy strumieniowo z nawiązaniem połączenia transportu.|  
|connectionPoolSettings|Określa ustawienia puli dodatkowego połączenia powiązania nazwanego potoku.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Identyfikatory URI w postaci używa tego transportu "net.tcp://hostname: port/ścieżki". Inne składniki identyfikatora URI są opcjonalne.  
  
 `tcpTransport` Element jest punkt początkowy do tworzenia niestandardowego powiązania, który implementuje ten protokół transportu TCP. Ten transport jest zoptymalizowana pod kątem komunikacji usługi WCF do usługi WCF.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.TcpTransportElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Transporty](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Wybieranie transportu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
