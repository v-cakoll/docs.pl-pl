---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 473d0fbd543a056ec2b152f43a76a0417a18016f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933208"
---
# <a name="namedpipetransport"></a>\<namedPipeTransport>
Definiuje transport, który powoduje, że kanał przesyła komunikaty przy użyciu nazwanych potoków, gdy zostanie uwzględniony w niestandardowym powiązaniu.  
  
\<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
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
|ChannelInitializationTimeout|Pobiera lub ustawia wartość <xref:System.TimeSpan> określającą maksymalny czas, przez który kanał może być w stanie inicjowania przed rozłączeniem.|  
|ConnectionBufferSize|Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentu serializowanego komunikatu w locie z klienta lub usługi.|  
|hostNameComparisonMode|Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI.|  
|Opcję ManualAddressing|Pobiera lub ustawia wartość wskazującą, czy ręczne adresowanie wiadomości jest wymagane.|  
|maxBufferPoolSize|Pobiera lub ustawia maksymalny rozmiar (w bajtach) wszystkich pul buforów używanych przez transport.|  
|maxBufferSize|Pobiera lub ustawia maksymalny rozmiar buforu do użycia. W przypadku komunikatów przesyłanych strumieniowo ta wartość powinna mieć co najmniej maksymalny możliwy rozmiar nagłówków komunikatów, które są odczytywane w trybie buforowanym.|  
|maxOutputDelay|Pobiera lub ustawia maksymalny przedział czasu, przez który fragment komunikatu lub pełny komunikat może pozostawać w pamięci przed wysłaniem.|  
|maxPendingAccepts|Pobiera lub ustawia maksymalną liczbę kanałów, jaką usługa może oczekiwać na odbiorniku do przetwarzania połączeń przychodzących do usługi.|  
|maxPendingConnections|Pobiera lub ustawia maksymalną liczbę połączeń oczekujących na wysłanie usługi.|  
|maxReceivedMessageSize|Pobiera i ustawia maksymalny dopuszczalny rozmiar wiadomości (w bajtach), która może zostać odebrana.|  
|transferMode|Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy przesyłane strumieniowo przy użyciu transportu zorientowanego na połączenia.|  
|[\<connectionPoolSettings > \<namedPipeTransport >](connectionpoolsettings.md)|Określa dodatkowe ustawienia puli połączeń dla powiązania nazwanego potoku.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
Ten transport używa identyfikatorów URI w postaci "net. pipe://hostname/Path". Inne składniki URI są opcjonalne.  
  
`namedPipeTransport` Element jest punktem początkowym do tworzenia niestandardowego powiązania, które implementuje protokół transportu nazwanych potoków. Ten transport jest używany w przypadku komunikacji między maszynami Windows Communication Foundation (WCF).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transporty](../../../wcf/feature-details/transports.md)
- [Wybieranie transportu](../../../wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
