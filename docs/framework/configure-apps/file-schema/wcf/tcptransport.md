---
title: '&lt;tcpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 21b63ab0b4546dc2f4d46c40b02c55fb639320f6
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151179"
---
# <a name="lttcptransportgt"></a>&lt;tcpTransport&gt;
Definiuje warstwę transportu TCP, który może służyć przez kanał do transferu wiadomości dla niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
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
                          maxOutboundConnectionsPerEndpopint="Integer" />
</tcpTransport>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|channelInitializationTimeout|Pobiera lub ustawia limit czasu na inicjowanie kanału do zaakceptowania.  Maksymalny czas kanału może być w stanie inicjowania przed rozłączeniem w ciągu kilku sekund. Ten limit przydziału obejmuje czas połączenia TCP można wykonać, aby uwierzytelniać przy użyciu programu .Net Framing komunikatu protokołu. Klient musi wysyłać niektórych danych początkowych, zanim serwer ma za mało informacji w celu przeprowadzenia uwierzytelniania. Wartość domyślna to 30 sekund.|  
|ConnectionBufferSize|Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentów serializacji wiadomości na łączu z klienta lub usługi.|  
|hostNameComparisonMode|Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.|  
|listenBacklog|Maksymalna liczba żądań połączenia w kolejce, oczekujących usługi sieci Web. `connectionLeaseTimeout` Atrybut ogranicza czas, klient będzie czekać połączenia zanim zostanie zgłoszony wyjątek połączenia. Jest to właściwość poziomu gniazda, która określa maksymalną liczbę żądań połączenia w kolejce, oczekujących usługi sieci Web. Gdy ListenBacklog jest zbyt niska, WCF zatrzymać, akceptując żądania i w związku z tym porzucić nowe połączenia, dopóki serwer uznaje, niektóre z istniejących połączeń umieszczonych w kolejce. Wartość domyślna to 16 * liczba procesorów.|  
|opcję manualAddressing|Pobiera lub ustawia wartość wskazującą, czy wymagane jest ręczne adresowanie wiadomości.|  
|maxBufferPoolSize|Pobiera lub ustawia maksymalny rozmiar żadnych pul buforu używany przez transportu.|  
|wartość maxBufferSize|Pobiera lub ustawia maksymalny rozmiar buforu do użycia. Komunikaty przesyłane strumieniowo ta wartość powinna być co najmniej maksymalny rozmiar nagłówków wiadomości, które są odczytywane w tryb buforowany w.|  
|MaxOutputDelay|Pobiera lub ustawia maksymalny interwał czasu, przez jaki fragmentów wiadomości lub cały komunikat może być buforowany w pamięci, zanim wysyłane.|  
|maxPendingAccepts|Pobiera lub ustawia maksymalną liczbę oczekujących asynchronicznego akceptować operacji, które są dostępne do przetwarzania przychodzących połączeń z usługą.|  
|maxPendingConnections|Pobiera lub ustawia maksymalną liczbę połączeń, oczekiwanie na wysłanie w usłudze.|  
|maxReceivedMessageSize|Pobiera lub ustawia rozmiar maksymalny dopuszczalny rozmiar komunikatu, który może zostać odebrany.|  
|portSharingEnabled|Wartość logiczna określająca, jeśli włączone jest udostępnianie portów TCP dla tego połączenia. Jeśli jest to `false`, każde powiązanie użyje wyłączne portu. Wartość domyślna to `false`.<br /><br /> To ustawienie dotyczy tylko usług. Nie dotyczy to klientów.<br /><br /> Przy użyciu tego ustawienia wymaga Włączanie usługa Udostępnianie portów TCP Windows Communication Foundation (WCF), zmieniając jej typ uruchamiania na ręczny lub automatyczny|  
|teredoEnabled|Wartość logiczna określająca, czy jest włączony protokół Teredo (technologia adresować klientów znajdujących się za zaporami). Wartość domyślna to `false`.<br /><br /> Ta właściwość umożliwia Teredo dla podstawowej gniazda TCP. Aby uzyskać więcej informacji, zobacz [Przegląd Teredo](https://go.microsoft.com/fwlink/?LinkId=95339).<br /><br /> Ta właściwość ma zastosowanie tylko w [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] i [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)]. [!INCLUDE[wv](../../../../../includes/wv-md.md)] jest dostępna opcja konfiguracji komputera dla protokołu Teredo, dzięki czemu podczas uruchamiania Vista, ta właściwość jest ignorowana. Teredo musi mieć czy maszyn klientem a usługą stosu IPv6 firmy Microsoft, zainstalowany i poprawnie skonfigurowany w celu użycia protokołu Teredo. Aby uzyskać więcej informacji na temat konfigurowania protokołu Teredo, zobacz [Przegląd Teredo](https://go.microsoft.com/fwlink/?LinkId=95339). Aby uzyskać więcej informacji, zobacz [systemu Windows Server 2003 technologii centra](https://go.microsoft.com/fwlink/?LinkId=49888).|  
|Tryb transferu|Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy strumieniowo z nawiązaniem połączenia transportu.|  
|connectionPoolSettings|Określa ustawienia puli dodatkowego połączenia powiązania nazwanego potoku.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Identyfikatory URI w postaci korzysta z tego transportu "net.tcp://hostname: ścieżka/port". Inne składniki identyfikatora URI są opcjonalne.  
  
 `tcpTransport` Element jest punktem wyjścia do tworzenia niestandardowego powiązania, który implementuje protokołu transportu TCP. Tego transportu jest zoptymalizowany pod kątem komunikacji WCF do usługi WCF.  
  
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
