---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 61b23957c56bad81598dd65b0dd68f7b44d329e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146799"
---
# <a name="mtommessageencoding"></a>\<mtomMessageEncoding>
Określa kodowanie i wersjonowanie wiadomości używanych dla wiadomości protokołu SOAP wiadomości transmisji optymalizacji mechanizm (MTOM) na podstawie.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<mtomMessageEncoding>  
  
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
|maxReadPoolSize|Liczba całkowita określająca ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników. Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy. Wartość domyślna to 64.|  
|maxWritePoolSize|Liczba całkowita określająca ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących. Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy. Wartość domyślna to 16.|  
|messageVersion|Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania. Prawidłowe wartości to:<br /><br /> -Soap11Addressing1<br />-Soap12Addressing10<br /><br /> Wartość domyślna to Soap12Addressing10. Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków. Prawidłowe wartości to:<br /><br /> -   UnicodeFffeTextEncoding: Unicode BigEndian z kodowaniem<br />-   Utf16TextEncoding: Kodowanie Unicode<br />-   Utf8TextEncoding: 8-bitowego kodowania<br /><br /> The default is Utf8TextEncoding. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Kodowanie jest procesem przekształcania wiadomość do sekwencji bajtów. Dekodowanie jest procesu. Windows Communication Foundation (WCF) obejmuje trzy typy kodowania dla protokołu SOAP wiadomości: Tekst pliku binarnego i mechanizmu optymalizacji transmisji wiadomości (MTOM).  
  
 `MtomMessageEncoding` Element określa znak kodowanie i wersjonowanie wiadomości i inne ustawienia, używany dla wiadomości przy użyciu kodowania komunikatu transmisji optymalizacji mechanizm (MTOM). MTOM to technologia wydajne przekazywania danych binarnych w wiadomościach WCF. Koder MTOM podejmuje próbę utworzenia równowagi między współdziałania i wydajność. Kodowanie MTOM przesyła większość kodu XML w postaci tekstowej, ale optymalizuje dużych bloków danych binarnych, przekazywania ich jako — jest bez konwersji do formatu ich zakodowane w formacie base64.  
  
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
- [Kodowanie komunikatu](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [Wybieranie kodera komunikatów](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
