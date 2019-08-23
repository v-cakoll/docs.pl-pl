---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 70a124fda5bc0e52e1271716f7e2166b7717b49a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933191"
---
# <a name="mtommessageencoding"></a>\<mtomMessageEncoding >
Określa kodowanie i przechowywanie wersji komunikatów na podstawie komunikatów opartych na mechanizmie optymalizacji transmisji wiadomości (MTOM) protokołu SOAP.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<mtomMessageEncoding >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|maxBufferSize|Liczba całkowita określająca maksymalny rozmiar buforu, który może być używany.|  
|maxReadPoolSize|Liczba całkowita, która określa, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników. Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym. Wartość domyślna to 64.|  
|maxWritePoolSize|Liczba całkowita określająca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących. Większe rozmiary puli sprawiają, że system jest bardziej odporny na obciążenia, a koszt większym zestawem roboczym. Wartość domyślna to 16.|  
|Element MessageVersion|Określa wersję SOAP komunikatów wysyłanych za pomocą powiązania. Prawidłowe wartości to<br /><br /> - Soap11Addressing1<br />- Soap12Addressing10<br /><br /> Wartość domyślna to Soap12Addressing10. Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Określa kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu. Prawidłowe wartości to<br /><br /> - UnicodeFffeTextEncoding: Kodowanie Unicode BigEndian<br />- Utf16TextEncoding: Kodowanie Unicode<br />-   Utf8TextEncoding: kodowanie 8-bitowe<br /><br /> Wartość domyślna to Utf8TextEncoding. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
  
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
  
 `MtomMessageEncoding` Element określa kodowanie znaków i przechowywanie wersji komunikatów oraz inne ustawienia używane w przypadku komunikatów przy użyciu kodowania mechanizmu optymalizacji transmisji komunikatów (MTOM). MTOM to wydajna technologia przesyłania danych binarnych w komunikatach programu WCF. Koder MTOM próbuje utworzyć balans między wydajnością i współdziałaniem. Kodowanie MTOM przesyła większość kodu XML w postaci tekstowej, ale optymalizuje duże bloki danych binarnych przez przesłanie ich jako-is, bez konwersji do formatu zakodowanego algorytmem Base64.  
  
## <a name="example"></a>Przykład  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [Kodowanie komunikatu](message-encoding.md)
- [Wybieranie kodera komunikatów](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
