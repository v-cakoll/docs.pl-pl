---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 819639eabf0332a34d6a7250159d24e42552f874
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423090"
---
# <a name="namedpipetransport"></a>\<namedPipeTransport>
Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych, gdy jest włączony do niestandardowego powiązania.  
  
\<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<namePipeTransport>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|ChannelInitializationTimeout|Pobiera lub ustawia <xref:System.TimeSpan> określa maksymalny czas kanału może być w stanie inicjowania przed rozłączeniem.|  
|ConnectionBufferSize|Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentów serializacji wiadomości na łączu z klienta lub usługi.|  
|hostNameComparisonMode|Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.|  
|opcję manualAddressing|Pobiera lub ustawia wartość wskazującą, czy wymagane jest ręczne adresowanie wiadomości.|  
|maxBufferPoolSize|Pobiera lub ustawia maksymalny rozmiar w bajtach żadnych pul buforu używany przez transportu.|  
|maxBufferSize|Pobiera lub ustawia maksymalny rozmiar buforu do użycia. Komunikaty przesyłane strumieniowo ta wartość powinna być co najmniej maksymalny rozmiar nagłówków wiadomości, które są odczytywane w tryb buforowany w.|  
|maxOutputDelay|Pobiera lub ustawia maksymalny interwał czasu, przez jaki fragmentów wiadomości lub cały komunikat może być buforowany w pamięci, zanim wysyłane.|  
|maxPendingAccepts|Pobiera lub ustawia maksymalną liczbę kanałów, o których usługa może mieć oczekiwanie na odbiornik do przetwarzania przychodzących połączeń z usługą.|  
|maxPendingConnections|Pobiera lub ustawia maksymalną liczbę połączeń, oczekiwanie na wysłanie w usłudze.|  
|maxReceivedMessageSize|Pobiera i ustawia maksymalny dozwolony rozmiar komunikatu, w bajtach, które mogą być odbierane.|  
|transferMode|Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy strumieniowo z nawiązaniem połączenia transportu.|  
|[\<connectionPoolSettings > z \<namedPipeTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|Określa ustawienia puli dodatkowego połączenia powiązania nazwanego potoku.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
Identyfikatory URI w postaci "net.pipe://hostname/path" korzysta z tego transportu. Inne składniki identyfikatora URI są opcjonalne.  
  
`namedPipeTransport` Element jest punktem wyjścia do tworzenia niestandardowego powiązania, który implementuje protokół transportowy nazwanych potoków. Tego transportu jest używany dla na komputerze Windows Communication Foundation (WCF) - do - komunikacji WCF.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transporty](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Wybieranie transportu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
