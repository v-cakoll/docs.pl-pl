---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 9b6b74200c807e6523ed3f7250945040bd12658d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919795"
---
# <a name="binarymessageencoding"></a>\<binaryMessageEncoding >
Definiuje binarny koder komunikatów, który koduje wiadomości Windows Communication Foundation (WCF) w postaci binarnej w sieci.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<binaryMessageEncoding >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|maxReadPoolSize|Liczba całkowita, która określa, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników. Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym. Wartość domyślna to 64.|  
|maxSessionSize|Dodatnia liczba całkowita, która ustawia rozmiar (w bajtach) bufora używanego do kodowania. Większy bufor zwiększa szybkość kodowania przy kosztach rozmiaru zestawu roboczego. Wartość domyślna to 2048.|  
|maxWritePoolSize|Liczba całkowita, która określa, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących. Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym. Wartość domyślna to 16.|  
|Element MessageVersion|Określa komunikat protokołu SOAP i wersje WS-Addressing, które są używane lub oczekiwane.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Kodowanie jest procesem przekształcania komunikatu w sekwencję bajtów. Dekodowanie jest procesem wycofywania. Windows Communication Foundation (WCF) zawiera trzy typy kodowania dla komunikatów SOAP: Mechanizm optymalizacji tekstu, binarny i przesyłania komunikatów (MTOM).  
  
 `binaryMessageEncoding` Element określa format binarny platformy .NET dla języka XML i zawiera opcje umożliwiające określenie kodowania znaków oraz wersji protokołu SOAP i WS-Addressing, która ma zostać użyta. Koder komunikatów binarnych koduje wiadomości Windows Communication Foundation (WCF) w postaci binarnej w sieci. Chociaż to kodowanie skutkuje bardzo szybką transmisją komunikatów, współpraca oparta na standardach protokołu WS-* zostanie utracona.  
  
## <a name="example"></a>Przykład  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [Kodowanie komunikatu](message-encoding.md)
- [Wybieranie kodera komunikatów](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
