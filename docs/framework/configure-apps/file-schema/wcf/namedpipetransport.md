---
title: '&lt;namedPipeTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 652cb551fb318d43d4284dbee48aeb994f056692
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746800"
---
# <a name="ltnamedpipetransportgt"></a>&lt;namedPipeTransport&gt;
Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych, gdy jest włączony do niestandardowego powiązania.  
  
\<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<namePipeTransport >  
  
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
                          idleTimeout"TimeSpan"  
                          maxOutboundConnectionsPerEndpopint="Integer" />  
</namedPipeTransport>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|limitu czasu channelInitializationTimeout|Pobiera lub ustawia <xref:System.TimeSpan> , który określa maksymalny czas kanału może być w stanie inicjowania przed rozłączeniem.|  
|connectionBufferSize|Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentu szeregowanego komunikatu podczas transmisji od klienta lub usługi.|  
|hostNameComparisonMode|Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.|  
|Opcję ManualAddressing|Pobiera lub ustawia wartość wskazującą, czy ręcznego adresowania wiadomości jest wymagana.|  
|MaxBufferPoolSize|Pobiera lub ustawia maksymalny rozmiar w bajtach pulami buforu, używany przez transport.|  
|wartość maxBufferSize|Pobiera lub ustawia maksymalny rozmiar buforu do użycia. Dla strumienia wiadomości wartość ta powinna być co najmniej maksymalna liczba nagłówków komunikatów, które są odczytywane w tryb buforowany.|  
|maxOutputDelay|Pobiera lub ustawia maksymalny interwał czasu, przez który fragment lub całość komunikatu może pozostawać buforowane w pamięci przed wysłaniem.|  
|maxPendingAccepts|Pobiera lub ustawia maksymalną liczbę kanałów, usługa może mieć oczekiwanie na odbiornik na potrzeby przetwarzania przychodzących połączeń z usługą.|  
|maxPendingConnections|Pobiera lub ustawia maksymalną liczbę połączeń oczekujących na wysyłania w usłudze.|  
|maxReceivedMessageSize|Pobiera i ustawia maksymalny dopuszczalny rozmiar wiadomości, w bajtach, które mogą być odebrane.|  
|Tryb transferu|Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy strumieniowo z nawiązaniem połączenia transportu.|  
|[\<connectionPoolSettings > z \<namedPipeTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|Określa ustawienia puli dodatkowego połączenia powiązania nazwanego potoku.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
Identyfikatory URI w postaci "net.pipe://hostname/path" korzysta z tego transportu. Inne składniki identyfikatora URI są opcjonalne.  
  
`namedPipeTransport` Element jest punkt początkowy do tworzenia niestandardowego powiązania, który implementuje ten protokół transportu nazwanych potoków. Ten transport jest używany dla na komputerze z systemem Windows Communication Foundation (WCF) - do - komunikacyjny WCF.  
  
## <a name="see-also"></a>Zobacz też  
<xref:System.ServiceModel.Configuration.NamedPipeTransportElement>   
<xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>   
<xref:System.ServiceModel.Channels.TransportBindingElement>   
<xref:System.ServiceModel.Channels.CustomBinding>   
[Transporty](../../../../../docs/framework/wcf/feature-details/transports.md)   
[Wybieranie transportu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
[Powiązania](../../../../../docs/framework/wcf/bindings.md)   
[Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
[Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
[\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
