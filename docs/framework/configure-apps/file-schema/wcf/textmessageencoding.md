---
title: '&lt;textMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 640cf8fce766f7107e297143e061f4f60d9f263d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753485"
---
# <a name="lttextmessageencodinggt"></a>&lt;textMessageEncoding&gt;
Określa kodowanie znaków i wiadomości versioning używany dla wiadomości tekstowych XML.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<textMessageEncoding >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|maxReadPoolSize|Liczba całkowita określająca ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników. Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy. Wartość domyślna to 64.|  
|maxWritePoolSize|Liczba całkowita określająca ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących. Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy. Wartość domyślna to 16.|  
|Element MessageVersion|Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania. Prawidłowe wartości to<br /><br /> -Soap11Addressing10<br />-Soap12Addressing10<br /><br /> Wartość domyślna to Soap12Addressing10. Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków. Prawidłowe wartości to<br /><br /> -UnicodeFffeTextEncoding: Kodowanie Unicode BigEndian<br />-Utf16TextEncoding: Kodowanie Unicode<br />-Utf8TextEncoding: 8-bitowego kodowania o<br /><br /> Wartość domyślna to Utf8TextEncoding. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Kodowanie jest procesem przekształcania komunikat do sekwencji bajtów. Dekodowanie jest procesu. Windows Communication Foundation (WCF) obejmuje trzy rodzaje kodowania protokołu SOAP wiadomości: tekst, dane binarne i mechanizmu optymalizacji transmisji wiadomości (MTOM).  
  
 Kodowanie tekstu reprezentowany przez `textMessageEncoding` element jest najbardziej współdziałanie, ale najmniej wydajne koder komunikatów XML.  Koder tekstu tworzy wiadomości tekstowych w sieci. Komunikaty generowane przez ten koder nadają się do usługi WS-* na podstawie interop. Klienta usługi sieci Web lub usługi sieci Web zwykle zrozumieć tekstowy XML. Jednak przesyłania dużych bloków danych binarnych jako tekst jest najmniej efektywną metodę kodowania komunikatów XML.  
  
## <a name="example"></a>Przykład  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [Wybieranie kodera komunikatów](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Kodowanie komunikatu](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
